---
title: 'IDebugThread2:: GetName |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718775"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
スレッドの名前を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>パラメーター
`pbstrName`\
入出力スレッドの名前を返します。

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="remarks"></a>注釈
 取得した名前は常に表示される名前であり、この名前はスレッドについて説明します。 スレッド名は、名前付きスレッドをサポートするランタイムアーキテクチャから派生する場合もあれば、デバッグエンジンから派生した名前である場合もあります。 また、 [Setthreadname](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) メソッドを呼び出すことによって、スレッドの名前を設定することもできます。

## <a name="see-also"></a>関連項目
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
