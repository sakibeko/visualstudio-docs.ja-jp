---
title: IDebugProperty3 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 479827cc83486d6bb9c68d0749b8870cd6c41861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694761"
---
# <a name="idebugproperty3"></a>IDebugProperty3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、次の機能をサポートします。  
  
- プロパティに関連付けられている任意の長い文字列を取得します。  
  
- 一意の ID をプロパティに関連付ける。  
  
- プロパティのカスタムビューアーの一覧を取得しています。  
  
- 結果のエラーを報告する機能を持つプロパティの値を設定する  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>実装側の注意  
 デバッグエンジン (DE) は、長い文字列、プロパティ Id、およびカスタムビューアーをサポートするために、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) を実装する同じオブジェクトにこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元に関する注意事項  
 インターフェイスの [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) を呼び出して、 `IDebugProperty2` このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 から継承されたメソッドに加えて、 `IDebugProperty2` `IDebugProperty3` インターフェイスは次のメソッドを公開します。  
  
|Method|説明|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|プロパティに関連付けられている文字列の長さを返します。|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|ユーザーが指定したバッファー内の文字列を返します。|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|このプロパティの一意の ID を作成します。|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|このプロパティの一意の ID を破棄します。|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|このプロパティが表示できるカスタムビューアーの数を返します。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|このプロパティを表示できるカスタムビューアーの一覧を返します。|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|このプロパティの値を設定し、何らかの問題が発生した場合にエラーメッセージを返します。|  
  
## <a name="remarks"></a>解説  
 [Setvalueasstringwitherror](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) は、セッションデバッグマネージャー (SDM) がプロパティの値を設定するために推奨される方法です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg. h  
  
 名前空間: VisualStudio。  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コアインターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
