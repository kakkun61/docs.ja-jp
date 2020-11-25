---
title: IGCThreadControl インターフェイス
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 02facbb0ff1c0f8978d4f4f720ab370f70f07fe2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721687"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="f8081-102">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8081-102">IGCThreadControl Interface</span></span>

<span data-ttu-id="f8081-103">ガベージコレクションに対してブロックされるスレッドのスケジュール設定に参加するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f8081-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8081-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8081-104">Methods</span></span>  
  
|<span data-ttu-id="f8081-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8081-105">Method</span></span>|<span data-ttu-id="f8081-106">説明</span><span class="sxs-lookup"><span data-stu-id="f8081-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8081-107">SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="f8081-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="f8081-108">ランタイムがガベージコレクションまたはその他の中断後にスレッドを再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="f8081-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="f8081-109">SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="f8081-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="f8081-110">ランタイムがガベージコレクションまたは他の中断のためにスレッドの中断を開始していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="f8081-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="f8081-111">ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="f8081-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="f8081-112">呼び出しを行っているスレッドがブロックしようとしていることをホストに通知します。ガベージコレクションやその他の中断が考えられます。</span><span class="sxs-lookup"><span data-stu-id="f8081-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8081-113">要件</span><span class="sxs-lookup"><span data-stu-id="f8081-113">Requirements</span></span>  

 <span data-ttu-id="f8081-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8081-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8081-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f8081-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8081-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f8081-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8081-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8081-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8081-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8081-118">See also</span></span>

- [<span data-ttu-id="f8081-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8081-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
