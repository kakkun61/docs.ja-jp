---
title: ICLRDebugManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
ms.openlocfilehash: 3836bd349423670a19a19dda67eba75419507a29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724289"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="4fd46-102">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fd46-102">ICLRDebugManager Interface</span></span>

<span data-ttu-id="4fd46-103">ホストが一連のタスクを識別子とフレンドリ名に関連付けることができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4fd46-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fd46-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-104">Methods</span></span>  
  
|<span data-ttu-id="4fd46-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-105">Method</span></span>|<span data-ttu-id="4fd46-106">説明</span><span class="sxs-lookup"><span data-stu-id="4fd46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fd46-107">BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-107">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="4fd46-108">ホストとデバッガーの間の新しい接続を確立して、タスクを識別子とフレンドリ名に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="4fd46-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="4fd46-109">EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-109">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="4fd46-110">タスクのリストと id とフレンドリ名の間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="4fd46-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="4fd46-111">GetDacl メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-111">GetDacl Method</span></span>](iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="4fd46-112">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="4fd46-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="4fd46-113">IsDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-113">IsDebuggerAttached Method</span></span>](iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="4fd46-114">デバッガーがプロセスにアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4fd46-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="4fd46-115">SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-115">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="4fd46-116">[ICLRTask](iclrtask-interface.md)インスタンスのリストを識別子とフレンドリ名に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="4fd46-116">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="4fd46-117">SetDacl メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-117">SetDacl Method</span></span>](iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="4fd46-118">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="4fd46-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="4fd46-119">SetSymbolReadingPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="4fd46-119">SetSymbolReadingPolicy Method</span></span>](iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="4fd46-120">プログラムデータベース (PDB) ファイルを読み取るためのポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="4fd46-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="4fd46-121">ポリシーは、行番号とファイルに関する情報が呼び出し履歴に含まれるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="4fd46-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fd46-122">注釈</span><span class="sxs-lookup"><span data-stu-id="4fd46-122">Remarks</span></span>  

 <span data-ttu-id="4fd46-123">デバッグシナリオでは、ホストは、独自のプログラミングロジックに従ってタスクをグループ化することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4fd46-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="4fd46-124">たとえば、グループ化により、開発者は、プロセスで実行されているすべてのタスクを表示するのではなく、開発者の Api に必要なタスクのみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="4fd46-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="4fd46-125">`ICLRDebugManager` ホストがこの種のグループ化を実装できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4fd46-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4fd46-126">、 `ICLRDebugManager` `BeginConnection` 、およびの3つのメソッドは相互に `SetConnectionTasks` `EndConnection` 依存しています。</span><span class="sxs-lookup"><span data-stu-id="4fd46-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="4fd46-127">これらは、想定どおりに動作するために、指定された順序で呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fd46-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="4fd46-128">グループ化、およびホストがグループに割り当てる識別子とフレンドリ名は、共通言語ランタイム (CLR) には意味がありません。</span><span class="sxs-lookup"><span data-stu-id="4fd46-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="4fd46-129">CLR は、情報をデバッガーに渡すだけです。</span><span class="sxs-lookup"><span data-stu-id="4fd46-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd46-130">要件</span><span class="sxs-lookup"><span data-stu-id="4fd46-130">Requirements</span></span>  

 <span data-ttu-id="4fd46-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fd46-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fd46-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4fd46-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fd46-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4fd46-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fd46-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fd46-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd46-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fd46-135">See also</span></span>

- [<span data-ttu-id="4fd46-136">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fd46-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
