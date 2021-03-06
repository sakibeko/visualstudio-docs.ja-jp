---
title: PROCESS_INFO |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205016"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

プロセスに関する情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>メンバー  
 フィールド  
 入力するフィールドを指定する、 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) 列挙のフラグの組み合わせ。  
  
 bstrFileName  
 プロセスの完全なパス名。 パラメーターを指定して [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) メソッドを呼び出す場合と同じ `GN_FILENAME` です。  
  
 bstrBaseName  
 プロセスのファイル名と拡張子。 パラメーターを指定してメソッドを呼び出す場合と同じ `IDebugProcess2::Getname` `GN_BASENAME` です。  
  
 bstrTitle  
 プロセスのタイトル (存在する場合)。 パラメーターを指定してメソッドを呼び出す場合と同じ `IDebugProcess2::Getname` `GN_TITLE` です。  
  
 ProcessId  
 プロセスを識別する [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 構造体。 [Getphysicalprocessid](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)メソッドの呼び出しと同じです。  
  
 dwSessionId  
 このプロセスが実行されているデバッグセッションの識別子。  
  
 bstrAttachedSessionName  
 アタッチされたセッション名。 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)メソッドの呼び出しに相当します。  
  
 CreationTime  
 プロセスが作成された時刻。  
  
 フラグ  
 プロセスのプロパティを指定する、 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) 列挙のフラグの組み合わせ。  
  
## <a name="remarks"></a>注釈  
 この構造体は、入力されている [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) メソッドに渡されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg. h  
  
 名前空間: VisualStudio。  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
