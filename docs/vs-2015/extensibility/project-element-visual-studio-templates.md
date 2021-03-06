---
title: Project 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c9708bb8c35e66199aaf3665883307e48a63c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193967"
---
# <a name="project-element-visual-studio-templates"></a>Project 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プロジェクトに追加するファイルまたはディレクトリを指定します。  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
  
## <a name="syntax"></a>構文  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`File`|必須の属性です。<br /><br /> テンプレート .zip ファイル内のプロジェクトファイルの名前を指定します。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> プロジェクトがテンプレートから作成されたときに置き換える必要があるパラメーター値をプロジェクトファイルに含めるかどうかを指定するブール値です。 既定値は `false`にする必要があります。|  
|`TargetFileName`|省略可能な属性です。<br /><br /> プロジェクトがテンプレートから作成されるときのプロジェクトファイルの名前を指定します。|  
|`IgnoreProjectParameter`|省略可能な属性です。<br /><br /> 現在のソリューションにプロジェクトを追加する必要があるかどうかを指定します。 カスタムパラメーター "$*Mycustomparameter*$" の値がパラメーター置換ファイルに存在する場合、プロジェクトは作成されますが、現在開いているソリューションの一部としては追加されません。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[フォルダー](../extensibility/folder-element-visual-studio-project-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するフォルダーを指定します。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するファイルを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必須の要素です。|  
  
## <a name="remarks"></a>注釈  
 `Project` は、`TemplateContent` の子要素で、省略可能な要素です。  
  
 要素はプロジェクトを指定 `Project` するために使用されます。したがって、はプロジェクトテンプレートでのみ有効です。  
  
 `Project` 要素には [フォルダー](../extensibility/folder-element-visual-studio-project-templates.md) children 要素または [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) 子要素を含めることができますが、要素 `Folder` と子要素の両方を混在させることはできません `ProjectItem` 。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [ **新しいプロジェクト** ] ダイアログボックスでユーザーが入力した名前に基づいて、プロジェクトファイル名の名前が自動的に変更されます。 `TargetFileName`テンプレートで作成されたプロジェクトファイルに別のファイル名を指定する場合は、属性を使用します。  
  
## <a name="example"></a>例  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。  
  
```  
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
            <ProjectItem>Form1.cs<ProjectItem>  
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
  
## <a name="see-also"></a>参照  
 [Visual Studio テンプレートスキーマリファレンス](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトテンプレートと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 要素 (Visual Studio プロジェクトテンプレート)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder 要素 (Visual Studio プロジェクト テンプレート)](../extensibility/folder-element-visual-studio-project-templates.md)
