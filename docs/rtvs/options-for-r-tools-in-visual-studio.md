---
title: R Tools のオプション
description: Visual Studio での R 言語および関連する機能のオプションに関するリファレンスです。
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c7c2cb57dc96d7bb0df09248eb7a877820e50521
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315084"
---
# <a name="r-tools-for-visual-studio-options"></a>R Tools for Visual Studio オプション

設定には **[R Tools]**  >  **[オプション]** メニューの順に選択してアクセスできます。あるいは、 **[ツール]**  >  **[オプション]** の順に選択し、 **[R Tools]** までスクロールしてください。

  ![R Tools のオプション ダイアログ](media/options-dialog.png)

R に固有のオプションと設定には、次の方法を使用してアクセスします。 以下のセクションがすべて表示されるようにするには、 **[オプション]** ダイアログ ボックスの下部にある **[すべての設定を表示]** ボックスを選択する必要があります。

- コードの書式オプション (「[エディター オプション](editing-r-code-in-visual-studio.md#editor-options)」を参照): **[ツール]**  >  **[オプション]** メニューの順に移動し、 **[テキスト エディター]**  >  **[R]**  >  **[書式設定]** の順に選択します。
- リンター オプション (「[Lint](linting-r-code.md)」を参照): **[ツール]**  >  **[オプション]** メニューの順に移動し、 **[テキスト エディター]**  >  **[R]**  >  **[Lint]** の順に選択します。
- 詳細エディター オプション ([こちらの記事の説明を参照](#text-editor--r--advanced-options)): **[ツール]**  >  **[オプション]** メニューの順に移動し、 **[テキスト エディター]**  >  **[R]**  >  **[詳細設定]** の順に選びます。
- 動作オプション ([こちらの記事の説明を参照](#r-tools--advanced-options)): **[R Tools]**  >  **[オプション]** の順に移動するか、 **[ツール]**  >  **[オプション]** の順に移動し、 **[R Tools]** までスクロールします。

**[R Tools]**  >  **[データ サイエンスの設定]** コマンドは、Visual Studio 全体のさまざまな設定にも影響します。 このオプションについては、次のセクションで説明します。

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>[R Tools] > [データ サイエンスの設定]

**[R Tools] には、[データ サイエンスの設定]** というメニュー項目があります。この項目では、データ サイエンティストのニーズに合わせて最適に作られたレイアウトで Visual Studio IDE を構成できます。 具体的には、このオプションで [[インタラクティブ]](interactive-repl-for-r-in-visual-studio.md)、[[変数エクスプローラー]](variable-explorer.md)、[[ワークスペース]](r-workspaces-in-visual-studio.md) というウィンドウが開きます。

![Visual Studio のデータ サイエンティスト ウィンドウ レイアウト](media/installation-data-scientist-layout-result.png)

後で他の Visual Studio 設定に戻るには、最初に **[ツール]**  >  **[設定のインポートとエクスポート]** コマンドを使用します。 **[選択された環境設定をエクスポート]** を選択し、ファイル名を指定します。 それらの設定を復元するには、同じコマンドを使用し、 **[選択された環境設定をインポート]** を選択します。 データ サイエンティスト レイアウトを変更し、後でそれに戻る場合、同じコマンドを使用することもできます ( **[データ サイエンスの設定]** コマンドを直接使用するのではなく)。

## <a name="text-editor--r--advanced-options"></a>[テキスト エディター] > [R] > [詳細設定] オプション

これらのオプションでは、R における書式設定、IntelliSense、アウトライン表示、インデント、構文チェックの動作を制御します。

![R のテキスト エディターの [詳細設定] オプションの [オプション] ダイアログ](media/options-dialog-advanced-text-editor.png)

各オプションをオンまたはオフに設定して、対象の動作を制御します。 各オプションが及ぼす影響の詳細については、ダイアログ ボックスの下部にあるヘルプ ウィンドウを参照してください。 そのヘルプ ウィンドウの上部を上にドラッグすると、ウィンドウが拡大します。

![R テキスト エディターの詳細オプション ダイアログで、展開されているヘルプ ウィンドウ](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>[R Tools] > [詳細設定] オプション

**[R Tools]**  >  **[オプション]** メニュー コマンドの順に移動すると、 **[オプション]** ダイアログが開き、R オプションが表示されます。

  ![R Tools のオプション ダイアログ](media/options-dialog.png)

次のセクションでは、このページで利用できるさまざまなオプションについて説明します。

### <a name="debugging"></a>デバッグ

これらのオプションにより、[変数エクスプローラー](variable-explorer.md)と、ウォッチやローカルのような、デバッガー ウィンドウにおける値の処理方法が制御されます ([R コードのデバッグ](debugging-r-in-visual-studio.md)に関するページを参照してください)。

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| アクティブなバインドを評価 | `True` | `True` の場合、変数やプロパティを調べるとき、必ず最新の日付値が表示されるようにします。 式の実装方法によっては、式を評価すると思わぬ結果が引き出される可能性があるというリスクがあります。 |
| ドット プレフィックス付き変数を表示 | `False` | `.` がプレフィックスとして付いている変数を表示するかどうかを指定します。 |

### <a name="grid-view"></a>グリッド ビュー

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| 動的評価 | `False` | 既定では、`View(<expression>)` 関数は、データのスナップショットをデータ フレームとして取得しますが、大規模なデータ セットの場合、大量のメモリが消費される可能性があります。 このオプションを `True` に設定すると、グリッドが最新の情報に更新されるときに式が評価されて、表示されているそのデータのみがフェッチされます。 ただし、式が変化すると、データも変化します。このことは dplyr pip 式には適していない場合があります。 |

### <a name="help"></a>[Help]

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| F1 Web ブラウザー | `Internal` | **Ctrl**+**F1** キーを使用し、用語を探すときのヘルプの表示方法を制御します。 `Internal` に設定すると、Visual Studio のツール ウィンドウ内にヘルプが表示されます。 `External` に設定すると、既定の Web ブラウザーにヘルプが表示されます。 |
| F1 Web 検索文字列 | `R site:stackoverflow.com` | エディターで、ある用語の上で **Ctrl**+**F1** キーを押したときに検索用語が検索エンジンに渡される方法を制御します。 既定では、文字列は `R site:stackoverflow.com` です。これは `R` を検索用語に追加します。 `site:stackoverflow.com` は検索エンジンへのディレクティブであり、`stackoverflow.com` ドメイン内のページに検索範囲を絞るように伝えます。 |
| R ヘルプ ブラウザー | `Automatic` | **F1**、 **?** または **??** を使用し、R ドキュメントを探すときのヘルプの表示方法を制御します。 `Automatic` に設定すると、ヘルプが該当するウィンドウで表示されます。 たとえば、HTML ヘルプは Visual Studio ツール ウィンドウ内に表示され、PDF は既定の PDF プログラムに表示されます。 `External` に設定すると、既定の Web ブラウザーにヘルプが表示されます。 |

### <a name="history"></a>履歴

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| 履歴を常に保存 | `True` | プロジェクトを閉じたとき、RTVS が作業ディレクトリの *.RHistory* ファイルにコマンド履歴を書き込むかどうかを制御します。 プロジェクトを保存せずに終了した場合にも履歴は保存されます。 |
| 検索フィルターのリセット | `True` | R 履歴ダイアログのフィルター条件に部分文字列が一致するコマンドのみを表示するように履歴ウィンドウでコマンド履歴をフィルター処理できるかどうかを決定します。 この設定により、新しいコマンドを実行したとき、あるいは新しいプロジェクトに切り替え、別の *.RHistory* ファイルの読み込みをトリガーしたとき、履歴の検索フィルターをリセットするかどうかが決定されます。 既定の設定である `True` を指定した場合、フィルター セットを付けてコマンドを実行したとき、予想外の結果の表示が最小限に抑えられます。今しがた実行したコマンドが履歴に表示されないので、不思議に思うことになります。 |
| 複数行選択を使用 | `True` | 履歴の複数行ステートメントを 1 回のクリックで選択できるかどうかを指定します。 また、インタラクティブな Windows で、行ではなくステートメントで上下矢印を動かすことができます。 |

### <a name="html"></a>HTML

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| HTML ページ ブラウザー | `External` | `ggvis` プロットのようなコンテンツや `shiny` アプリケーションを表示する場所を決定します。 `Internal` では、Visual Studio のツール ウィンドウ内に HTML 出力が表示されます。`External` では、既定のブラウザーに HTML 出力が表示されます。 |

### <a name="logging"></a>ログ記録

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| ログ イベント | `Normal` | RTVS 診断に使用するログ記録の詳細度を制御します。 既定値の `Normal` の場合、`TEMP` ディレクトリにログ ファイルが作成されます。 `Traffic` に設定すると、すべてのコマンドとセッションにおける応答が RTVS により記録されます。 コンピューターに残しておくようなログ ファイルですが、RTVS の問題の診断に役に立つ場合があります。 |

### <a name="markdown"></a>Markdown

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| マークダウン プレビュー ブラウザー | `External` | RMarkdown HTML 出力が表示される場所を決定します。 `Internal` の場合、Visual Studio のツール ウィンドウ内に RMarkdown HTML ドキュメントが表示されます。`External` の場合、既定のブラウザーを利用して RMarkdown HTML が表示されます。 |

### <a name="r-engine"></a>R エンジン

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| コード ページ | `(OS Default)` | R のコード ページ (ロケール) を設定します。既定では、オペレーティング システムの基礎ロケールが使用されます。 |
| CRAN ミラー | `(Use .Rprofile)` | パッケージ インストールに既定の CRAN ミラーを設定します。 既定の設定の `Use .Rprofile` の場合、 *.RProfile* ファイルの CRAN ミラー設定を順守します。 |

### <a name="workspace"></a>ワークスペース

| オプション | 既定値 | [説明] |
| --- | --- | --- |
| プロジェクトを開くときにワークスペースを読み込む | `No` | `Yes` に設定すると、プロジェクトを開いたとき、 *.RData* ファイルからグローバル環境にセッション データが読み込まれます。 |
| リセット時にワークスペースを保存するためのダイアログを表示 | `Yes` | `No` に設定すると、インタラクティブな Window の [リセット] ボタンをクリックしたとき、ワークスペースを保存するように求められなくなります。 |
| プロジェクトを閉じるときにワークスペースを保存 | `No` | `Yes` に設定すると、プロジェクトを閉じたとき、 *.RData* ファイルにグローバル環境が保存されます。 |
| ワークスペースを切り替える前に確認ダイアログを表示する | `Yes` | `No` に設定すると、ワークスペースを切り替えるとき、ユーザーに確認が求められません。 「[ワークスペースの切り替え](r-workspaces-in-visual-studio.md#switch-between-workspaces)」を参照してください。 |
| マシン負荷インジケーターを表示する | `False` | ステータス バーにある CPU/メモリ/ネットワーク負荷インジケーターの表示を制御します。 インジケーターではネットワーク トラフィックが発生するため、リモート従量制課金シナリオではこの設定を `False` に保持しておくと便利です。 このオプションを変更するには、Visual Studio を再起動する必要があります。 |
