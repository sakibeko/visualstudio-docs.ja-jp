---
title: 'IDebugBinder3:: GetAllAliases |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735811"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
このメソッドは、プログラムからエイリアスの一覧を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>パラメーター
`uRequest`\
から返されるエイリアスの最大数 (に渡される配列の長さを指定し `ppAliases` ます)。

`ppAliases`\
[入力、出力]エイリアスを格納する配列 (これが null 値で、 `uRequest` が0の場合、返される可能性がある別名の数はによって返され `puFetched` ます)。

`puFetched`\
入出力取得されたエイリアスの数を返します。

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="see-also"></a>関連項目
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
