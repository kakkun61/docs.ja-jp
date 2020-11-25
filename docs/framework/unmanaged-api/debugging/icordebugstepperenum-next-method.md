---
title: ICorDebugStepperEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: b8156b858bde550bb66a8f4ac254f850058ea1a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697195"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="4a1e3-102">ICorDebugStepperEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="4a1e3-102">ICorDebugStepperEnum::Next Method</span></span>

<span data-ttu-id="4a1e3-103">現在の位置から開始して、指定した数の ICorDebugStepper インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="4a1e3-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a1e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="4a1e3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a1e3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4a1e3-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="4a1e3-106">から `ICorDebugStepper` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="4a1e3-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="4a1e3-107">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugStepper` ます。</span><span class="sxs-lookup"><span data-stu-id="4a1e3-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4a1e3-108">入出力実際に返されたインスタンスの数へのポインター `ICorDebugStepper` 。</span><span class="sxs-lookup"><span data-stu-id="4a1e3-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="4a1e3-109">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="4a1e3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a1e3-110">要件</span><span class="sxs-lookup"><span data-stu-id="4a1e3-110">Requirements</span></span>  

 <span data-ttu-id="4a1e3-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a1e3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a1e3-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a1e3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a1e3-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a1e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a1e3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a1e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
