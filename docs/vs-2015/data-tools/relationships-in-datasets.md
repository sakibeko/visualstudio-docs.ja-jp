---
title: データセット内のリレーションシップ |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eb13ad7db9a4f13ce9bf983ce6327045f885f4d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652887"
---
# <a name="relationships-in-datasets"></a>データセットのリレーションシップ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

関連するデータテーブルを含むデータセット <xref:System.Data.DataRelation> は、オブジェクトを使用して、テーブル間の親子関係を表し、相互に関連するレコードを返します。 **データソース構成ウィザード**または**データセットデザイナー**を使用して、関連テーブルをデータセットに追加すると、オブジェクトが作成および構成さ <xref:System.Data.DataRelation> れます。

 オブジェクトは、 <xref:System.Data.DataRelation> 次の2つの関数を実行します。

- これにより、使用しているレコードに関連するレコードを利用できるようになります。 子レコード () を使用している場合は、子レコード ( <xref:System.Data.DataRow.GetChildRows%2A> ) および親レコード () を使用し <xref:System.Data.DataRow.GetParentRow%2A> ます。

- 親レコードを削除するときに関連する子レコードを削除するなど、参照整合性の制約を適用できます。

  オブジェクトの真の結合と関数の違いを理解しておくことが重要です <xref:System.Data.DataRelation> 。 実際の結合では、レコードは親テーブルと子テーブルから取得され、1つのフラットレコードセットに格納されます。 オブジェクトを使用する場合 <xref:System.Data.DataRelation> 、新しいレコードセットは作成されません。 代わりに、DataRelation はテーブル間のリレーションシップを追跡し、親レコードと子レコードの同期を維持します。

## <a name="datarelation-objects-and-constraints"></a>DataRelation オブジェクトと制約
 <xref:System.Data.DataRelation>オブジェクトは、次の制約を作成して適用するためにも使用されます。

- Unique 制約。テーブル内の列に重複が含まれていないことを保証します。

- 外部キー制約。データセット内の親テーブルと子テーブルの間の参照整合性を維持するために使用できます。

  オブジェクトで指定する制約 <xref:System.Data.DataRelation> は、適切なオブジェクトを自動的に作成するか、プロパティを設定することによって実装されます。 オブジェクトを使用して外部キー制約を作成すると <xref:System.Data.DataRelation> 、クラスのインスタンス <xref:System.Data.ForeignKeyConstraint> がオブジェクトのプロパティに追加され <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ChildKeyConstraint%2A> ます。

  Unique 制約を実装するには、単 <xref:System.Data.DataColumn.Unique%2A> にデータ列のプロパティをに設定するか `true` 、クラスのインスタンス <xref:System.Data.UniqueConstraint> を <xref:System.Data.DataRelation> オブジェクトのプロパティに追加し <xref:System.Data.DataRelation.ParentKeyConstraint%2A> ます。 データセットの制約を中断する方法の詳細については、「 [データセットの読み込み中に制約をオフにする](../data-tools/turn-off-constraints-while-filling-a-dataset.md)」を参照してください。

### <a name="referential-integrity-rules"></a>参照整合性規則
 外部キー制約の一部として、次の3つの点で適用される参照整合性規則を指定できます。

- 親レコードが更新されたとき

- 親レコードが削除されたとき

- 変更が受け入れられるか拒否されたとき

  作成できる規則は列挙体で指定され、 <xref:System.Data.Rule> 次の表に示します。

|外部キー制約規則|アクション|
|----------------------------------|------------|
|<xref:System.Data.Rule>|親レコードに対して行われた変更 (update または delete) は、子テーブルの関連レコードでも行われます。|
|<xref:System.Data.Rule>|子レコードは削除されませんが、子レコードの外部キーはに設定され <xref:System.DBNull> ます。 この設定では、子レコードを "孤立" として残すことができます。つまり、親レコードとの関係はありません。 **注:**  このルールを使用すると、子テーブルに無効なデータが生成される可能性があります。|
|<xref:System.Data.Rule>|関連する子レコードの外部キーは、(列のプロパティによって確立される) 既定値に設定され <xref:System.Data.DataColumn.DefaultValue%2A> ます。|
|<xref:System.Data.Rule>|関連する子レコードに変更は加えられません。 この設定では、子レコードに無効な親レコードへの参照を含めることができます。|

 データセットテーブルの更新の詳細については、「 [データベースにデータを保存する](../data-tools/save-data-back-to-the-database.md)」を参照してください。

