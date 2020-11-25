---
title: IHostMemoryManager::ReleasedVirtualAddressSpace メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
ms.openlocfilehash: 8a875d59d270f087ce22079830818a9205309cc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731294"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="40c0f-102">IHostMemoryManager::ReleasedVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="40c0f-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>

<span data-ttu-id="40c0f-103">指定されたメモリを使用して共通言語ランタイム (CLR) が終了したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="40c0f-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="40c0f-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c0f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40c0f-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="40c0f-106">から解放されるメモリの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="40c0f-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40c0f-107">注釈</span><span class="sxs-lookup"><span data-stu-id="40c0f-107">Remarks</span></span>  

 <span data-ttu-id="40c0f-108">`ReleasedVirtualAddressSpace`メソッドはコールバックメソッドであり、ホストアプリケーションのライターによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c0f-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="40c0f-109">これは CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="40c0f-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c0f-110">要件</span><span class="sxs-lookup"><span data-stu-id="40c0f-110">Requirements</span></span>  

 <span data-ttu-id="40c0f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40c0f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c0f-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="40c0f-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40c0f-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="40c0f-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40c0f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c0f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c0f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="40c0f-115">See also</span></span>

- [<span data-ttu-id="40c0f-116">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40c0f-116">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
