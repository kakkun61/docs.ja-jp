---
title: IGCHost::GetStats メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: 7e664d88bf9f67e936e693b663f27ca490da13ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670109"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="a8514-102">IGCHost::GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="a8514-102">IGCHost::GetStats Method</span></span>

<span data-ttu-id="a8514-103">ガベージコレクションシステムの現在の状態の統計を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8514-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8514-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8514-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8514-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8514-105">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="a8514-106">[入力、出力]ガベージコレクションシステムの現在の状態の統計情報を格納している [COR_GC_STATS](cor-gc-stats-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a8514-106">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8514-107">注釈</span><span class="sxs-lookup"><span data-stu-id="a8514-107">Remarks</span></span>  

 <span data-ttu-id="a8514-108">統計は、ガベージコレクションシステムが動作するためにスマートアロケーションシステムによって使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8514-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="a8514-109">たとえば、割り当てシステムでは、統計情報を確認した後に、メモリを追加したり、コレクションを強制したりする必要があることを判断できます。</span><span class="sxs-lookup"><span data-stu-id="a8514-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8514-110">要件</span><span class="sxs-lookup"><span data-stu-id="a8514-110">Requirements</span></span>  

 <span data-ttu-id="a8514-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8514-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8514-112">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="a8514-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a8514-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a8514-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8514-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8514-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8514-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8514-115">See also</span></span>

- [<span data-ttu-id="a8514-116">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8514-116">IGCHost Interface</span></span>](igchost-interface.md)
