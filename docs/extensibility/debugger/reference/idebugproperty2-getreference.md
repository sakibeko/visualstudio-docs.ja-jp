---
title: 'IDebugProperty2:: GetReference |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f119a00139e2af44f771fa0903c73b8003dd77f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721362"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
プロパティの値への参照を返します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>パラメーター
`ppRererence`\
入出力プロパティの値への参照を表す [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) オブジェクトを返します。

## <a name="return-value"></a>戻り値
 成功した場合は、を返し `S_OK` ます。それ以外の場合は、エラーコード (通常はまたは) を返します `E_NOTIMPL` `E_GETREFERENCE_NO_REFERENCE` 。

## <a name="see-also"></a>関連項目
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
