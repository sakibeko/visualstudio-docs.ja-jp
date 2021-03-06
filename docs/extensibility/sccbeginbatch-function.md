---
title: SccBeginBatch 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701192"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 関数
この関数は、ソース管理操作のバッチシーケンスを開始します。 バッチを終了するために [Sccendbatch](../extensibility/sccendbatch-function.md) が呼び出されます。 これらのバッチを入れ子にすることはできません。

## <a name="syntax"></a>構文

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>パラメーター
 [なし] :

## <a name="return-value"></a>戻り値
 この関数のソース管理プラグインの実装では、次の値のいずれかが返されることが想定されています。

|値|説明|
|-----------|-----------------|
|SCC_OK|操作のバッチが正常に開始しました。|
|SCC_E_UNKNOWNERROR|不特定のエラーです。|

## <a name="remarks"></a>注釈
 ソース管理バッチは、複数のプロジェクトまたは複数のコンテキストで同じ操作を実行するために使用されます。 バッチ処理を使用すると、バッチ操作中のユーザーエクスペリエンスから、プロジェクトごとの冗長なダイアログボックスを削除できます。 `SccBeginBatch`関数と[Sccendbatch](../extensibility/sccendbatch-function.md)は、操作の開始と終了を示すために関数のペアとして使用されます。 入れ子にすることはできません。 `SccBeginBatch` バッチ操作が進行中であることを示すフラグを設定します。

 バッチ操作が有効になっている間、ソース管理プラグインは、すべての質問に対して1つのダイアログボックスを表示し、後続のすべての操作にそのダイアログボックスから応答を適用する必要があります。

## <a name="see-also"></a>こちらもご覧ください
- [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
