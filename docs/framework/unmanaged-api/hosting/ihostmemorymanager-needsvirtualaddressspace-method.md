---
title: IHostMemoryManager::NeedsVirtualAddressSpace メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: 74fbb2f162fbb68871f1bb4e1a1de32f5f913cd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731320"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="a7c7c-102">IHostMemoryManager::NeedsVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="a7c7c-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>

<span data-ttu-id="a7c7c-103">共通言語ランタイム (CLR) が、指定されたメモリを使用しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a7c7c-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c7c-104">構文</span><span class="sxs-lookup"><span data-stu-id="a7c7c-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7c7c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a7c7c-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="a7c7c-106">からメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a7c7c-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="a7c7c-107">からメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="a7c7c-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7c7c-108">注釈</span><span class="sxs-lookup"><span data-stu-id="a7c7c-108">Remarks</span></span>  

 <span data-ttu-id="a7c7c-109">`NeedsVirtualAddressSpace`メソッドはコールバックメソッドであり、ホストアプリケーションのライターによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7c7c-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="a7c7c-110">これは CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a7c7c-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="a7c7c-111">ホストが指定されたメモリを使用しないようにする場合は、E_OUTOFMEMORY HRESULT が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a7c7c-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7c7c-112">要件</span><span class="sxs-lookup"><span data-stu-id="a7c7c-112">Requirements</span></span>  

 <span data-ttu-id="a7c7c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7c7c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c7c-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a7c7c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7c7c-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a7c7c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7c7c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c7c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c7c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7c7c-117">See also</span></span>

- [<span data-ttu-id="a7c7c-118">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7c7c-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
