---
title: ICorProfilerInfo::GetThreadInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 516a12b7a4457a0f67da24294ad96fb79d1aa5aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707517"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="a5da8-102">ICorProfilerInfo::GetThreadInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="a5da8-102">ICorProfilerInfo::GetThreadInfo Method</span></span>

<span data-ttu-id="a5da8-103">指定したスレッドの現在の Win32 スレッド id を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5da8-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5da8-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5da8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5da8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5da8-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="a5da8-106">から現在の Win32 ID を取得するスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="a5da8-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="a5da8-107">入出力指定したスレッドの現在の Win32 スレッド ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5da8-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5da8-108">要件</span><span class="sxs-lookup"><span data-stu-id="a5da8-108">Requirements</span></span>  

 <span data-ttu-id="a5da8-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5da8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5da8-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5da8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5da8-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5da8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5da8-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5da8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5da8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5da8-113">See also</span></span>

- [<span data-ttu-id="a5da8-114">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5da8-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
