---
title: '方法: GPU スレッドウィンドウを使用する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7b97c346cc933e14292fbb1198bfb69ecf59717
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696163"
---
# <a name="how-to-use-the-gpu-threads-window"></a>方法: GPU スレッド ウィンドウを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

GPU スレッド ウィンドウでは、デバッグ中のアプリケーション内の GPU 上で実行されているスレッドを調べて操作できます。 GPU 上で実行されるアプリケーションの詳細については、「[C++ AMP の概要](https://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc)」を参照してください。  
  
 GPU スレッド ウィンドウには、すべての列で同じ値を持つ一連の GPU スレッドを各行が表すテーブルが表示されます。 列内の項目を並べ替え、順序変更、削除、およびグループ化することができます。 GPU スレッド ウィンドウから、スレッドのフラグ設定、フラグ解除、凍結 (中断)、および凍結解除 (再開) を実行できます。 GPU スレッド ウィンドウには次の列が表示されます。  
  
- フラグ列。特に注意する必要のあるスレッドをマークできます。  
  
- アクティブ スレッド列。黄色の矢印は、アクティブ スレッドであることを示します。 矢印は、実行がデバッガーに割り込んだスレッドを示します。  
  
- **[スレッド数]** 列。同じ位置のスレッドの数を表示します。  
  
- **[行]** 列。スレッドの各グループがあるコード行を表示します。  
  
- **[アドレス]** 列。スレッドの各グループがある命令アドレスを表示します。 既定では、この列は非表示になっています。  
  
- **[場所]** 列。ソース コード内の位置です。  
  
- **[ステータス]** 列。スレッドのステータスがアクティブ、ブロック、未開始状態、または完了であるかどうかを示します。  
  
- **[タイル]** 列。行内のスレッドのタイル インデックスを示します。  
  
  テーブルのヘッダーは、表示されているタイルとスレッドを示します。  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>GPU スレッド ウィンドウを表示するには  
  
1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。  
  
2. プロジェクトの **[プロパティ ページ]** ウィンドウで、 **[構成プロパティ]** の **[デバッグ]** をクリックします。  
  
3. **[起動するデバッガー]** の一覧で、 **[ローカル Windows デバッガー]** を選択します。 **[デバッガーの種類]** の一覧で、 **[GPU のみ]** を選択します。 GPU 上で実行されるコードのブレークポイントで中断するには、このデバッガーを選択する必要があります。  
  
4. **[OK]** を選択します。  
  
5. GPU コードにブレークポイントを設定します。  
  
6. メニュー バーで、 **[デバッグ]** 、 **[デバッグ開始]** の順に選択します。 アプリケーションがブレークポイントに到達するを待機します。  
  
7. メニュー バーで、 **[デバッグ]** 、 **[Windows]** 、 **[GPU スレッド]** の順にクリックします。  
  
### <a name="to-change-to-a-different-active-thread"></a>別のアクティブなスレッドに変更するには  
  
- 列をダブルクリックします。 (キーボード: 行を選択し、Enter キーを押します。)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>特定のタイルとスレッドを表示するには  
  
1. GPU スレッド ウィンドウの **[スレッド スイッチャーの展開]** をクリックします。  
  
2. テキスト ボックスにタイルとスレッドの値を入力します。  
  
3. 矢印が表示されているボタンをクリックします。  
  
### <a name="to-display-or-hide-a-column"></a>列の表示と非表示を切り替えるには  
  
- GPU スレッド ウィンドウのショートカット メニューを開いて **[列]** をクリックし、表示と非表示を切り替える列を選択します。  
  
### <a name="to-sort-by-a-column"></a>列で並べ替えるには  
  
- 列見出しを選択します。  
  
### <a name="to-group-threads"></a>スレッドをグループ化するには  
  
- GPU スレッド ウィンドウのショートカット メニューを開いて **[グループ化]** をクリックし、表示される列名の 1 つを選択します。 スレッドのグループ化を解除するには、 **[なし]** をクリックします。  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>スレッドの行を凍結または凍結解除するには  
  
- 行のショートカット メニューを開き、 **[凍結]** または **[凍結解除]** をクリックします。  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>スレッドの行をフラグ設定またはフラグ解除するには  
  
- スレッドのフラグ列を選択するか、スレッドのショートカット メニューを開いて **[フラグ設定]** または **[フラグ解除]** をクリックします。  
  
### <a name="to-display-only-flagged-threads"></a>フラグが設定されたスレッドのみ表示するには  
  
- GPU スレッド ウィンドウでフラグ ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 [マルチスレッドアプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法: [並列ウォッチ] ウィンドウを使用する](../debugger/how-to-use-the-parallel-watch-window.md)   
 [チュートリアル: C++ AMP アプリケーションのデバッグ](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
