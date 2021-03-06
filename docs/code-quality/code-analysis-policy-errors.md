---
title: Code Analysis Policy Errors
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac7a949b3f8a1e0c9d44c6194f87745b4e3f17a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587746"
---
# <a name="code-analysis-policy-errors"></a>Code Analysis Policy Errors

以下のエラーは、チェックインにおいてコード分析ポリシーに適合しない場合に発生します。

**1 つ以上のプロジェクトのコード分析設定がコード分析ポリシーに準拠していません。**

プロジェクトソース管理にチェックインするコード分析の要件が、1つ以上のコードプロジェクトで満たされませんでした。 このエラーは、次に示す 1 つ以上の条件によって発生します。

- ソリューション内のすべてのプロジェクトで、ビルドに対してコード分析が有効になっていない。

- Visual studio でのプロジェクトのローカル規則セットには、プロジェクト規則セットよりも制限の緩い**アクション**設定があります。たとえば、サーバーで **[アクション**エラー] に設定されているルールのアクションは、 = **Error** visual studio で実行されているルールセットでは [**警告**] または **[なし**] に設定されています。 **Action**

- Visual Studio で指定された規則セットには、プロジェクトのコード分析チェックインポリシーで指定された規則セットに指定されているすべての規則が含まれていません。

**コード分析ポリシーが失敗しました。プロジェクトにエラーがある {0} か、ビルドが最新ではありません。**

ビルドにエラーがあるか、エラーが修正された後にコード分析が実行されませんでした。

**チェックインに失敗しました。コード分析ポリシーを使用するには、Visual Studio でソリューションを開いてチェックインする必要があります。**

コード分析ポリシーには、チェックインするファイルがすべて現在開いているソリューションに含まれていなければならないと規定されています。 このエラーを修正するには、チェックインするファイルが含まれるソリューションを開きます。

**保留中のチェックインのいくつかのファイルが、現在開いているソリューション内にありません。**

コード分析ポリシーには、チェックインするファイルがすべて現在開いているソリューションに含まれていなければならないと規定されています。 このエラーは、ソリューションは開いているものの [保留中のチェックイン] ビューに表示されているファイルの中に現在開いているソリューションに属していないものがある場合に発生します。 このエラーを修正するには、チェックインするファイルが含まれるソリューションを開きます。

**' ' のバージョン {0} が正しくありません。ポリシーで指定された厳密な名前は ' {1} ' です。**

このエラーは、.NET プロジェクトで発生します。 コード分析ポリシーで必要な規則の .dll がローカル コンピューターに存在しますが、バージョンまたは公開キーが一致しません。 このエラーを解決するには、ポリシー作成者がコンピューターの*C:\Program Tools\FxCop\Rules \\ Visual Studio 8 \ Team ツールの静的分析*のディレクトリにある .dll を更新する必要があります。

**{0}ポリシーで指定された ' ' アセンブリは存在しません。**

このエラーは、.NET プロジェクトで発生します。 コード分析ポリシーで必要な規則に対応する dll が、クライアント コンピューターにインストールされていません。 このエラーを修正するには、ポリシー作成者がコンピューターの*C:\Program Tools\FxCop\Rules \\ Visual Studio 8 \ Team ツールの静的分析*のディレクトリにある dll を更新する必要があります。

**プロジェクト {0} 規則の設定は、コード分析ポリシーに準拠していません。**

このエラーは、.NET プロジェクトで発生します。 マネージド コード規則の設定が、ポリシーで要求されている厳密さを満たしていません。 このエラーを修正するには、クライアント設定をサーバー側のポリシー要件と同等以上に厳密にします。

**アクティブな構成でコード分析が有効になっていません。チェックイン {0} する前に、[構成] に切り替えてプロジェクトをビルドし {1} ます。**

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、アクティブ構成ではコード分析は有効ではありませんが、有効になっているコード分析が少なくとも 1 つあります。

**チェックイン {0} する前に、プロジェクトのプロパティとビルドでマネージバイナリのコード分析を有効にする必要があります。**

このエラーは、[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .NET アプリケーションで発生します。 ポリシーでは、マネージド コード分析の実行を要求していますが、クライアント上の現在のプロジェクトでは有効になっていません。

**チェックイン {0} する前に、プロジェクトのプロパティとビルドでコード分析を有効にする必要があります。**

このエラーは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 、プロジェクトと web プロジェクトに適用されます。 ポリシーでは、マネージド コード分析の実行を要求していますが、クライアント上の現在のプロジェクトでは有効になっていません。

**チェックイン {0} する前に、プロジェクトのプロパティとビルドで C/c + + コード分析を有効にする必要があります。**

このエラーは、アンマネージ プロジェクトで発生します。 コード分析ポリシーでは、C/C++ のコード分析の実行を要求していますが、クライアント上の現在のプロジェクトでは有効になっていません。

## <a name="see-also"></a>こちらもご覧ください

- [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)
