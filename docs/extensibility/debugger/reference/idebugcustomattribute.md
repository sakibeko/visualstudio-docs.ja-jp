---
title: IDebugCustomAttribute |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732683"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
このインターフェイスはカスタム属性を表し、属性の名前、親、およびクラスの型を提供できます。

## <a name="syntax"></a>構文

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>実装側の注意
 シンボルプロバイダーは、シンボルに関連付けられているカスタム属性をサポートするために、このインターフェイスを実装します。 通常は、独自のオブジェクトに実装されます。

## <a name="notes-for-callers"></a>呼び出し元に関する注意事項
 [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)を呼び出すと、このインターフェイスが返されます。 [Enumcustomattributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)メソッドを呼び出すと、 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)インターフェイスが返されます。

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド
 次の表に、のメソッドを示し `IDebugCustomAttribute` ます。

|Method|説明|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|現在の属性がアタッチされているフィールドを取得します。|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|カスタム属性クラスの型を取得します。|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|カスタム属性の名前を取得します。|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|属性情報をバイトの blob として取得します。|

## <a name="remarks"></a>解説
 カスタム属性は、特定のクラスまたはメソッドに関連付けられたカスタムメタデータを提供する C# の構造体です。

## <a name="requirements"></a>必要条件
 ヘッダー: sh. h

 名前空間: VisualStudio。

 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [シンボル プロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
