---
title: エラー - ターゲット コンピューター上の Visual Studio リモート デバッガーが、このコンピューターに接続できません
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
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
ms.openlocfilehash: b372b1f6fcdab357e87ff91fa4df257e8da7d68d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536670"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>エラー :ターゲット コンピューター上の Visual Studio リモート デバッガーが、このコンピューターに接続できません
このエラーは、リモート デバッガー サービスでデバッグを開始したコンピューターに接続するときに、このサービスを実行しているユーザー アカウントを認証できないことを意味します。 このエラーは、レガシ デバッグ エンジンを使用したリモート デバッグで、リモート デバッガーがサービスとして実行されている場合に発生する可能性があります。

 コンピューターにアクセスできるアカウントは、次の表のとおりです。

|シナリオ|LocalSystem アカウント|ドメイン アカウント|両方のコンピューターに同じユーザー名とパスワードを持つローカル アカウント|
|-|-|-|-|
|両方のコンピューターが同じドメインにある場合|はい|はい|はい|
|両方のコンピューターが双方向の信頼関係を持つドメインにある場合|いいえ|いいえ|はい|
|一方または両方のコンピューターがワークグループにある場合|いいえ|いいえ|はい|
|コンピューターが異なるドメインにある場合|いいえ|いいえ|はい|

 さらに:

- Visual Studio リモート デバッガー サービスを実行するアカウントは、すべてのプロセスをデバッグできるように、リモート コンピューターの管理者アカウントであることが必要です。

- このアカウントには、**ローカル セキュリティ ポリシー**管理ツールを使用して、リモート コンピューターに対する `Log on as a service` 特権が与えられている必要もあります。

- ローカル アカウントを使用してコンピューターにアクセスしている場合は、ローカル アカウントで Visual Studio リモート デバッガー サービスを実行する必要があります。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. リモート コンピューターに Visual Studio リモート デバッガー サービスが正しく設定されていることを確認します。 詳細については、「[リモート デバッグ](../debugger/remote-debugging.md)」を参照してください。

2. 上の表に示した、デバッガー ホスト コンピューターにアクセスできる適切なアカウントを使用して、リモート デバッガー サービスを実行します。

### <a name="to-add-log-on-as-a-service-privilege"></a>"サービスとしてログオンする" 特権を追加するには

1. **[スタート]** メニューの **[コントロール パネル]** を選択します。

2. 必要に応じて、[コントロール パネル] で **[クラシック表示]** を選択します。

3. **[管理ツール]** をダブルクリックします。

4. [管理ツール] ウィンドウで、 **[ローカル セキュリティ ポリシー]** をダブルクリックします。

5. **[ローカル セキュリティ設定]** ウィンドウで、 **[ローカル ポリシー]** フォルダーを展開します。

6. **[ユーザー権利の割り当て]** をクリックします。

7. **[ポリシー]** 列の **[サービスとしてログオン]** をダブルクリックすると、現在のローカル グループ ポリシーの割り当てが **[サービスとしてログオン]** ダイアログ ボックスに表示されます。

8. 新しいユーザーを追加するには、 **[ユーザーまたはグループの追加]** をクリックします。

9. ユーザーの追加作業が終了したら、 **[OK]** をクリックします。

### <a name="to-work-around-this-error"></a>このエラーを回避するには

- リモート デバッグ モニターをサービスとして実行する代わりに、アプリケーションとして実行します。

## <a name="see-also"></a>関連項目
- [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)