### <a name="constraint-only-relations"></a>制約のみのリレーション
 オブジェクトを作成するときに、 <xref:System.Data.DataRelation> リレーションシップを適用するためにのみ使用することを指定するオプションがあります。これは、関連するレコードへのアクセスにも使用されないことを示します。 このオプションを使用すると、より効率的で、関連レコード機能を持つ1つよりも少数のメソッドを含むデータセットを生成できます。 ただし、関連するレコードにアクセスすることはできません。 たとえば、制約のみのリレーションシップでは、子レコードが残っている親レコードを削除することはできません。また、親を介して子レコードにアクセスすることもできません。

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>データセットデザイナーでのデータリレーションシップの手動作成
 Visual Studio のデータデザインツールを使用してデータテーブルを作成する場合、データのソースから情報を収集できる場合、リレーションシップは自動的に作成されます。 **ツールボックス**の [データ**セット**] タブから手動でデータテーブルを追加した場合は、リレーションシップを手動で作成することが必要になる場合があります。 プログラムによるオブジェクトの作成の詳細につい <xref:System.Data.DataRelation> ては、「 [Datarelation の追加](https://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4)」を参照してください。

 データテーブル間のリレーションシップは、リレーションシップの一対多の側面を表すキーと無限大のグリフを使用して、 **データセットデザイナー**内の行として表示されます。 既定では、Relationshipコメントの終了 Id = ' 1c8c78e19b7fa441 ' の名前がデザイン画面に表示されません。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>2つのデータテーブル間のリレーションシップを作成するには

1. **データセット デザイナー**でご自分のデータセットを開きます。 詳細については、「 [方法: データセットデザイナーでデータセットを開く](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)」を参照してください。

2. **リレーションシップオブジェクトを****データセット**ツールボックスからリレーションシップの子データテーブルにドラッグします。

     [ **リレーションシップ** ] ダイアログボックスが開き、[ **子テーブル** ] ボックスに、 **リレーションシップ** オブジェクトをドラッグしたテーブルが挿入されます。

3. [ **親テーブル** ] ボックスから親テーブルを選択します。 親テーブルには、一対多リレーションシップの "一" 側のレコードが含まれています。

4. [ **子テーブル** ] ボックスに正しい子テーブルが表示されていることを確認します。 子テーブルには、一対多リレーションシップの "多" 側のレコードが含まれます。

5. [ **名前** ] ボックスにリレーションシップの名前を入力するか、選択したテーブルに基づいて既定の名前をそのまま使用します。 これは、コード内の実際のオブジェクトの名前です <xref:System.Data.DataRelation> 。

6. [ **キー列** ] ボックスと [ **外部キー列** ] ボックスの一覧で、テーブルを結合する列を選択します。

7. リレーションシップ、制約、またはその両方を作成するかどうかを選択します。 詳細については、「 [DataRelation オブジェクトの概要](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)」を参照してください。

8. [ **入れ子になったリレーション** ] ボックスをオンまたはオフにします。 このオプションを選択すると、プロパティがに設定され、 <xref:System.Data.DataRelation.Nested%2A> `true` これらの行が XML データとして書き込まれるか、と同期されるときに、リレーションシップの子行が親列内に入れ子になり <xref:System.Xml.XmlDataDocument> ます。 詳しくは、「[DataRelation の入れ子化](https://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab)」をご覧ください。

9. これらのテーブルのレコードに変更を加えるときに適用されるルールを設定します。 詳細については、 <xref:System.Data.Rule> を参照してください。

10. [ **OK** ] をクリックしてリレーションシップを作成します。 2つのテーブル間の関係線がデザイナーに表示されます。

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>データセットデザイナーに関係名を表示するには

1. **データセット デザイナー**でご自分のデータセットを開きます。 詳細については、「 [方法: データセットデザイナーでデータセットを開く](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)」を参照してください。

2. [ **データ** ] メニューの [ **リレーションシップラベルの表示** ] をクリックして、リレーションシップ名を表示します。 リレーションシップ名を非表示にするには、そのコマンドをオフにします。
