---
title: CONTEXT_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737573"
---
# <a name="context_info"></a>CONTEXT_INFO
この構造体は、メモリコンテキストまたはコードコンテキストを記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>メンバー
`dwFields`\
入力するフィールドを指定する、 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) 列挙型のフラグの組み合わせ<strong>。</strong>

`bstrModuleUrl`\
コンテキストが配置されているモジュールの名前。

`bstrFunction`\
コンテキストが配置されている関数の名前。

`posFunctionOffset`\
コードコンテキストに関連付けられている関数の行と列のオフセットを識別する [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 構造体。

`bstrAddress`\
指定したコンテキストが配置されているコード内のアドレス。

`bstrAddressOffset`\
指定したコンテキストが配置されているコード内のアドレスのオフセット。

`bstrAddressAbsolute`\
指定したコンテキストが配置されているメモリ内の絶対アドレス。

## <a name="remarks"></a>解説
この構造体は、 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) メソッドの呼び出しから返されます。

この構造体の一般的な用途は、 **メモリ** デバッグウィンドウをサポートすることです。

## <a name="requirements"></a>必要条件
ヘッダー: msdbg. h

名前空間: VisualStudio。

アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
