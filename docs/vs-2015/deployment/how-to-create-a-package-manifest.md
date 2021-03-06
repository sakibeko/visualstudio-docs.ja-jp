---
title: '方法: パッケージマニフェストを作成する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153834"
---
# <a name="how-to-create-a-package-manifest"></a>方法: パッケージ マニフェストを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーションの前提条件を展開するには、ブートストラップパッケージを使用します。 ブートストラップパッケージには、1つの製品マニフェストファイルが含まれていますが、各ロケールのパッケージマニフェストが含まれています。 ローカライズされたさまざまなバージョンの共有機能は、製品マニフェストに入ります。  
  
 パッケージマニフェストの詳細については、「 [方法: 製品マニフェストを作成](../deployment/how-to-create-a-product-manifest.md)する」を参照してください。  
  
## <a name="creating-the-package-manifest"></a>パッケージマニフェストの作成  
  
#### <a name="to-create-the-package-manifest"></a>パッケージマニフェストを作成するには  
  
1. ブートストラップパッケージ用のディレクトリを作成します。 この例では、C:\ packageを使用します。  
  
2. ロケールの名前 (英語の場合は en など) を使用してサブディレクトリを作成します。  
  
3. Visual Studio で、という名前の XML ファイルを作成 `package.xml` し、c:\ フォルダーに保存します。  
  
4. ブートストラップパッケージの名前、このローカライズされたパッケージマニフェストのカルチャ、およびオプションの使用許諾契約の一覧を表示するには、XML を追加します。 次の XML は、 `DisplayName` 以降の `Culture` 要素で定義されている変数とを使用します。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. ロケール固有のディレクトリにあるすべてのファイルを一覧表示するには、XML を追加します。 次の XML は、 **en** ロケールに適用される eula.txt という名前のファイルを使用します。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. ブートストラップパッケージのローカライズ可能な文字列を定義するための XML を追加します。 次の XML は、en ロケールのエラー文字列を追加します。  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. C:\ パッケージフォルダーを Visual Studio ブートストラップディレクトリにコピーします。 Visual Studio 2010 の場合、これは SDKs\Windows\v7.0A\Bootstrapper\Packages ディレクトリです。  
  
## <a name="example"></a>例  
 パッケージマニフェストには、エラーメッセージ、ソフトウェアライセンス条項、言語パックなど、ロケール固有の情報が含まれています。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)
