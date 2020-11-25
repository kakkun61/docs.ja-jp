---
title: ICorDebugStepper::StepOut メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 1396e7a8ca61734a9363a9c852502290675249d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727667"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="6ae18-102">ICorDebugStepper::StepOut メソッド</span><span class="sxs-lookup"><span data-stu-id="6ae18-102">ICorDebugStepper::StepOut Method</span></span>

<span data-ttu-id="6ae18-103">この ICorDebugStepper は、それを含むスレッドを1ステップずつ実行し、現在のフレームが呼び出し元のフレームに制御を返すときに完了します。</span><span class="sxs-lookup"><span data-stu-id="6ae18-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae18-104">構文</span><span class="sxs-lookup"><span data-stu-id="6ae18-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ae18-105">解説</span><span class="sxs-lookup"><span data-stu-id="6ae18-105">Remarks</span></span>  

 <span data-ttu-id="6ae18-106">操作は、 `StepOut` 通常は現在のフレームから呼び出し元のフレームに戻り、正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="6ae18-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="6ae18-107">`StepOut`アンマネージコードでが呼び出されたときにが呼び出された場合、現在のフレームがそれを呼び出したマネージコードに戻ると、手順が完了します。</span><span class="sxs-lookup"><span data-stu-id="6ae18-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="6ae18-108">.NET Framework バージョン2.0 では、 `StepOut` STOP_UNMANAGED フラグが設定されていないため、を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6ae18-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="6ae18-109">(ステップ実行のフラグを設定するには、 [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) を使用します。)相互運用デバッガーは、ネイティブコード自体にステップアウトする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae18-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ae18-110">要件</span><span class="sxs-lookup"><span data-stu-id="6ae18-110">Requirements</span></span>  

 <span data-ttu-id="6ae18-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ae18-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ae18-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ae18-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ae18-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ae18-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ae18-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae18-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
