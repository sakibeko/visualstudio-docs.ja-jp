---
title: ParallelCustomBuild タスク | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279267"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild タスク

[CustomBuild タスク](../msbuild/custombuild-task.md)の並列インスタンスを実行します。

## <a name="parameters"></a>パラメーター

以下の表では **ParallelCustomBuild** タスクのパラメーターについて説明します。

|パラメーター|[説明]|
|---------------|-----------------|
|**BreakOnFirstFailure**|省略可能な **bool** 型のパラメーターです。|
|**MaxItemsInBatch**|省略可能な **int** 型のパラメーターです。|
|**MaxProcesses**|省略可能な **int** 型のパラメーターです。|
|**Sources**|必須の **ITaskItem[]** 型のパラメーターです。|

## <a name="see-also"></a>参照

[タスク リファレンス](../msbuild/msbuild-task-reference.md)