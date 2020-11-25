---
title: ICorProfilerThreadEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 12b7b53c408388c21d7508f6591ead5ccf55936b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721180"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="dada7-102">ICorProfilerThreadEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="dada7-102">ICorProfilerThreadEnum::Skip Method</span></span>

<span data-ttu-id="dada7-103">指定した数の要素をスキップするため、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="dada7-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dada7-104">構文</span><span class="sxs-lookup"><span data-stu-id="dada7-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dada7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dada7-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="dada7-106">からスキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="dada7-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dada7-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="dada7-107">Return Value</span></span>  

 <span data-ttu-id="dada7-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="dada7-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dada7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dada7-109">HRESULT</span></span>|<span data-ttu-id="dada7-110">説明</span><span class="sxs-lookup"><span data-stu-id="dada7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dada7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dada7-111">S_OK</span></span>|<span data-ttu-id="dada7-112">`celt` 要素はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="dada7-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="dada7-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dada7-113">S_FALSE</span></span>|<span data-ttu-id="dada7-114">より小さい `celt` 要素がスキップされました。これは、要素がこれ以上存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="dada7-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dada7-115">注釈</span><span class="sxs-lookup"><span data-stu-id="dada7-115">Remarks</span></span>  

 <span data-ttu-id="dada7-116">この列挙子のカーソルの新しい位置は、(現在位置) + `celt` です。</span><span class="sxs-lookup"><span data-stu-id="dada7-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dada7-117">要件</span><span class="sxs-lookup"><span data-stu-id="dada7-117">Requirements</span></span>  

 <span data-ttu-id="dada7-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dada7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dada7-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dada7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dada7-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dada7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dada7-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dada7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dada7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="dada7-122">See also</span></span>

- [<span data-ttu-id="dada7-123">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dada7-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="dada7-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dada7-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
