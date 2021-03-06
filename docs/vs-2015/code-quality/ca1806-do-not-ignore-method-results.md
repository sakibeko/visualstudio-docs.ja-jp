---
title: 'CA1806: メソッドの結果を無視しません |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 726cde42eb08ee5508481887fae2e9d2b059256c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543872"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806:メソッドの結果を無視しない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|値|
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|カテゴリ|Microsoft. 使用方法|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 この警告には、次のようないくつかの原因が考えられます。

- 新しいオブジェクトが作成されましたが、使用されませんでした。

- 新しい文字列を作成して返すメソッドが呼び出され、新しい文字列が使用されることはありません。

- 使用されていない HRESULT またはエラーコードを返す COM メソッドまたは P/Invoke メソッド。 ルールの説明

  不要なオブジェクトの作成と、使用されていないオブジェクトの関連するガベージコレクションにより、パフォーマンスが低下します。

  文字列は不変であり、ToUpper などのメソッドは、呼び出し元のメソッド内の文字列のインスタンスを変更するのではなく、文字列の新しいインスタンスを返します。

  HRESULT またはエラーコードを無視すると、エラー状態やリソース不足の状態で予期しない動作が発生する可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 メソッド A が使用されていない B オブジェクトの新しいインスタンスを作成する場合は、インスタンスを引数として別のメソッドに渡すか、インスタンスを変数に代入します。 オブジェクトの作成が不要な場合は、それを削除します。-または-

 メソッド A がメソッド B を呼び出しますが、メソッド B が返す新しい文字列インスタンスを使用しない場合。 インスタンスを引数として別のメソッドに渡し、インスタンスを変数に代入します。 不要な場合は、呼び出しを削除します。

 - または -

 メソッド A がメソッド B を呼び出しても、メソッドが返す HRESULT またはエラーコードを使用しない場合。 条件付きステートメントで結果を使用するか、変数に結果を代入するか、または別のメソッドに引数として渡します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 オブジェクトを作成する操作によって何らかの目的がある場合を除き、この規則による警告を抑制しないでください。

## <a name="example"></a>例
 次の例は、文字列 Trim の呼び出し結果を無視するクラスを示しています。

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>例
 次の例では、前の違反を修正しました。この結果は、呼び出された変数に代入して戻します。

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>例
 次の例は、作成したオブジェクトを使用しないメソッドを示しています。

> [!NOTE]
> Visual Basic でこの違反を再現することはできません。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>例
 次の例では、オブジェクトの不要な作成を削除することによって、以前の違反を修正します。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>例
 次の例は、ネイティブメソッドの Get短いパス名が返すエラーコードを無視するメソッドを示しています。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>例
 次の例では、エラーコードをチェックし、呼び出しが失敗したときに例外をスローすることによって、以前の違反を修正します。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]