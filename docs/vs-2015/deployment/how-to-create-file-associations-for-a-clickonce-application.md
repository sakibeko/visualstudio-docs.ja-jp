---
title: '方法: ClickOnce アプリケーションのファイルの関連付けを作成する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697700"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>方法 : ClickOnce アプリケーションのファイルの関連付けを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションを1つまたは複数のファイル名拡張子に関連付けることができるため、ユーザーがこれらの種類のファイルを開いたときに、アプリケーションが自動的に起動されます。 ファイル名拡張子のサポートをアプリケーションに追加する [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] のは簡単です。  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce アプリケーションのファイルの関連付けを作成するには  
  
1. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]通常どおりにアプリケーションを作成するか、既存のアプリケーションを使用し [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ます。  
  
2. メモ帳などのテキストエディターまたは XML エディターを使用して、アプリケーションマニフェストを開きます。  
  
3. `assembly` 要素を検索します。 詳細については、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」を参照してください。  
  
4. 要素の子として `assembly` 、要素を追加し `fileAssociation` ます。 `fileAssociation`要素には、次の4つの属性があります。  
  
   - `extension`: アプリケーションに関連付けるファイル名拡張子。  
  
   - `description`: Windows シェルに表示されるファイルの種類の説明。  
  
   - `progid`: ファイルの種類を一意に識別する文字列。レジストリにマークを付けます。  
  
   - `defaultIcon`: このファイルの種類に使用するアイコン。 このアイコンは、アプリケーションマニフェストでファイルリソースとして追加する必要があります。 詳細については、「[方法:ClickOnce アプリケーションにデータ ファイルを含める](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)」を参照してください。  
  
     要素と要素の例につい `file` `fileAssociation` ては、「 [ \<fileAssociation> Element](../deployment/fileassociation-element-clickonce-application.md)」を参照してください。  
  
5. 複数のファイルの種類をアプリケーションに関連付ける場合は、追加の要素を追加し `fileAssociation` ます。 属性は、 `progid` それぞれで異なる必要があることに注意してください。  
  
6. アプリケーションマニフェストの作成が完了したら、マニフェストに再署名します。 これは、Mage.exe を使用してコマンドラインから行うことができます。  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    詳細については、「 [Mage.exe (マニフェスト生成および編集ツール)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [\<fileAssociation> Element](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce アプリケーションマニフェスト](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (マニフェストの生成および編集ツール)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
