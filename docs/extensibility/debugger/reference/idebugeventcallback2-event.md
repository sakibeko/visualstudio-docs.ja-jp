---
title: 'IDebugEventCallback2:: Event |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729896"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
デバッグイベントの通知を送信します。

## <a name="syntax"></a>構文

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>パラメーター
`pEngine`\
からこのイベントを送信しているデバッグエンジン (DE) を表す [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) オブジェクト。 このパラメーターを入力するには、DE が必要です。

`pProcess`\
からイベントが発生するプロセスを表す [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) オブジェクト。 このパラメーターは、セッションデバッグマネージャー (SDM) によって入力されます。 DE は、常にこのパラメーターに null 値を渡します。

`pProgram`\
からこのイベントが発生するプログラムを表す [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) オブジェクト。 ほとんどのイベントでは、このパラメーターは null 値ではありません。

`pThread`\
からこのイベントが発生したスレッドを表す [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) オブジェクト。 イベントを停止する場合、このパラメーターからスタックフレームが取得されるため、このパラメーターに null 値を指定することはできません。

`pEvent`\
からデバッグイベントを表す [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) オブジェクト。

`riidEvent`\
からパラメーターから取得するイベントインターフェイスを識別する GUID `pEvent` 。

`dwAttrib`\
から [Eventattributes](../../../extensibility/debugger/reference/eventattributes.md) 列挙のフラグの組み合わせ。

## <a name="return-value"></a>戻り値
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。

## <a name="remarks"></a>解説
 このメソッドを呼び出す場合、パラメーターは、 `dwAttrib` パラメーターで渡されるイベントオブジェクトで呼び出される [getattributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) メソッドから返される値と一致する必要があり `pEvent` ます。

 すべてのデバッグイベントは、イベント自体が非同期であるかどうかに関係なく、非同期的にポストされます。 DE がこのメソッドを呼び出すと、戻り値は、イベントが処理されたかどうかを示すのではなく、イベントが受信されたかどうかのみを示します。 実際、ほとんどの状況では、このメソッドから制御が戻ったときにイベントは処理されていません。

## <a name="see-also"></a>関連項目
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
