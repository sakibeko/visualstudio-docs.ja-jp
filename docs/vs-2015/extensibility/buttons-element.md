---
title: Buttons 要素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8e0a17e3580b238c63a23e5943e98afbbb9268b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184551"
---
# <a name="buttons-element"></a>Buttons 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

個々のコマンドを表すグループ [ボタン](../extensibility/button-element.md) 要素。  
  
## <a name="syntax"></a>構文  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|条件|省略可能。 「 [条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)|グループボタン要素。|  
|[Button 要素](../extensibility/button-element.md)|ユーザーが操作できるコマンドを定義します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage ツールバーのコマンドのコレクションを表します。|  
  
## <a name="example"></a>例  
  
```  
<Buttons>  
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">  
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>  
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>  
    <Strings>  
      <ButtonText>C# Command Sample</ButtonText>  
    </Strings>  
  </Button>  
</Buttons>  
```  
  
## <a name="see-also"></a>参照  
 [Vspackage のユーザーインターフェイス要素の追加方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)
