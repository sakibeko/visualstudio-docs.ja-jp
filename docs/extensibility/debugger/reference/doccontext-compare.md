---
title: DOCCONTEXT_COMPARE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737231"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
2つのドキュメントコンテキストを比較するための条件を指定します。

## <a name="syntax"></a>構文

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>フィールド
`DOCCONTEXT_EQUAL`\
リスト内でターゲットドキュメントコンテキストと同じ最初のドキュメントコンテキストを検索します。

`DOCCONTEXT_LESS_THAN`\
リスト内でターゲットドキュメントコンテキストより小さい最初のドキュメントコンテキストを検索します。

`DOCCONTEXT_GREATER_THAN`\
リスト内でターゲットドキュメントコンテキストよりも大きい最初のドキュメントコンテキストを検索します。

`DOCCONTEXT_SAME_DOCUMENT`\
リスト内で、ターゲットドキュメントコンテキストと同じドキュメント内にある最初のドキュメントコンテキストを検索します。

## <a name="remarks"></a>解説
[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)メソッドに引数として渡されます。

これらの値は、リスト内の最初のドキュメントコンテキストを検索するための比較条件を指定するために使用されます。 ドキュメントコンテキストには、メソッドを通じて比較するドキュメントコンテキストのリストが与えられ `IDebugDocumentContext2::Compare` ます。 次に、比較演算子があるリスト内の最初のドキュメントコンテキスト `true` が返されます。

## <a name="requirements"></a>必要条件
ヘッダー: msdbg. h

名前空間: VisualStudio。

アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
