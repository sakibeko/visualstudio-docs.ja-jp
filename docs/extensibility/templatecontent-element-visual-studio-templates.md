---
title: TemplateContent 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699231"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent 要素 (Visual Studio テンプレート)

テンプレートの内容を指定します。

要素階層:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>構文

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>属性および要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|プロジェクトがテンプレートから作成されたときにソリューションをビルドするかどうかを指定します。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 複数プロジェクトのテンプレートの構成と内容を指定します。|
|[プロジェクト](../extensibility/project-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するファイルまたはディレクトリを指定します。|
|[参照](../extensibility/references-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 項目テンプレートに必要なアセンブリ参照を指定します。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|省略可能な要素です。<br /><br /> テンプレートに含まれるファイルを指定します。|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> プロジェクトまたは項目がテンプレートから作成されるときに使用されるカスタムパラメーターを指定します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必須の要素です。<br /><br /> プロジェクトテンプレート、項目テンプレート、またはスタートキットのすべてのメタデータが含まれます。|

## <a name="remarks"></a>注釈
 `TemplateContent` は必須の要素です。

## <a name="example"></a>例
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>こちらもご覧ください

- [Visual Studio テンプレートスキーマリファレンス](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクトテンプレートと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)
