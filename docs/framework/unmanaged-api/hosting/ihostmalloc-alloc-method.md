---
title: IHostMAlloc::Alloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: 5858b03676db0839621b121131ded4da9950ce88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675127"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="42bcd-102">IHostMAlloc::Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="42bcd-102">IHostMAlloc::Alloc Method</span></span>

<span data-ttu-id="42bcd-103">ホストが指定された量のメモリをヒープから割り当てることを要求します。</span><span class="sxs-lookup"><span data-stu-id="42bcd-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42bcd-104">構文</span><span class="sxs-lookup"><span data-stu-id="42bcd-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42bcd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42bcd-105">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="42bcd-106">から現在のメモリ割り当て要求のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="42bcd-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="42bcd-107">から割り当てエラーの影響を示す [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="42bcd-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="42bcd-108">入出力割り当てられたメモリへのポインター。要求を完了できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="42bcd-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42bcd-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="42bcd-109">Return Value</span></span>  
  
|<span data-ttu-id="42bcd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42bcd-110">HRESULT</span></span>|<span data-ttu-id="42bcd-111">説明</span><span class="sxs-lookup"><span data-stu-id="42bcd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42bcd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="42bcd-112">S_OK</span></span>|<span data-ttu-id="42bcd-113">`Alloc` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="42bcd-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="42bcd-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42bcd-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42bcd-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="42bcd-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42bcd-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42bcd-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42bcd-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="42bcd-117">The call timed out.</span></span>|  
|<span data-ttu-id="42bcd-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42bcd-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42bcd-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="42bcd-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42bcd-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42bcd-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42bcd-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="42bcd-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42bcd-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42bcd-122">E_FAIL</span></span>|<span data-ttu-id="42bcd-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="42bcd-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42bcd-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="42bcd-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42bcd-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="42bcd-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="42bcd-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="42bcd-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="42bcd-127">割り当て要求を完了するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="42bcd-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42bcd-128">注釈</span><span class="sxs-lookup"><span data-stu-id="42bcd-128">Remarks</span></span>  

 <span data-ttu-id="42bcd-129">CLR は、 `IHostMalloc` [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) メソッドを呼び出すことによって、インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="42bcd-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42bcd-130">要件</span><span class="sxs-lookup"><span data-stu-id="42bcd-130">Requirements</span></span>  

 <span data-ttu-id="42bcd-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42bcd-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42bcd-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="42bcd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42bcd-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="42bcd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42bcd-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42bcd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42bcd-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="42bcd-135">See also</span></span>

- [<span data-ttu-id="42bcd-136">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42bcd-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="42bcd-137">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42bcd-137">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
