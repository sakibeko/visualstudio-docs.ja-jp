---
title: コード マップ
ms.date: 05/16/2018
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 771a6ccf4749a3464204d3da75f4d403d1ab2dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532718"
---
# <a name="map-dependencies-with-code-maps"></a>依存関係をコードマップとマップする

コードマップを作成することによって、コード間の依存関係を視覚化できます。 コードマップを使用すると、ファイルやコード行を読まなくても、コードがどのように適合するかを確認できます。

![Visual Studio でコードマップを使用して依存関係を表示する](../modeling/media/codemapsmainintro.png)

コードマップを作成および編集するには Visual Studio Enterprise エディションが必要です。 Visual Studio Community および Professional エディションでは、Enterprise edition で生成されたダイアグラムを開くことができますが、編集することはできません。

> [!NOTE]
> Visual Studio Enterprise で作成されたマップを Visual Studio Professional を使用する他のユーザーと共有する前に、マップのすべての項目 (非表示項目、展開されたグループ、グループ間リンクなど) が表示されていることを確認してください。

次の言語でコードの依存関係をマップできます。

- ソリューションまたはアセンブリ内の Visual C# または Visual Basic (*.dll* または *.exe*)

- Visual C++ プロジェクト、ヘッダーファイル (*.h* または `#include` )、またはバイナリのネイティブまたはマネージ c または C++ コード

- Microsoft Dynamics AX の .NET モジュールから作られた X++ プロジェクトおよびアセンブリ

> [!NOTE]
> C# または Visual Basic 以外のプロジェクトの場合、コードマップを開始したり、既存のコードマップに項目を追加したりするためのオプションはほとんどありません。 たとえば、C++ プロジェクトのテキスト エディター内のオブジェクトを右クリックすることも、コード マップにそのオブジェクト追加することもできません。 ただし、 **ソリューションエクスプローラー**、 **クラスビュー**、および **オブジェクトブラウザー**から個々のコード要素またはファイルをドラッグアンドドロップすることができます。

## <a name="install-code-map-and-live-dependency-validation"></a>コードマップとライブ依存関係検証のインストール

Visual Studio でコードマップを作成するには、最初に **コードマップ** と **ライブ依存関係検証** コンポーネントをインストールします。

1. **Visual Studio インストーラー**を開きます。 Windows の [スタート] メニューから開くことも、Visual Studio 内で [**ツール**] [  >  **ツールと機能の取得**] を選択して開くこともできます。

1. **[個々のコンポーネント]** タブを選択します。

1. [ **コードツール** ] セクションまで下にスクロールし、[ **コードマップ** ] と [ **ライブ依存関係の検証**] を選択します。

   ![Visual Studio インストーラーのコードマップとライブ依存関係検証コンポーネント](media/modeling-components.png)

1. **[変更]** を選択します。

   **コードマップ**と**ライブ依存関係検証**コンポーネントは、インストールを開始します。 Visual Studio を閉じるように求められる場合があります。

## <a name="add-a-code-map"></a>コードマップの追加

空のコードマップを作成し、アセンブリ参照、ファイル、フォルダーなどの項目をドラッグしたり、ソリューションの全体または一部のコードマップを生成したりすることができます。

空のコードマップを追加するには、次のようにします。

1. **ソリューション エクスプローラー**で、最上位のソリューション ノードのショートカット メニューを表示します。 [ **Add**  >  **新しい項目**の追加] を選択します。

2. [ **新しい項目の追加** ] ダイアログの [ **インストール済み**] の下で、[ **全般** ] カテゴリを選択します。

3. **有向グラフドキュメント (.dgml)** テンプレートを選択し、[**追加**] を選択します。

   > [!TIP]
   > このテンプレートはアルファベット順に表示されない場合があるため、テンプレートリストの一番下まで下にスクロールします (表示されない場合)。

   ソリューションの [ **ソリューション項目** ] フォルダーに空のマップが表示されます。

同様に、[**アーキテクチャ**] [  >  **新しいコードマップ**] または [**ファイル**] [  >  **新しい**  >  **ファイル**] の順に選択すると、ソリューションに追加せずに新しいコードマップファイルを作成できます。

## <a name="generate-a-code-map-for-your-solution"></a>ソリューションのコードマップを生成する

ソリューション内のすべての依存関係を表示するには、次のようにします。

