---
title: IHostMemoryManager::VirtualAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: a2deabc5f1c7ea0f42b6d8ec3944d984854ae571
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731281"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="1543f-102">IHostMemoryManager::VirtualAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="1543f-102">IHostMemoryManager::VirtualAlloc Method</span></span>

<span data-ttu-id="1543f-103">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="1543f-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="1543f-104">の Win32 実装は、 `VirtualAlloc` 呼び出し元プロセスの仮想アドレス空間にあるページの領域を予約またはコミットします。</span><span class="sxs-lookup"><span data-stu-id="1543f-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1543f-105">構文</span><span class="sxs-lookup"><span data-stu-id="1543f-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1543f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1543f-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="1543f-107">から割り当てる領域の開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1543f-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="1543f-108">から領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="1543f-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="1543f-109">からメモリ割り当ての種類。</span><span class="sxs-lookup"><span data-stu-id="1543f-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="1543f-110">から割り当てられるページの領域のメモリ保護。</span><span class="sxs-lookup"><span data-stu-id="1543f-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="1543f-111">から割り当てエラーの影響を示す [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="1543f-111">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="1543f-112">入出力割り当てられたメモリの開始アドレスへのポインター。要求を満たすことができなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="1543f-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1543f-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="1543f-113">Return Value</span></span>  
  
|<span data-ttu-id="1543f-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1543f-114">HRESULT</span></span>|<span data-ttu-id="1543f-115">説明</span><span class="sxs-lookup"><span data-stu-id="1543f-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1543f-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1543f-116">S_OK</span></span>|<span data-ttu-id="1543f-117">`VirtualAlloc` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="1543f-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="1543f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1543f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1543f-119">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="1543f-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1543f-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1543f-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1543f-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1543f-121">The call timed out.</span></span>|  
|<span data-ttu-id="1543f-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1543f-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1543f-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1543f-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1543f-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1543f-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1543f-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="1543f-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1543f-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1543f-126">E_FAIL</span></span>|<span data-ttu-id="1543f-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1543f-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1543f-128">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1543f-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1543f-129">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="1543f-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1543f-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1543f-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1543f-131">割り当て要求を完了するのに十分なメモリがありませんでした</span><span class="sxs-lookup"><span data-stu-id="1543f-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1543f-132">注釈</span><span class="sxs-lookup"><span data-stu-id="1543f-132">Remarks</span></span>  

 <span data-ttu-id="1543f-133">を呼び出して、プロセスのアドレス空間にリージョンを予約し `VirtualAlloc` ます。</span><span class="sxs-lookup"><span data-stu-id="1543f-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="1543f-134">パラメーターには、 `pAddress` 必要なメモリブロックの開始アドレスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="1543f-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="1543f-135">通常、このパラメーターは null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1543f-135">This parameter is typically set to null.</span></span> <span data-ttu-id="1543f-136">オペレーティングシステムは、プロセスで使用可能な空きアドレス範囲の記録を保持します。</span><span class="sxs-lookup"><span data-stu-id="1543f-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="1543f-137">値が null の場合は、 `pAddress` 必要に応じてリージョンを予約するようにシステムに指示します。</span><span class="sxs-lookup"><span data-stu-id="1543f-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="1543f-138">または、メモリブロックの特定の開始アドレスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1543f-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="1543f-139">どちらの場合も、出力パラメーター `ppMem` は、割り当てられたメモリへのポインターとして返されます。</span><span class="sxs-lookup"><span data-stu-id="1543f-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="1543f-140">関数自体は HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="1543f-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="1543f-141">Win32 関数にはパラメーターがないため、 `VirtualAlloc` `ppMem` 代わりに割り当てられたメモリへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="1543f-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="1543f-142">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1543f-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1543f-143">要件</span><span class="sxs-lookup"><span data-stu-id="1543f-143">Requirements</span></span>  

 <span data-ttu-id="1543f-144">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1543f-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1543f-145">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1543f-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1543f-146">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1543f-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1543f-147">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1543f-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1543f-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="1543f-148">See also</span></span>

- [<span data-ttu-id="1543f-149">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1543f-149">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
