---
title: Group 要素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26479257511d74f122dd4064330f5b6a1e8dadd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711229"
---
# <a name="group-element"></a>Group 要素
VSPackage コマンドグループを定義します。

## <a name="syntax"></a>構文

```xml
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">
  <Parent>... </Parent>
</Group>
```

## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|guid|必須です。 GUID/ID コマンド識別子の GUID。|
|id|必須です。 GUID/ID コマンド識別子の ID。|
|priority|省略可能。 優先度を示す数値です。|
|条件|省略可能。 「 [条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|Parent|省略可能。 ボタンの親要素。|
|Annotation|コメント (省略可能)。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[Groups 要素](../extensibility/groups-element.md)|VSPackage のコマンドグループを定義するエントリが含まれています。|

## <a name="example"></a>例

```xml
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
</Group>
```

## <a name="see-also"></a>関連項目
- [Visual Studio コマンドテーブル (vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
