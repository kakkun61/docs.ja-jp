---
title: ICorProfilerInfo::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: 2e24d72c8be1ace10b2feb15101ed8f83db386c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724092"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="41116-102">ICorProfilerInfo::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="41116-102">ICorProfilerInfo::GetThreadContext Method</span></span>

<span data-ttu-id="41116-103">指定したスレッドに現在関連付けられているコンテキスト id を取得します。</span><span class="sxs-lookup"><span data-stu-id="41116-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41116-104">構文</span><span class="sxs-lookup"><span data-stu-id="41116-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41116-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41116-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="41116-106">からスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="41116-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="41116-107">入出力指定されたスレッドに現在関連付けられているコンテキスト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="41116-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="41116-108">スレッドに現在関連付けられているコンテキストがない場合、この関数は CORPROF_E_DATAINCOMPLETE を返します。</span><span class="sxs-lookup"><span data-stu-id="41116-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41116-109">要件</span><span class="sxs-lookup"><span data-stu-id="41116-109">Requirements</span></span>  

 <span data-ttu-id="41116-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41116-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41116-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41116-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41116-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41116-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41116-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41116-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41116-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="41116-114">See also</span></span>

- [<span data-ttu-id="41116-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41116-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
