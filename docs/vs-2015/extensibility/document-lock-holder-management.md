---
title: ドキュメントロック所有者の管理 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73c6151b5c02cb81a10c2725091c16457db70e33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204629"
---
# <a name="document-lock-holder-management"></a>ドキュメント ロック ホルダーの管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

実行中のドキュメントテーブル (RDT) は、開いているドキュメントの数と、ロックされているすべての編集ロックを保持します。 ユーザーがドキュメントウィンドウに開いているドキュメントを表示せずに、プログラムによってバックグラウンドで編集されるドキュメントに対しては、RDT の編集ロックを配置できます。 この機能は、グラフィカルユーザーインターフェイスを使用して複数のファイルを変更するデザイナーによってよく使用されます。  
  
## <a name="document-lock-holder-scenarios"></a>ドキュメントロックホルダーのシナリオ  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>ファイル "a" はファイル "b" に依存しています  
 ファイルの種類が "a" の標準エディター "A" を実装し、種類が "a" の各ファイルに "b" というファイルへの参照 (またはその依存) がある状況について考えてみます。 "B" という種類のファイルには、標準のエディター "B" が存在します。 エディター "A" がファイル "a" を開くと、対応するファイル "b" への参照が取得されます。 ファイル "b" は表示されませんが、エディター "A" で変更できます。 エディター "A" は、メソッドからファイル "b" のドキュメントデータへの参照を取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> し、ファイル "b" の編集ロックも保持します。 エディター "A" がファイル "b" の変更を完了すると、メソッドを呼び出すことによって、ファイル "b" の編集ロック数を減らすことができ <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> ます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>パラメーターをに設定してメソッドを呼び出した場合は、この手順を省略でき `dwRDTLockType` <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> ます。  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>ファイル "b" は別のエディターで開かれています  
 エディター "A" でファイル "b" を開こうとしたときに、ファイル "b" が既に開かれている場合は、次の2つの異なるシナリオを処理する必要があります。  
  
- ファイル "b" が互換性のあるエディターで開かれている場合は、メソッドを使用して、エディター "A" がファイル "b" にドキュメントの編集ロックを登録する必要があり <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> ます。 エディター "A" でファイル "b" の変更が完了したら、メソッドを使用してドキュメントの編集ロックを解除し <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> ます。  
  
- ファイル "b" が互換性のない方法で開かれている場合、エディター "A" によってファイル "b" を開こうとしたことを許可するか、エディター "A" に関連付けられているビューを部分的に開いて、適切なエラーメッセージを表示することができます。 エラーメッセージは、互換性のないエディターでファイル "b" を閉じ、エディター "A" を使用してファイル "a" を再度開くようにユーザーに指示する必要があります。 メソッドを実装して [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> 互換性のないエディターで開かれているファイル "b" を閉じるようにユーザーに求めることもできます。 ユーザーがファイル "b" を閉じると、エディター "A" でファイル "a" を開く処理は通常どおり続行されます。  
  
## <a name="additional-document-edit-lock-considerations"></a>ドキュメントの編集ロックに関する追加の考慮事項  
 エディター "A" がファイル "b" に対してドキュメントの編集ロックを持つ唯一のエディターである場合、エディター "b" がファイル "b" に対してドキュメントの編集ロックを保持しているだけの場合、動作は異なります。 で [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] は、 **クラスデザイナー** は、関連付けられたコードファイルの編集ロックを保持しないビジュアルデザイナーの例です。 つまり、ユーザーがデザインビューでクラスダイアグラムを開いていて、関連付けられているコードファイルが同時に開いていて、ユーザーがコードファイルを変更しても変更を保存していない場合は、クラスダイアグラム (.cd) ファイルにも変更が反映されません。 **クラスデザイナー**にコードファイルに対する唯一のドキュメント編集ロックがある場合、ユーザーはコードファイルを閉じるときに変更を保存するように求められません。 IDE は、ユーザーが **クラスデザイナー**を閉じた後にのみ、変更を保存するようにユーザーに要求します。 保存された変更は両方のファイルに反映されます。 **クラスデザイナー**とコードファイルエディターの両方で、ドキュメントの編集ロックがコードファイルに保持されている場合、コードファイルまたはフォームを閉じるときにユーザーに保存を求めるメッセージが表示されます。 その時点で、保存された変更はフォームとコードファイルの両方に反映されます。 クラスダイアグラムの詳細については、「 [クラスダイアグラムの使用 (クラスデザイナー)](../ide/working-with-class-diagrams-class-designer.md)」を参照してください。  
  
 編集ロックをエディター以外のドキュメントに配置する必要がある場合は、インターフェイスを実装する必要があることに注意してください <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 。  
  
 コードファイルをプログラムによって変更する UI デザイナーは、多くの場合、複数のファイルに変更を加えます。 このような場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> メソッドは、[ **次の項目に変更を保存しますか?** ] ダイアログボックスを使用して、1つまたは複数のドキュメントの保存を処理します。  
  
## <a name="see-also"></a>参照  
 [実行 (ドキュメントテーブルを)](../extensibility/internals/running-document-table.md)   
 [ドキュメント テーブルの保存と実行](../extensibility/internals/persistence-and-the-running-document-table.md)
