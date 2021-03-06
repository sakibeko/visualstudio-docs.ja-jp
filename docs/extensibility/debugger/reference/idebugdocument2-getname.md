---
title: 'IDebugDocument2:: GetName |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2af7f4dc01ee3a2fe3fb5026602a0b5d4f766b17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731962"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
複数の形式のいずれかで文書の名前を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>パラメーター
`gnType`\
から返される名前の型を決定する、 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 列挙の値です。

`pbstrFileName`\
入出力ドキュメント名を含む文字列を返します。

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="remarks"></a>解説
 たとえば、このメソッドは、ドキュメントの名前をタイトルまたはファイル名またはファイル名の一部として返すことができます。

## <a name="see-also"></a>関連項目
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
