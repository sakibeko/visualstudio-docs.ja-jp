---
title: エラー - リモート コンピューターで DCOM 通信を初期化できませんでした | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a1f5216953adc1b257e432b1e4f1eb4d041b836
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460705"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>エラー :リモート コンピューターは DCOM 通信を初期化できませんでした
リモート コンピューターがローカル コンピューターと通信しようとしたときに DCOM エラーが発生しました。 ローカル コンピューターは、

 Visual Studio を実行しているコンピューターです。 このエラーが発生する原因は複数あります。

- ローカル マシンのファイアウォールが有効になっていない。

- リモート マシンからローカル マシンへの Windows 認証が機能していない。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. ローカル コンピューターで Windows ファイアウォールが有効になっている場合は、「[リモート デバッグ](../debugger/remote-debugging.md)」で、ローカル デバッグ用にファイアウォールを設定する手順を確認してください。

2. リモート サーバーからローカル コンピューターのファイル共有を開いてみて Windows 認証をテストします。

3. Windows 認証を復元するために、両方のコンピューターを再起動してみます。 Kerberos エラーがないかどうかローカル コンピューターとリモート コンピューターのイベント ログを確認し、既知の問題がないかどうかドメイン管理者に問い合わせてください。

## <a name="see-also"></a>関連項目
 [Remote Debugging](../debugger/remote-debugging.md)