---
title: ICorProfilerCallback::AssemblyUnloadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 3f2b4a64b3f17b043f193e054c56601d706a10e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700380"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="a50bd-102">ICorProfilerCallback::AssemblyUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="a50bd-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>

<span data-ttu-id="a50bd-103">アセンブリがアンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a50bd-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a50bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="a50bd-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a50bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a50bd-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="a50bd-106">\[in] は、アンロードされるアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="a50bd-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="a50bd-107">\[in] アセンブリが正常にアンロードされたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="a50bd-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="a50bd-108">注釈</span><span class="sxs-lookup"><span data-stu-id="a50bd-108">Remarks</span></span>  

 <span data-ttu-id="a50bd-109">`assemblyId` [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md)メソッドがを返すと、の値は情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="a50bd-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="a50bd-110">アセンブリのアンロードの一部は、コールバック後に続行される場合があり `AssemblyUnloadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="a50bd-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="a50bd-111">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="a50bd-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="a50bd-112">ただし、の成功 HRESULT は、 `hrStatus` アセンブリのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a50bd-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a50bd-113">要件</span><span class="sxs-lookup"><span data-stu-id="a50bd-113">Requirements</span></span>  

 <span data-ttu-id="a50bd-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a50bd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a50bd-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a50bd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a50bd-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a50bd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a50bd-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a50bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a50bd-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a50bd-118">See also</span></span>

- [<span data-ttu-id="a50bd-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a50bd-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
