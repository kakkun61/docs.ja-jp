---
title: IHostMemoryManager::AcquiredVirtualAddressSpace メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: 58fce616ae05dcc622369a706f010f91d657389f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700627"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="87454-102">IHostMemoryManager::AcquiredVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="87454-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>

<span data-ttu-id="87454-103">共通言語ランタイム (CLR) が、指定されたメモリをオペレーティングシステムから取得したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="87454-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87454-104">構文</span><span class="sxs-lookup"><span data-stu-id="87454-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87454-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87454-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="87454-106">からメモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="87454-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="87454-107">からメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="87454-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87454-108">注釈</span><span class="sxs-lookup"><span data-stu-id="87454-108">Remarks</span></span>  

 <span data-ttu-id="87454-109">`AcquiredVirtualAddressSpace`メソッドはコールバックメソッドであり、ホストアプリケーションのライターによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="87454-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="87454-110">これは CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="87454-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87454-111">要件</span><span class="sxs-lookup"><span data-stu-id="87454-111">Requirements</span></span>  

 <span data-ttu-id="87454-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87454-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87454-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="87454-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87454-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="87454-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87454-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87454-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87454-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="87454-116">See also</span></span>

- [<span data-ttu-id="87454-117">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87454-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
