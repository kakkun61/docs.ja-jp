---
title: ICorProfilerInfo3::EnumModules メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 698f6abc872a7e072ae47520386aa9c7ddfb44fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681471"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="420f0-102">ICorProfilerInfo3::EnumModules メソッド</span><span class="sxs-lookup"><span data-stu-id="420f0-102">ICorProfilerInfo3::EnumModules Method</span></span>

<span data-ttu-id="420f0-103">アプリケーションに読み込まれるマネージド モジュールのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="420f0-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="420f0-104">構文</span><span class="sxs-lookup"><span data-stu-id="420f0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="420f0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="420f0-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="420f0-106">入出力 [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="420f0-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="420f0-107">解説</span><span class="sxs-lookup"><span data-stu-id="420f0-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="420f0-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="420f0-108">Requirements</span></span>  

 <span data-ttu-id="420f0-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="420f0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="420f0-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="420f0-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="420f0-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="420f0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="420f0-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="420f0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420f0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="420f0-113">See also</span></span>

- [<span data-ttu-id="420f0-114">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="420f0-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="420f0-115">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="420f0-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="420f0-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="420f0-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="420f0-117">プロファイル</span><span class="sxs-lookup"><span data-stu-id="420f0-117">Profiling</span></span>](index.md)
