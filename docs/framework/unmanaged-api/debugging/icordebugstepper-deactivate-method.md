---
title: ICorDebugStepper::Deactivate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 0d7d5e7e6c9bc1a68feda85c5214f3ae95df9b97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730592"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="4388d-102">ICorDebugStepper::Deactivate メソッド</span><span class="sxs-lookup"><span data-stu-id="4388d-102">ICorDebugStepper::Deactivate Method</span></span>

<span data-ttu-id="4388d-103">この ICorDebugStepper は、受け取った最後のステップコマンドをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="4388d-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4388d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4388d-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4388d-105">解説</span><span class="sxs-lookup"><span data-stu-id="4388d-105">Remarks</span></span>  

 <span data-ttu-id="4388d-106">最後に受信したステップコマンドが取り消された後に、新しいステップ実行コマンドが発行される場合があります。</span><span class="sxs-lookup"><span data-stu-id="4388d-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4388d-107">要件</span><span class="sxs-lookup"><span data-stu-id="4388d-107">Requirements</span></span>  

 <span data-ttu-id="4388d-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4388d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4388d-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4388d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4388d-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4388d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4388d-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4388d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
