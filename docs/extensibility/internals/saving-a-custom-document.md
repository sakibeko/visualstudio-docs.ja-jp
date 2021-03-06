---
title: カスタムドキュメントを保存する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705609"
---
# <a name="saving-a-custom-document"></a>カスタム ドキュメントの保存
環境は、[ **保存**]、[名前を付け **て保存**]、および [ **すべてを保存** ] コマンドを処理します。 ユーザーが [**ファイル**の保存]、[名前を付け**て保存**]、**または [すべて**を保存]**をクリックする**と、すべて保存が行われるため、次のプロセスが実行されます。

 ![ユーザーエディターの保存](../../extensibility/internals/media/private.gif "プライベート") カスタムエディターのすべてのコマンド処理を保存、名前を付けて保存、および保存する

 このプロセスについては、次の手順で詳しく説明します。

1. [ **名前** を付けて保存] コマンドと [名前を付け **て保存** ] コマンドでは、このサービスを使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> アクティブなドキュメントウィンドウと、保存する項目を決定します。 アクティブなドキュメントウィンドウが判明すると、環境は、実行中のドキュメントテーブル内のドキュメントの階層ポインターと項目識別子 (itemID) を検索します。 詳細については、「 [Document Table の実行](../../extensibility/internals/running-document-table.md)」を参照してください。

     [すべてを保存] コマンドの場合、環境は、実行中のドキュメントテーブルの情報を使用して、保存するすべての項目の一覧をコンパイルします。

2. ソリューションは、呼び出しを受け取ると <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 、選択された一連の項目 (つまり、サービスによって公開される複数の選択項目) を反復処理し <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> ます。

3. ソリューションでは、選択項目の各項目に対して、階層ポインターを使用してメソッドを呼び出し、[ <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 保存] メニューコマンドを有効にする必要があるかどうかを判断します。 1つ以上の項目がダーティの場合、[保存] コマンドが有効になります。 階層で標準のエディターが使用されている場合、階層はメソッドを呼び出して、ダーティステータスのクエリをエディターに委任し <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> ます。

4. 選択された各項目がダーティである場合、ソリューションは階層ポインターを使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 適切な階層でメソッドを呼び出します。

     カスタムエディターの場合、ドキュメントデータオブジェクトとプロジェクト間の通信はプライベートになります。 したがって、この2つのオブジェクトの間で、特別な永続化の問題が処理されます。

    > [!NOTE]
    > 独自の永続性を実装する場合は、必ずメソッドを呼び出して時間を節約してください <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 。 このメソッドは、ファイルが安全に保存されていることを確認します (たとえば、ファイルが読み取り専用ではない)。

## <a name="see-also"></a>関連項目
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [プロジェクト項目のオープンと保存](../../extensibility/internals/opening-and-saving-project-items.md)
