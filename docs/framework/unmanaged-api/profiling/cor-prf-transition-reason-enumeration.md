---
title: COR_PRF_TRANSITION_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 747313f217092652d5a9404fbf81383fa0828ee9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696662"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="a4980-102">COR_PRF_TRANSITION_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="a4980-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>

<span data-ttu-id="a4980-103">マネージド コードからアンマネージド コードへ、またはその逆の遷移の理由を示します。</span><span class="sxs-lookup"><span data-stu-id="a4980-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4980-104">構文</span><span class="sxs-lookup"><span data-stu-id="a4980-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="a4980-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a4980-105">Members</span></span>  
  
|<span data-ttu-id="a4980-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a4980-106">Member</span></span>|<span data-ttu-id="a4980-107">説明</span><span class="sxs-lookup"><span data-stu-id="a4980-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="a4980-108">遷移は、関数の呼び出しによるものです。</span><span class="sxs-lookup"><span data-stu-id="a4980-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="a4980-109">遷移は、関数からの戻り値によるものです。</span><span class="sxs-lookup"><span data-stu-id="a4980-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4980-110">注釈</span><span class="sxs-lookup"><span data-stu-id="a4980-110">Remarks</span></span>  

 <span data-ttu-id="a4980-111">遷移が発生すると、プロファイラーは [ICorProfilerCallback:: ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) または [ICorProfilerCallback:: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) コールバックを受け取ります。どちらのコールバックでも、 `COR_PRF_TRANSITION_REASON` 遷移の理由を示す列挙体の値が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a4980-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4980-112">要件</span><span class="sxs-lookup"><span data-stu-id="a4980-112">Requirements</span></span>  

 <span data-ttu-id="a4980-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4980-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4980-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4980-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4980-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4980-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4980-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4980-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
