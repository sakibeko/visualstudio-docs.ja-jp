---
title: 'IDebugExpressionEvaluator:: GetMethodLocationProperty |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d82b002d9253b2d48f78e74fdf964cf42d241d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144389"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、メソッドの場所とオフセットをメモリアドレスに変換します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `upstrFullyQualifiedMethodPlusOffset`  
 から文字列として表現されるメソッドの場所とオフセット。  
  
 `pSymbolProvider`  
 から [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) オブジェクトとして表現されるシンボルプロバイダー。  
  
 `pAddress`  
 から [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) オブジェクトとして表される、メソッド内のアドレス。  
  
 `pBinder`  
 から [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) オブジェクトとして表現されたバインダー。  
  
 `ppProperty`  
 入出力メモリアドレスを表す [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) インターフェイスを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。  
  
## <a name="remarks"></a>注釈  
 返されたアドレスを使用して、ブレークポイントを設定できます。たとえば、のようになります。  
  
 名前にかかわらず `upstrFullyQualifiedMethodPlusOffset` 、このパラメーターには部分的に修飾されたメソッド名を渡すことができます。 その場合は、選択されたメソッドが、を囲むメソッドです `pAddress` 。 このパラメーターがどのように解釈されるかは、式エバリュエーターとそれがサポートする言語の実装になります。  
  
## <a name="see-also"></a>参照  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
