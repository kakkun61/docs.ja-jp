---
title: EPolicyAction 列挙型
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: 72b371d72b2f055f2840da5595d9022ffd7e2507
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674743"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="a855c-102">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="a855c-102">EPolicyAction Enumeration</span></span>

<span data-ttu-id="a855c-103">[EClrOperation](eclroperation-enumeration.md)によって記述された操作や[eclrfailure](eclrfailure-enumeration.md)によって記述されたエラーについて、ホストが設定できるポリシーアクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a855c-103">Describes the policy actions the host can set for operations described by [EClrOperation](eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a855c-104">構文</span><span class="sxs-lookup"><span data-stu-id="a855c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="a855c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a855c-105">Members</span></span>  
  
|<span data-ttu-id="a855c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a855c-106">Member</span></span>|<span data-ttu-id="a855c-107">説明</span><span class="sxs-lookup"><span data-stu-id="a855c-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="a855c-108">共通言語ランタイム (CLR) がスレッドを正常に中止する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="a855c-109">正常な中止には、すべて `finally` のブロック、 `catch` スレッドの中止に関連するブロック、およびファイナライザーを実行する試行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a855c-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="a855c-110">CLR が無効化された状態になるように指定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="a855c-111">影響を受けるプロセスでは、それ以上のマネージコードを実行できず、スレッドは CLR への入力がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="a855c-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="a855c-112">CLR がプロセスを正常に終了する必要があることを指定します。これには、ファイナライザーの実行やクリーンアップおよびログ操作の実行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a855c-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="a855c-113">CLR がファイナライザーを実行したりクリーンアップ操作やログ操作を実行したりせずに、プロセスをすぐに終了するように指定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="a855c-114">ただし、通知はデバッガーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="a855c-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="a855c-115">アクションを実行しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="a855c-116">CLR がルースレッド中止を実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="a855c-117">`catch` `finally` でマークされたおよびブロックだけ <xref:System.EnterpriseServices.MustRunInClientContextAttribute> が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a855c-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="a855c-118">CLR がファイナライザーまたはログ操作を実行せずにプロセスを終了する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="a855c-119">CLR がのルードアンロードを実行する必要があることを指定し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="a855c-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="a855c-120">でマークされたファイナライザーだけ <xref:System.EnterpriseServices.MustRunInClientContextAttribute> が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a855c-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="a855c-121">同様に、スタック内のこのを持つすべてのスレッドはを <xref:System.AppDomain> 受け取り `ThreadAbortException` ますが、 `catch` `finally` でマークされたおよびブロックだけ <xref:System.EnterpriseServices.MustRunInClientContextAttribute> が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a855c-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="a855c-122">メモリ不足、バッファーオーバーフローなどの条件に適した例外をスローする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="a855c-123">をアンロードすることを指定し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="a855c-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="a855c-124">CLR はファイナライザーの実行を試みます。</span><span class="sxs-lookup"><span data-stu-id="a855c-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a855c-125">注釈</span><span class="sxs-lookup"><span data-stu-id="a855c-125">Remarks</span></span>  

 <span data-ttu-id="a855c-126">ホストは、 [ICLRPolicyManager](iclrpolicymanager-interface.md) インターフェイスのメソッドを呼び出すことによって、ポリシーアクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a855c-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="a855c-127">ルードと正常な中止の詳細については、 [EClrOperation](eclroperation-enumeration.md) 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a855c-127">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a855c-128">要件</span><span class="sxs-lookup"><span data-stu-id="a855c-128">Requirements</span></span>  

 <span data-ttu-id="a855c-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a855c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a855c-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a855c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a855c-131">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a855c-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a855c-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a855c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a855c-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="a855c-133">See also</span></span>

- [<span data-ttu-id="a855c-134">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="a855c-134">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="a855c-135">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a855c-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="a855c-136">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a855c-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="a855c-137">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="a855c-137">Hosting Enumerations</span></span>](hosting-enumerations.md)
