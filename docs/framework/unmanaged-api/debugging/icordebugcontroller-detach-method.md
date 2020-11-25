---
title: ICorDebugController::Detach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 55acb6e3ec60925cba3d8aa5328547c54f270356
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732672"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="de0b7-102">ICorDebugController::Detach メソッド</span><span class="sxs-lookup"><span data-stu-id="de0b7-102">ICorDebugController::Detach Method</span></span>

<span data-ttu-id="de0b7-103">プロセスまたはアプリケーションドメインからデバッガーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="de0b7-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de0b7-104">構文</span><span class="sxs-lookup"><span data-stu-id="de0b7-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="de0b7-105">解説</span><span class="sxs-lookup"><span data-stu-id="de0b7-105">Remarks</span></span>  

 <span data-ttu-id="de0b7-106">プロセスまたはアプリケーションドメインは通常どおり実行されますが、"" のプロセス "オブジェクトまたは" 表示されない Appdomain "オブジェクトは無効になり、それ以上のコールバックは発生しません。</span><span class="sxs-lookup"><span data-stu-id="de0b7-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="de0b7-107">.NET Framework バージョン2.0 では、アンマネージデバッグが有効になっている場合、オペレーティングシステムの制限により、このメソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="de0b7-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de0b7-108">要件</span><span class="sxs-lookup"><span data-stu-id="de0b7-108">Requirements</span></span>  

 <span data-ttu-id="de0b7-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de0b7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de0b7-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de0b7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de0b7-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de0b7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de0b7-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de0b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de0b7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="de0b7-113">See also</span></span>
