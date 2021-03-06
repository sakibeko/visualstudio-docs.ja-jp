---
title: UsingTask の Task 要素 (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263189"
---
# <a name="task-element-of-usingtask-msbuild"></a>UsingTask の Task 要素 (MSBuild)

`UsingTask` `TaskFactory` に渡されるデータを含みます。 詳細については、「[UsingTask 要素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)」を参照してください。

 \<Project> \<UsingTask> \<Task>
 \<Task>

## <a name="syntax"></a>構文

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>属性と要素

 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`Evaluate`|省略可能な Boolean 属性です。<br /><br /> `true` の場合、MSBuild は内部要素をすべて評価し、タスクがインスタンス化されるときに項目とプロパティを展開してから情報を `TaskFactory` に渡します。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|データ|`Task` タグ間のテキストは `TaskFactory` にそのまま送信されます。|

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | MSBuild でタスクを登録する方法を指定します。 1 つのプロジェクトに 0 個以上の `UsingTask` 要素を含めることができます。 |

## <a name="example"></a>例

 次の例では、`Evaluate` 属性で `Task` 要素を使用する方法を示します。

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>関連項目

- [タスク](../msbuild/msbuild-tasks.md)
- [タスク リファレンス](../msbuild/msbuild-task-reference.md)
- [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)