1. メニューバーで、[**アーキテクチャ**] [  >  **ソリューションのコードマップの生成**] の順に選択します。 最後にビルドしてからコードが変更されていない場合は、[**アーキテクチャ**] [  >  **ソリューションのコードマップを生成**する] を選択します。

   ![コード マップ生成コマンド](../modeling/media/codemapsarchitecturemenu.png)

   最上位レベルのアセンブリと、それらの間の集約されたリンクを示すマップが生成されます。 集約リンクを広げると、表される依存関係が多くなります。

2. コード マップ ツールバーの **[凡例]** ボタンを使用して、プロジェクトの種類のアイコン (テスト プロジェクト、Web プロジェクト、Phone プロジェクトなど)、コード項目 (クラス、メソッド、プロパティなど)、および関係の種類 (継承元、実装、呼び出しなど) のリストを表示または非表示にします。

   ![アセンブリの最上位の依存関係グラフ](../modeling/media/dependencygraph_toplevelassemblies.png)

   このソリューション例には、ソリューション フォルダー (**[テスト]** と **[コンポーネント]**)、テスト プロジェクト、Web プロジェクト、およびアセンブリが含まれています。 既定では、コンテインメイト リレーションシップはすべて、展開および折りたたみができる *グループ*として表示されます。 **[外部]** グループには、プラットフォームの依存関係など、ソリューションの外部のものがすべて含まれます。 外部アセンブリには、使用中の項目のみが表示されます。 既定では、視認性を高めるため、システムの基本型はマップに表示されません。

3. マップをドリル ダウンするには、プロジェクトおよびアセンブリを表すグループを展開します。 **CTRL キーを押しながら A キー** を押してすべてのノードを選択し、ショートカット メニューから **[グループ]**、 **[展開]** の順に選択すると、すべてを展開できます。

   ![コード マップ内のすべてのグループを展開する](../modeling/media/codemapsexpandallgroups.png)

4. ただし、これは大規模なソリューションには不向きな場合があります。 実際、複雑なソリューションでは、メモリ制限のためにすべてのグループを展開できない場合があります。 代わりに、個々のノードを展開して内部を表示します。 マウス ポインターをノード上に移動し、シェブロン (下矢印) が表示されたらクリックします。

   ![コード マップ内のノードを展開する](../modeling/media/dependencygraph_containment.png)

   または、キーボードを使用して項目を選択し、プラスキー () を押し **+** ます。 さらに深いレベルのコードを確認するには、名前空間、型、およびメンバーに対して同じ操作を行います。

   > [!TIP]
   > マウス、キーボード、およびタッチを使用したコードマップの操作の詳細については、「 [コードマップの参照および再配置](../modeling/browse-and-rearrange-code-maps.md)」を参照してください。

5. マップを簡略化し個々の部分に注目するには、コード マップ ツールバーで **[フィルター]** を選択し、必要なノードおよびリンクの種類だけを選択します。 たとえば、すべてのソリューション フォルダーとアセンブリのコンテナーを非表示にできます。

   ![コンテナーをフィルター処理して、マップを簡略化する](../modeling/media/codemapsfilterfoldersassemblies.png)

   個々のグループおよび項目をマップで非表示にしたりマップから削除したりして、マップを簡略化できます。この操作は、基のソリューション コードには影響を与えません。

6. 項目間のリレーションシップを表示するには、マップでそれらを選択します。 リンクの色は、 **[凡例]** ウィンドウの表示に対応しており、リレーションシップの種類を表しています。

   ![ソリューション間の依存関係を表示する](../modeling/media/codemapsmainintro.png)

   この例で、紫色のリンクは呼び出し、点線のリンクは参照、および薄青色のリンクはフィールド アクセスを表しています。 緑色のリンクは継承を表す場合もありますが、複数のリレーションシップ (または *カテゴリ* ) の種類を表す *集約リンク*の可能性もあります。

   > [!TIP]
   > 緑色のリンクが表示されている場合、単に継承関係の存在のみを示しているわけではない可能性があります。 メソッドの呼び出しも存在する場合がありますが、これらは継承関係によって非表示になっています。 特定の種類のリンクを表示するには、[ **フィルター** ] ウィンドウのチェックボックスを使用して、目的の種類を非表示にします。

7. 項目またはリンクに関する詳細情報を確認するには、ポインターをその項目の上に移動してツールヒントを表示します。 これにより、コード要素またはリンクが表すカテゴリの詳細が表示されます。

   ![リレーションシップのカテゴリを表示する](../modeling/media/codemapsshowlinkcatgories.png)

8. 集約リンクによって表される項目と依存関係を調べるには、最初にリンクを選択して、そのショートカット メニューを開きます。 **[寄与するリンクの表示]** または **[新しいコード マップ上の寄与するリンクの表示]** をクリックします。 これにより、リンクの両端のグループが展開され、リンクに関係する項目と依存関係のみが表示されます。

