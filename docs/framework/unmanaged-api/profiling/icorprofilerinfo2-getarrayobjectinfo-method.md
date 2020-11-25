---
title: ICorProfilerInfo2::GetArrayObjectInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: a1e321e141059ccf1da7292d28e7099418a5134e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727199"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="67671-102">ICorProfilerInfo2::GetArrayObjectInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="67671-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>

<span data-ttu-id="67671-103">配列オブジェクトに関する詳細情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="67671-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67671-104">構文</span><span class="sxs-lookup"><span data-stu-id="67671-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67671-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67671-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="67671-106">から有効な配列オブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="67671-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="67671-107">から配列のランク (次元数)。</span><span class="sxs-lookup"><span data-stu-id="67671-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="67671-108">入出力それぞれが配列の次元のサイズを表す整数を格納している配列。</span><span class="sxs-lookup"><span data-stu-id="67671-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="67671-109">入出力それぞれが配列の次元の下限を表す整数を格納している配列。</span><span class="sxs-lookup"><span data-stu-id="67671-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="67671-110">入出力配列の生バッファーのアドレスへのポインター。これは、C++ 規則に従ってレイアウトされます。</span><span class="sxs-lookup"><span data-stu-id="67671-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67671-111">注釈</span><span class="sxs-lookup"><span data-stu-id="67671-111">Remarks</span></span>  

 <span data-ttu-id="67671-112">`pDimensionSizes`とは `pDimensionLowerBounds` 並列配列であるため、各配列内の同じインデックスにある要素は同じエンティティの特性です。</span><span class="sxs-lookup"><span data-stu-id="67671-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67671-113">要件</span><span class="sxs-lookup"><span data-stu-id="67671-113">Requirements</span></span>  

 <span data-ttu-id="67671-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67671-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67671-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67671-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67671-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67671-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67671-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67671-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67671-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="67671-118">See also</span></span>

- [<span data-ttu-id="67671-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67671-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="67671-120">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67671-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
