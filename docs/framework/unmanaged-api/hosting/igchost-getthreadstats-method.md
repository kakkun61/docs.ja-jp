---
title: IGCHost::GetThreadStats メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: c48b580e632d67db5a9826c210415adab1bdba96
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670070"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="77719-102">IGCHost::GetThreadStats メソッド</span><span class="sxs-lookup"><span data-stu-id="77719-102">IGCHost::GetThreadStats Method</span></span>

<span data-ttu-id="77719-103">ガベージコレクションのスレッドごとの統計を取得します。</span><span class="sxs-lookup"><span data-stu-id="77719-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77719-104">構文</span><span class="sxs-lookup"><span data-stu-id="77719-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77719-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77719-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="77719-106">から統計を取得するスレッドを指定するファイバークッキーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="77719-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="77719-107">[入力、出力]指定したスレッドのガベージコレクションの統計情報を格納している [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="77719-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77719-108">要件</span><span class="sxs-lookup"><span data-stu-id="77719-108">Requirements</span></span>  

 <span data-ttu-id="77719-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77719-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77719-110">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="77719-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="77719-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="77719-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77719-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77719-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77719-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="77719-113">See also</span></span>

- [<span data-ttu-id="77719-114">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77719-114">IGCHost Interface</span></span>](igchost-interface.md)
