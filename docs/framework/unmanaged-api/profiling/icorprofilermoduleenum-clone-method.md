---
title: ICorProfilerModuleEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: ae9f6b7865a80e3edc4cae8fd1298e5eed864377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722831"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="fa0ea-102">ICorProfilerModuleEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="fa0ea-102">ICorProfilerModuleEnum::Clone Method</span></span>

<span data-ttu-id="fa0ea-103">この [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="fa0ea-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa0ea-104">構文</span><span class="sxs-lookup"><span data-stu-id="fa0ea-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa0ea-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fa0ea-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="fa0ea-106">入出力次に、この [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) インターフェイスのコピーを指すインターフェイスポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fa0ea-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="fa0ea-107">列挙子のコピーは、この列挙子とは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="fa0ea-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="fa0ea-108">ただし、コピーの初期カーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="fa0ea-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa0ea-109">要件</span><span class="sxs-lookup"><span data-stu-id="fa0ea-109">Requirements</span></span>  

 <span data-ttu-id="fa0ea-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa0ea-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa0ea-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa0ea-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa0ea-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa0ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa0ea-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa0ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa0ea-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa0ea-114">See also</span></span>

- [<span data-ttu-id="fa0ea-115">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa0ea-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="fa0ea-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa0ea-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
