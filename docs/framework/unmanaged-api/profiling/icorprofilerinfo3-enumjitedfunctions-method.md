---
title: ICorProfilerInfo3::EnumJITedFunctions メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: 6227baaead518eae2de5913369b72de1072ac052
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681497"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="a358b-102">ICorProfilerInfo3::EnumJITedFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="a358b-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>

<span data-ttu-id="a358b-103">以前に JIT でコンパイルされたすべての関数の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="a358b-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a358b-104">構文</span><span class="sxs-lookup"><span data-stu-id="a358b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a358b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a358b-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="a358b-106">入出力 [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) 列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a358b-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a358b-107">注釈</span><span class="sxs-lookup"><span data-stu-id="a358b-107">Remarks</span></span>  

 <span data-ttu-id="a358b-108">このメソッドは `JITCompilation` 、 [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) メソッドなどのコールバックと重複する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a358b-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="a358b-109">このメソッドによって返される列挙子には、Ngen.exe で生成されたネイティブイメージから読み込まれた関数は含まれません。</span><span class="sxs-lookup"><span data-stu-id="a358b-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a358b-110">返された列挙体には、フィールドの値に対して "0" のみが含まれ `COR_PRF_FUNCTION::reJitId` ます。</span><span class="sxs-lookup"><span data-stu-id="a358b-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="a358b-111">有効な値が必要な場合は `COR_PRF_FUNCTION::reJitId` 、 [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a358b-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a358b-112">要件</span><span class="sxs-lookup"><span data-stu-id="a358b-112">Requirements</span></span>  

 <span data-ttu-id="a358b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a358b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a358b-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a358b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a358b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a358b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a358b-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a358b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a358b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a358b-117">See also</span></span>

- [<span data-ttu-id="a358b-118">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a358b-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a358b-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a358b-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a358b-120">プロファイル</span><span class="sxs-lookup"><span data-stu-id="a358b-120">Profiling</span></span>](index.md)
