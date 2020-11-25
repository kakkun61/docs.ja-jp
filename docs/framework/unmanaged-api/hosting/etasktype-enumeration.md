---
title: ETaskType 列挙型
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 332488fee4c982fdbaecceeaa2a6a3876f1602a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733699"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="70060-102">ETaskType 列挙型</span><span class="sxs-lookup"><span data-stu-id="70060-102">ETaskType Enumeration</span></span>

<span data-ttu-id="70060-103">[ICLRTask](iclrtask-interface.md)または[IHostTask](ihosttask-interface.md)インターフェイスによって表されるタスクの種類を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="70060-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70060-104">構文</span><span class="sxs-lookup"><span data-stu-id="70060-104">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="70060-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="70060-105">Members</span></span>  
  
|<span data-ttu-id="70060-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="70060-106">Member</span></span>|<span data-ttu-id="70060-107">説明</span><span class="sxs-lookup"><span data-stu-id="70060-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="70060-108">インターフェイスは、アプリケーションドメインのアンロードタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="70060-109">インターフェイスは、デバッガーヘルパータスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="70060-110">インターフェイスは、ファイナライザータスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="70060-111">インターフェイスは、ガベージコレクションタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="70060-112">インターフェイスは、ゲートスレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="70060-113">インターフェイスは、i/o スレッドタスクまたは完了ポートスレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="70060-114">インターフェイスは、タイマースレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="70060-115">インターフェイスは、待機スレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="70060-116">インターフェイスは、ワーカースレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="70060-117">タスクは不明です。</span><span class="sxs-lookup"><span data-stu-id="70060-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="70060-118">インターフェイスは、ユーザータスクを表します。</span><span class="sxs-lookup"><span data-stu-id="70060-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70060-119">要件</span><span class="sxs-lookup"><span data-stu-id="70060-119">Requirements</span></span>  

 <span data-ttu-id="70060-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70060-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70060-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="70060-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70060-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70060-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70060-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70060-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70060-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="70060-124">See also</span></span>

- [<span data-ttu-id="70060-125">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="70060-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
