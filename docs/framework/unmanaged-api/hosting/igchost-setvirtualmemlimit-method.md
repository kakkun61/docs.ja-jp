---
title: IGCHost::SetVirtualMemLimit メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: 9898b760edbb149afcd6bf957a30d0a47287485b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687809"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="ce9ee-102">IGCHost::SetVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="ce9ee-102">IGCHost::SetVirtualMemLimit Method</span></span>

<span data-ttu-id="ce9ee-103">ランタイムの仮想メモリの最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="ce9ee-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9ee-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce9ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce9ee-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce9ee-105">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="ce9ee-106">からランタイムの仮想メモリの最大サイズ (mb 単位)。</span><span class="sxs-lookup"><span data-stu-id="ce9ee-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce9ee-107">注釈</span><span class="sxs-lookup"><span data-stu-id="ce9ee-107">Remarks</span></span>  

 <span data-ttu-id="ce9ee-108">ランタイムの仮想メモリの最大サイズは動的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="ce9ee-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9ee-109">要件</span><span class="sxs-lookup"><span data-stu-id="ce9ee-109">Requirements</span></span>  

 <span data-ttu-id="ce9ee-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce9ee-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9ee-111">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="ce9ee-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ce9ee-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ce9ee-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce9ee-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9ee-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce9ee-114">See also</span></span>

- [<span data-ttu-id="ce9ee-115">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce9ee-115">IGCHost Interface</span></span>](igchost-interface.md)
