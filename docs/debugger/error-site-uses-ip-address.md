---
title: エラー - サイトで IP アドレスが使用されています | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58db12ba9dbbc9526ac86262a6be5b2c0a7f765e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460547"
---
# <a name="error-site-uses-ip-address"></a>エラー :サイトは IP アドレスを使用しています
このエラーは、IP アドレスを使用している Web アプリケーションに、デバッガーが自動アタッチしようとしたときに発生します。 これは、IIS で **[Web サイトの識別]** を **[特定の IP アドレスを使用]** に変更した場合に発生します。

 自動アタッチが機能するには、コンピューター名だけでなく、IP アドレスを指定したプロジェクトを作成する必要があります。 そうしないと、コンピューター名は localhost に変更されるため、DEBUG 動詞を IIS に送信するときにエラーが発生します。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 手動のアタッチを使用します ([デバッグ] メニューの **[プロセスにアタッチ]** を選択します)。

     または

2. IIS の **[Web サイトの識別]** 設定を変更します。

## <a name="see-also"></a>関連項目
- [Web アプリケーションのデバッグ: エラーとトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)