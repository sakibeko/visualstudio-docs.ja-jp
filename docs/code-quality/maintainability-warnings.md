---
title: 保守性に関する警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb985a6482b76b79604ce58f85e7f8cf3e83e97c
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509901"
---
# <a name="maintainability-warnings"></a>保守性に関する警告

保守容易性の警告により、ライブラリとアプリケーションのメンテナンスがサポートされます。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
|-----------|-----------------------------------|
| [CA1501:継承を使用しすぎないでください](../code-quality/ca1501.md) | 型が、その継承階層内の 5 つ以上深いレベルにあります。 深いレベルで入れ子にされた型の確認、理解、および保守は困難です。 |
| [CA1502:メソッドの実装を複雑にしすぎないでください](../code-quality/ca1502.md) | この規則は、線形独立のメソッド経路数を示す尺度で、条件分岐の数と複雑さによって決まります。 |
| [CA1505:メンテナンスできないコードを使用しないでください](../code-quality/ca1505.md) | 型またはメソッドの保守容易性指数が低い値です。 保守容易性指数の低い型またはメソッドは、保守が困難な可能性があるため、デザインの変更を検討することをお勧めします。 |
| [CA1506:クラス結合度を大きくしすぎないでください](../code-quality/ca1506.md) | この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。 |
| [CA1507:文字列の代わりに nameof を使用します](../code-quality/ca1507.md) | 文字列リテラルは、式を使用できる引数として使用され `nameof` ます。 |
| [CA1508:使用されない条件付きコードを回避する](../code-quality/ca1508.md) | メソッドには、常にまたは実行時に評価される条件付きコードがあり `true` `false` ます。 これにより、条件の分岐でコードが停止し `false` ます。 |
| [CA1509: コード メトリック構成ファイルのエントリが無効です](../code-quality/ca1509.md) | [CA1501](ca1501.md)、 [CA1502](ca1502.md)、 [CA1505](ca1505.md) 、 [CA1506](ca1506.md)などのコードメトリックス規則には、無効なエントリを持つという名前の構成ファイルが指定されてい `CodeMetricsConfig.txt` ます。 |

## <a name="see-also"></a>関連項目

- [マネージコードの複雑さと保守性の測定](../code-quality/code-metrics-values.md)
