---
title: コード化された UI テスト エディターを使用したコード化された UI テストの編集 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c070f1bafb157e3979eb9c1f49b317b17807f1e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "82587001"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>コード化された UI テスト エディターを使用したコード化された UI テストの編集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コード化された UI テスト エディターを使用すると、コード化された UI テストを簡単に変更できます。 コード化された UI テスト エディターを使用して、テスト メソッドや UI 操作のプロパティを検索、表示、および編集できます。 また、対応するコントロールを表示および編集するための UI コントロール マップを使用できます。

 **必要条件**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>この操作を行う理由
 コード化された UI テスト エディターを使用することは、コード化された UI テスト メソッドのコードをコード エディターを使用して編集するよりも効率的です。 コード化された UI テスト エディターでは、ツール バーとショートカット メニューを使用して、UI 操作とコントロールに関連付けられているプロパティ値をすばやく検出して修正することができます。 たとえば、コード化された UI テスト エディターのツール バーを使用して、次のコマンドを実行できます。

 ![UI テスト エディター](../test/media/uitesteditor.png "UITestEditor")

1. [検索](../ide/finding-and-replacing-text.md) : UI 操作とコントロールを見つけることができます。

2. [削除](#CodedUITestEditor_DeleteUIActions) : 不要な UI 操作を削除します。

3. **名前の変更** : テスト メソッドとコントロールの名前を変更します。

4. **プロパティ** : 選択した項目のプロパティ ウィンドウが開きます。

5. [新しいメソッドに分割](#CodedUITestEditor_SplitMethods) : UI 操作をモジュール化できます。

6. [コードの移動](#CodedUITestEditor_MoveMethods) : テスト メソッドにカスタム コードを追加します。

7. [前に遅延を挿入](#CodedUITestEditor_InsertDelay) : ミリ秒単位で指定された UI 操作の前に一時停止を追加します。

8. [UI コントロールの検索](#CodedUITestEditor_LocateUIControl) : テスト対象のアプリケーションの UI におけるコントロールの位置を特定します。

9. [[すべて検索](#CodedUITestEditor_LocateDecendants)] は、コントロールのプロパティと、アプリケーションのコントロールに対する重要な変更を確認するのに役立ちます。

## <a name="how-do-i-do-this"></a>それを実現する方法を教えてください。
 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]では、コード化された UI テスト プロジェクトのコード化された UI テストと結合した UIMap.uitest ファイルを開くと、コード化された UI テストがコード化された UI テスト エディターに自動的に表示されます。 次の手順では、エディターのツール バーとショートカット メニューを使用してテスト メソッド、UI 操作のプロパティ、コントロールを検索および編集する方法について説明します。

## <a name="open-a-coded-ui-test"></a>コード化された UI テストを開く
 コード化された UI テスト エディターを使用して、Visual C# および Visual Basic ベースのコード化された UI テストを表示および編集できます。

 ![コード化された UI テスト ビルダーを使用したコンテキスト メニューの編集](../test/media/editcodeduitest.png "EditCodedUITest")

 ソリューションエクスプローラーで、 **uitest** のショートカットメニューを開き、[ **開く**] を選択します。 コード化された UI テスト エディターに、コード化された UI テストが表示されます。 これで、コード化された UI テストの記録されたメソッド、操作、および対応するコントロールを表示および編集できるようになります。

> [!TIP]
> **[UI 操作]** ウィンドウでメソッド内にある UI 操作を選択すると、対応するコントロールが強調表示されます。 UI 操作またはコントロール プロパティも変更できます。

 コード化された UI テスト エディターが*表示されません* 。
Visual Studio Enterprise の 2012 よりも前のバージョンを使用している可能性があります。 コード化された UI テスト エディターは、MSDN サブスクリプションを備えた Visual Studio 2010 Feature Pack 2 でも使用できます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)]「[Microsoft Visual Studio 2010 Feature Pack 2](https://msdn.microsoft.com/library/gg269474.aspx)」を参照してください。

## <a name="modify-ui-action-properties-and-their-corresponding-control-properties"></a><a name="CodedUITestEditor_EditActionAndControlProperties"></a>UI 操作プロパティとそれに対応するコントロールのプロパティを変更する
 コード化された UI テスト エディターを使用すると、テスト メソッドですべての UI 操作をすばやく検索および表示できます。 エディターで UI 操作を選択すると、対応するコントロールが自動的に強調表示されます。 同様に、コントロールを選択すると、関連付けられた UI 操作が強調表示されます。 UI 操作またはコントロールを選択すると、[プロパティ] ウィンドウを使用して対応するプロパティを変更することが容易になります。

 ![UI 操作のプロパティ](../test/media/codeduiedituiaction.png "CodedUIEditUIAction") UI 操作のプロパティの編集

 UI 操作のプロパティを **[UI 操作]** ウィンドウで変更する場合は、プロパティを編集する対象の UI 操作を含むテスト メソッドを展開し、UI 操作を選択してから [プロパティ] ウィンドウを使用してプロパティを変更します。

 たとえば、サーバーが使用できない状態で、web**ページ <http://Contoso1/default.aspx’> に移動**することを示す UI 操作が web ブラウザーに関連付けられている場合は、URL をに変更でき `‘http://Contoso2/default.aspx’` ます。

 ![コントロールのプロパティ](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp") コントロールプロパティの編集

 コントロールのプロパティの変更は、UI 操作のプロパティの場合と同じ方法で実行します。 **[UI コントロール マップ]** ウィンドウで、編集するコントロールを選択し、 [プロパティ] ウィンドウを使用してプロパティを変更します。

 たとえば、開発者が "idSubmit" から "Idsubmit" にテストされるアプリケーションのソースコードで、ボタンコントロールの **(ID)** プロパティを変更したとします。 アプリケーションで **(ID)** プロパティを変更すると、コード化された UI テストでボタン コントロールを検索できずに失敗します。 この場合、テスト担当者は、 **[検索プロパティ]** コレクションを開き、開発者がアプリケーションで使用した新しい値に合わせて **Id** プロパティを変更できます。 テスト担当者は、[ **フレンドリ名** ] プロパティの値を "Submit" から "Login" に変更することもできます。 この変更を実行すると、コード化された UI テスト エディターでの関連付けられた UI 操作が "'Submit' ボタンをクリック" から "'Login' ボタンをクリック" に更新されます。

 変更が完了したら、 **ツール バーの** [保存] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] をクリックすることで、UIMap.Designer ファイルに変更を保存します。

 *その他に知っておく必要があること*
 **テクニック**

- ![ヒント](../test/media/tip.png "ヒント") プロパティウィンドウが表示されない場合は、 **Alt** キーを押したまま **enter キーを押すか**、または **F4**キーを押します。

- ![ヒント](../test/media/tip.png "ヒント")プロパティの変更を元に戻すには、[**編集**] メニューの [**元に戻す**] を選択するか、Ctrl キーを押しながら Z キーを押します。

- ![ヒント](../test/media/tip.png "ヒント") コード化された UI テストエディターのツールバーにある [ **検索** ] ボタンを使用すると、Visual Studio の検索と置換ツールを開くことができます。 そうすれば、検索コントロールを使用して、コード化された UI テスト エディターで UI 操作を検索できます。 たとえば、"'Login' ボタンをクリック" を検索できます。 これは、大規模なテストの場合に便利です。 コード化された UI テスト エディターでは検索と置換ツールの置換機能を使用できないことに注意してください。 詳細については、「 [Finding and Replacing Text](../ide/finding-and-replacing-text.md)」の「検索コントロール」を参照してください。

- ![ヒント](../test/media/tip.png "ヒント") 場合によっては、テスト対象のアプリケーションの UI にコントロールが配置されている場所を視覚化することが困難になることがあります。 コード化された UI テスト エディターの機能の 1 つとして、UI コントロール マップに一覧表示されているコントロールを選択し、テスト対象のアプリケーションにおけるそのコントロールの位置を表示することができます。 [!INCLUDE[crdefault](../includes/crdefault-md.md)]「[テスト対象のアプリケーションで UI コントロールを検索する](#CodedUITestEditor_LocateUIControl)」(このトピックの後の方) を参照してください。

- ![ヒント](../test/media/tip.png "ヒント") 編集するコントロールを含むコンテナーコントロールを展開する必要がある場合があります。 [!INCLUDE[crdefault](../includes/crdefault-md.md)]「[コントロールとその子孫を検索する](#CodedUITestEditor_LocateDecendants)」(このトピックの後の方) を参照してください。

## <a name="delete-unwanted-ui-actions"></a><a name="CodedUITestEditor_DeleteUIActions"></a> 不要な UI 操作を削除する
 コード化された UI テストの不要な UI 操作を簡単に削除できます。

 ![UI アクションの削除](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")

 **[UI 操作]** ウィンドウで、削除する UI 操作を含むテスト メソッドを展開します。 UI 操作のショートカット メニューを開き、 **[削除]** をクリックします。

## <a name="split-a-test-method-into-two-separate-methods"></a><a name="CodedUITestEditor_SplitMethods"></a> テストメソッドを2つの異なるメソッドに分割する
 テスト メソッドを分割し、UI 操作を調整またはモジュール化することができます。 たとえば、テストには 2 個のコンテナー コントロールの UI 操作を含む単一のテスト メソッドが存在する場合があります。 UI 操作は、1 個のコンテナーで対応する 2 種類のメソッドにおいてより適切にモジュール化される可能性があります。

 ![テスト メソッドの分割](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")

 ![2 つのテスト メソッド](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")

 **[UI 操作]** ウィンドウで、2 種類の異なるメソッドに分割するテスト メソッドを展開し、新しいテスト メソッドを開始する UI 操作を選択します。 UI 操作のショートカット メニューを開いて **[新しいメソッドに分割]** をクリックするか、コード化された UI テスト エディターのツール バーにある **[新しいメソッドに分割]** をクリックします。 新しいテスト メソッドが [UI 操作] ウィンドウに表示されます。 これには、分割を指定したアクションを先頭とする UI 操作が含まれています。

 メソッドの分割が完了したら、 **ツール バーの** [保存] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] をクリックし、UIMap.Designer ファイルに変更を保存します。

 *その他に知っておく必要があること*
 **重要な問題**

- ![注意アイコン](../test/media/caution.gif "注意")**警告:** メソッドを分割する場合は、既存のメソッドを呼び出すすべてのコードを変更して、作成しようとしている新しいメソッドを呼び出すようにする必要があります (UI 操作が含まれている場合)。 メソッドを分割すると、Microsoft Visual Studio のダイアログ ボックスが表示されます。 既存のメソッドを呼び出すコードを変更し、作成しようとしている新しいメソッドも呼び出すコードにする必要があることを示す警告が表示されます。 **[はい]** をクリックします。

  **ヒント**

- ![ヒント](../test/media/tip.png "ヒント")分割を元に戻すには、[**編集**] メニューの [**元に戻す**] をクリックするか、Ctrl キーを押しながら Z キーを押します。

- ![ヒント](../test/media/tip.png "ヒント") 新しいメソッドの名前を変更できます。 [UI 操作] ウィンドウでメソッドを選択し、コード化された UI テスト エディターのツール バーにある **[名前の変更]** をクリックします。

   \- または -

   新しいテスト メソッドのショートカット メニューを開き、 **[名前の変更]** をクリックします。

   Microsoft Visual Studio のダイアログ ボックスが表示されます。 メソッドを参照しているコードを変更する必要があることを示す警告が表示されます。 **[はい]** をクリックします。

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a><a name="CodedUITestEditor_MoveMethods"></a> カスタマイズを容易にするためにテストメソッドを UIMap ファイルに移動する
 コード化された UI テストのテスト メソッドにカスタム コードが必要であることが判明した場合は、そのテスト メソッドを UIMap.cs ファイルまたは UIMap.vb ファイルに移動する必要があります。 それ以外の場合、コード化された UI テストが再コンパイルされるたびにコードが上書きされます。 メソッドを移動しない場合は、テストが再コンパイルするたびにカスタム コードが上書きされます。

 [ **UI 操作** ] ウィンドウで、テストコードの再コンパイル時に上書きされないカスタムコード機能を容易にするために、UIMap.cs ファイルまたは uimap .vb ファイルに移動するテストメソッドを選択します。 次に、コード化された UI テスト エディターのツール バーにある **[コードの移動]** をクリックするか、テスト メソッドのショートカット メニューを開いて **[コードの移動]** をクリックします。 テスト メソッドが UIMap.uitest ファイルから削除され、[UI Actions] (UI 操作) ペインに表示されなくなります。 移動したテスト ファイルを編集するには、ソリューション エクスプローラーから UIMap.cs ファイルまたは UIMap.vb ファイルを開きます。

 メソッドの移動が完了したら、 **ツール バーの** [保存] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] をクリックし、UIMap.Designer ファイルに変更を保存します。

 *その他に知っておく必要があること*
 **重要な問題**

- 警告![アイコン](../test/media/caution.gif "注意")**警告:** メソッドを移動すると、コード化された UI テストエディターを使用してそのメソッドを編集できなくなります。 カスタム コードを追加し、コード エディターを使って管理する必要があります。 メソッドを移動すると、Microsoft Visual Studio のダイアログ ボックスが表示されます。 メソッドが UIMap.uitest ファイルから UIMap.cs ファイルまたは UIMap.vb ファイルに移動すること、およびコード化された UI テスト エディターを使用してメソッドを編集できなくなることを示す警告が表示されます。 **[はい]** をクリックします。

  **ヒント**

- ![ヒント](../test/media/tip.png "ヒント")移動を元に戻すには、[**編集**] メニューの [**元に戻す**] を選択するか、Ctrl キーを押しながら Z キーを押します。 ただし、その場合は UIMap.cs ファイルまたは UIMap.vb ファイルからコードを手動で削除する必要があります。

## <a name="locating-a-ui-control-in-the-application-under-test"></a><a name="CodedUITestEditor_LocateUIControl"></a> テスト対象のアプリケーションで UI コントロールを検索する
 テスト対象のアプリケーションの UI におけるコントロールの位置を表示するのが難しい場合があります。 コード化された UI テスト エディターの機能の 1 つとして、UI コントロール マップに一覧表示されているコントロールを選択し、テスト対象のアプリケーションにおけるそのコントロールの位置を表示することができます。 テスト対象のアプリケーションで **[UI コントロールの検索]** 機能を使用すると、コントロールに対して行った検索プロパティの変更を確認することもできます。

 ![UI コントロールの検索](../test/media/codeduilocatecontrol.png "CodedUILocateControl")

 ![テスト中のアプリケーションで検索されたコントロール](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")

 **[UI コントロール マップ]** ウィンドウで、テストに関連付けられたアプリケーション内で検索するコントロールを選択します。 次に、コントロールのショートカット メニューを開き、 **[UI コントロールの検索]** をクリックします。 テストされているアプリケーションでは、該当するコントロールは青色の枠線で示されます。

 *その他に知っておく必要があること*
 **重要な問題**

- ![注意アイコン](../test/media/caution.gif "注意")**警告:** UI コントロールを検索する前に、テストに関連付けられているアプリケーションが実行されていることを確認してください。

  **テクニック**

- ![ヒント](../test/media/tip.png "ヒント") または、[ **すべて検索** ] オプションを使用して、コンテナー内のすべてのコントロールが正しく配置されていることを確認できます。 このオプションについては、次のセクションで説明します。

## <a name="locating-a-control-and-its-descendants"></a><a name="CodedUITestEditor_LocateDecendants"></a> コントロールとその子孫を検索する
 コンテナーにあるすべてのコントロールをテスト対象のアプリケーションの UI に正しく配置できることを確認できます。 これは、コンテナーに対して行った検索プロパティの変更を確認するときに便利です。 さらに、テスト対象のアプリケーションの UI を大幅に変更した場合に、既存のコントロール検索プロパティが正しいことを確認できます。

 ![すべての下位コントロールを検索](../test/media/codeduilocateall.png "CodedUILocateAll")

 ![検出されたすべてのコントロール](../test/media/codeduilocateall2.png "CodedUILocateAll2")

 **[UI コントロール マップ]** ウィンドウで、すべての子孫を検索して表示する対象のコンテナー コントロールを選択します。 次に、コントロールのショートカット メニューを開き、 **[すべてを検索]** をクリックします。 コンテナー コントロールとそのすべての子孫のコントロールは、コード化された UI テスト エディターにおいて、緑色のチェック マークまたは赤色の X でマークされます。 これらのマークを見れば、テスト対象のアプリケーションでコントロールが正しく配置されているかどうかを確認できます。

 *その他に知っておく必要があること*
 **重要な問題**

- 警告![アイコン](../test/media/caution.gif "注意")**警告:** UI コントロールを検索する前に、テストに関連付けられているアプリケーションが実行されていることを確認してください。

## <a name="inserting-a-delay-before-a-ui-action"></a><a name="CodedUITestEditor_InsertDelay"></a> UI 操作の前に遅延を挿入する
 ウィンドウの表示やプログレス バーの非表示などの特定のイベントが発生するまでテストを待機させる必要がある場合があります。 コード化された UI テスト エディターを使用し、UI 操作の前に遅延を挿入することで、この処理を実行できます。 遅延する秒数を指定できます。

 ![UI アクションの前への遅延の挿入](../test/media/codeduidelay.png "Codeduide のレイアウト")

 ![5 秒間の遅延の追加](../test/media/codeduidealy2.png "CodedUIDealy2")

 **[UI 操作]** ウィンドウで、事前に遅延を挿入する対象の UI 操作を含むテスト メソッドを展開します。 UI 操作を選択します。 次に、UI 操作のショートカット メニューを開き、 **[前に遅延を挿入]** をクリックします。 選択した UI 操作の前に遅延が挿入されて強調表示され、"**操作間のユーザー遅延として 1 秒待機します**" というテキストが示されます。 [プロパティ] ウィンドウで、 **[遅延]** プロパティの値を目的のミリ秒数に変更します。

 遅延の挿入が完了したら、 **ツール バーの** [保存] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] をクリックすることで、UIMap.Designer ファイルに変更を保存します。

 *その他に知っておく必要があること*
 **ノート**

- ![Prerequsite](../test/media/prereq.png "前提条件") UI 操作の前に特定のコントロールを使用できるようにする必要がある場合は、適切な UITestControl. WaitForControlXXX () メソッドを使用して、テストメソッドにカスタムコードを追加することを検討してください。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][コード化された UI テストは、再生中に特定のイベントを待機](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)します。

  **テクニック**

- ![ヒント](../test/media/tip.png "ヒント") プロパティウィンドウが表示されない場合は、Alt キーを押したまま enter キーを押すか、F4 キーを押します。

## <a name="external-resources"></a>外部リソース

### <a name="guidance"></a>ガイダンス
 [Visual Studio 2012 を使用した継続的デリバリーのためのテスト – 第 2 章: 単体テスト: 内部のテスト](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="faq"></a>よく寄せられる質問
 [Coded UI Tests FAQ - 1 (コード化された UI テストの FAQ - 1)](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Coded UI Tests FAQ - 2 (コード化された UI テストの FAQ - 2)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>フォーラム
 [Visual Studio の UI オートメーションのテスト (CodedUI を含む)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>参照
 [Ui オートメーションを使用してコードをテストするコード](../test/use-ui-automation-to-test-your-code.md)[化](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)された Ui テストを作成する[データドリブン](../test/creating-a-data-driven-coded-ui-test.md)のコード化された ui テストを作成する[既存の操作の記録からコード化された Ui テストを生成](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)する[チュートリアル: コード化された ui テストの作成、編集、および保守](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
