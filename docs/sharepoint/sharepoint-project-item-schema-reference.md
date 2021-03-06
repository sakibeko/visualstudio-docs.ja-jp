---
title: SharePoint プロジェクト項目スキーマリファレンス |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "63007720"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint プロジェクト項目スキーマのリファレンス
  Visual Studio では、SharePoint プロジェクト項目スキーマを使用して、 *sharepointprojectitem.spdata* ファイルの内容を検証します。 *Sharepointprojectitem.spdata*ファイルは、SharePoint プロジェクトアイテムの内容と動作を指定します。 SharePoint プロジェクト項目の内容の詳細については、「 [sharepoint プロジェクト項目の項目テンプレートとプロジェクトテンプレートを作成](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)する」を参照してください。

 SharePoint プロジェクト項目スキーマは ProjectItemModelSchema という名前で、既定では% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ xmlschema にインストールされます。

 ルート要素は [ProjectItem](../sharepoint/projectitem-element.md) 要素です。 次の表では、スキーマで定義されているすべての要素について説明します。

|要素|説明|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint プロジェクトアイテムに関連付けられているカスタムデータアイテムのコレクションを表します。|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|SharePoint プロジェクト項目に関連付けられているカスタムデータ項目を表します (キー/値の形式)。 キーと値は、どちらも文字列である必要があります。|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint に配置されるときにフィーチャーに含まれるプロパティ値のコレクションを表します。 フィーチャーが配置されると、コード内のプロパティ値にアクセスできるようになります。|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|SharePoint に配置されるときにフィーチャーに含まれるカスタムプロパティを表します。 フィーチャーが配置された後、コード内のプロパティにアクセスできます。|
|[[ファイル]](../sharepoint/files-element.md)|フィーチャー要素ファイルやプロジェクトの出力など、SharePoint プロジェクトアイテムと共に配置するファイルを指定します。|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクトアイテムを表します。|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|SharePoint に配置されるときにプロジェクト項目に含める、フィーチャー要素ファイルなどの SharePoint ファイルを表します。|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|マップされたフォルダーを表します。|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|SharePoint に配置されるときにプロジェクト項目に含めるプロジェクトの出力を表します。|
|[SafeControl](../sharepoint/safecontrol-element.md)|SharePoint サイトの任意の ASPX ページで任意のユーザーがアクセスできるようにセキュリティで保護されていると指定された ASPX コントロールまたは Web パーツを表します。|
|[SafeControls](../sharepoint/safecontrols-element.md)|SharePoint サイトの任意の ASPX ページですべてのユーザーがアクセスできるようにセキュリティで保護されたものとして指定された ASPX コントロールおよび Web パーツのコレクションを表します。|

## <a name="see-also"></a>こちらもご覧ください
- [SharePoint プロジェクト項目の項目テンプレートとプロジェクトテンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
