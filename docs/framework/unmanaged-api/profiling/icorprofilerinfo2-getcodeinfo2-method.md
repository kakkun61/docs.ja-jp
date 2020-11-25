---
title: ICorProfilerInfo2::GetCodeInfo2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: e88fe1b3c93ca278d0e64a5eb3274c86bd8f0f6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727134"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="18063-102">ICorProfilerInfo2::GetCodeInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="18063-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>

<span data-ttu-id="18063-103">指定した `FunctionID` に関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="18063-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18063-104">構文</span><span class="sxs-lookup"><span data-stu-id="18063-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18063-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18063-105">Parameters</span></span>  

 `functionID`  
 <span data-ttu-id="18063-106">[in] ネイティブ コードが関連付けられている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="18063-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="18063-107">[in] `codeInfos` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="18063-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="18063-108">入出力使用可能な [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体の合計数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="18063-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="18063-109">[out] 呼び出し元が提供したバッファー。</span><span class="sxs-lookup"><span data-stu-id="18063-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="18063-110">メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="18063-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18063-111">注釈</span><span class="sxs-lookup"><span data-stu-id="18063-111">Remarks</span></span>  

 <span data-ttu-id="18063-112">エクステンとは Microsoft Intermediate Language (MSIL) オフセットの昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="18063-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="18063-113">`GetCodeInfo2` から制御が戻ったら、`codeInfos` バッファーのサイズが十分で、すべての `COR_PRF_CODE_INFO` 構造体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18063-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="18063-114">これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="18063-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="18063-115">`COR_PRF_CODE_INFO` 構造体のサイズによって除算された `cCodeInfos` が `pcCodeInfos` より小さい場合は、`codeInfos` バッファーの割り当てを増やし、`cCodeInfos` を新しい大きいサイズに更新した後、`GetCodeInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="18063-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="18063-116">別の方法として、最初に `GetCodeInfo2` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="18063-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="18063-117">その後、`codeInfos` バッファーのサイズを、`pcCodeInfos` で返された値に `COR_PRF_CODE_INFO` 構造体のサイズを掛けた値に設定し、`GetCodeInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="18063-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18063-118">要件</span><span class="sxs-lookup"><span data-stu-id="18063-118">Requirements</span></span>  

 <span data-ttu-id="18063-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18063-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18063-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="18063-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18063-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18063-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18063-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18063-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18063-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="18063-123">See also</span></span>

- [<span data-ttu-id="18063-124">GetCodeInfo3 メソッド</span><span class="sxs-lookup"><span data-stu-id="18063-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="18063-125">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18063-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="18063-126">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="18063-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="18063-127">プロファイル</span><span class="sxs-lookup"><span data-stu-id="18063-127">Profiling</span></span>](index.md)
