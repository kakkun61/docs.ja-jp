---
title: ICorDebugController::IsRunning メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
ms.openlocfilehash: 73ed86ee12b02d292dc6dfc1d652459a679f81ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679937"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="a7037-102">ICorDebugController::IsRunning メソッド</span><span class="sxs-lookup"><span data-stu-id="a7037-102">ICorDebugController::IsRunning Method</span></span>

<span data-ttu-id="a7037-103">プロセス内のスレッドが現在実行中であるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a7037-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7037-104">構文</span><span class="sxs-lookup"><span data-stu-id="a7037-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7037-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a7037-105">Parameters</span></span>  

 `pbRunning`  
 <span data-ttu-id="a7037-106">入出力プロセス内のスレッドが自由に実行されている場合は、値へのポインター `true` 。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="a7037-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7037-107">要件</span><span class="sxs-lookup"><span data-stu-id="a7037-107">Requirements</span></span>  

 <span data-ttu-id="a7037-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7037-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7037-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7037-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7037-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7037-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7037-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7037-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7037-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7037-112">See also</span></span>
