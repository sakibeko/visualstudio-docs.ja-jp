---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733143"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
このメソッドは、サーバーのマシンユーティリティを取得します。

> [!NOTE]
> このメソッドは互換性のために残されています。使用しないでください ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `E_NOTIMPL` このメソッドが呼び出された場合は、常にを返します)。 この情報は、履歴上の理由で保持されます。

## <a name="syntax"></a>構文

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>パラメーター
`ppUtil`\
入出力 `IDebugMDMUtil2_V7` コンピューターユーティリティ情報を表すインターフェイスを返します。

## <a name="return-value"></a>戻り値
 は常にを返し `E_NOTIMPL` ます。これは、メソッドが実装されていないことを示します。

## <a name="remarks"></a>解説
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]`E_NOTIMPL`このメソッドが呼び出された場合は、常にを返します。

## <a name="see-also"></a>関連項目
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
