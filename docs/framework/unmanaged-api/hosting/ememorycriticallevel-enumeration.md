---
title: EMemoryCriticalLevel 列挙型
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 3b9ad4b40ce94420f2ab5fc25335c41dec15dc09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720554"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="585e3-102">EMemoryCriticalLevel 列挙型</span><span class="sxs-lookup"><span data-stu-id="585e3-102">EMemoryCriticalLevel Enumeration</span></span>

<span data-ttu-id="585e3-103">特定のメモリ割り当てが要求されたが、満たされない場合のエラーの影響を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="585e3-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="585e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="585e3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="585e3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="585e3-105">Members</span></span>  
  
|<span data-ttu-id="585e3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="585e3-106">Member</span></span>|<span data-ttu-id="585e3-107">説明</span><span class="sxs-lookup"><span data-stu-id="585e3-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="585e3-108">割り当てを要求したドメイン内のマネージコードを実行するために割り当てが不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="585e3-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="585e3-109">メモリを割り当てることができない場合、CLR はドメインが引き続き使用可能であることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="585e3-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="585e3-110">ホストは、割り当てを満たすことができない場合に実行するアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="585e3-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="585e3-111">CLR は、を自動的に中止するように指示することも、 `AppDomain` [ICLRPolicyManager](iclrpolicymanager-interface.md)でメソッドを呼び出すことによって実行を継続できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="585e3-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="585e3-112">は、プロセス内のマネージコードの実行に対して割り当てが不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="585e3-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="585e3-113">この値は、起動時とファイナライザーの実行時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="585e3-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="585e3-114">メモリを割り当てることができない場合、CLR はプロセスで動作できません。</span><span class="sxs-lookup"><span data-stu-id="585e3-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="585e3-115">割り当てが失敗した場合、CLR は実質的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="585e3-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="585e3-116">CLR への後続の呼び出しはすべて、HOST_E_CLRNOTAVAILABLE で失敗します。</span><span class="sxs-lookup"><span data-stu-id="585e3-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="585e3-117">割り当てを要求したタスクを実行するために割り当てが不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="585e3-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="585e3-118">メモリを割り当てることができない場合、CLR はタスクを実行できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="585e3-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="585e3-119">エラーが発生した場合、CLR は <xref:System.Threading.ThreadAbortException> 物理操作システムスレッドでを発生させます。</span><span class="sxs-lookup"><span data-stu-id="585e3-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="585e3-120">注釈</span><span class="sxs-lookup"><span data-stu-id="585e3-120">Remarks</span></span>  

 <span data-ttu-id="585e3-121">[IHostMemoryManager](ihostmemorymanager-interface.md)インターフェイスと[IHostMAlloc](ihostmalloc-interface.md)インターフェイスで定義されているメモリ割り当てメソッドは、この型のパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="585e3-121">The memory allocation methods defined in the [IHostMemoryManager](ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="585e3-122">障害の重大度に応じて、割り当て要求を直ちに失敗させるか、または満たされるまで待機するかをホストが決定できます。</span><span class="sxs-lookup"><span data-stu-id="585e3-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="585e3-123">要件</span><span class="sxs-lookup"><span data-stu-id="585e3-123">Requirements</span></span>  

 <span data-ttu-id="585e3-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="585e3-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="585e3-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="585e3-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="585e3-126">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="585e3-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="585e3-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="585e3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585e3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="585e3-128">See also</span></span>

- [<span data-ttu-id="585e3-129">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="585e3-129">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="585e3-130">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="585e3-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
