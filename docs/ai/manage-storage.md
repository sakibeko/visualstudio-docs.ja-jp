---
title: データをアップロードするストレージを参照する
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 188ebee353261ba49f6677a0f96db68b7e8d46d9
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371613"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>データのアップロードまたはモデルとログのダウンロードを行うストレージを参照する

リモート マシンまたは Azure のファイル共有ですべての記憶域を参照して、データのアップロードまたはモデルとログのダウンロードを有効にすることができます。 または、特定のジョブのログ出力およびジョブ出力にアクセスする場合は、ジョブ ブラウザーからでもアクセスすることができます。

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>リモート マシンまたはファイル共有上のすべてのデータにアクセスするには

1. **サーバー エクスプローラー**を開きます。
2. リモート マシンまたは Batch AI 計算コンテキストを展開します。
3. **[ストレージ]** を右クリックしてから **[参照]** をクリックします。

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>リモート マシンまたはファイル共有上にあるジョブ固有のデータにアクセスするには

1. [[ジョブ履歴]](job-details.md) を開きます。
2. ジョブを選択します。
3. **[作業フォルダー]** をクリックします。あるいは、これらの重要なログ ファイルにすばやくアクセスするために **[StdOut] または [Stderr]** をクリックします。

    ![storage](media/manage-storage/job-workingfolder.png)
