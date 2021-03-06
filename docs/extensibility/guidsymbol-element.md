---
title: GuidSymbol 要素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711126"
---
# <a name="guidsymbol-element"></a>GuidSymbol 要素
要素には、 `GuidSymbol` メニュー、グループ、またはコマンドを表す guid: ID ペアの guid が含まれます。 ID は、要素の要素から取得され `IDSymbol` `GuidSymbol` ます。 `GuidSymbol`要素には、 `name` 属性に含まれている GUID のフレンドリ名を提供する属性があり `value` ます。

## <a name="syntax"></a>構文

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|name|必須です。 GUID シンボルの名前。|
|value|必須です。 GUID シンボルの GUID。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[IDSymbol 要素](../extensibility/idsymbol-element.md)|メニュー、グループ、またはコマンドを表す GUID: ID ペアの ID を格納します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[Symbols 要素](../extensibility/symbols-element.md)|`GuidSymbol` *Vsct*ファイル内の要素をグループ化します。|

## <a name="remarks"></a>注釈
 通常、 *. vsct* ファイルには、パッケージ自体用の3つの要素が含まれています。1つはパッケージ自体用で、もう1つは `GuidSymbol` `Symbols` コマンドセット (パッケージが使用可能にするメニュー、グループ、およびコマンドのコレクション)、もう1つはボタンとその他のビジュアルコンポーネントのアイコンを提供するビットマップ用です。 `IDSymbol`指定された要素内のすべての要素は `GuidSymbol` 、一意である必要があり `value` ます。ただし、 `IDSymbol` 同一の値を持つ要素は、異なる親を持つ限り、パッケージ内に存在することができます。

## <a name="see-also"></a>関連項目
- [Visual Studio コマンドテーブル (vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
