---
title: IHostMAlloc::Free メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: d4c9048c89d55ed048a55a771572823905a056df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687139"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="f018c-102">IHostMAlloc::Free メソッド</span><span class="sxs-lookup"><span data-stu-id="f018c-102">IHostMAlloc::Free Method</span></span>

<span data-ttu-id="f018c-103">[Alloc](ihostmalloc-alloc-method.md)関数を使用して割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="f018c-103">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f018c-104">構文</span><span class="sxs-lookup"><span data-stu-id="f018c-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f018c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f018c-105">Parameters</span></span>  

 `pMem`  
 <span data-ttu-id="f018c-106">から解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f018c-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f018c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="f018c-107">Return Value</span></span>  
  
|<span data-ttu-id="f018c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f018c-108">HRESULT</span></span>|<span data-ttu-id="f018c-109">説明</span><span class="sxs-lookup"><span data-stu-id="f018c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f018c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f018c-110">S_OK</span></span>|<span data-ttu-id="f018c-111">`Free` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f018c-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="f018c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f018c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f018c-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f018c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f018c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f018c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f018c-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f018c-115">The call timed out.</span></span>|  
|<span data-ttu-id="f018c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f018c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f018c-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f018c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f018c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f018c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f018c-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f018c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f018c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f018c-120">E_FAIL</span></span>|<span data-ttu-id="f018c-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f018c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f018c-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f018c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f018c-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f018c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f018c-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="f018c-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="f018c-125">ホストを通じて割り当てられていないメモリを解放しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f018c-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f018c-126">注釈</span><span class="sxs-lookup"><span data-stu-id="f018c-126">Remarks</span></span>  

 <span data-ttu-id="f018c-127">パラメーターが、 `pMem` の呼び出しを使用して割り当てられていないメモリ領域を参照している場合 `Alloc` 、ホストは HOST_E_INVALIDOPERATION を返します。</span><span class="sxs-lookup"><span data-stu-id="f018c-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f018c-128">要件</span><span class="sxs-lookup"><span data-stu-id="f018c-128">Requirements</span></span>  

 <span data-ttu-id="f018c-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f018c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f018c-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f018c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f018c-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f018c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f018c-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f018c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f018c-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="f018c-133">See also</span></span>

- [<span data-ttu-id="f018c-134">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f018c-134">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="f018c-135">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f018c-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
