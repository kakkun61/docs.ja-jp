---
title: ICorDebugBreakpoint::Activate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
ms.openlocfilehash: 70a07f0ce7f1fa4c904fde594dcf82c5149616fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721531"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="7b680-102">ICorDebugBreakpoint::Activate メソッド</span><span class="sxs-lookup"><span data-stu-id="7b680-102">ICorDebugBreakpoint::Activate Method</span></span>

<span data-ttu-id="7b680-103">こののアクティブな状態を設定 `ICorDebugBreakpoint` します。</span><span class="sxs-lookup"><span data-stu-id="7b680-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b680-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b680-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b680-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b680-105">Parameters</span></span>  

 `bActive`  
 <span data-ttu-id="7b680-106">から状態をアクティブとして指定するには、この値をに設定します。 `true` それ以外の場合は、この値をに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="7b680-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b680-107">要件</span><span class="sxs-lookup"><span data-stu-id="7b680-107">Requirements</span></span>  

 <span data-ttu-id="7b680-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b680-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b680-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b680-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b680-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b680-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b680-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b680-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
