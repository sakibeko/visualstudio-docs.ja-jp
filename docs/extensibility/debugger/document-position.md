---
title: ドキュメントの位置 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19b88ead19e4578adb7c151a681583120cf2ec17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738905"
---
# <a name="document-position"></a>ドキュメントの位置
デバッグでは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、 *ドキュメントの位置*は次のようになります。

- IDE で認識されているソースファイル内の位置の抽象化を提供します。 現在、ほとんどの言語では、ドキュメントの位置はソースファイル内の位置と考えることができます。

- ソースドキュメント内のデバッグエンジンへの位置を記述します。

- は、 [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) インターフェイスによって実装されます。

## <a name="see-also"></a>関連項目
- [コードコンテキスト](../../extensibility/debugger/code-context.md)
- [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)
- [シンボルプロバイダー](../../extensibility/debugger/symbol-provider.md)
- [シンボルプロバイダーインターフェイス](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [デバッガーコンテキスト](../../extensibility/debugger/debugger-contexts.md)