9. マップの特定の部分に焦点を当てるには、関心のない項目を引き続き削除することができます。 たとえば、クラス ビューとメンバー ビューを詳細表示するには、 **[フィルター]** ウィンドウですべての名前空間ノードをフィルター処理するだけです。

   ![クラスとメンバーのレベルまでグループをドリルダウンする](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. 複雑なソリューション マップで必要な項目に注目するもう 1 つの方法は、既存のマップから、選択した項目を含む新しいマップを生成することです。 **Ctrl キー**を押しながら、フォーカスを設定する項目を選択し、ショートカットメニューを開いて、[**選択項目から新しいグラフを作成**] を選択します。

    ![選択された項目を新しいコード マップに表示する](../modeling/media/codemapsshowonnewmap.png)

11. 含んでいるコンテキストは、新しいマップに引き継がれます。 [ **フィルター** ] ウィンドウを使用して、表示したくないソリューションフォルダーとその他のコンテナーを非表示にします。

    ![コンテナーをフィルター処理してビューを簡略化する](../modeling/media/codemapsexpandnewgroups.png)

12. グループを展開し、リレーションシップを表示するマップ内の項目を選択します。

    ![リレーションシップを表示する項目を選択する](../modeling/media/codemapsviewnewrelationships.png)

こちらもご覧ください。

- [コード マップの参照および再配置](../modeling/browse-and-rearrange-code-maps.md)
- [DGML ファイルを編集してコード マップをカスタマイズする](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [アナライザーを実行](../modeling/find-potential-problems-using-code-map-analyzers.md)して、コード内の潜在的な問題を見つける

## <a name="view-specific-dependencies-in-a-code-map"></a>コードマップ内の特定の依存関係の表示

保留中の変更があるいくつかのファイルでコードレビューを実行するとします。 これらの変更の依存関係を表示するため、これらのファイルからコード マップを作成できます。

   ![特定の依存関係をコード マップに表示する](../modeling/media/codemapsspecificdependenciesintro.png)

1. **ソリューションエクスプローラー**で、マップするプロジェクト、アセンブリ参照、フォルダー、ファイル、型、またはメンバーを選択します。

   ![マップする項目を選択する](../modeling/media/codemapsselectinsolutionexplorer.png)

1. **ソリューションエクスプローラー**ツールバーで、[選択したノードから新しいグラフを作成します] ボタン**をクリックし** ![ ](../modeling/media/createnewgraphfromselectedbutton.gif) ます。 または、1つまたは複数の項目グループのショートカットメニューを開き、[ **コードマップに表示**] をクリックします。

   **ソリューションエクスプローラー**、**クラスビュー**、または**オブジェクトブラウザー**から、[新規](#add-a-code-map)または既存のコードマップに項目をドラッグすることもできます。 項目の親階層を含めるには、 **ctrl** キーを押したまま項目をドラッグします。または、コードマップツールバーの [ **親を含める** ] ボタンを使用して、既定のアクションを指定します。 また、 **Windows エクスプローラー**などの Visual Studio の外部からアセンブリファイルをドラッグすることもできます。

   > [!NOTE]
   > 複数のアプリで共有されているプロジェクト (Windows Phone や Microsoft Store など) から項目を追加すると、それらの項目は現在アクティブなアプリプロジェクトと共にマップに表示されます。 コンテキストを別のアプリ プロジェクトに変更し、共有プロジェクトからさらに項目を追加した場合、その項目は、新しくアクティブになったアプリ プロジェクトと共に表示されます。 マップ上の項目に実行する操作は、同じコンテキストを共有する項目にのみ適用されます。

3. アセンブリ内の選択した項目がマップに表示されます。

   ![マップでグループとして表示するように選択された項目](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. 項目を確認するには、その項目を展開します。 マウス ポインターを項目の上に移動し、シェブロン (下矢印) アイコンが表示されたらクリックします。

   ![コードマップ内のノードを展開する](../modeling/media/dependencygraph_containment.png)

   すべての項目を展開するには、 **Ctrl**A を使用して項目を選択し、 + **A**マップのショートカットメニューを開き、[**グループ**の展開] を選択し  >  **Expand**ます。 ただし、すべてのグループを展開すると使用に適さないマップになったりメモリの問題が発生したりする場合、このオプションは使用できません。

5. 必要に応じて、目的の項目をクラスおよびメンバーレベルまで展開します。

   ![クラスとメンバーのレベルにグループを展開する](../modeling/media/codemapsexpandtoclassandmember.png)

   コードに含まれるがマップに表示されないメンバーを表示するには、グループの左上隅にある **再フェッチ children** アイコン ![ 再フェッチ children アイコンをクリックし ](../modeling/media/dependencygraph_deletednodesicon.png) ます。

6. マップ上の項目に関連する項目をさらに表示するには、1 つを選択し、コード マップ ツールバーで **[関連表示]** を選択して、マップに追加する関連項目の種類を選択します。 または、1つまたは複数の項目を選択してショートカットメニューを開き、マップに追加する関連項目の種類の [ **表示** ] オプションを選択します。 次に例を示します。

    **アセンブリ**の場合、次のように選択します。

    |オプション|説明|
    |-|-|
    |**参照されるアセンブリの表示**|このアセンブリの参照先のアセンブリを追加します。 外部アセンブリは **[外部]** グループに表示されます。|
    |**参照元のアセンブリの表示**|このアセンブリを参照するソリューション内のアセンブリを追加します。|

    **名前空間**の場合、表示されていなければ、 **[含んでいるアセンブリの表示]** をクリックします。

    **クラス** または **インターフェイス**の場合は、次から選択します。

    |オプション|説明|
    |-|-|
    |**基本型の表示**|クラスの場合、基底クラスおよび実装されたインターフェイスを追加します。<br /><br /> インターフェイスの場合、基本インターフェイスを追加します。|
    |**派生型の表示**|クラスの場合、派生クラスを追加します。<br /><br /> インターフェイスの場合、派生インターフェイスと、実装するクラスまたは構造体を追加します。|
    |**参照される型の表示**|すべてのクラスと、このクラスが使用するメンバーを追加します。|
    |**参照元の型の表示**|すべてのクラスと、このクラスを使用するメンバーを追加します。|
    |**含んでいる名前空間の表示**|親の名前空間を追加します。|
    |**含んでいる名前空間とアセンブリの表示**|親コンテナーの階層を追加します。|
    |**すべての基本型の表示**|基底クラスまたはインターフェイス階層を再帰的に追加します。|
    |**すべての派生型の表示**|クラスの場合、すべての派生クラスを再帰的に追加します。<br /><br /> インターフェイスの場合、すべての派生インターフェイスと、実装するクラスまたは構造体を再帰的に追加します。|

     **メソッド**の場合、次から選択します。

    |オプション|説明|
    |-|-|
    |**呼び出されるメソッドの表示**|このメソッドが呼び出すメソッドを追加します。|
    |**参照されるフィールドの表示**|このメソッドが参照するフィールドを追加します。|
    |**含んでいる型の表示**|親の型を追加します。|
    |**含んでいる型、名前空間、およびアセンブリの表示**|親コンテナーの階層を追加します。|
    |**オーバーライドされたメソッドの表示**|他のメソッドをオーバーライドするか、インターフェイスのメソッドを実装するメソッドの場合、オーバーライドされた基底クラスのすべての抽象メソッドまたは仮想メソッド、および実装されたインターフェイスのメソッドがある場合はそのメソッドを追加します。|

     **フィールド** または **プロパティ**の場合、次から選択します。

    |オプション|説明|
    |-|-|
    |**含んでいる型の表示**|親の型を追加します。|
    |**含んでいる型、名前空間、およびアセンブリの表示**|親コンテナーの階層を追加します。|

    ![このメンバーによって呼び出されるメソッドを表示する](../modeling/media/codemapsshowrelatedmethods.png)

7. マップには、リレーションシップが表示されます。 この例では、マップには、メソッドによって呼び出されるメソッド `Find` と、ソリューション内または外部のメソッドが表示されます。

   ![特定の依存関係をコード マップに表示する](../modeling/media/codemapsspecificdependenciesintro.png)

8. マップを簡略化し個々の部分に注目するには、コード マップ ツールバーで **[フィルター]** を選択し、必要なノードおよびリンクの種類だけを選択します。 たとえば、ソリューション フォルダー、アセンブリ、および名前空間の表示をオフにします。

   ![フィルター ペインを使用して表示を簡略化する](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>関連項目

- [ビデオ: Visual Studio 2015 コードマップでコードのデザインを理解する](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [コード マップを使用してアプリケーションをデバッグする](../modeling/use-code-maps-to-debug-your-applications.md)
- [デバッグを行うときの呼び出し履歴に対するメソッドのマップ](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [コード マップ アナライザーを使用して潜在的な問題を検索する](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [コード マップの参照および再配置](../modeling/browse-and-rearrange-code-maps.md)
- [DGML ファイルを編集してコード マップをカスタマイズする](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
