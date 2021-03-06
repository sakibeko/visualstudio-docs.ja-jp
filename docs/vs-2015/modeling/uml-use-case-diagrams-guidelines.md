---
title: 'UML ユースケース図: ガイドライン |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "74302837"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML ユース ケース図: ガイドライン
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio では、 *ユースケース図* を描画して、アプリケーションまたはシステムを使用しているユーザーと、それを使用して実行できる操作を要約できます。 UML ユースケース図を作成するには、[ **アーキテクチャ** ] メニューの [ **新しい Uml またはレイヤー図**] をクリックします。

 ビデオデモについては、「 [ユースケースへの特徴の整理](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)」を参照してください。

 この機能をサポートする Visual Studio のバージョンを確認するには、「 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。

 ユース ケース図は、次の情報を検討および伝達するのに役立ちます。

- システムまたはアプリケーションが人、組織、または外部システムと対話するシナリオ。

- ユース ケース図でこれらのアクターが達成する目的。

- システムの範囲。

  ユース ケース図には、ユース ケースの詳細は示されません。ユース ケース、アクター、およびシステムの間のいくつかの関係を要約したものにすぎません。 特に、この図では、それぞれのユース ケースの目的を達成するために実行される各ステップの順序は示されません。 これらの詳細は、各ユース ケースにリンクできる他の図やドキュメントに記述できます。 詳細については、このトピックの「 [ユースケースの詳細な記述](#Details) 」を参照してください。

  ユース ケースの記述では、システムが運用されるドメインに関連するいくつかの用語 ("販売"、"メニュー"、"顧客" など) を使用します。 これらの用語とその関係を明確に定義することが重要になりますが、これは、UML クラス図を利用することで可能になります。 詳細については、「 [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)」を参照してください。

  ユース ケースでは、システムの機能要求のみを扱います。 ビジネス ルール、サービス品質要求、および制約の実装などの他の要求は別途記述する必要があります。 アーキテクチャと内部の詳細も、別途記述する必要があります。 ユーザー要件を定義する方法の詳細については、「 [ユーザー要件のモデル](../modeling/model-user-requirements.md)化」を参照してください。

  このトピックでは、顧客が近所のレストランに料理を注文できる Web サイトに関する例を使用します。

  ![ユース ケース ダイアグラムの要素](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- *アクター* (1) は、ユーザー、組織、デバイス、またはシステムと対話する外部ソフトウェアコンポーネントのクラスです。 アクターの例としては、 **顧客**、 **レストラン**、 **温度センサー**、クレジットカードの承認者などが **あります。**

- *ユースケース*(2) は、特定の目標を達成するために1つ以上のアクターによって実行されるアクションを表します。 ユースケースの例としては、 **注文料理**、 **更新メニュー**、 **プロセスの支払い**などがあります。

   ユース ケース図では、ユース ケースを、ユース ケースを実行するアクターと関連付けます (3)。

- *システム (4)* は、開発中のあらゆるものです。 システムは、アクターが他のソフトウェア コンポーネントにすぎない小さなソフトウェア コンポーネントである場合もあれば、1 つの完全なアプリケーションであったり、多数のコンピューターとデバイスに展開される大規模な分散アプリケーション スイートであったりする場合もあります。 サブシステムの例として、 **料理の注文 Web サイト**、 **料理デリバリービジネス**、 **web サイトバージョン 2**があります。

   ユース ケース図では、システムまたはそのサブシステムでサポートされるユース ケースを表すことができます。

## <a name="basic-steps-for-drawing-use-case-diagrams"></a><a name="BasicSteps"></a> ユースケース図を描画するための基本的な手順

> [!NOTE]
> モデリング図を作成するための詳細な手順については、「 [UML モデルとダイアグラムの編集](../modeling/edit-uml-models-and-diagrams.md)」を参照してください。

#### <a name="to-create-a-new-use-case-diagram"></a>新しいユース ケース図を作成するには

1. [ **アーキテクチャ** ] メニューの [ **新しい UML またはレイヤー図**] をクリックします。

2. [ **テンプレート**] の [ **Umluse Case ダイアグラム**] をクリックします。

3. 図に名前を付けます。

4. [ **モデリングプロジェクトへの追加**] で、ソリューション内の既存のモデリングプロジェクトを選択するか、 **新しいモデリングプロジェクトを作成**して、[ **OK]** をクリックします。

#### <a name="to-draw-a-use-case-diagram"></a>ユース ケース図を描画するには

1. **サブ**システムの境界をツールボックスから図にドラッグし、システム全体または主要なコンポーネントのいずれかを表します。

    - どのユース ケースがシステムまたはそのコンポーネントによってサポートされるかを記述しない場合は、システム境界なしでユース ケース図を描画できます。

    - 必要に応じて、システムの隅をドラッグしてサイズを大きくします。

    - 名前を適切に変更します。

2. **アクター**をツールボックスから図にドラッグします (システム境界の外側に配置します)。

    - アクターは、このシステムと対話するユーザー、組織、および外部システムのクラスを表します。

    - 各アクターの名前を変更します。 例: **Customer、レストラン、クレジットカード機関。**

3. [ツールボックス] から [ **ユースケース** ] を適切なシステムにドラッグします。

    - ユース ケースは、アクターがこのシステムを利用して実行するアクティビティを表します。

    - 各アクティビティの名前を、アクターが理解できるタイトルに変更します。 コードに関係するタイトルは使用しないでください。 たとえば、 **注文料理、料理の支払い、料理の配送**などです。

    - **注文料理**などの主要な取引から開始します。それ以降は、 **[メニュー項目の選択]** などのより小さな相互作用が行われます。

    - システムおよびそのシステムをサポートする主なサブシステムに各ユース ケースを配置します (ユーザーへの接続にのみ関係するファサードやコンポーネントはすべて無視します)。

    - ユース ケースをシステム境界の外側に描画して、(特定のバージョンやリリースの) システムでサポートされないことを示すことができます。

4. ツールボックスの [ **関連付け** ]、ユースケース、ユースケースに参加するアクターの順にクリックします。 このようにして、各アクターをそのユース ケースにリンクします。

5. **包含**、**拡張**、および**汎**化関係を使用してユースケースを構造化します。 これらのリンクを作成するには、ツールをクリックし、ソースのユース ケースをクリックしてから、ターゲットのユース ケースをクリックします。 「 [ユースケース](#Structuring)の構成」というセクションを参照してください。

6. ユース ケースを詳細に記述します。 [詳細につい](#Details)ては、次のセクションを参照してください。

7. サブシステムまたは関連するユース ケース グループごとに、それぞれをフォーカスした図を描画します。 1 つのモデリング プロジェクトのすべての図は、同じモデルのビューです。

## <a name="drawing-actors-and-use-cases"></a><a name="Actors"></a> アクターとユースケースの描画
 ユース ケース図の主な目的は、システムと対話するユーザーと、ユーザーがシステムを使用して実現する主要なゴールを示すことにあります。

- システムまたはサブシステムと対話するユーザー、組織、他のシステム、ソフトウェア、またはデバイスのクラスを表す **アクター** を作成します。

  - アクターとその他の要素を描画する方法については、「 [UML モデルとダイアグラムの編集](../modeling/edit-uml-models-and-diagrams.md)」を参照してください。

  - それぞれの目的のセットに対して、種類またはロールに基づいてアクターを指定します。実際には同じ人間またはエンティティになることがある場合でも、区別します。 たとえば、"レストラン" と "顧客" は、レストランの従業員が顧客になる場合があったとしても、別のアクターです。

- 各アクターがシステムを使用して達成する各目標の **ユースケース** を作成します。

  - 実装のための用語ではなく、アクターが理解できる表現でユース ケースに名前をつけて記述します。

- **関連付け**を使用してアクターをユースケースにリンクします。

### <a name="inheritance-between-actors"></a>アクター間での継承
 ![継承を示すユース ケース ダイアグラム](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 アクター間には **汎** 化リンクを描画できます。 特化されたアクター (この例の "会員の顧客" など) は、汎化されたアクター ("顧客" など) のユース ケースを継承します。 矢じりで、より一般的なアクター ("顧客" など) を指し示す必要があります。 リンクを作成する際は、先に、より特化されたアクターをポイントします。

 特化されたアクターは、汎化されたアクターにはない追加のユース ケースを独自に持つことができます。

> [!CAUTION]
> アクターがアクター自体を汎化することになる汎化関係のループを作成しないでください。 ループによってエラーが発生する場合があります。

### <a name="alternative-actor-icons"></a>代替アクター アイコン
 標準の棒人形の代わりに、カスタム アイコンを使用してアクターを表すことができます。 たとえば、デバイス、レストラン、銀行などに見えるようにアイコンを変更できます。

##### <a name="to-change-the-appearance-of-an-actor"></a>アクターの外観を変更するには

1. アクターを右クリックし、[ **プロパティ**] をクリックします。

     **[プロパティ]** ウィンドウが表示されます。

2. イメージの **パス** プロパティをイメージファイルの場所に設定します。

    - いくつかのイメージ形式 (.gif、.jpg、.bmp など) を使用できます。

    - ソリューションまたはプロジェクトのソース管理に含まれているファイルを使用して、ソリューションが移動またはコピーされた場合にも使用できるようにします。

3. この外観を他のユース ケース図に複製するには、アクターをコピーして別の図に貼り付けます。

    - イメージに対する変更は、特定の図のビューにしか適用されません。 この変更は、基になるモデル要素には適用されません。 このアクターを [UML モデル エクスプ ローラー] から別の図にドラッグした場合は、標準の棒人形として表示されます。

### <a name="multiplicities-between-actors-and-use-cases"></a>アクターとユース ケース間の多重度
 アクターとユースケースの間の関連付けにより、各端で *多重度* を示すことができます。

 ![アクターと 1 対 1 対応のユース ケース](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> ユースケース図でのアソシエーションの多重度は、両方が **1**の場合は非表示になります。

 既定では、各多重度は **1**です。 このモデルの厳密な解釈では、多重度 1 は、たとえば、ある料理を注文できる顧客は 1 人だけで、1 人の顧客は一度に料理を 1 つだけ注文できることを意味します。

 これらの多重度は変更できます。

 次に例を示します。

 ![多対多の多重度を示すユース ケース](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- 同じクラスの複数のアクターがユースケースの1回の出現に参加できるようにするには、アソシエーションのアクター end で多重度を1に設定**し \* **ます。

   この図では、1 つ以上のレストランが同じ料理の注文を受けることができます。

- 各アクターがユースケースの複数回の出現に同時に参加できることを示すには、アソシエーションのユースケース end での複数要素の接続性をに設定し **\*** ます。

   この図では、各レストランは一度に複数の注文に対応できます。

##### <a name="to-set-multiplicities-on-an-association"></a>関連付けの多重度を設定するには

1. アソシエーションを右クリックし、[ **プロパティ**] をクリックします。

2. [ **最初のロール** ] または [ **2 番目のロール**] を展開します。

    *Role* は、アソシエーションの一方の端にある要素を意味します。

3. 多重度プロパティを次の一覧から選択して設定します。

   - **1** は、このロールの1つのインスタンスが各リンクに参加することを示すものです。

   - **1.. \* **このロールの1つ以上のインスタンスが各リンクに参加することを示す。

   - **0 ..1** 参加が省略可能であることを示します。

   - **\*** このロールの0個以上のインスタンスがリンクに含まれることを示す場合。

> [!NOTE]
> チームの多くがユース ケース図に多重度の情報を設定せず、多重度を既定値の 1 のままにしておきます。 代わりに、そのユース ケースの別の説明にこの情報を記述します。 その場合、ユース ケース図のすべての多重度が非表示になります。

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>1 つのアクターまたはユース ケースを複数の図で使用する
 同じアクターとユース ケースを複数の図に表示できます。 次に例を示します。

- 1 つのアクターが関係している異なるユース ケースを異なる図に記述できます

- ユース ケースが関連付けられているアクターおよびサブシステムを 1 つの図に示し、このユース ケースを、包含されるユース ケースと拡張されるユース ケースにどのように構成するかを別の図に示すことができます。

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>同じアクターまたはユース ケースを異なる図に表示するには

1. アクターまたはユース ケースを 1 つの図に作成します。

2. 別のユース ケース図を作成します。

3. アクターまたはユースケースを **モデルエクスプローラー** から新しい図にドラッグします。

    > [!NOTE]
    > 既に関連付けられているアクターとユース ケースを新しい図に配置すると、それらの間の関連付けが新しい図に自動的に表示されます。

## <a name="describing-use-cases-in-detail"></a><a name="Details"></a> ユースケースの詳細を説明する
 ユース ケースは次のことを表します。

- システムを使用するアクターの目標 ( **料理の購入**など)。そして

- 1つまたは複数の *シナリオ*({**Order 料理、支払い、配送**} などの目標を達成するために実行されるステップのシーケンス)。 成功のシナリオに加えて、 **クレジットカードが拒否**されたなど、いくつかの例外またはエラーが発生する場合があります。

  1 つのユース ケースは、さまざまな詳細レベルで記述できます。 設計の初期段階では、ユース ケース図の名前だけで十分です。  シナリオの詳細な説明は後で記述できます。

  Visual Studio Ultimate では、ユース ケースをさまざまな方法で記述して、別個に使用したり、組み合わせて使用したりできます。

- ユース ケースをプロジェクト内の別の図 (1 つまたは複数) にリンクする。

  - アクティビティ図は、ループ、分岐、および並列スレッドを含むより複雑なプロセスを説明するのに便利です。 プロセスの個々の部分の間のデータ フローを示すこともできます。 詳細については、「 [UML アクティビティ図: ガイドライン](../modeling/uml-activity-diagrams-guidelines.md)」を参照してください。

  - シーケンス図は、さまざまなアクター間で行われる一連の複雑な対話を説明するのに便利です。 シーケンス図を使用して、各ユース ケースに対してシステム内部で発生する処理を示すこともできます。 詳細については、「 [UML シーケンス図: ガイドライン](../modeling/uml-sequence-diagrams-guidelines.md)」を参照してください。

- ユース ケースを詳細に記述した OneNote のページ、セクション、または段落にユース ケースをリンクする。

- テキスト、スクリーン ショットなどを使用してユース ケースのシナリオを記述した Word 文書に、ユース ケースをリンクする。 詳細については、「 [ユーザー要件のモデル](../modeling/model-user-requirements.md)化」を参照してください。

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>ユース ケースを、同じソリューション内の図またはファイルにリンクするには

1. シーケンス図やアクティビィティ図を描画して、ユース ケースのシナリオを例示します。

2. ユース ケース図に戻ります。

3. 図またはファイルを、ソリューション エクスプローラーからユース ケース図の空白部分にドラッグします。

4. **依存関係**を使用して、成果物からユースケースに接続します。

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Word 文書や PowerPoint プレゼンテーションなどのソリューション ファイルにリンクするには

1. テキスト、スクリーン ショットなどを使用してユース ケースのシナリオを説明するドキュメントを記述します。

2. このドキュメントをソリューションに追加します。

    1. Word 文書をソリューションとして、同じ Windows フォルダーに移動します。

    2. ソリューションエクスプローラーで、ソリューションを右クリックして [ **追加**] をポイントし、[ **既存の項目**] をクリックします。

    3. Word 文書に移動し、[ **追加**] をクリックします。

         ソリューション エクスプローラーのソリューション フォルダーに、Word 文書が表示されます。

3. Word 文書を、ソリューション エクスプローラーからユース ケース図の空白部分にドラッグします。

     新しい成果物が表示されます。

4. **依存関係**を使用して、成果物からユースケースに接続します。

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>共有ドキュメント、OneNote 要素、または Web ページにリンクを設定するには

1. 共有要素の URL を取得します。 たとえば、"" を開始するネットワークファイルパス、" \\ \\ http://" を開始する web ページまたは Sharepoint URL、または onenote セクション、ページ、または "onenote:" を開始する段落へのリンクなどです。

2. [ツールボックス] で [ **アーティファクト** ] をクリックし、ユースケース図をクリックします。

3. 新しい成果物が選択された状態で、 **Hyperlink** プロパティに URL を入力するか貼り付けます。

> [!NOTE]
> 成果物をダブルクリックして、成果物のリンク先の図またはドキュメントを開くことができます。

### <a name="linking-use-cases-to-work-items"></a>ユース ケースを作業項目にリンクする
 プロジェクトでを使用していて、を使用している場合は [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 、の作業項目に各ユースケースをリンクでき [!INCLUDE[esprfound](../includes/esprfound-md.md)] ます。 これらのリンクを作成する方法については、「 [モデル要素と作業項目のリンク](../modeling/link-model-elements-and-work-items.md)」を参照してください。

 これを使用すると、次のことができます。

- リンクされた作業項目でユース ケースについて説明する。 特に、プロジェクトで Visual Studio の正式なプロセス テンプレートを使用している場合、ユース ケースの作業項目にリンクできます。 この種の作業項目には、ユース ケースの目的とシナリオを記述するためのフィールドが用意されています。

- テスト ケースをユース ケースにリンクして、開発中のコードにどの程度ユース ケースが実装されているかのレポートを取得できます。

- タスクをユース ケースにリンクして、開発作業の進捗状況を追跡できます。

## <a name="structuring-use-cases"></a><a name="Structuring"></a> ユースケースの構造化
 システムの動作の記述には、少数の主要なユース ケースだけを使用してください。 それぞれの主要なユース ケースでは、"製品を購入する"、"(ベンダーの視点から) 販売用の製品を提供する" など、アクターが実現する主要な目的を定義します。

 これらの目的を明確にしたら、それぞれの目的を達成する方法、および基本の目的のバリエーションについての詳細に進むことができます。

 ユース ケースを細かく分解しすぎないようにしてください。 ユース ケースは、システムの内部動作ではなく、システムに関するユーザーのエクスペリエンスを表します。 また、一般的には、早い段階でコードの試作版を作成する方が、詳細なユース ケースを構成するために時間を費やすよりも生産的です。

 主要なユース ケースと詳細なユース ケースの間の関係はユース ケース図に要約できます。 以下の各セクションでは、このことについて説明します。

- [包含によるユース ケースの詳細の表示](#Include)

- [汎化による目的の共有](#Inheritance)

- [拡張による異なるケースの分離](#Extend)

### <a name="showing-the-details-of-a-use-case-with-include"></a><a name="Include"></a> Include を使用したユースケースの詳細の表示
 **包含**関係を使用して、あるユースケースで別のユースケースの詳細の一部が記述されていることを示します。 この図では、料理を含む料理、[**メニュー** **]、[****メニュー項目]****の順に注文**します。 包含されている側のより詳細なユース ケースのそれぞれは、包含している側のユース ケースの全体的なゴールを達成するためにアクターが実行する必要があるステップを表しています。 より詳細な、包含される側のユース ケースを矢印で指し示す必要があります。

> [!CAUTION]
> ユース ケースがユース ケース自体を包含することになる包含関係のループを作成しないでください。 ループによってエラーが発生する可能性があります。

 包含される側のユース ケースは共有できます。 この例では、 **料理を注文** して **レビューをサブスクライブする** ユースケースには、両方とも **支払い**が含まれます。

 ![包含によって分解されたユース ケース](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 包含される側のユース ケースの目的とシナリオは、後で設計されたユース ケースで包含できるように、単独で意味を成している必要があります。

 ユース ケースを、包含する部分と包含される部分に分けることで、次の目的を達成するのが容易になります。

- ユース ケースの記述を異なる詳細レイヤーに構成する。

- 共有のシナリオを複数のユース ケースで繰り返すことを防ぐ。

#### <a name="defining-the-order-of-the-detailed-steps"></a><a name="Steps"></a> 詳細な手順の順序の定義
 ユース ケース図では、より詳細なステップを実行する順序や、各ステップを必ず実行する必要があるかどうかは示されません。

 ステップの順序を明確にするために、 **成果物** を使用して、インクルードするユースケースに個別のドキュメントを添付できます。 次の例では、アクティビティ図が "料理を注文する" ユース ケースにアタッチされています。 代わりに、ステップの一覧や一連のスクリーン ショットが含まれたテキスト ドキュメントを使用することもできます。 詳細については、「 [ユースケースの詳細](#Details)」を参照してください。

 アクティビティ図を使用する場合は、次の名前付け規則に注意してください。

- アクティビティ全体の名前が、包含する側のユース ケースの名前と同じである。

- アクティビティ図内のアクションに、包含される側のユース ケースと同じ名前が付いている。

  詳細については、「 [UML アクティビティ図: ガイドライン](../modeling/uml-activity-diagrams-guidelines.md)」を参照してください。

  ![リンクされたアクティビティ ダイアグラムに示されたユース ケースのステップ](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="sharing-goals-with-generalization"></a><a name="Inheritance"></a> 汎化による目標の共有
 汎化関係を使用して、 *特* 化されたユースケースが、別の *一般的* なユースケースで表される目標を達成する特定の方法であることを示します。 白抜きの矢じりで、より一般的なユース ケースを指し示す必要があります。

 ![汎化関係を示すユース ケース](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 たとえば、" **支払い** 一般化" は **クレジットカードごと** に支払い、 **現金ごと**に支払います。

> [!CAUTION]
> アクターがアクター自体を汎化することになる汎化関係のループを作成しないでください。 ループによってエラーが発生する場合があります。

 特化されたユース ケースによって、同じゴールを実現するためにシステムが実行できる異なる方法を示すことができます。

 特化されたユース ケースは、一般的なユース ケースの目的およびアクターを継承するものと見なされます。 一般的なユース ケースに独自のシナリオが含まれている必要はありません。特化によって、目的を達成するための異なる方法を記述します。

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>共通の目的を 2 つ以上のユース ケースからリファクタリングするには

1. 新しい一般的なユース ケースを作成し、名前を付けます。

2. 新しい一般的なユースケースを指し示す大きな矢印を使用して、 **汎** 化関係を作成します。

    1. ツールボックスの [ **汎** 化] をクリックします。

    2. 特化されたユースケース (例では**クレジットカードによる支払い** ) をクリックします。

    3. 一般的なユースケース (例では**支払い** ) をクリックします。

3. 特化されたユース ケースの目的を記述したら、共通部分を一般的なユース ケースの記述に移動します。

4. 特化されたユース ケース間で共有されるアクターは、一般的なユース ケースに移動できます。

### <a name="separating-variant-cases-with-extend"></a><a name="Extend"></a> 拡張によるバリアントケースの分離
 特定の状況下においてあるユース ケースが別のユース ケースに機能を追加できることを示すには、拡張リンクを使用します。 メインの拡張される側のユース ケースを、矢印で指し示す必要があります。

 ![1 つのユース ケースが別のユース ケースを拡張](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> アクターがアクター自体を汎化することになる拡張関係のループを作成しないでください。 ループによってエラーが発生する場合があります。

 たとえば、一般的な Web サイトの **ログイン** ユースケースには、ユーザーがまだアカウントを持っていない場合にのみ、[ **新しいユーザーの登録** ] を含めることができます。

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>1 つのユース ケースを主な部分と拡張する部分に分割するには

1. 新しい拡張ユース ケースを作成し、名前を付けます。

2. 拡張されたユースケースを指している矢印を使用して、 **拡張** 関係を作成します。

   1. ツールボックスの [ **拡張** ] をクリックします。

   2. 拡張するユースケースをクリックします (この例では、**新しいユーザーを登録** します)。

   3. 拡張されたユースケース (例では**ログイン** ) をクリックします。

       > [!NOTE]
       > 図に拡張関係ループを作成することは避けてください。 ユース ケースをそれ自体の拡張にすることはできません。

3. 拡張される側のユース ケースのシナリオを既に作成した場合は、関連するステップを拡張のシナリオに移動します。

4. 拡張機能の説明 (例では**新しいユーザーを登録** します) には、主なユースケースシナリオでの場所の詳細と、その状況についての詳細が含まれている必要があります。 拡張は、メインのケースの説明を変更したものと考えてください。

   拡張ユース ケースは、メインのユース ケースのシナリオとなるようなシナリオ ステップを表します。 拡張のシナリオおよび目的は、必ず、メインのユース ケースのコンテキストで読み取られます。したがって、これらが単独で機能する必要はありません。

   拡張の分離は、次のような状況の記述に役立ちます。

- 拡張ユース ケースにのみ関わる追加のアクターが存在する場合。 たとえば、Web サイトの顧客登録の承認には管理者が必要です。

- 拡張ユース ケースが別のサブシステムで処理される場合。

- この拡張を利用できるのがシステムの特定のバージョンに限られる場合。 ユース ケース図で、各バージョンを別個のサブシステムとして示すことができます。

## <a name="using-subsystem-boundaries"></a><a name="Subsystems"></a> サブシステムの境界の使用
 サブシステム境界を使用して、システムの範囲内にあるユース ケースを示します。

#### <a name="to-draw-a-subsystem-boundary"></a>サブシステム境界を描画するには

1. ツールボックスで、[ **サブシステム**] をクリックし、図をクリックします。

    サブシステムが図上に表示されます。

2. サブシステムのサイズを調整するには、そのサブシステムの隅をドラッグします。

3. サブシステムの内容を調整するには、既存のユース ケースをサブシステムの内側または外側にドラッグします。

   \- または

   サブシステムで新しいユースケースを直接作成するには、ツールボックスで [ **ユースケース** ] をクリックし、サブシステム内をクリックします。

> [!NOTE]
> ユースケースの " **サブジェクト** " プロパティは、どのサブシステムが含まれているかを示します。

### <a name="use-cases-outside-the-system-scope"></a>システムの範囲外のユース ケース
 ビジネスの一部に含まれているユース ケースであれば、開発中のシステムで処理されないものであっても、図に含めておくと便利です。 これにより、開発者は自分たちの作業のコンテキストを理解できます。 たとえば、"料理を配達する" を、アクターの "レストラン" と "顧客" が関わるけれども "料理の注文 Web サイト" の責任の範囲外であるユース ケースとして示すことができます。

### <a name="multiple-subsystems"></a>複数のサブシステム
 複数のサブシステム境界を作成すると、システムの異なるコンポーネントで異なるユース ケースが処理されることを示すことができます。 たとえば、 **レストランの評定の追加** は、別のフォーラム Web サイトで処理される場合があります。 ユース ケース図では、ユーザーに表示するものを扱う必要があります。 システムで社内の職務の分担について記述したい場合は、コンポーネント図の使用を検討します。

### <a name="system-versions"></a>システムのバージョン
 複数のサブシステム境界を使用して、システムの異なるバージョンを示すことができます。 たとえば、支払いユースケースは、バージョン1ではなく、Web サイトバージョン2に含まれている場合があります。これは、顧客が注文を行う際にシステムが使用することを意味します。 ただし、顧客は代金をレストランに直接支払う必要があります。

 **依存**関係を使用して、異なるバージョンまたはバリエーションを表すサブシステムをリンクします。

 ![サブシステムがシステムの異なるバージョンを示している](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>参照
 [ユーザー要件のモデル化](../modeling/model-user-requirements.md) [uml シーケンス図: ガイドライン](../modeling/uml-sequence-diagrams-guidelines.md) [uml モデルおよび図の編集](../modeling/edit-uml-models-and-diagrams.md) [Uml ユースケース図](../modeling/uml-use-case-diagrams-reference.md): リファレンス uml[クラス図](../modeling/uml-class-diagrams-reference.md): リファレンス uml[コンポーネント図](../modeling/uml-component-diagrams-reference.md): リファレンス uml[アクティビティ図](../modeling/uml-activity-diagrams-guidelines.md) [Video: Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
