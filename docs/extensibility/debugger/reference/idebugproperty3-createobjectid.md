---
title: 'IDebugProperty3:: CreateObjectID |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721176"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
このプロパティの一意の ID を作成して、他のすべてのプロパティ間で一意であることを確認します。

## <a name="syntax"></a>構文

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="remarks"></a>注釈
 このメソッドは、セッションデバッグマネージャーが、このプロパティが他のすべてのプロパティで一意に識別されるようにする必要があるときに呼び出されます。 デバッグエンジン (DE) は、対応するプロパティが既に一意に識別されている場合を除き、このメソッドをサポートします。 DE がこのメソッドをサポートしていない場合は、を返し `E_NOTIMPL` ます。

 で作成された一意の ID `CreateObjectID` は、 [destroyobjectid](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) メソッドが呼び出されたときに破棄されます。これにより、このプロパティを一意に識別する必要があることが通知されます。

> [!NOTE]
> この一意の ID を取得する方法はありません。そのため、メソッドが呼び出されたときに、DE は一意の Id に必要な操作を実行でき `CreateObjectID` ます。

## <a name="see-also"></a>関連項目
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
