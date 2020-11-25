---
title: MDAInfo 構造体
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
ms.openlocfilehash: 8e88d90e3291d21888fae7aa162f84b6377658c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730020"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="ab010-102">MDAInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="ab010-102">MDAInfo Structure</span></span>

<span data-ttu-id="ab010-103">`Event_MDAFired`マネージデバッグアシスタント (MDA) の作成をトリガーするイベントについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="ab010-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab010-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab010-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="ab010-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ab010-105">Members</span></span>  
  
|<span data-ttu-id="ab010-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ab010-106">Member</span></span>|<span data-ttu-id="ab010-107">説明</span><span class="sxs-lookup"><span data-stu-id="ab010-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="ab010-108">現在の MDA のタイトル。</span><span class="sxs-lookup"><span data-stu-id="ab010-108">The title of the current MDA.</span></span> <span data-ttu-id="ab010-109">タイトルには、イベントを発生させたエラーの種類が示され `Event_MDAFired` ます。</span><span class="sxs-lookup"><span data-stu-id="ab010-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="ab010-110">現在の MDA によって提供される出力メッセージ。</span><span class="sxs-lookup"><span data-stu-id="ab010-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab010-111">注釈</span><span class="sxs-lookup"><span data-stu-id="ab010-111">Remarks</span></span>  

 <span data-ttu-id="ab010-112">マネージデバッグアシスタント (Mda) は、共通言語ランタイム (CLR) と連携して動作し、ランタイム実行エンジンで無効な条件を特定したり、エンジンの状態に関する追加情報をダンプするなどのタスクを実行したりするためのデバッグ補助機能です。</span><span class="sxs-lookup"><span data-stu-id="ab010-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="ab010-113">Mda は、トラップが困難なイベントに関する XML メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="ab010-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="ab010-114">これらは、マネージコードとアンマネージコードの間の遷移をデバッグする場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="ab010-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="ab010-115">MDA の作成をトリガーするイベントが発生した場合、ランタイムは次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ab010-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="ab010-116">[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)を呼び出してイベントを通知することで、ホストが[Iactiononclrevent](iactiononclrevent-interface.md)インスタンスを登録していない場合 `Event_MDAFired` 、ランタイムは既定のホストされていない動作に進みます。</span><span class="sxs-lookup"><span data-stu-id="ab010-116">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="ab010-117">ホストがこのイベントのハンドラーを登録している場合、ランタイムはデバッガーがプロセスにアタッチされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ab010-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="ab010-118">存在する場合、ランタイムはデバッガーに中断します。</span><span class="sxs-lookup"><span data-stu-id="ab010-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="ab010-119">デバッガーが続行されると、ホストが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ab010-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="ab010-120">デバッガーがアタッチされていない場合、ランタイムはを呼び出し、 `IActionOnCLREvent::OnEvent` `MDAInfo` パラメーターとしてインスタンスへのポインターを渡し `data` ます。</span><span class="sxs-lookup"><span data-stu-id="ab010-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="ab010-121">ホストは mda をアクティブ化し、MDA がアクティブになったときに通知を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="ab010-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="ab010-122">これにより、ホストは、既定の動作をオーバーライドし、イベントを発生させたマネージスレッドを中止して、プロセスの状態が破損するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="ab010-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="ab010-123">Mda の使用方法の詳細については、「 [マネージデバッグアシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab010-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab010-124">要件</span><span class="sxs-lookup"><span data-stu-id="ab010-124">Requirements</span></span>  

 <span data-ttu-id="ab010-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab010-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab010-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ab010-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="ab010-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ab010-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab010-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab010-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab010-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab010-129">See also</span></span>

- [<span data-ttu-id="ab010-130">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="ab010-130">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="ab010-131">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="ab010-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
