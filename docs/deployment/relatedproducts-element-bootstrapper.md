---
title: '&lt;"関連性のある製品" &gt; 要素 (ブートストラップ) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42756b21e631ec14e9c590833f6f0e95a317cc22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "66747465"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;"関連性のある製品" &gt; 要素 (ブートストラップ)
要素は、 `RelatedProducts` または現在の製品に含まれている他の製品を定義します。

## <a name="syntax"></a>構文

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>要素と属性
 要素は `RelatedProducts` 要素の子です `Product` 。 属性はありません。

## <a name="dependsonproduct"></a>依存 Sonproduct
 要素は、 `DependsOnProduct` 現在の製品が名前付き製品に依存していること、および指定された製品を現在の製品より前にインストールする必要があることを示します。 これは要素の子です `RelatedProducts` 。 `RelatedProducts`要素には、1つまたは複数の要素を含めることができ `DependsOnProduct` ます。

 `DependsOnProduct` には次の属性があります。

|属性|説明|
|---------------|-----------------|
|`Code`|要素の属性によって指定された、含まれている製品のコード名 `ProductCode` `Product` 。 詳細については、[\<Product> 要素](../deployment/product-element-bootstrapper.md)に関するページを参照してください。|

## <a name="eitherproducts"></a>製品
 `EitherProducts`要素は0個以上 `DependsOnProduct` の要素を定義し、属性はありません。 `DependsOnProduct`このセット内の少なくとも1つは、現在の製品の前にインストールする必要があります。 要素には、 `RelatedProducts` 0 個以上の要素を含めることができ `EitherProducts` ます。

## <a name="includesproduct"></a>IncludesProduct
 要素は、 `IncludesProduct` 製品が現在のインストールに含まれており、個別にインストールする必要がないことを示します。 これは要素の子です `RelatedProducts` 。 `RelatedProducts`要素には、1つまたは複数の要素を含めることができ `IncludesProduct` ます。

 `IncludesProduct` には次の属性があります。

|属性|説明|
|---------------|-----------------|
|`Code`|要素の属性によって指定された、含まれている製品のコード名 `ProductCode` `Product` 。 詳細については、[\<Product> 要素](../deployment/product-element-bootstrapper.md)に関するページを参照してください。|

## <a name="example"></a>例
 次のコード例では、Microsoft インストーラーが .NET Framework と共にインストールされるように指定します。そのため、個別にインストールする必要はありません。

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>関連項目
- [\<Product> element](../deployment/product-element-bootstrapper.md)