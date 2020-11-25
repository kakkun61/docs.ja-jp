---
title: ICorProfilerModuleEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: 53009a1805056b83047299ebdca8f21d98ad5137
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732984"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="8fd62-102">ICorProfilerModuleEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="8fd62-102">ICorProfilerModuleEnum::GetCount Method</span></span>

<span data-ttu-id="8fd62-103">アプリケーションによって読み込まれたマネージド モジュールの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="8fd62-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fd62-104">構文</span><span class="sxs-lookup"><span data-stu-id="8fd62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fd62-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8fd62-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="8fd62-106">入出力コレクション内のランタイムモジュールの数。</span><span class="sxs-lookup"><span data-stu-id="8fd62-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fd62-107">要件</span><span class="sxs-lookup"><span data-stu-id="8fd62-107">Requirements</span></span>  

 <span data-ttu-id="8fd62-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fd62-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fd62-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8fd62-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fd62-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fd62-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fd62-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fd62-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd62-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fd62-112">See also</span></span>

- [<span data-ttu-id="8fd62-113">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fd62-113">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="8fd62-114">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fd62-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
