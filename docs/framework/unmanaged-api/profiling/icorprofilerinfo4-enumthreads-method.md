---
title: ICorProfilerInfo4::EnumThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: df0e66c8563404d7de4f1e11f41483f2f61f519c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721557"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="7319a-102">ICorProfilerInfo4::EnumThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="7319a-102">ICorProfilerInfo4::EnumThreads Method</span></span>

<span data-ttu-id="7319a-103">プロファイリングされたプロセス内のすべてのマネージスレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="7319a-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7319a-104">構文</span><span class="sxs-lookup"><span data-stu-id="7319a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7319a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7319a-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="7319a-106">入出力 [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7319a-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7319a-107">解説</span><span class="sxs-lookup"><span data-stu-id="7319a-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7319a-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="7319a-108">Requirements</span></span>  

 <span data-ttu-id="7319a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7319a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7319a-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7319a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7319a-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7319a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7319a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7319a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7319a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7319a-113">See also</span></span>

- [<span data-ttu-id="7319a-114">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7319a-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="7319a-115">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7319a-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="7319a-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7319a-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7319a-117">プロファイル</span><span class="sxs-lookup"><span data-stu-id="7319a-117">Profiling</span></span>](index.md)
