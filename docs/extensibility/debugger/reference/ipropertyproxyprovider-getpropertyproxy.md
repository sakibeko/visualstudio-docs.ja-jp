---
title: 'IPropertyProxyProvider:: GetPropertyProxy |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35c23fc56c883845bdb7fb73daa60a845ee5e21a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714835"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
指定されたプロキシ ID のプロパティプロキシインターフェイスを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetPropertyProxy(
   DWORD                  dwID,
   IPropertyProxyEESide** proxy
);
```

```csharp
int GetPropertyProxy(
   uint                     dwID,
   out IPropertyProxyEESide proxy
);
```

## <a name="parameters"></a>パラメーター
`dwID`\
から目的のプロパティプロキシの ID。

`proxy`\
入出力 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) オブジェクトを返します。

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="remarks"></a>注釈
 外部型ビジュアライザーをサポートするために、このメソッドは通常、呼び出しを [Getpropertyproxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) メソッドに転送します。 IEEVisualizerService の取得方法の詳細については、「 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md) 」を参照してください。

## <a name="see-also"></a>関連項目
- [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)
