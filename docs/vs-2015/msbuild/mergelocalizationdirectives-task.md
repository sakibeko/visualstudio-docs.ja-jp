---
title: MergeLocalizationDirectives タスク | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d6c2aa6cea687119e69b565da5468e8fa723641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703412"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> タスクは、1 つ以上の [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] バイナリ形式ファイルのローカリゼーション属性とコメントを、アセンブリ全体で単一のファイルにマージします。  
  
## <a name="task-parameters"></a>タスク パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|必須の **ITaskItem[]** 型のパラメーターです。<br /><br /> [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] バイナリ形式の個々のファイルに対するローカリゼーション ディレクティブ ファイルの一覧を指定します。|  
|`OutputFile`|省略可能な **String** 型の出力パラメーターです。<br /><br /> コンパイルされたローカリゼーション ディレクティブ アセンブリの出力パスを指定します。|  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] のコンテンツには、ローカリゼーション属性とコメントを追加できます。 [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)] のローカリゼーション サポートを使用すると、ローカリゼーション属性とコメントを取り出し、生成されるアセンブリとは別の .loc ファイルに格納できます。 これを行うには、**LocalizationPropertyStorage** 属性を使用します。 ローカリゼーション属性とコメント、および **Localizationpropertystorage**の詳細については、「 [ローカリゼーション属性とコメント](https://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f)」を参照してください。  
  
## <a name="example"></a>例  
 いくつかの [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] バイナリ形式ファイルのローカリゼーション コメントを単一の .loc ファイルにマージする方法を次の例に示します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>参照  
 [WPF MSBuild リファレンス](../msbuild/wpf-msbuild-reference.md)   
 [タスクリファレンス](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [タスクリファレンス](../msbuild/msbuild-task-reference.md)   
 [WPF アプリケーションのビルド (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
