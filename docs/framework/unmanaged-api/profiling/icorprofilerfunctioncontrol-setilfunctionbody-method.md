---
title: ICorProfilerFunctionControl::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: fa82cd1e646777c9841c1b3d653134aa7ba7ed7c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712743"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="5ded6-102">ICorProfilerFunctionControl::SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="5ded6-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>

<span data-ttu-id="5ded6-103">メソッドの中間共通言語 (CIL) 本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="5ded6-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ded6-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ded6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ded6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ded6-105">Parameters</span></span>  

 `cbNewILMethodHeader`  
 <span data-ttu-id="5ded6-106">[入力] ヘッダー、および本体の後に続く構造を含む、新しい CIL の合計サイズ。</span><span class="sxs-lookup"><span data-stu-id="5ded6-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="5ded6-107">[入力] 新しい CIL ヘッダーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5ded6-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ded6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5ded6-108">Return Value</span></span>  

 <span data-ttu-id="5ded6-109">このメソッドは、次の特定の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="5ded6-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="5ded6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ded6-110">HRESULT</span></span>|<span data-ttu-id="5ded6-111">説明</span><span class="sxs-lookup"><span data-stu-id="5ded6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ded6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ded6-112">S_OK</span></span>|<span data-ttu-id="5ded6-113">置換が成功しました。</span><span class="sxs-lookup"><span data-stu-id="5ded6-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ded6-114">注釈</span><span class="sxs-lookup"><span data-stu-id="5ded6-114">Remarks</span></span>  

 <span data-ttu-id="5ded6-115">[ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)メソッドとは異なり、 `SetILFunctionBody` メソッドは新しい CIL 本体に必要なメモリを管理します。</span><span class="sxs-lookup"><span data-stu-id="5ded6-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="5ded6-116">これは、プロファイラーによって提供される CIL 本体を [Imethodmalloc](imethodmalloc-interface.md) インターフェイスを使用して割り当てたり、特定の範囲内で割り当てたりする必要がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="5ded6-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="5ded6-117">この本体は、どのヒープにも割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5ded6-117">It can be allocated on any heap.</span></span> <span data-ttu-id="5ded6-118">プロファイラーは、が返された後に、その CIL 本体に使用されるメモリを解放でき `SetILFunctionBody` ます。</span><span class="sxs-lookup"><span data-stu-id="5ded6-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ded6-119">要件</span><span class="sxs-lookup"><span data-stu-id="5ded6-119">Requirements</span></span>  

 <span data-ttu-id="5ded6-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ded6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ded6-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ded6-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ded6-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ded6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ded6-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ded6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ded6-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ded6-124">See also</span></span>

- [<span data-ttu-id="5ded6-125">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ded6-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
