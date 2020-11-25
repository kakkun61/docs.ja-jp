---
title: ICorDebugStepper::SetInterceptMask メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 814bf87039ef57056f13994af1b873f8f57c7804
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718216"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="de6f3-102">ICorDebugStepper::SetInterceptMask メソッド</span><span class="sxs-lookup"><span data-stu-id="de6f3-102">ICorDebugStepper::SetInterceptMask Method</span></span>

<span data-ttu-id="de6f3-103">ステップインするコードの種類を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="de6f3-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6f3-104">構文</span><span class="sxs-lookup"><span data-stu-id="de6f3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de6f3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de6f3-105">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="de6f3-106">からコードの種類を指定する CorDebugIntercept 列挙子の値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="de6f3-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de6f3-107">注釈</span><span class="sxs-lookup"><span data-stu-id="de6f3-107">Remarks</span></span>  

 <span data-ttu-id="de6f3-108">インターセプターのビットが設定されている場合、指定された種類のインターセプトコードが検出されると、ステッパが完了します。</span><span class="sxs-lookup"><span data-stu-id="de6f3-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="de6f3-109">ビットがオフの場合、インターセプトコードはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="de6f3-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="de6f3-110">メソッドは、 `SetInterceptMask` [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (ユーザーの視点から見た) との予期しない相互作用を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="de6f3-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="de6f3-111">たとえば、クラス初期化コードの表示されている (つまり、内部ではない) 部分にマッピング情報がなく、STOP_NO_MAPPING_INFO が設定されていない場合 (「 [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) メソッドと CorDebugUnmappedStop 列挙を参照してください)、ステッパはクラスの初期化をステップオーバーします。</span><span class="sxs-lookup"><span data-stu-id="de6f3-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="de6f3-112">既定では、列挙体の INTERCEPT_NONE 値のみ `CorDebugIntercept` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="de6f3-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6f3-113">要件</span><span class="sxs-lookup"><span data-stu-id="de6f3-113">Requirements</span></span>  

 <span data-ttu-id="de6f3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de6f3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de6f3-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de6f3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de6f3-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de6f3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de6f3-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
