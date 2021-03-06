---
title: '方法: プログラムによって文書内の範囲を拡張する'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 35ef0ea0352141f18945632f996237c2d9d90204
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547421"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>方法: プログラムによって文書内の範囲を拡張する
  Microsoft Office Word ドキュメントで <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを定義した後、その始点と終点を <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> メソッドと <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> メソッドを使用して変更します。 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>メソッドと <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> メソッドは、同じ2つの引数 ( *Unit*と*Count*) を受け取ります。 *Count*引数は移動する単位の数で、 *Unit*引数には次のいずれかの値を指定でき <xref:Microsoft.Office.Interop.Word.WdUnits> ます。

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  次の例では、7 文字の範囲を定義します。 その後、開始位置を元の開始位置から 7 文字後に移動します。 範囲の終了位置も開始位置より 7 文字後にあるため、結果はゼロ文字からなる範囲になります。 このコードは続いて、終了位置を現在の終了位置から 7 文字後に移動します。

## <a name="to-extend-a-range"></a>範囲を拡張するには

1. 文字の範囲を定義します。 詳細については、「 [方法: ドキュメント内の範囲をプログラムによって定義および選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)」を参照してください。

     次のコード例はドキュメント レベルのカスタマイズで使用できます。

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     次のコード例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2. <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range> メソッドを使用して、範囲の開始位置を移動します。

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3. <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range> メソッドを使用して、範囲の終了位置を移動します。

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>ドキュメントレベルのカスタマイズコード

### <a name="to-extend-a-range-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで範囲を拡張するには

1. 次の例は、ドキュメント レベルのカスタマイズのコード全体を示しています。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>VSTO アドイン コード

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>アプリケーション レベルの VSTO アドインで範囲を拡張するには

1. 次の例は、VSTO アドインのコード全体を示しています。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>関連項目
- [方法: プログラムによって Word 文書の範囲をリセットする](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [方法: プログラムによって文書内の範囲または選択項目を折りたたむ](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [方法: プログラムによって文書内の範囲を定義および選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [方法: プログラムによって範囲内の開始文字と終了文字を取得する](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [方法: 範囲を作成するときにプログラムによって段落記号を除外する](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
