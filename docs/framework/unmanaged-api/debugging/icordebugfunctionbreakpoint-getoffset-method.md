---
title: ICorDebugFunctionBreakpoint::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
ms.openlocfilehash: 8b9e483e24068656ddda0a3ecfee5934a2df962d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695895"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="78fd0-102">ICorDebugFunctionBreakpoint::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="78fd0-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>

<span data-ttu-id="78fd0-103">関数内のブレークポイントのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="78fd0-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fd0-104">構文</span><span class="sxs-lookup"><span data-stu-id="78fd0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78fd0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78fd0-105">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="78fd0-106">入出力ブレークポイントのオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="78fd0-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78fd0-107">要件</span><span class="sxs-lookup"><span data-stu-id="78fd0-107">Requirements</span></span>  

 <span data-ttu-id="78fd0-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fd0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78fd0-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78fd0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78fd0-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78fd0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78fd0-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78fd0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
