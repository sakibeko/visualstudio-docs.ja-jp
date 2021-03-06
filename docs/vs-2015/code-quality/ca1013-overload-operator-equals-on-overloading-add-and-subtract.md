---
title: 'CA1013: オーバーロードされた加算および減算 | で、演算子 equals をオーバーロードします。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545419"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013:オーバーロードする加算および減算で、演算子 equals をオーバーロードします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|値|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|カテゴリ|Microsoft Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック型またはプロテクト型で、等値演算子を実装しないまま、加算演算子または減算演算子を実装しています。

## <a name="rule-description"></a>ルールの説明
 加算や減算などの演算を使用して型のインスタンスを組み合わせることができる場合は、ほとんどの場合、 `true` 同じ構成値を持つ2つのインスタンスに対して返される等値を定義する必要があります。

 等値演算子のオーバーロードされた実装では、既定の等値演算子を使用できません。 そうすると、スタックオーバーフローが発生します。 等値演算子を実装するには、実装で Object.equals メソッドを使用します。 次の例を参照してください。

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、加算および減算演算子と数学的に一致するように等値演算子を実装します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 等値演算子の既定の実装で型の正しい動作が提供されている場合は、この規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例では、 `BadAddableType` この規則に違反する型 () を定義しています。 この型は、同じフィールド値を持つ2つのインスタンスが等しいかどうかをテストするために、等値演算子を実装する必要があり `true` ます。 この型は、修正され `GoodAddableType` た実装を示します。 この型は非等値演算子も実装し、 <xref:System.Object.Equals%2A> 他の規則を満たすようにオーバーライドすることに注意してください。 完全な実装でも、が実装 <xref:System.Object.GetHashCode%2A> します。

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>例
 次の例では、このトピックで以前に定義した型のインスタンスを使用して、等値演算子の既定の動作と正しい動作を示すことにより、等しいかどうかをテストします。

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **無効な型: {2,2} {2,2}等しいか?** 
 **適切な型がありません。 {3,3} {3,3} 等しいかどうかを確認してください。○** 
 **良好な種類: {3,3} {3,3} = =?  ○** 
 **正しくない型: {2,2} {9,9} 等しい** 
 **適切な型ではありません: {3,3} {9,9} = =?  いいえ**
## <a name="see-also"></a>参照
 [等値演算子](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
