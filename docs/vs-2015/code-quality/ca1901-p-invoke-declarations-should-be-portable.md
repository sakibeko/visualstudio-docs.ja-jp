---
title: 'CA1901: P-Invoke 宣言は portable | である必要があります。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e669d87ad5ecc53c1523db16ab77578c6a703a33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545263"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: P/Invoke 宣言はポータブルでなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|値|
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|カテゴリ|Microsoft. 移植性|
|互換性に影響する変更点|中断-P/Invoke がアセンブリの外部で参照可能である場合。 非中断-P/Invoke がアセンブリの外部で参照できない場合。|

## <a name="cause"></a>原因
 このルールは、P/Invoke の各パラメーターと戻り値のサイズを評価し、32ビットおよび64ビットのプラットフォームでアンマネージコードにマーシャリングされたときのサイズが正しいことを確認します。 この規則の最も一般的な違反は、プラットフォームに依存するポインターサイズの変数が必要な固定サイズの整数を渡すことです。

## <a name="rule-description"></a>ルールの説明
 次のいずれかのシナリオがこの規則に違反しています。

- 戻り値またはパラメーターは、として型指定する必要がある場合、固定サイズの整数として型指定され `IntPtr` ます。

- 戻り値またはパラメーターは、 `IntPtr` 固定サイズの整数として型指定する必要があるときに、として型指定されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 またはを使用して、またはではなくハンドルを表すことで、この違反を修正できます `IntPtr` `UIntPtr` `Int32` `UInt32` 。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この警告を抑制しないでください。

## <a name="example"></a>例
 次の例は、このルールの違反を示しています。

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 この例では、 `nIconIndex` パラメーターはとして宣言されてい `IntPtr` ます。これは32ビットプラットフォームでは幅が4バイト、64ビットプラットフォームでは幅が8バイトです。 次のアンマネージ宣言で `nIconIndex` は、がすべてのプラットフォームの4バイト符号なし整数であることがわかります。

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>例
 違反を修正するには、次のように宣言を変更します。

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>参照
 [移植性に関する警告](../code-quality/portability-warnings.md)
