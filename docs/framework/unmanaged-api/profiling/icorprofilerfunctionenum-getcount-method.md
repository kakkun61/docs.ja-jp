---
title: ICorProfilerFunctionEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: 3ccf75523eb9362b8ef5c38d224a419502cb8b92
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724147"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="b32cd-102">ICorProfilerFunctionEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="b32cd-102">ICorProfilerFunctionEnum::GetCount Method</span></span>

<span data-ttu-id="b32cd-103">アプリケーションによって読み込まれたか、またはプロファイラーによって強制的に読み込まれた関数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="b32cd-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b32cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="b32cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b32cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b32cd-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="b32cd-106">入出力読み込まれた関数の数。</span><span class="sxs-lookup"><span data-stu-id="b32cd-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b32cd-107">要件</span><span class="sxs-lookup"><span data-stu-id="b32cd-107">Requirements</span></span>  

 <span data-ttu-id="b32cd-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b32cd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b32cd-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b32cd-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b32cd-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b32cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b32cd-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b32cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b32cd-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b32cd-112">See also</span></span>

- [<span data-ttu-id="b32cd-113">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b32cd-113">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="b32cd-114">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b32cd-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
