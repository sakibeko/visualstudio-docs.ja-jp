---
title: 'IDebugField:: GetExtendedInfo |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728869"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
このメソッドは、フィールドに関する拡張情報を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>パラメーター
`guidExtendedInfo`\
から返される情報を選択します。 有効な値は次のとおりです。

|値|説明|
|-----------|-----------------|
|`guidConstantValue`|バイトシーケンスとしての値。|
|`guidConstantType`|型のシグネチャとしての型。|

`prgBuffer`\
入出力拡張された情報を返します。

`pdwLen`\
[入力、出力]拡張情報のサイズをバイト単位で返します。

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="remarks"></a>解説
 現在、このメソッドは定数の型または値のみを返します。 呼び出し元は、 `prgBuffer` COM の `CoTaskMemFree` 関数 (C++) または (C#) を呼び出すことによって、で返されたバッファーを解放する必要があり <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> ます。

## <a name="see-also"></a>関連項目
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
