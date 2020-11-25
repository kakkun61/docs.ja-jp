---
title: WAIT_OPTION 列挙型
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 056d41df328de5796eec9f04589205d18b408f1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732802"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="c5284-102">WAIT_OPTION 列挙型</span><span class="sxs-lookup"><span data-stu-id="c5284-102">WAIT_OPTION Enumeration</span></span>

<span data-ttu-id="c5284-103">共通言語ランタイム (CLR) ブロックによって操作が要求された場合にホストが実行するアクションを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="c5284-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5284-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5284-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="c5284-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5284-105">Members</span></span>  
  
|<span data-ttu-id="c5284-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5284-106">Member</span></span>|<span data-ttu-id="c5284-107">説明</span><span class="sxs-lookup"><span data-stu-id="c5284-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="c5284-108">CLR が [IHostTask:: Alert](ihosttask-alert-method.md) メソッドを呼び出した場合に、タスクが起こされる必要があることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="c5284-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="c5284-109">スレッドがブロックされた場合に、現在の OS スレッドでメッセージをポンプする必要があることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="c5284-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="c5284-110">ランタイムは、スレッドに対してのみこの値を指定し <xref:System.Threading.ApartmentState.STA> ます。</span><span class="sxs-lookup"><span data-stu-id="c5284-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="c5284-111">指定された同期要求がホストによって壊れていないことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="c5284-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="c5284-112">つまり、ホストはを返すことができません `HOST_E_DEADLOCK` 。</span><span class="sxs-lookup"><span data-stu-id="c5284-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5284-113">注釈</span><span class="sxs-lookup"><span data-stu-id="c5284-113">Remarks</span></span>  

 <span data-ttu-id="c5284-114">[IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md)メソッドと[IHostTaskManager:: switchtotask](ihosttaskmanager-switchtotask-method.md)メソッドは、どちらもこの型のパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c5284-114">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5284-115">要件</span><span class="sxs-lookup"><span data-stu-id="c5284-115">Requirements</span></span>  

 <span data-ttu-id="c5284-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5284-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5284-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c5284-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5284-118">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5284-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5284-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5284-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5284-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5284-120">See also</span></span>

- [<span data-ttu-id="c5284-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="c5284-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
