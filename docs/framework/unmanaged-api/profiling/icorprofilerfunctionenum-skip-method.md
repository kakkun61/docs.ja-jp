---
title: ICorProfilerFunctionEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: da578e02db0744b1f64c1d392844aa020721e784
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669259"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="2f86d-102">ICorProfilerFunctionEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="2f86d-102">ICorProfilerFunctionEnum::Skip Method</span></span>

<span data-ttu-id="2f86d-103">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="2f86d-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f86d-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f86d-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f86d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f86d-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="2f86d-106">からスキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="2f86d-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f86d-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="2f86d-107">Return Value</span></span>  

 <span data-ttu-id="2f86d-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="2f86d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2f86d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f86d-109">HRESULT</span></span>|<span data-ttu-id="2f86d-110">説明</span><span class="sxs-lookup"><span data-stu-id="2f86d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f86d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f86d-111">S_OK</span></span>|<span data-ttu-id="2f86d-112">`celt` 要素はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="2f86d-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="2f86d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2f86d-113">S_FALSE</span></span>|<span data-ttu-id="2f86d-114">より小さい `celt` 要素がスキップされました。これは、要素がこれ以上存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="2f86d-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f86d-115">注釈</span><span class="sxs-lookup"><span data-stu-id="2f86d-115">Remarks</span></span>  

 <span data-ttu-id="2f86d-116">この列挙子のカーソルの新しい位置は、(現在位置) + `celt` です。</span><span class="sxs-lookup"><span data-stu-id="2f86d-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f86d-117">要件</span><span class="sxs-lookup"><span data-stu-id="2f86d-117">Requirements</span></span>  

 <span data-ttu-id="2f86d-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f86d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f86d-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f86d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f86d-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f86d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f86d-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f86d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f86d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f86d-122">See also</span></span>

- [<span data-ttu-id="2f86d-123">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f86d-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="2f86d-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f86d-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
