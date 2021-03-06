---
title: 'チュートリアル: C++ を使用した SDK の作成 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15fa0714097efda31b52f1d389d3a26cf581e506
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905010"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>チュートリアル: C++ を使用して SDK を作成する
このチュートリアルでは、ネイティブ C++ math library SDK を作成し、SDK を Visual Studio 拡張機能 (VSIX) としてパッケージ化して、それを使用してアプリを作成する方法について説明します。 このチュートリアルは、次の手順に分かれています。

- [ネイティブライブラリと Windows ランタイムライブラリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Nativem、Vsix 拡張機能プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [クラスライブラリを使用するサンプルアプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>前提条件
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、「 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)」を参照してください。

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> ネイティブライブラリと Windows ランタイムライブラリを作成するには

1. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

2. テンプレートの一覧で**Visual C++**[  >  **Windows ユニバーサル**] を展開し、[ **DLL (windows ユニバーサルアプリ)** ] テンプレートを選択します。 [ **名前** ] ボックスにを指定し、[ `NativeMath` **OK** ] をクリックします。

3. 次のコードに一致するように *NativeMath* を更新します。

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. 次のコードに一致するように *NativeMath* を更新します。

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. **ソリューションエクスプローラー**で、**ソリューション ' NativeMath '** のショートカットメニューを開き、[新しいプロジェクトの**追加**] を選択し  >  **New Project**ます。

6. テンプレートの一覧で [ **Visual C++**] を展開し、[ **Windows ランタイムコンポーネント** ] テンプレートを選択します。 [ **名前** ] ボックスにを指定し、[ `NativeMathWRT` **OK** ] をクリックします。

7. 次のコードに一致するように *Class1* を更新します。

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. 次のコードに一致するように *Class1* を更新します。

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** の順にクリックします。

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Nativem、Vsix 拡張機能プロジェクトを作成するには

1. **ソリューションエクスプローラー**で、**ソリューション ' NativeMath '** のショートカットメニューを開き、[新しいプロジェクトの**追加**] を選択し  >  **New Project**ます。

2. テンプレートの一覧で、[ **Visual C#** の  >  **機能拡張**] を展開し、[ **VSIX プロジェクト**] を選択します。 [ **名前** ] ボックスに「 **Nativemthe vsix**」と入力し、[ **OK** ] をクリックします。

3. **ソリューションエクスプローラー**で、 **source.extension.vsixmanifest**のショートカットメニューを開き、[**コードの表示**] を選択します。

4. 次の XML を使用して、既存の XML を置き換えます。

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. **ソリューションエクスプローラー**で、 **nativem、vsix**プロジェクトのショートカットメニューを開き、[新しい項目の**追加**] を選択し  >  **New Item**ます。

6. **Visual C# の項目**の一覧で、[**データ**] を展開し、[ **XML ファイル**] を選択します。 [ **名前** ] ボックスにを指定し、[ `SDKManifest.xml` **OK** ] をクリックします。

7. ファイルの内容を置き換えるには、次の XML を使用します。

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. **ソリューションエクスプローラー**の [ **Nativem] vsix**プロジェクトで、次のフォルダー構造を作成します。

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. **ソリューションエクスプローラー**で、**ソリューション ' NativeMath '** のショートカットメニューを開き、[**エクスプローラーでフォルダーを開く**] を選択します。

10. **ファイルエクスプローラー**で *$SolutionRoot $ \NativeMath\NativeMath.h*をコピーし、**ソリューションエクスプローラー**で、[ **nativem** ] プロジェクトの下の [ *$SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include \\ * ] フォルダーに貼り付けます。

     *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib*をコピーし、 * \\ $SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86*フォルダーに貼り付けます。

     *$\Debug\NativeMath\NativeMath.dll$SolutionRoot*コピーし、 * \\ $SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86*フォルダーに貼り付けます。

     *$\Debug\NativeMathWRT\NativeMathWRT.dll$SolutionRoot*コピーし、 *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86*フォルダーに貼り付けます。
     *$ \Debug\NativeMathWRT\NativeMathWRT.winmd $SolutionRoot*コピーし、 *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral*フォルダーに貼り付けます。

     *$ \Debug\NativeMathWRT\NativeMathWRT.pri $SolutionRoot*コピーし、 *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral*フォルダーに貼り付けます。

11. *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\ *フォルダーに、 *nativem*という名前のテキストファイルを作成し、次の内容を貼り付けます。

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. メニューバーで、[ **View**  >  **他のウィンドウの**プロパティウィンドウを表示] を選択し  >  **Properties Window**ます (キーボード: **F4**キーを押します)。

13. **ソリューションエクスプローラー**で、 **NativeMathWRT**ファイルを選択します。 [ **プロパティ** ] ウィンドウで、" **ビルドアクション** " プロパティを " **コンテンツ**" に変更し、[ **VSIX に含める** ] プロパティを [ **True**] に変更します。

     **NativeMath**ファイルに対してこのプロセスを繰り返します。

     **NativeMathWRT**ファイルに対してこのプロセスを繰り返します。

     **NativeMath**ファイルに対してこのプロセスを繰り返します。

     このプロセスを **Nativemthe** のプロパティのプロパティに対して繰り返します。

14. **ソリューションエクスプローラー**で、 **NativeMath**ファイルを選択します。 [ **プロパティ** ] ウィンドウで、[ **VSIX に含める** ] プロパティを [ **True**] に変更します。

     **NativeMath.dll**ファイルに対してこの手順を繰り返します。

     **NativeMathWRT.dll**ファイルに対してこの手順を繰り返します。

     **SDKManifest.xml**ファイルに対してこの手順を繰り返します。

15. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** の順にクリックします。

16. **ソリューションエクスプローラー**で、 **Nativem、vsix**プロジェクトのショートカットメニューを開き、[**エクスプローラーでフォルダーを開く**] を選択します。

17. **エクスプローラー**で、 *$SolutionRoot $ \NativeMathVSIX\bin\Debug*フォルダーに移動し、次に*nativemの*vsix を実行してインストールを開始します。

18. [ **インストール** ] ボタンをクリックし、インストールが完了するのを待ってから、Visual Studio を開きます。

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> クラスライブラリを使用するサンプルアプリを作成するには

1. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

2. テンプレートの一覧で、[ **Visual C++** Windows ユニバーサル] を展開し、  >  **Windows Universal** [**空のアプリ**] を選択します。 [ **名前** ] ボックスに **NativeMathSDKSample**を指定し、[ **OK** ] をクリックします。

3. **ソリューションエクスプローラー**で、 **NativeMathSDKSample**プロジェクトのショートカットメニューを開き、[参照の**追加**] を選択し  >  **Reference**ます。

4. [ **参照の追加** ] ダイアログボックスの [参照の種類] の一覧で、[ **ユニバーサル Windows**] を展開し、[ **拡張機能**] を選択します。 最後に、[ **Native MATH SDK** ] チェックボックスをオンにし、[ **OK** ] をクリックします。

5. NativeMathSDKSample のプロジェクトプロパティを表示します。

    参照を追加したときに、 *Nativemに* 定義したプロパティが適用されました。 プロジェクトの**構成プロパティ**の [ **VC + + ディレクトリ**] プロパティを調べることで、プロパティが適用されたことを確認できます。

6. **ソリューションエクスプローラー**で**mainpage.xaml**を開き、次の xaml を使用してそのコンテンツを置き換えます。

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. 次のコードに一致するように *mainpage.xaml* を更新します。

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. 次のコードに一致するように *mainpage.xaml* を更新します。

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. F5 キーを **押し** てアプリを実行します。

10. アプリで、任意の2つの数値を入力し、操作を選択して、ボタンをクリックし **=** ます。

     正しい結果が表示されます。

    このチュートリアルでは、拡張 SDK を作成して使用し、 [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] ライブラリと以外のライブラリを呼び出す方法について説明しました [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] 。

## <a name="next-steps"></a>次のステップ

## <a name="see-also"></a>関連項目
- [チュートリアル: C# または Visual Basic を使用した SDK の作成](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [ソフトウェア開発キットを作成する](../extensibility/creating-a-software-development-kit.md)
