---
title: ICorProfilerInfo::GetFunctionFromIP メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
ms.openlocfilehash: 4a7e21ae60253c741b57674212e0ecabdd844d2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722561"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="3df73-102">ICorProfilerInfo::GetFunctionFromIP メソッド</span><span class="sxs-lookup"><span data-stu-id="3df73-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>

<span data-ttu-id="3df73-103">マネージコード命令ポインターをにマップ `FunctionID` します。</span><span class="sxs-lookup"><span data-stu-id="3df73-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df73-104">構文</span><span class="sxs-lookup"><span data-stu-id="3df73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3df73-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3df73-105">Parameters</span></span>

- `ip`

  <span data-ttu-id="3df73-106">\[in) マネージコード内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="3df73-106">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="3df73-107">\[out] 返された関数 ID。</span><span class="sxs-lookup"><span data-stu-id="3df73-107">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="3df73-108">要件</span><span class="sxs-lookup"><span data-stu-id="3df73-108">Requirements</span></span>  

 <span data-ttu-id="3df73-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df73-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df73-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3df73-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3df73-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3df73-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3df73-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df73-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df73-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3df73-113">See also</span></span>

- [<span data-ttu-id="3df73-114">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3df73-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
