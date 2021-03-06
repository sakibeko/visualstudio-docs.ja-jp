---
title: Open With Command | を使用したファイルの表示Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708579"
---
# <a name="display-files-by-using-the-open-with-command"></a>[ファイルを開くアプリケーションの表示] コマンドを使用してファイルを表示する
プロジェクトでは、[ **ファイルを開くアプリケーション** の選択] ダイアログボックスを表示するよう IDE に要求できます。 この要求は、標準エディターを選択したファイルを開くようにユーザーに求めます。 次の手順では、このプロセスについて説明します。

1. プロジェクトは <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> を呼び出し、パラメーターにの値を指定 `OSE_UseOpenWithDialog` `OSEOpenDocEditor` します。

2. IDE では、ドキュメントのファイル名拡張子に基づいて、指定されたドキュメントを開くことができるエディターを特定し、その情報を [ファイル **を開くアプリケーション** の選択] ダイアログボックスに表示します。

    > [!NOTE]
    > [ **ファイルを開くアプリケーション** の選択] ダイアログボックスに含める必要がある固有のエディターを持つプロジェクトでは、そのようなエディターごとにエディターファクトリを登録する必要があります。 固有のエディターは、特定の種類のプロジェクトと共にのみ機能します。これは、メソッドの実装に適用され <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ます。 IDE には、コアテキストエディターとバイナリエディター用の組み込みエディターファクトリが用意されています。 IDE では、登録されている各 Windows ファイルの関連付けに代わって、エディターファクトリのインスタンスも作成されます。 このようなファイルの例として、Microsoft Word があります。

3. ユーザーが [ **ファイルを開くアプリケーション** の選択] ダイアログボックスから項目を選択するとすぐに、IDE はメソッドを呼び出してドキュメントを開き <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ます。 詳細については、「 [方法: 標準エディターを開く](../../extensibility/how-to-open-standard-editors.md)」を参照してください。

## <a name="see-also"></a>関連項目
- [プロジェクト項目を開いて保存する](../../extensibility/internals/opening-and-saving-project-items.md)
- [[ファイルを開く] コマンドを使用してファイルを表示する](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [方法: 標準エディターを開く](../../extensibility/how-to-open-standard-editors.md)
