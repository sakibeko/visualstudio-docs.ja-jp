---
title: ツールバーの追加 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de74961715a82dde4e184509094d05145ad0f79c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184867"
---
# <a name="adding-a-toolbar"></a>ツール バーの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、Visual Studio IDE にツールバーを追加する方法について説明します。  
  
 ツールバーは、コマンドにバインドされているボタンを含む、水平または垂直のストリップです。 実装によっては、IDE のツールバーを再配置したり、メイン IDE ウィンドウの任意の辺にドッキングしたり、他のウィンドウの手前に表示したりすることができます。  
  
 さらに、ユーザーはツールバーにコマンドを追加したり、[ **カスタマイズ** ] ダイアログボックスを使用してコマンドを削除したりできます。 通常、Vspackage のツールバーはユーザーがカスタマイズできます。 IDE はすべてのカスタマイズを処理し、VSPackage はコマンドに応答します。 VSPackage は、コマンドが物理的に配置されている場所を知る必要はありません。  
  
 メニューの詳細については、「 [コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 Visual Studio 2015 以降では、ダウンロードセンターから Visual Studio SDK をインストールしません。 これは、Visual Studio セットアップでオプション機能として含まれています。 VS SDK は、後でインストールすることもできます。 詳細については、「 [Visual STUDIO SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## <a name="creating-an-extension-with-a-toolbar"></a>ツールバーを使用した拡張機能の作成  
 という名前の VSIX プロジェクトを作成 `IDEToolbar` します。 **Toolbartestcommand**という名前のメニューコマンド項目テンプレートを追加します。 これを行う方法の詳細については、「 [メニューコマンドを使用した拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
## <a name="creating-a-toolbar-for-the-ide"></a>IDE 用のツールバーの作成  
  
1. ToolbarTestCommandPackage. vsct で、[シンボル] セクションを探します。 Guidtoolbartestcommand/Mdset という GuidSymbol 要素で、次のようにツールバーとツールバーグループの宣言を追加します。  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2. [コマンド] セクションの上部で、[メニュー] セクションを作成します。 メニュー要素をメニューセクションに追加して、ツールバーを定義します。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     ツールバーは、サブメニューのように入れ子にすることはできません。 したがって、親グループを割り当てる必要はありません。 また、ユーザーはツールバーを移動できるため、優先度を設定する必要はありません。 通常、ツールバーの最初の配置はプログラムによって定義されますが、ユーザーによるその後の変更は保持されます。  
  
3. [ [グループ](../extensibility/groups-element.md) ] セクションで、既存のグループエントリの後に、ツールバーのコマンドを含む [グループ](../extensibility/group-element.md) 要素を定義します。  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4. ツールバーにボタンを表示します。 [ボタン] セクションで、ボタンの親ブロックをツールバーに置き換えます。 結果のボタンブロックは次のようになります。  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     既定では、ツールバーにコマンドがない場合、ツールバーは表示されません。  
  
5. プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
6. Visual Studio のメニューバーを右クリックすると、ツールバーの一覧が表示されます。 **テストツールバー**を選択します。  
  
7. ツールバーが [フォルダーを指定して検索] アイコンの右側にアイコンとして表示されます。 アイコンをクリックすると、[Toolbartestcommandpackage] というメッセージボックスが表示さ **れます。Ide ツールバー内で、ToolbarTestCommand. MenuItemCallback ()** を実行します。  
  
## <a name="see-also"></a>参照  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)
