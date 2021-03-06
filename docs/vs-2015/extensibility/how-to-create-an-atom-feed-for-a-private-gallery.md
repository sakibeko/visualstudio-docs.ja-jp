---
title: '方法: プライベートギャラリーの Atom フィードを作成する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204209"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>方法: プライベート ギャラリーの Atom フィード
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

拡張機能を含むイントラネットの場所に Atom (RSS) フィードを作成し、そのフィードをプライベートギャラリーとして **拡張機能と更新プログラム** に追加することができます。 詳細については、「 [Private Galleries](../extensibility/private-galleries.md)」を参照してください。  
  
## <a name="creating-an-atom-feed"></a>Atom フィードの作成  
 Atom フィードをプライベートギャラリーとして作成するには、まず、拡張機能 (.vsix ファイル) をフォルダーに集めます。 必要に応じて、サブフォルダーに整理することができます。 また、次のリソースも必要になります。  
  
- 拡張機能をプライベートギャラリーとして使用できるようにする atom.xml ファイル。 atom.xml ファイルを **拡張機能と更新プログラム**に接続する方法の詳細については、「 [プライベートギャラリー](../extensibility/private-galleries.md)」を参照してください。  
  
- 拡張機能から抽出されたイメージファイル (スクリーンショットなど) を含むフォルダー。 atom.xml ファイルには、 **拡張機能と更新プログラム**で使用できるように、これらのイメージへの相対リンクが含まれています。  
  
  たとえば、フォルダーに次の2つの拡張機能を収集したとします。  
  
- Template_Wizard_239 .vsix。これは空の VSIX プロジェクトテンプレートです。  
  
- SelectionHighlight。 .vsix は、選択した単語のすべてのインスタンスを強調表示するツールです。  
  
  atom.xml ファイルの内容は、次の例のようになります。  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 2つのリンクタグが、生成されるイメージのフォルダー内のスクリーンショットを参照していることに注意してください。  
  
## <a name="see-also"></a>参照  
 [プライベート ギャラリー](../extensibility/private-galleries.md)
