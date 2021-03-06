---
title: 'チュートリアル: QuickInfo ツールヒントの表示 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 0eb70e5d39708ffd532fe39d6d597043621158d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904823"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>チュートリアル: QuickInfo ツールヒントの表示
QuickInfo は、ユーザーがメソッド名の上にポインターを移動したときに、メソッドのシグネチャと説明を表示する IntelliSense 機能です。 Quickinfo などの言語ベースの機能を実装するには、QuickInfo の説明を提供する識別子を定義した後、コンテンツを表示するためのツールヒントを作成します。 言語サービスのコンテキストで QuickInfo を定義することも、独自のファイル名の拡張子とコンテンツの種類を定義し、その種類のクイックヒントを表示することもできます。または、既存のコンテンツの種類 ("text" など) の QuickInfo を表示することもできます。 このチュートリアルでは、"text" コンテンツタイプの QuickInfo を表示する方法について説明します。

 このチュートリアルの QuickInfo の例では、ユーザーがポインターをメソッド名の上に移動したときにツールヒントを表示します。 この設計では、次の4つのインターフェイスを実装する必要があります。

- ソースインターフェイス

- ソースプロバイダーインターフェイス

- コントローラーインターフェイス

- コントローラープロバイダーインターフェイス

  ソースプロバイダーとコントローラープロバイダーは、Managed Extensibility Framework (MEF) コンポーネントのパーツであり、ソースとコントローラーのクラスのエクスポートと、ツールヒントテキストバッファーを作成するなどのサービスおよびブローカーのインポート、 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> および QuickInfo セッションを開始するの役割を担い <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> ます。

  この例では、QuickInfo ソースはメソッド名と説明のハードコーディングされたリストを使用しますが、完全な実装では、言語サービスと言語ドキュメントがそのコンテンツを提供する役割を担います。

## <a name="prerequisites"></a>前提条件
 Visual Studio 2015 以降では、ダウンロードセンターから Visual Studio SDK をインストールする必要はありません。 これは、Visual Studio セットアップでオプション機能として含まれています。 VS SDK は、後でインストールすることもできます。 詳細については、「 [Visual STUDIO SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。

## <a name="create-a-mef-project"></a>MEF プロジェクトを作成する

### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには

1. C# VSIX プロジェクトを作成します。 ([ **新しいプロジェクト** ] ダイアログで、[Visual C#]、[ **拡張機能**]、[ **VSIX プロジェクト**] の順に選択します)。ソリューションにという名前を指定 `QuickInfoTest` します。

2. エディター分類子項目テンプレートをプロジェクトに追加します。 詳細については、「 [エディター項目テンプレートを使用して拡張機能を作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)する」を参照してください。

3. 既存のクラス ファイルを削除します。

## <a name="implement-the-quickinfo-source"></a>QuickInfo ソースを実装する
 QuickInfo ソースは、識別子とその説明のセットを収集し、いずれかの識別子が検出されたときに、ツールヒントテキストバッファーにコンテンツを追加します。 この例では、識別子とその説明がソースコンストラクターに追加されています。

#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo ソースを実装するには

1. クラス ファイルを追加し、その名前を `TestQuickInfoSource`にします。

2. *VisualStudio*への参照を追加します。

3. 次のインポートを追加します。

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. を実装するクラスを宣言 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> し、という名前を指定 `TestQuickInfoSource` します。

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. QuickInfo ソースプロバイダー、テキストバッファー、および一連のメソッド名とメソッドシグネチャのフィールドを追加します。 この例では、メソッド名とシグネチャがコンストラクターで初期化され `TestQuickInfoSource` ます。

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. QuickInfo ソースプロバイダーとテキストバッファーを設定するコンストラクターを追加し、メソッド名、メソッドのシグネチャ、および説明を設定します。

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> メソッドを実装します。 この例では、メソッドは、現在の単語を検索します。カーソルが行またはテキストバッファーの末尾にある場合は、前の単語を検索します。 Word がメソッド名の1つである場合、そのメソッド名の説明は QuickInfo コンテンツに追加されます。

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. でを実装するため、Dispose () メソッドも実装する必要があり <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable> ます。

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>QuickInfo ソースプロバイダーを実装する
 QuickInfo ソースのプロバイダーは、主に MEF コンポーネントパーツとしてエクスポートし、QuickInfo ソースをインスタンス化します。 MEF コンポーネント部分であるため、他の MEF コンポーネントパーツをインポートできます。

#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo ソースプロバイダーを実装するには

1. を実装するという名前の QuickInfo ソースプロバイダーを宣言 `TestQuickInfoSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> し、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip quickinfo Source"、 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default"、および "text" のを使用してエクスポートし <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ます。

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. 2つのエディターサービス ( <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> と <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> ) をのプロパティとしてインポートし `TestQuickInfoSourceProvider` ます。

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. を実装して <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> 、新しいを返し `TestQuickInfoSource` ます。

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>QuickInfo コントローラーを実装する
 Quickinfo コントローラーは、QuickInfo がいつ表示されるかを決定します。 この例では、メソッド名のいずれかに対応する単語の上にポインターを置いたときに、QuickInfo と表示されます。 QuickInfo コントローラーは、QuickInfo セッションをトリガーするマウスホバーイベントハンドラーを実装します。

### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo コントローラーを実装するには

1. を実装するクラスを宣言 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> し、という名前を指定 `TestQuickInfoController` します。

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. テキストビューのプライベートフィールド、テキストビューで表されるテキストバッファー、QuickInfo セッション、および QuickInfo コントローラープロバイダーを追加します。

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. フィールドを設定し、マウスのホバーイベントハンドラーを追加するコンストラクターを追加します。

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. QuickInfo セッションを開始するマウスホバーイベントハンドラーを追加します。

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>コントロールがテキストビューからデタッチされたときにマウスホバーイベントハンドラーが削除されるように、メソッドを実装します。

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>この例では、メソッドと <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> メソッドを空のメソッドとして実装します。

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo コントローラープロバイダーの実装
 QuickInfo コントローラーのプロバイダーは、主に MEF コンポーネントパーツとしてエクスポートし、QuickInfo コントローラーをインスタンス化します。 MEF コンポーネント部分であるため、他の MEF コンポーネントパーツをインポートできます。

### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo コントローラープロバイダーを実装するには

1. を実装するという名前のクラスを宣言 `TestQuickInfoControllerProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> し、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip quickinfo Controller" と "text" のを使用してエクスポートし <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ます。

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> をプロパティとしてインポートします。

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. QuickInfo コントローラーをインスタンス化して、メソッドを実装し <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> ます。

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>コードをビルドしてテストする
 このコードをテストするには、QuickInfoTest ソリューションをビルドし、実験用インスタンスで実行します。

### <a name="to-build-and-test-the-quickinfotest-solution"></a>QuickInfoTest ソリューションをビルドしてテストするには

1. ソリューションをビルドします。

2. デバッガーでこのプロジェクトを実行すると、Visual Studio の2番目のインスタンスが開始されます。

3. テキストファイルを作成し、"add" と "減算" という単語を含むテキストを入力します。

4. "Add" のいずれかの位置にポインターを移動します。 メソッドの署名と説明が `add` 表示されます。

## <a name="see-also"></a>関連項目
- [チュートリアル: コンテンツの種類をファイル名拡張子にリンクする](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
