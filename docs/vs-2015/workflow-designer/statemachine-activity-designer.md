---
title: StateMachine アクティビティデザイナー |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660119"
---
# <a name="statemachine-activity-designer"></a>StateMachine アクティビティ デザイナー
<xref:System.Activities.Statements.StateMachine> アクティビティには状態のコレクションが含まれており、一般的なステート マシン パラダイムを使用してワーク フローをモデル化します。

## <a name="using-the-statemachine-activity-designer"></a>StateMachine アクティビティ デザイナーの使用
 アクティビティを追加するには <xref:System.Activities.Statements.StateMachine> 、[**ツールボックス**] の [**ステートマシン**] セクションから**StateMachine**アクティビティデザイナーをドラッグし、画面にドロップし [!INCLUDE[wfd1](../includes/wfd1-md.md)] ます。 このアクティビティに子の状態を追加するには、[ <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State> ツールボックス] からまたはをドラッグして、[ <xref:System.Activities.Core.Presentation.FinalState> **StateMachine**] にドロップし**Toolbox**ます。

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの StateMachine アクティビティのプロパティ
 次の表に、ワークフロー デザイナーを使用して設定できる <xref:System.Activities.Statements.StateMachine> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部はデザイナー画面で編集できます。

|プロパティ名|必須|使用|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|×|ヘッダーの <xref:System.Activities.Statements.StateMachine> アクティビティ デザイナーの表示名を指定します。 既定値は **StateMachine**です。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。 <xref:System.Activities.Activity.DisplayName%2A> は、ワークフロー デザイナーの上部に表示される階層リンク バーで使用されます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>参照
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)の [制御フロー](../workflow-designer/control-flow-activity-designers.md)