---
title: 'IDebugExpressionEvaluator2:: SetCorPath |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- SetCorPath
- IDebugExpressionEvaluator2::SetCorPath
ms.assetid: 27b614ff-7325-4f9b-8da4-61ee020c9410
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c1508c7c0936f8ed8d92852e5b75c073cb9d85a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179912"
---
# <a name="idebugexpressionevaluator2setcorpath"></a>IDebugExpressionEvaluator2::SetCorPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

デバッガーに読み込まれている共通言語ランタイム (CLR) へのパスを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT SetCorPath(  
   LPCOLESTR pcstrCorPath  
);  
```  
  
```csharp  
int SetCorPath(  
   string pcstrCorPath  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcstrCorPath`  
 からデバッガーに読み込まれた CLR へのパス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合はを返し `S_OK` ます。それ以外の場合はエラーコードを返します。  
  
## <a name="example"></a>例  
 次の例は、 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)インターフェイスを公開する**式 evaluatorpackage**オブジェクトに対してこのメソッドを実装する方法を示しています。  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::SetCorPath(LPCOLESTR pcstrCorPath)  
{  
    VerifyInPtr(pcstrCorPath);  
    HRESULT hr = E_FAIL;  
  
    VBEECompilerSingleton *pVBEECompilerSingleton = VBEECompilerSingleton::Instance();  
  
    if (pVBEECompilerSingleton)  
    {  
        pVBEECompilerSingleton->LockEECompiler();  
  
        try  
        {  
            if (!m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))  
            {  
                CComObject<CVBEECompilerHost> *pEECompilerHost;  
  
                if (SUCCEEDED(CComObject<CVBEECompilerHost>::CreateInstance(&pEECompilerHost)))  
                {  
                    pEECompilerHost->AddRef();  
                    pEECompilerHost->Init(pcstrCorPath);  
  
                    CComPtr<IVbCompilerHost> srpVBHost;  
                    HRESULT hr2 = pEECompilerHost->QueryInterface(IID_IVbCompilerHost, (void **)&srpVBHost);  
  
                    pEECompilerHost->Release();  
  
                    if (SUCCEEDED(hr2))  
                    {  
                        m_pCompiler->RegisterEECompilerHost(srpVBHost);  
                    }  
                }  
            }  
            else  
            {  
                hr = S_OK;  
            }  
  
            if (m_pCompiler->FindEECompilerHost(pcstrCorPath, &m_pCompilerHost))  
            {  
                ULONG cErrors = 0;  
                ULONG cWarnings = 0;  
  
                m_pCompiler->CompileToBound(m_pCompilerHost, &cErrors, &cWarnings, NULL);  
  
                // This needs to happen after bound  
                if (m_pCompilerHost->GetVbLibraryType() == TLB_AutoDetect)  
                {  
                    m_pCompilerHost->AutoSetVbLibraryType();  
                }  
  
                VSASSERT(m_pCompiler && m_pCompilerHost && m_pCompilerHost->GetIntrinsicSymbol(t_i4) != NULL, "Invalid state");  
  
                if (cErrors + cWarnings > 0)  
                {  
                    VSFAIL("Errors from mscorlib.dll and vb runtime!");                 
                    __leave;  
                }  
  
                hr = S_OK;  
            }  
            else  
            {  
                VSFAIL("FindCompilerHost shouldn't have failed!");  
            }  
        }  
        catch_hresult;  
  
        VSASSERT(m_pCompilerHost->GetComPlusProject()->GetCompState() >= CS_Bound, "Debugger mscorlib not in bound state");  
  
        pVBEECompilerSingleton->UnlockEECompiler();  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>参照  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
