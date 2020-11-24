---
title: ICorDebugThread2::GetVolatileOSThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
ms.openlocfilehash: 177c6057432912c402c379c70a22506d9bde261e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678611"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="e826e-102">ICorDebugThread2::GetVolatileOSThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="e826e-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>

<span data-ttu-id="e826e-103">この ICorDebugThread2 のオペレーティングシステムスレッド識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="e826e-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e826e-104">構文</span><span class="sxs-lookup"><span data-stu-id="e826e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e826e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e826e-105">Parameters</span></span>  

 `pdwTid`  
 <span data-ttu-id="e826e-106">入出力このスレッドのオペレーティングシステムスレッド識別子。</span><span class="sxs-lookup"><span data-stu-id="e826e-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e826e-107">要件</span><span class="sxs-lookup"><span data-stu-id="e826e-107">Requirements</span></span>  

 <span data-ttu-id="e826e-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e826e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e826e-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e826e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e826e-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e826e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e826e-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e826e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
