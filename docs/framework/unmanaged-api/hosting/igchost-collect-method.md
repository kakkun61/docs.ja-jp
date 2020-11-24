---
title: IGCHost::Collect メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: f32b91f0d47449f80c38542162035999d616813b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670143"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="ec064-102">IGCHost::Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="ec064-102">IGCHost::Collect Method</span></span>

<span data-ttu-id="ec064-103">現在のガベージコレクションの状態に関係なく、指定したジェネレーションに対して強制的にコレクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ec064-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec064-104">構文</span><span class="sxs-lookup"><span data-stu-id="ec064-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec064-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec064-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="ec064-106">からガベージコレクションを実行する生成。</span><span class="sxs-lookup"><span data-stu-id="ec064-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="ec064-107">値-1 は、すべてのジェネレーションがガベージコレクションを実行することを示します。</span><span class="sxs-lookup"><span data-stu-id="ec064-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec064-108">要件</span><span class="sxs-lookup"><span data-stu-id="ec064-108">Requirements</span></span>  

 <span data-ttu-id="ec064-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec064-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec064-110">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="ec064-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ec064-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ec064-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec064-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec064-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec064-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec064-113">See also</span></span>

- [<span data-ttu-id="ec064-114">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec064-114">IGCHost Interface</span></span>](igchost-interface.md)
