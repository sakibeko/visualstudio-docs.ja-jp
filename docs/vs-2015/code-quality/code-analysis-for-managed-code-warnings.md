---
title: マネージコードの警告のコード分析 |Microsoft Docs
ms.date: 08/31/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: mikadumont
ms.author: midumont
manager: wpickett
ms.openlocfilehash: e689d137e071096d096e117ef3b79df405a060ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285750"
---
# <a name="net-code-analysis-rules"></a>.NET コード分析規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

マネージド コード分析ツールには、マネージド コード ライブラリの規則違反を示す警告機能があります。 警告は、デザイン、ローカリゼーション、パフォーマンス、セキュリティなどの規則の区分に分類されています。 個々の警告によって、マネージド コード分析規則の違反がわかります。 ここでは、マネージド コード分析の各警告について、詳細な説明と例を紹介します。

 次の表に、各警告で示される情報の種類を示しています。

|項目|説明|
|----------|-----------------|
|Type|規則の TypeName。|
|CheckId|規則の一意の識別子。 CheckId とカテゴリは、ソース内で警告の省略表記として使用されます。|
|カテゴリ|警告のカテゴリ。|
|互換性に影響する変更点|規則違反を修正することが、互換性に影響する変更点かどうかを示します。 互換性に影響する変更点とは、違反の原因となった対象に対して依存関係を持つアセンブリが、新たに修正したバージョンで再コンパイルされないこと、または変更によって実行時にエラーになる可能性があることを示します。 複数の修正を適用でき、互換性に影響する変更点があるものとないものがある場合、"あり" と "なし" を併記しています。|
|原因|規則に従って警告が生成される原因になった特定のマネージド コード。|
|Description|警告の背景にある問題について説明します。|
|違反の修正方法|規則に適合し、警告が生成されないようにソース コードを変更する方法について説明します。|
|警告を抑制する状況|規則による警告を抑制しても安全な場合について説明します。|
|コード例|規則に違反する例と、規則に適合する修正した例を示します。|
|関連する警告|関連する警告。|

## <a name="in-this-section"></a>このセクションの内容

|Item|値|
|-|-|
|[CheckId 別の警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|すべての警告を CheckId 別に一覧表示します。|
|[暗号化の警告](../code-quality/cryptography-warnings.md)|暗号化の適切な使用によって、より安全なライブラリとアプリケーションをサポートする警告です。|
|[デザインの警告](../code-quality/design-warnings.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] デザイン ガイドラインで規定されている、適切なライブラリ デザインをサポートする警告です。|
|[グローバリゼーションの警告](../code-quality/globalization-warnings.md)|国際対応ライブラリおよびアプリケーションをサポートする警告です。|
|[相互運用性の警告](../code-quality/interoperability-warnings.md)|COM クライアントとの相互作用をサポートする警告です。|
|[保守容易性に関する警告](../code-quality/maintainability-warnings.md)|ライブラリとアプリケーションの保守をサポートする警告です。|
|[モビリティの警告](../code-quality/mobility-warnings.md)|効率的な電力の使用法をサポートする警告です。|
|[名前付けに関する警告](../code-quality/naming-warnings.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] デザイン ガイドラインの名前付け規則の順守をサポートする警告です。|
|[パフォーマンスの警告](../code-quality/performance-warnings.md)|高パフォーマンスのライブラリとアプリケーションをサポートする警告です。|
|[移植性に関する警告](../code-quality/portability-warnings.md)|異なるプラットフォーム間の移植性をサポートする警告です。|
|[信頼性の警告](../code-quality/reliability-warnings.md)|メモリやスレッドの適切な使用など、ライブラリとアプリケーションの信頼性をサポートする警告です。|
|[セキュリティの警告](../code-quality/security-warnings.md)|より安全なライブラリとアプリケーションをサポートする警告です。|
|[使用状況に関する警告](../code-quality/usage-warnings.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]の適切な使用をサポートする警告です。|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|チェックインにおいてコード分析ポリシーに適合しない場合に発生するエラーです。|
