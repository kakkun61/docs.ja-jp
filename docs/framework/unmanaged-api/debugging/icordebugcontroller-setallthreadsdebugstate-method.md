---
title: ICorDebugController::SetAllThreadsDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: d8375948be5820aaf6e879b82bcfde6471cccf3f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679898"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="a9ec3-102">ICorDebugController::SetAllThreadsDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="a9ec3-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>

<span data-ttu-id="a9ec3-103">プロセス内のすべてのマネージスレッドのデバッグ状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9ec3-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9ec3-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9ec3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9ec3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9ec3-105">Parameters</span></span>  

 `state`  
 <span data-ttu-id="a9ec3-106">からデバッグ用のスレッドの状態を指定する "CorDebugThreadState" 列挙の値。</span><span class="sxs-lookup"><span data-stu-id="a9ec3-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="a9ec3-107">からデバッグ状態設定から除外されるスレッドを表す "のスレッド" オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a9ec3-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="a9ec3-108">この値が null の場合、スレッドは除外されません。</span><span class="sxs-lookup"><span data-stu-id="a9ec3-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9ec3-109">注釈</span><span class="sxs-lookup"><span data-stu-id="a9ec3-109">Remarks</span></span>  

 <span data-ttu-id="a9ec3-110">メソッドは、 `SetAllThreadsDebugState` [EnumerateThreads メソッド](icordebugcontroller-enumeratethreads-method.md)によって表示されないスレッドに影響を与える可能性があります。そのため、メソッドを使用して中断されたスレッド `SetAllThreadsDebugState` は、メソッドを使用して再開する必要があり `SetAllThreadsDebugState` ます。</span><span class="sxs-lookup"><span data-stu-id="a9ec3-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9ec3-111">要件</span><span class="sxs-lookup"><span data-stu-id="a9ec3-111">Requirements</span></span>  

 <span data-ttu-id="a9ec3-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9ec3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9ec3-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9ec3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9ec3-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9ec3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9ec3-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9ec3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ec3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9ec3-116">See also</span></span>
