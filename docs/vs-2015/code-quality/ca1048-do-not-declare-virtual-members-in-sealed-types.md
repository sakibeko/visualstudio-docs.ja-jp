---
title: 'CA1048: SEALED: シールド型の仮想メンバーを宣言しません |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19ae3a4fdc620343f18aa0845c33e1d73529adfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546797"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048:シールド型の仮想メンバーを宣言しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|値|
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|カテゴリ|Microsoft Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型はシールされており、 `virtual` ( `Overridable` Visual Basic の) 両方であり、final ではないメソッドを宣言します。 この規則は、このパターンに従う必要があるデリゲート型の違反を報告しません。

## <a name="rule-description"></a>ルールの説明
 型でメソッドを仮想と宣言するのは、継承する型が仮想メソッドの実装をオーバーライドできるようにするためです。 定義上、シール型から継承することはできません。シール型の仮想メソッドを使用することは無意味です。

 Visual Basic .NET コンパイラと C# コンパイラでは、型がこの規則に違反することはありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッドを非仮想にするか、型を継承可能にしてください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 型を現在の状態のままにすると、メンテナンスの問題が発生する可能性があるため、利点はありません。

## <a name="example"></a>例
 次の例は、この規則に違反する型を示しています。

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
