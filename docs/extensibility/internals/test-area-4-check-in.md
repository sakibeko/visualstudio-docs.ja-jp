---
title: 'テスト領域 4: チェックイン |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704574"
---
# <a name="test-area-4-check-in"></a>テスト領域 4: チェックイン
このソース管理プラグインのテスト領域では、[ **チェックイン** ] コマンドを使用して、更新された項目をバージョンストアに送信します。

## <a name="command-menu-access"></a>コマンドメニューへのアクセス
 テストケースでは、次の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 統合開発環境メニューパスが使用されます。

##### <a name="check-in"></a>チェックイン:
 [**ファイル**]、[**ソース管理**]、[**チェックイン**]。

 **ファイル**を **チェックイン**します。

 ショートカットメニューの [ **チェックイン**]。

## <a name="common-expected-behavior"></a>想定される一般的な動作

- ソース管理下にあるソリューションまたはプロジェクトに追加されたプロジェクトとファイルは、[ **チェックイン** ] ダイアログボックスと [ **保留中のチェックイン** ] ウィンドウに表示されます。

- チェックインの後、追加した項目がソース管理に表示されます。

- チェックインの後に、更新された項目がストアで適切にバージョン管理されます。

## <a name="test-cases"></a>テスト ケース
 次に、チェックインテスト領域の特定のテストケースを示します。

### <a name="case-4a-modified-items"></a>ケース 4a: 変更された項目
 [チェックイン] アクションを使用して、変更されたソース管理下にあるファイルを更新する方法について説明します。

|アクション|テストステップ|確認が必要な結果|
|------------|----------------|--------------------------------|
|チェックアウトされたテキストファイルを変更する (**[チェックイン] ダイアログボックス** )|1. テキストファイルで新しいプロジェクトを作成します。<br />2. ソース管理にソリューションを追加します。<br />3. テキストファイルをチェックアウトして変更します。<br />4. [チェックイン] ダイアログボックス ([**ファイル**]、[ **ソース管理**]、[ **チェックイン**]) を使用してチェックインします。|予期される動作は一般的です。|
|チェックアウトされたテキストファイルを変更する、[ファイルのみをチェックイン] ([**保留中のチェックイン** ] ウィンドウ)|1. テキストファイルで新しいプロジェクトを作成します。<br />2. ソース管理にソリューションを追加します。<br />3. テキストファイルをチェックアウトして変更します。<br />4. [ **保留中のチェックイン** ] ウィンドウでチェックインします。|予期される動作は一般的です。|

### <a name="case-4b-adding-files"></a>ケース 4b: ファイルの追加
 プロジェクトまたはソリューションの項目にファイルを追加する場合は、プロジェクトまたはソリューションも変更する必要があります。 したがって、親ファイルもチェックアウトされます。追加を完了するには、このファイルをチェックインする必要があります。

|アクション|テストステップ|確認が必要な結果|
|------------|----------------|--------------------------------|
|テキストファイルを追加してすべてをチェックインする (**[チェックイン** ] ダイアログボックス)|1. 新しいプロジェクトを作成します。<br />2. ソース管理にソリューションを追加します。<br />3. プロジェクトにテキストファイルを追加します。<br />4. 要求された場合は、プロジェクトのチェックアウトを受け入れます。<br />5. **ソリューションエクスプローラー**でソリューションを選択します。<br />6. **[チェックイン] ダイアログボックス** からチェックインします。|予期される動作は一般的です。|
|テキストファイルを追加し、すべてをチェックインする ([**保留中のチェックイン** ] ウィンドウ)|1. 新しいプロジェクトを作成します。<br />2. ソース管理にソリューションを追加します。<br />3. プロジェクトにテキストファイルを追加します。<br />4. 要求された場合は、プロジェクトのチェックアウトを受け入れます。<br />5. [ **保留中のチェックイン** ] ウィンドウからソリューションをチェックインします。|想定される一般的な動作|

### <a name="case-4c-adding-projects"></a>ケース 4c: プロジェクトの追加
 ソリューションにプロジェクトを追加する場合は、ソリューションも変更する必要があります。 そのため、ソリューションファイルもチェックアウトされるため、追加を完了するにはチェックインする必要があります。

|アクション|テストステップ|確認が必要な結果|
|------------|----------------|--------------------------------|
|[ソース管理 **] ダイアログボックスで空** のソリューションにプロジェクトを追加する|1. 空のソリューションを作成します。<br />2. ソース管理にソリューションを追加します。<br />3. 新しいプロジェクトを追加します。<br />4. メッセージが表示されたら、ソリューションのチェックアウトを受け入れます。<br />5. **[チェックイン] ダイアログボックス** からチェックインします。|予期される動作は一般的です。|
|[ソース管理] ([**保留中のチェックイン** ] ウィンドウ) で、空のソリューションにプロジェクトを追加する|1. 空のソリューションを作成します。<br />2. ソース管理にソリューションを追加します。<br />3. 新しいプロジェクトを追加します。<br />4. メッセージが表示されたら、ソリューションのチェックアウトを受け入れます。<br />5. [ **保留中のチェックイン** ] ウィンドウからソリューションをチェックインします。|予期される動作は一般的です。|

## <a name="see-also"></a>関連項目
- [ソース管理プラグイン向けのテスト ガイド](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
