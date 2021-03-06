---
title: 'IDebugBinder3:: FindAlias |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735867"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
このメソッドは、名前を指定してエイリアスを検索します。 これにより、プログラム内のすべてのエイリアスが検索されます。

## <a name="syntax"></a>構文

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>パラメーター
`pcstrName`\
から検索するエイリアスの名前。

`ppAlias`\
入出力 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) インターフェイスによって表されるエイリアス (存在する場合) が見つかりました。

## <a name="return-value"></a>戻り値
 成功した場合は、を返し `S_OK` ます。それ以外の場合はを返します `S_FALSE` 。エイリアスが見つからない場合は、エラーコードを返します。

## <a name="remarks"></a>解説
 このメソッドは、を呼び出す前に、対象のオブジェクトを null に初期化します。次に、エイリアスが見つかったかどうかを判断するために、後で null 値をテストします。

## <a name="see-also"></a>関連項目
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
