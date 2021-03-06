---
title: VSPackage ファイルの場所を VS Shell に指定する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704978"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VSPackage ファイルの場所を VS Shell に指定する
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は、VSPackage を読み込むアセンブリ DLL を見つけることができる必要があります。 次の表で説明するように、さまざまな方法で見つけることができます。

| メソッド | 説明 |
| - | - |
| CodeBase レジストリキーを使用します。 | コードベースキーを使用すると、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 完全修飾ファイルパスから VSPackage アセンブリを読み込むことができます。 キーの値は、DLL へのファイルパスである必要があります。 これは、パッケージアセンブリを読み込むのに最適な方法です [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 この手法は、"コードベース/プライベートインストールディレクトリの手法" と呼ばれることもあります。 登録時に、コードベースの値が、型のインスタンスを介して登録属性クラスに渡され <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> ます。 |
| DLL を **Privateassemblies** ディレクトリに配置します。 | アセンブリをディレクトリの **Privateassemblies** サブディレクトリに配置し [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ます。 **Privateassemblies**にあるアセンブリは自動的に検出されますが、[**参照の追加**] ダイアログボックスには表示されません。 **Privateassemblies**と**publicassemblies**の違いは、 **publicassemblies**内のアセンブリが [参照の**追加**] ダイアログボックスで列挙されることです。 "CodeBase/private installation directory" 手法を使用しないことを選択した場合は、 **Privateassemblies** ディレクトリにをインストールする必要があります。 |
| 厳密な名前を持つアセンブリとアセンブリレジストリキーを使用します。 | アセンブリキーを使用して、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 厳密な名前付き VSPackage アセンブリを読み込むために明示的に指示することができます。 キーの値は、アセンブリの厳密な名前である必要があります。 |
| DLL を **Publicassemblies** ディレクトリに配置します。 | 最後に、アセンブリを **Publicassemblies** サブディレクトリに配置することもできます。 **Publicassemblies**にあるアセンブリは自動的に検出され、の [**参照の追加**] ダイアログボックスにも表示され [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ます。<br /><br /> VSPackage アセンブリは、他の VSPackage 開発者によって再利用されることを意図したマネージコンポーネントが含まれている場合にのみ、 **publicassemblies** ディレクトリに配置する必要があります。 アセンブリの大部分は、この条件を満たしていません。 |

> [!NOTE]
> すべての依存アセンブリに対して、厳密な名前の署名付きアセンブリを使用します。 これらのアセンブリは、独自のディレクトリまたはグローバルアセンブリキャッシュ (GAC) にもインストールする必要があります。 これにより、同じ基本ファイル名を持つアセンブリ (ウィーク名バインドと呼ばれる) との競合から保護されます。
