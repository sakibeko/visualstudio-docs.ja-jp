---
title: データベースおよびデータ層アプリケーションの作成と管理
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851683"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Visual Studio でのデータベースおよびデータ層アプリケーションの作成と管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

重要]
> 以前のバージョンのに含まれていたデータベースプロジェクト [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] は、ツールで提供されるようになりました [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] 。 詳細については、「 [SQL Server Developer ツール](https://msdn.microsoft.com/library/hh272686(VS.103).aspx)」を参照してください。

 データベースプロジェクトを使用して、新しいデータベース、新しいデータ層アプリケーション (Dac) を作成したり、既存のデータベースおよびデータ層アプリケーションを更新したりできます。 データベースプロジェクトと DAC プロジェクトの両方を使用すると、これらの手法をマネージコードまたはネイティブコードに適用するのとほぼ同じ方法で、データベース開発作業にバージョンコントロールおよびプロジェクト管理手法を適用できます。 *DAC プロジェクト*、*データベースプロジェクト*、または*サーバープロジェクト*を作成してバージョン管理することにより、開発チームがデータベースおよびデータベースサーバーの変更を管理するのに役立ちます。 チームのメンバーは、ファイルをチェックアウトして、 *分離開発環境*またはサンドボックスで変更を行ってビルドし、テストしてから、チームと共有することができます。 コードの品質を確保するために、チームは、変更を運用環境に配置する前に、ステージング環境でデータベースの特定のリリースに関するすべての変更を完了し、テストすることができます。

 データ層アプリケーションでサポートされているデータベース機能の一覧については、Microsoft web サイトの「 [データ層アプリケーションでサポートされる機能](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) 」を参照してください。 データ層アプリケーションでサポートされていない機能をデータベースで使用する場合は、代わりにデータベースプロジェクトを使用して、データベースへの変更を管理する必要があります。

## <a name="common-high-level-tasks"></a>一般的な概要タスク

|高レベルタスク|関連する参照先|
|----------------------|------------------------|
|**データ層アプリケーションの開発を開始します。** DAC は、で導入された新しい概念です。これには、 [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] データベースの定義 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と、クライアント/サーバーまたは3層アプリケーションによって使用されるサポートインスタンスオブジェクトが含まれています。 DAC には、テーブルやビューなどのデータベースオブジェクトと共に、ログインなどのインスタンスエンティティが含まれます。 を使用すると、dac [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトを作成し、dac パッケージファイルを作成し、その dac パッケージファイルをデータベース管理者に送信して、データベースエンジンのインスタンスに配置することができ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。|-   [データ層アプリケーションの作成と管理](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (Microsoft web サイト)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**反復的なデータベース開発の実行:** 開発者またはテスト担当者の場合は、プロジェクトの一部をチェックアウトし、分離開発環境で更新します。 この種類の環境を使用すると、チームの他のメンバーに影響を与えることなく、変更をテストできます。 変更が完了したら、ファイルをバージョン管理に戻します。他のチームメンバーが変更を取得して、テストサーバーにビルドして配置することができます。|-   [クエリおよびテキストエディター (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft web サイト)<br />-   [Transact-sql デバッガー](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (Microsoft web サイト)|
|**プロトタイプの生成、テスト結果の検証、およびデータベーススクリプトとオブジェクトの変更:** エディターを使用して、 [!INCLUDE[tsql](../includes/tsql-md.md)] これらの一般的なタスクのいずれかを実行できます。|-   [クエリおよびテキストエディター (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft web サイト)|

## <a name="see-also"></a>参照
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)
