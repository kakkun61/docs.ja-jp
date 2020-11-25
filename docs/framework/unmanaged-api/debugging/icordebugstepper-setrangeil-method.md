---
title: ICorDebugStepper::SetRangeIL メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 5a27f155021661022b27022bbb252e00dfa67255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698781"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="230ac-102">ICorDebugStepper::SetRangeIL メソッド</span><span class="sxs-lookup"><span data-stu-id="230ac-102">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="230ac-103">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md)の呼び出しで、ネイティブコードに対して相対的な引数値を渡すか、またはステップスルー中のメソッドの MSIL (Microsoft 中間言語) コードに対する相対パスを指定するかを指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="230ac-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230ac-104">構文</span><span class="sxs-lookup"><span data-stu-id="230ac-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="230ac-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="230ac-105">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="230ac-106">から `true` 範囲が MSIL コードに対して相対的であることを指定するには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="230ac-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="230ac-107">`false`範囲がネイティブコードに対して相対的であることを指定するには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="230ac-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="230ac-108">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="230ac-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="230ac-109">要件</span><span class="sxs-lookup"><span data-stu-id="230ac-109">Requirements</span></span>  

 <span data-ttu-id="230ac-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="230ac-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="230ac-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="230ac-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="230ac-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="230ac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="230ac-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="230ac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
