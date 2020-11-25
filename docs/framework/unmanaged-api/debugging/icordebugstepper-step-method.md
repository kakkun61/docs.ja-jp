---
title: ICorDebugStepper::Step メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: 234705e4495a1a582f3801ad1e645f923cd6f4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727693"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="d7402-102">ICorDebugStepper::Step メソッド</span><span class="sxs-lookup"><span data-stu-id="d7402-102">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="d7402-103">この ICorDebugStepper は、含まれるスレッドを1ステップずつ実行します。また、必要に応じて、スレッド内で呼び出される関数を使用したシングルステップ実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="d7402-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7402-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7402-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7402-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7402-105">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="d7402-106">から `true` スレッド内で呼び出される関数にステップインするには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="d7402-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="d7402-107">関数を `false` ステップオーバーするには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="d7402-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7402-108">注釈</span><span class="sxs-lookup"><span data-stu-id="d7402-108">Remarks</span></span>  

 <span data-ttu-id="d7402-109">共通言語ランタイムがこのステッパのフレームで次のマネージ命令を実行すると、手順が完了します。</span><span class="sxs-lookup"><span data-stu-id="d7402-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="d7402-110">`Step`マネージコードに含まれていないステッパでが呼び出された場合、次のマネージコード命令がスレッドによって実行されると、手順が完了します。</span><span class="sxs-lookup"><span data-stu-id="d7402-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7402-111">要件</span><span class="sxs-lookup"><span data-stu-id="d7402-111">Requirements</span></span>  

 <span data-ttu-id="d7402-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7402-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7402-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7402-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7402-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7402-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7402-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7402-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
