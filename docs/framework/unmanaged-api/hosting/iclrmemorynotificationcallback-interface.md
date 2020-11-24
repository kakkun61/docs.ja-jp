---
title: ICLRMemoryNotificationCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 5762a354bec485cb382b5460dfd2a337f79bee1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689538"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="45e69-102">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45e69-102">ICLRMemoryNotificationCallback Interface</span></span>

<span data-ttu-id="45e69-103">Win32 関数と同様の方法を使用して、ホストがメモリ不足状態を報告できるようにし `CreateMemoryResourceNotification` ます。</span><span class="sxs-lookup"><span data-stu-id="45e69-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45e69-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="45e69-104">Methods</span></span>  
  
|<span data-ttu-id="45e69-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="45e69-105">Method</span></span>|<span data-ttu-id="45e69-106">説明</span><span class="sxs-lookup"><span data-stu-id="45e69-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45e69-107">OnMemoryNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="45e69-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="45e69-108">コンピューターのメモリ負荷の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="45e69-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45e69-109">注釈</span><span class="sxs-lookup"><span data-stu-id="45e69-109">Remarks</span></span>  

 <span data-ttu-id="45e69-110">ホストは、このインターフェイスを使用して、 `ICLRMemoryNotificationCallback` CLR のメモリリソースを解放するように要求します。</span><span class="sxs-lookup"><span data-stu-id="45e69-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e69-111">要件</span><span class="sxs-lookup"><span data-stu-id="45e69-111">Requirements</span></span>  

 <span data-ttu-id="45e69-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45e69-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e69-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="45e69-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45e69-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="45e69-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45e69-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e69-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e69-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="45e69-116">See also</span></span>

- [<span data-ttu-id="45e69-117">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45e69-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="45e69-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45e69-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
