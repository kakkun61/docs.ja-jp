---
title: ICorProfilerInfo2::GetClassIDInfo2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 4b018a329396e0be684c999a33d4ef7c3518cb1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703906"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="0e046-102">ICorProfilerInfo2::GetClassIDInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0e046-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>

<span data-ttu-id="0e046-103">指定されたクラスのオープンジェネリック定義、 `ClassID` その親クラスの、および `ClassID` 各型引数 (存在する場合) のがクラスの親モジュールとメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0e046-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e046-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e046-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e046-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e046-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="0e046-106">[in] 情報が取得されるクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="0e046-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="0e046-107">入出力指定したクラスのオープンジェネリック定義の親モジュールの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0e046-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="0e046-108">入出力指定したクラスのオープンジェネリック定義のメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0e046-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="0e046-109">[out] 親クラスの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0e046-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="0e046-110">[in] `typeArgs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="0e046-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="0e046-111">[out] 使用できる要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0e046-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="0e046-112">[out] `ClassID` 値の配列。各値は、クラスの型引数の ID を表します。</span><span class="sxs-lookup"><span data-stu-id="0e046-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="0e046-113">このメソッドが戻るとき、使用できる `ClassID` 値の一部またはすべてが `typeArgs` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0e046-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e046-114">注釈</span><span class="sxs-lookup"><span data-stu-id="0e046-114">Remarks</span></span>  

 <span data-ttu-id="0e046-115">`GetClassIDInfo2`メソッドは[ICorProfilerInfo:: Getclassid dinfo](icorprofilerinfo-getclassidinfo-method.md)メソッドに似ていますが、 `GetClassIDInfo2` ジェネリック型に関する追加情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0e046-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="0e046-116">プロファイラーコードは、 [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) を呼び出して、指定されたモジュールの [メタデータ](../metadata/index.md) インターフェイスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="0e046-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="0e046-117">`pTypeDefToken` によって参照される場所に返されるメタデータ トークンを使用すると、クラスのメタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0e046-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="0e046-118">`GetClassIDInfo2` から制御が戻ったら、`typeArgs` バッファーのサイズが十分で、すべての `ClassID` 値を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e046-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="0e046-119">これを行うには、`pcNumTypeArgs` が指している値を `cNumTypeArgs` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="0e046-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="0e046-120">`pcNumTypeArgs` が指している値が `cNumTypeArgs` の値より大きい場合は、`typeArgs` バッファーの割り当てを増やし、`cNumTypeArgs` を新しい大きいサイズに更新して、`GetClassIDInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0e046-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="0e046-121">別の方法として、最初に `GetClassIDInfo2` を長さゼロの `typeArgs` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="0e046-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0e046-122">その後、`typeArgs` バッファーのサイズを `pcNumTypeArgs` に返された値に設定し、`GetClassIDInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0e046-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e046-123">要件</span><span class="sxs-lookup"><span data-stu-id="0e046-123">Requirements</span></span>  

 <span data-ttu-id="0e046-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e046-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e046-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0e046-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e046-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e046-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e046-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e046-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e046-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e046-128">See also</span></span>

- [<span data-ttu-id="0e046-129">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e046-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0e046-130">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e046-130">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="0e046-131">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e046-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0e046-132">プロファイル</span><span class="sxs-lookup"><span data-stu-id="0e046-132">Profiling</span></span>](index.md)
