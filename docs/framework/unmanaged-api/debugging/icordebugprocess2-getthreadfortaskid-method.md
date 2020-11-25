---
title: ICorDebugProcess2::GetThreadForTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
ms.openlocfilehash: 2b18289af460f64085fedd7b32387ebcb8c51715
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713549"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="b3fdd-102">ICorDebugProcess2::GetThreadForTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="b3fdd-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>

<span data-ttu-id="b3fdd-103">指定した id を持つタスクが実行されているスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="b3fdd-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3fdd-104">構文</span><span class="sxs-lookup"><span data-stu-id="b3fdd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3fdd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3fdd-105">Parameters</span></span>  

 `taskid`  
 <span data-ttu-id="b3fdd-106">からタスクの識別子です。</span><span class="sxs-lookup"><span data-stu-id="b3fdd-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="b3fdd-107">入出力取得するスレッドを表す ICorDebugThread2 オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b3fdd-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3fdd-108">注釈</span><span class="sxs-lookup"><span data-stu-id="b3fdd-108">Remarks</span></span>  

 <span data-ttu-id="b3fdd-109">ホストは、 [ICLRTask:: SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) メソッドを使用してタスク識別子を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b3fdd-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3fdd-110">要件</span><span class="sxs-lookup"><span data-stu-id="b3fdd-110">Requirements</span></span>  

 <span data-ttu-id="b3fdd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3fdd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3fdd-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3fdd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3fdd-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3fdd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3fdd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3fdd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
