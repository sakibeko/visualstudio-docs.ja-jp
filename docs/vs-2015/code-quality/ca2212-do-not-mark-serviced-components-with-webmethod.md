---
title: 'CA2212: サービスコンポーネントに WebMethod | を設定しません。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534564"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212:サービス コンポーネントを WebMethod に設定しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|値|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|カテゴリ|Microsoft. 使用方法|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 から継承される型のメソッド <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> は、でマークされ <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> ます。

## <a name="rule-description"></a>ルールの説明
 <xref:System.Web.Services.WebMethodAttribute> ASP.NET を使用して作成された XML Web サービス内のメソッドに適用されます。これにより、メソッドがリモート Web クライアントから呼び出すことができるようになります。 メソッドとクラスはパブリックであり、ASP.NET Web アプリケーションで実行されている必要があります。 <xref:System.EnterpriseServices.ServicedComponent> 型は COM + アプリケーションによってホストされ、COM + サービスを使用できます。 <xref:System.Web.Services.WebMethodAttribute> は、 <xref:System.EnterpriseServices.ServicedComponent> 同じシナリオを想定していないため、型には適用されません。 具体的には、メソッドに属性を追加し <xref:System.EnterpriseServices.ServicedComponent> ても、リモート Web クライアントからメソッドを呼び出すことはできません。 <xref:System.Web.Services.WebMethodAttribute>とメソッドには <xref:System.EnterpriseServices.ServicedComponent> コンテキストおよびトランザクションフローの動作と要件が競合しているため、メソッドの動作は一部のシナリオでは正しくありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッドから属性を削除し <xref:System.EnterpriseServices.ServicedComponent> ます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 これらの要素を組み合わせた方が正しいシナリオはありません。

## <a name="see-also"></a>参照
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
