---
title: 起動ベースの添付ファイル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738459"
---
# <a name="launch-based-attachment"></a>起動ベースの添付ファイル
プログラムへの起動に基づく添付ファイルは自動的に実行されます。 プログラムをホストするプロセスが SDM によって起動されると、起動ベースの添付ファイルは、手動添付メソッドと同様のパスに従います。 詳細については、「 [プログラムへのアタッチ](../../extensibility/debugger/attaching-to-the-program.md)」を参照してください。

## <a name="the-attaching-process"></a>アタッチプロセス
 主な違いは、次のように、 **アタッチ** 呼び出しの後のイベントのシーケンスです。

1. **IDebugEngineCreateEvent2**イベントオブジェクトを SDM に送信します。 詳細については、「 [イベントの送信](../../extensibility/debugger/sending-events.md)」を参照してください。

2. `IDebugProgram2::GetProgramId` **Attach**メソッドに渡された**IDebugProgram2**インターフェイスでメソッドを呼び出します。

3. **IDebugProgramCreateEvent2**イベントオブジェクトを送信して、ローカルの**IDebugProgram2**オブジェクトが作成されたことを SDM に通知します。

4. [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)イベントオブジェクトを送信して、起動したプロセスに対して新しいスレッドが作成されたことを SDM に通知します。

## <a name="see-also"></a>関連項目
- [必要なイベントを送信する](../../extensibility/debugger/sending-the-required-events.md)
- [プログラムのデバッグを有効にする](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
