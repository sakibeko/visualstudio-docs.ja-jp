---
title: 'IDebugModuleLoadEvent2:: GetModule |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b90547709e5524ce005b0598b0b8d482cfecf173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726724"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
読み込まれている、またはアンロードされているモジュールを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>パラメーター
`pModule`\
入出力読み込み中またはアンロード中のモジュールを表す [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) オブジェクトを返します。

`pbstrDebugMessage`\
[入力、出力]このイベントを記述するオプションのメッセージを返します。 このパラメーターが null 値の場合、メッセージは要求されません。

`pbLoad`\
[入力、出力]モジュールが読み込み中の場合は0以外 ( `TRUE` ) `FALSE` 。モジュールがアンロード中の場合は 0 ()。 このパラメーターが null 値の場合、状態は要求されません。

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="see-also"></a>関連項目
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
