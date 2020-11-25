---
title: ICorProfilerThreadEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
ms.openlocfilehash: dc8e85c5a6047ad5dd99520b57789605333d5bf2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721206"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="342fe-102">ICorProfilerThreadEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="342fe-102">ICorProfilerThreadEnum::Next Method</span></span>

<span data-ttu-id="342fe-103">スレッドのシーケンシャル コレクションから、列挙子の現在の位置以降にある指定した数の隣接するスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="342fe-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="342fe-104">構文</span><span class="sxs-lookup"><span data-stu-id="342fe-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="342fe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="342fe-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="342fe-106">[in] 取得するスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="342fe-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="342fe-107">[out] `ThreadID` 値の配列。それぞれの値は、取得されたスレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="342fe-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="342fe-108">[out] `ids` 配列で実際に返されるスレッドの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="342fe-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="342fe-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="342fe-109">Return Value</span></span>  

 <span data-ttu-id="342fe-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="342fe-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="342fe-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="342fe-111">HRESULT</span></span>|<span data-ttu-id="342fe-112">説明</span><span class="sxs-lookup"><span data-stu-id="342fe-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="342fe-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="342fe-113">S_OK</span></span>|<span data-ttu-id="342fe-114">`celt` 要素が返されました。</span><span class="sxs-lookup"><span data-stu-id="342fe-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="342fe-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="342fe-115">S_FALSE</span></span>|<span data-ttu-id="342fe-116">`celt` よりも少ない数の要素が返されました。これは、列挙が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="342fe-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="342fe-117">要件</span><span class="sxs-lookup"><span data-stu-id="342fe-117">Requirements</span></span>  

 <span data-ttu-id="342fe-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="342fe-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="342fe-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="342fe-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="342fe-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="342fe-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="342fe-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="342fe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="342fe-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="342fe-122">See also</span></span>

- [<span data-ttu-id="342fe-123">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="342fe-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="342fe-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="342fe-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
