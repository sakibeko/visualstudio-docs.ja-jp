---
title: ストアアプリのデバッグ
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc2d05c6b6aae4b2f33d135c6859da7b17de963
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533160"
---
# <a name="debug-store-apps-in-visual-studio"></a>Visual Studio でのストア アプリのデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio デバッガーを使用すると、プログラムの実行を制御し、その状態を確認できます。 Windows ストア アプリの障害の原因を検出し、アプリの動作のしくみを十分に理解するためにデバッガーを使用します。 デバッガーで実行を中断すると、実行中のコードが含まれるソース ファイルが Visual Studio に表示され、実行中のステートメントが強調表示されます。 変数の値、実行関数の呼び出し履歴、およびプログラムの状態の他の側面を確認できます。 1 つのステートメントごとにプログラムを実行 (ステップ スルー) し続けると、ステートメントがプログラムの値を変化させるしくみを確認できます。 JavaScript で記述されたアプリでは、ページの DOM を調べて操作できます。

## <a name="in-this-section"></a>このセクションの内容

|Title|説明|
|-|-|
|[デバッグ セッションの開始 (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|「デバッグ セッションを開始する方法」では、JavaScript アプリのデバッグ セッションを構成し開始するための、いくつかのオプションについて説明します。|
|[デバッグ セッションでの実行制御 (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|「デバッガー ナビゲーション」では、簡単なアプリを使って、デバッグの開始と停止、コード内の移動、プログラムの状態を表示する方法を説明します。|
|[クイック スタート:HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)|「HTML および CSS のデバッグ」では、ライブ DOM 検査ツールを使って JavaScript アプリを対話的にデバッグし、HTML と CSS の表示方法や変更方法を示します。|
|[クイック スタート: JavaScript をデバッグする](../debugger/quickstart-debug-javascript-using-the-console.md)|「コンソールを使用した JavaScript のデバッグ」では、javascript [コンソールのコマンド](../debugger/javascript-console-commands.md)を使用して javascript アプリを対話的にデバッグする方法を示します。|
|[デバッグ セッションを開始する (VB、C#、C++、および XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|「デバッグ セッション (Visual C++、Visual C#、Visual Basic) を開始する方法」では、Visual C++、Visual C#、または Visual Basic で記述されたアプリのデバッグ セッションを構成し開始するための、さまざまなオプションについて説明します。|
|[デバッグ セッションのナビゲート (XAML および C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|「デバッガー ナビゲーション」では、簡単なアプリを使って、デバッグの開始と停止、コード内の移動、プログラムの状態の表示と変更を行う方法を説明します。|
|[Windows ストアの中断、再開、およびバックグラウンド イベントをトリガーする](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|デバッガーは、アプリを中断、再開、および終了する Windows のプロセス継続時間管理 (PLM) イベントを無効にします。 これらのイベントは、デバッガー ツール バーでトリガーさせることができます。<br /><br /> バックグラウンド タスクは、アプリが中断された場合でも重要な操作を実行できるようにします。 デバッガーは、これらのバックグラウンド タスクを開始してデバッグできるようにします。|

## <a name="see-also"></a>参照
 [Visual Studio でデバッグする (MSDN ライブラリ内)](https://msdn.microsoft.com/library/sc65sadd(VS.110).aspx)
