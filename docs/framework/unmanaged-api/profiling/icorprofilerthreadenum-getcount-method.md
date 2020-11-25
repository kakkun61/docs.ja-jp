---
title: ICorProfilerThreadEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: a35f2e69515ea520396641effc05371b54ad8afc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702330"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="f991d-102">ICorProfilerThreadEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="f991d-102">ICorProfilerThreadEnum::GetCount Method</span></span>

<span data-ttu-id="f991d-103">アプリケーションで使用されるスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f991d-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f991d-104">構文</span><span class="sxs-lookup"><span data-stu-id="f991d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f991d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f991d-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f991d-106">入出力アプリケーションによって使用されるスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="f991d-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f991d-107">要件</span><span class="sxs-lookup"><span data-stu-id="f991d-107">Requirements</span></span>  

 <span data-ttu-id="f991d-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f991d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f991d-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f991d-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f991d-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f991d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f991d-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f991d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f991d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f991d-112">See also</span></span>

- [<span data-ttu-id="f991d-113">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f991d-113">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="f991d-114">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f991d-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
