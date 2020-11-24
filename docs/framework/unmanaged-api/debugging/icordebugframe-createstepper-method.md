---
title: ICorDebugFrame::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 5dfb64d0c440cbd2c8a8a65b2c18d78f02a7615e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679716"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="4abde-102">ICorDebugFrame::CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="4abde-102">ICorDebugFrame::CreateStepper Method</span></span>

<span data-ttu-id="4abde-103">デバッガーがこのテキストフレームに対して相対的なステップ実行操作を実行できるようにするステッパを取得します。</span><span class="sxs-lookup"><span data-stu-id="4abde-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4abde-104">構文</span><span class="sxs-lookup"><span data-stu-id="4abde-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4abde-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4abde-105">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="4abde-106">入出力デバッガーが現在のフレームに対して相対的なステップ実行操作を実行できるようにする ICorDebugStepper オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4abde-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4abde-107">注釈</span><span class="sxs-lookup"><span data-stu-id="4abde-107">Remarks</span></span>  

 <span data-ttu-id="4abde-108">フレームがアクティブでない場合、通常、ステッパオブジェクトは、手順が完了する前にフレームに戻る必要があります。</span><span class="sxs-lookup"><span data-stu-id="4abde-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4abde-109">要件</span><span class="sxs-lookup"><span data-stu-id="4abde-109">Requirements</span></span>  

 <span data-ttu-id="4abde-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4abde-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4abde-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4abde-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4abde-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4abde-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4abde-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4abde-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
