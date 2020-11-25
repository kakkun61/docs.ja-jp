---
title: ICorDebugModule::GetFunctionFromRVA メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromRVA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromRVA
helpviewer_keywords:
- GetFunctionFromRVA method [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromRVA method [.NET Framework debugging]
ms.assetid: f5a34517-2422-484f-be89-2ce0b4bce195
topic_type:
- apiref
ms.openlocfilehash: 85f368eaa024e7792e5feefeb08f0bac1b59494d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710130"
---
# <a name="icordebugmodulegetfunctionfromrva-method"></a><span data-ttu-id="68c6f-102">ICorDebugModule::GetFunctionFromRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="68c6f-102">ICorDebugModule::GetFunctionFromRVA Method</span></span>

<span data-ttu-id="68c6f-103">このメソッドは、現在のバージョンの .NET Framework では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="68c6f-103">This method has not been implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c6f-104">構文</span><span class="sxs-lookup"><span data-stu-id="68c6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromRVA(  
    [in]  CORDB_ADDRESS      rva,  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="68c6f-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="68c6f-105">Requirements</span></span>  

 <span data-ttu-id="68c6f-106">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68c6f-106">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c6f-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="68c6f-107">See also</span></span>
