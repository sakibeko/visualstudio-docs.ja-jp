---
title: ワークフローデザイナー-Persist アクティビティデザイナー
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75236d7955cba6b8c62b9a4504f02c66cebe4062
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114772"
---
# <a name="persist-activity-designer"></a>Persist アクティビティ デザイナー

**Persist**アクティビティデザイナーは、アクティビティを作成および構成するために使用され <xref:System.Activities.Statements.Persist> ます。

## <a name="the-persist-activity"></a>Persist アクティビティ

<xref:System.Activities.Statements.Persist> アクティビティで、ワークフローをディスクに保存します (可能な場合)。 <xref:System.Activities.Statements.Persist> アクティビティは、<xref:System.Activities.Statements.TransactionScope> アクティビティ内などの非永続化ゾーンでは実行できません。 <xref:System.Activities.Statements.Persist>非永続化スコープでアクティビティを使用すると、実行時に例外がスローされます。

### <a name="using-the-persist-activity-designer"></a>Persist アクティビティ デザイナーの使用

**Persist**アクティビティデザイナーは、 **[ツールボックス**] の [**ランタイム**] カテゴリにあります。このカテゴリにアクセスするには、[**ツール**ボックス] タブをクリックします (または、[**表示**] メニューの [**ツールボックス**] を選択するか、CTRL + ALT + X キーを押します)。

**Persist**アクティビティデザイナーは、[**ツールボックス**] からドラッグして、アクティビティを通常配置している任意の場所 (内など) にワークフローデザイナー画面にドロップできます <xref:System.Activities.Statements.Sequence> 。 これ <xref:System.Activities.Statements.Persist> により、Persist という既定の **DisplayName** を持つアクティビティが作成されます。 は、 <xref:System.Activities.Activity.DisplayName%2A> **Persist** アクティビティデザイナーのヘッダー、またはプロパティグリッドの [ **DisplayName** ] ボックスで編集できます。

### <a name="the-persist-properties"></a>Persist のプロパティ

次の表に、<xref:System.Activities.Statements.Persist> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティグリッドで編集することができ、一部のプロパティはワークフローデザイナー画面で編集できます。

|プロパティ名|必須|使用法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|×|<xref:System.Activities.Statements.Persist> アクティビティの表示名。 既定値は Persist です。 表示名は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>関連項目

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
