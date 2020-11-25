---
title: ICorProfilerCallback2::ThreadNameChanged メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 8398febd17c7e77f2ad281ebeafc138fca4a47d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718034"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="eaf4d-102">ICorProfilerCallback2::ThreadNameChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="eaf4d-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>

<span data-ttu-id="eaf4d-103">スレッドの名前が変更されたことをコードプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="eaf4d-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="eaf4d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaf4d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eaf4d-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="eaf4d-106">からスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="eaf4d-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="eaf4d-107">からスレッドの新しい名前の長さ。</span><span class="sxs-lookup"><span data-stu-id="eaf4d-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="eaf4d-108">からスレッドの新しい名前。</span><span class="sxs-lookup"><span data-stu-id="eaf4d-108">[in] The new name of the thread.</span></span> <span data-ttu-id="eaf4d-109">名前が null で終了していません。</span><span class="sxs-lookup"><span data-stu-id="eaf4d-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf4d-110">要件</span><span class="sxs-lookup"><span data-stu-id="eaf4d-110">Requirements</span></span>  

 <span data-ttu-id="eaf4d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaf4d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf4d-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eaf4d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eaf4d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaf4d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaf4d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf4d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf4d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="eaf4d-115">See also</span></span>

- [<span data-ttu-id="eaf4d-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eaf4d-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="eaf4d-117">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eaf4d-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
