---
title: 'IDebugBreakpointUnboundEvent2:: GetReason |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6633fa2b3950d49a3db3b286157d50c026261300
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160035"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ブレークポイントがバインド解除された理由を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetReason(   
   BP_UNBOUND_REASON* pdwUnboundReason  
);  
```  
  
```csharp  
int GetReason(   
   out enum_ BP_UNBOUND_REASON pdwUnboundReason  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwUnboundReason`  
 入出力ブレークポイントがバインド解除された理由を指定する [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) 列挙から値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。  
  
## <a name="remarks"></a>注釈  
 理由として、エディットコンティニュ操作の後にブレークポイントが別の場所に再バインドされているか、ブレークポイントがバインドされたことを示すエラーがあります。  
  
## <a name="example"></a>例  
 次の例は、 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)インターフェイスを公開する**Cbreakpointunbounddebugeventbase**オブジェクトに対してこのメソッドを実装する方法を示しています。  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(  
    BP_UNBOUND_REASON* pdwUnboundReason)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( EVAL(pdwUnboundReason) )  
    {  
        *pdwUnboundReason = m_dwReason;  
  
        hRes = S_OK;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>参照  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
