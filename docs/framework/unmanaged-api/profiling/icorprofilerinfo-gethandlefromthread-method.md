---
title: ICorProfilerInfo::GetHandleFromThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 94c2c6e01e4188f1fa13c3b6a9f638d4b79a502f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678183"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="ea30e-102">ICorProfilerInfo::GetHandleFromThread メソッド</span><span class="sxs-lookup"><span data-stu-id="ea30e-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="ea30e-103">スレッドの ID を Win32 スレッドハンドルにマップします。</span><span class="sxs-lookup"><span data-stu-id="ea30e-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea30e-104">構文</span><span class="sxs-lookup"><span data-stu-id="ea30e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea30e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea30e-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="ea30e-106">から割り当てられるスレッド ID。</span><span class="sxs-lookup"><span data-stu-id="ea30e-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="ea30e-107">入出力Win32 スレッドハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea30e-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea30e-108">解説</span><span class="sxs-lookup"><span data-stu-id="ea30e-108">Remarks</span></span>  

 <span data-ttu-id="ea30e-109">プロファイラーは、 `DuplicateHandle` 使用する前にハンドルで Win32 関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea30e-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="ea30e-110">このメソッドから返されたハンドルはランタイムによって所有されており、プロファイラーはそれを閉じることはできません。</span><span class="sxs-lookup"><span data-stu-id="ea30e-110">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ea30e-111">要件</span><span class="sxs-lookup"><span data-stu-id="ea30e-111">Requirements</span></span>  

 <span data-ttu-id="ea30e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea30e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea30e-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea30e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea30e-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea30e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea30e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea30e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea30e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea30e-116">See also</span></span>

- [<span data-ttu-id="ea30e-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea30e-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
