---
title: ClickOnce 配置 API を使用して必要に応じてアセンブリをダウンロードする
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f52d853399bb568407b5022dca7f6288e3901a7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "66262900"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>チュートリアル: ClickOnce 配置 API を使用して必要に応じてアセンブリをダウンロードする
既定では、アプリケーションに含まれるすべてのアセンブリ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、アプリケーションの初回実行時にダウンロードされます。 ただし、少数のユーザーによって使用されるアプリケーションの一部を使用することもできます。 その場合は、そのような型を作成するときにだけアセンブリをダウンロードすることができます。 以下のチュートリアルでは、アプリケーション内の特定のアセンブリに "オプション" マークを付ける方法、および共通言語ランタイム (CLR) でそのアセンブリが必要なときに <xref:System.Deployment.Application> 名前空間にあるクラスを使用してアセンブリをダウンロードする方法について説明します。

> [!NOTE]
> これを行うには、アプリケーションが完全な信頼で実行する必要があります。

## <a name="prerequisites"></a>前提条件
 このチュートリアルを完了するには、次のコンポーネントのいずれかが必要です。

- Windows SDK。 Windows SDK は、Microsoft ダウンロードセンターからダウンロードできます。

- 見ることができます。

## <a name="create-the-projects"></a>プロジェクトを作成する

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>オンデマンドアセンブリを使用するプロジェクトを作成するには

1. Click、Ondemand という名前のディレクトリを作成します。

2. Windows SDK コマンドプロンプトまたは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コマンドプロンプトを開きます。

3. Clickondemand のディレクトリに移動します。

4. 次のコマンドを使用して、公開キーと秘密キーのペアを生成します。

   ```cmd
   sn -k TestKey.snk
   ```

5. メモ帳などのテキストエディターを使用して、という名前の1つのプロパティを持つという名前のクラスを定義し `DynamicClass` `Message` ます。

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. テキストを ClickOnceLibrary.cs という名前のファイルとして保存*するか、* 使用している言語に応じて [ *click* *] ディレクトリに*クリックします。

7. ファイルをアセンブリにコンパイルします。

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. アセンブリの公開キートークンを取得するには、次のコマンドを使用します。

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. テキストエディターを使用して新しいファイルを作成し、次のコードを入力します。 このコードでは、必要に応じて Clicklibrary アセンブリをダウンロードする Windows フォームアプリケーションを作成します。

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. コードで、への呼び出しを見つけ <xref:System.Reflection.Assembly.LoadFile%2A> ます。

11. は、前の手順で取得した `PublicKeyToken` 値に設定されます。

12. ファイルを *Form1.cs* または *form1.vb*として保存します。

13. 次のコマンドを使用して、実行可能ファイルにコンパイルします。

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>アセンブリをオプションとしてマークする

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe を使用して ClickOnce アプリケーションでアセンブリをオプションとしてマークするには

1. *MageUI.exe*を使用して、「[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」の説明に従って、アプリケーションマニフェストを作成します。 アプリケーションマニフェストには、次の設定を使用します。

    - アプリケーションマニフェストに名前を指定 `ClickOnceOnDemand` します。

    - [ **ファイル** ] ページの [ *ClickOnceLibrary.dll* ] 行で、[ **ファイルの種類** ] 列を **[なし**] に設定します。

    - [ **ファイル** ] ページの [ *ClickOnceLibrary.dll* ] 行で、[ `ClickOnceLibrary.dll` **グループ]** 列に「」と入力します。

2. *MageUI.exe*を使用して、「[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」の説明に従って配置マニフェストを作成します。 配置マニフェストには、次の設定を使用します。

    - 配置マニフェストに名前を指定 `ClickOnceOnDemand` します。

## <a name="testing-the-new-assembly"></a>新しいアセンブリをテストする

#### <a name="to-test-your-on-demand-assembly"></a>オンデマンド アセンブリをテストするには

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Web サーバーに配置をアップロードします。

2. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェストの URL を入力して、Web ブラウザーからでデプロイされたアプリケーションを起動します。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション `ClickOnceOnDemand` を呼び出し、adatum.com のルートディレクトリにアップロードすると、URL は次のようになります。

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. メイン フォームが表示されたら、 <xref:System.Windows.Forms.Button>をクリックします。 メッセージ ボックス ウィンドウに "Hello, World!" という文字列が表示されます。

## <a name="see-also"></a>関連項目
- <xref:System.Deployment.Application.ApplicationDeployment>