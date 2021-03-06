---
title: エンコードされる URI に無効な文字 | が含まれています。Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6091968dcbdd98240b1705e0fa7dc855dad3bda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816073"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>エンコードする URI は無効な文字を含んでいます。
文字列を URI (Uniform Resource Identifier) としてエンコードしようとしましたが、無効な文字が含まれていました。 Uri に変換する文字列内では、ほとんどの文字が有効ですが、一部の Unicode 文字シーケンスは無効です。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- エンコードする文字列に有効な Unicode シーケンスだけが含まれていることを確認してください。 完全な URI は、一連のコンポーネントと区切り記号で構成されます。 山かっこで囲まれた名前はコンポーネントを表し、":"、"/"、";"、および "?" は、区切り記号として使用される予約文字です。 一般的な形式は次のとおりです。  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 関数](../../javascript/reference/encodeuricomponent-function-javascript.md)