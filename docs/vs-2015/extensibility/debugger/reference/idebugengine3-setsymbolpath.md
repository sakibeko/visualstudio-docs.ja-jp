---
title: 'IDebugEngine3:: Setシンボル Path |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ea3086931ab655209a5ca26d4d1527462fb205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476805"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

デバッグシンボル用に検索されるパスを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`szSymbolSearchPath`|からシンボルの検索パスを含む文字列。 詳細については、「解説」を参照してください。 null にすることはできません。|  
|`szSymbolCachePath`|からシンボルをキャッシュできるローカルパスを含む文字列。 null にすることはできません。|  
|`Flags`|から使用しません。常に0に設定されます。|  
  
## <a name="return-value"></a>戻り値  
 成功した場合は S_OK を返します。それ以外の場合は、エラーコードを返します。  
  
## <a name="remarks"></a>注釈  
 文字列は、 `szSymbolSearchPath` 記号を検索するための、セミコロンで区切られた1つ以上のパスの一覧です。 これらのパスには、ローカルパス、UNC スタイルのパス、または URL を指定できます。 これらのパスは、異なる種類を混在させることもできます。 パスが UNC (たとえば、 \\ \ Sym\ シンボル) の場合、デバッグエンジンは、パスがシンボルサーバーであるかどうかを判断し、そのサーバーからシンボルを読み込んで、で指定したパスにキャッシュする必要があり `szSymbolCachePath` ます。  
  
 シンボルパスには、1つまたは複数のキャッシュの場所を含めることもできます。 キャッシュは優先順位順に一覧表示され、優先順位が最も高いキャッシュが先頭になり、* 記号で区切られます。 次に例を示します。  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com  
```  
  
 [Loadsymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)メソッドは、シンボルの実際の読み込みを実行します。  
  
## <a name="see-also"></a>参照  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
