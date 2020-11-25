---
title: ICorDebugStepper2::SetJMC メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: 1bbcbcfbb78d421f247a13f58070b68f701e4ed1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697208"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="105dd-102">ICorDebugStepper2::SetJMC メソッド</span><span class="sxs-lookup"><span data-stu-id="105dd-102">ICorDebugStepper2::SetJMC Method</span></span>

<span data-ttu-id="105dd-103">この ICorDebugStepper が、アプリケーションの開発者によって作成されたコードのみを使用するかどうかを指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="105dd-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="105dd-104">このプロセスは、"マイコードのみ" (JMC) デバッグとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="105dd-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105dd-105">構文</span><span class="sxs-lookup"><span data-stu-id="105dd-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="105dd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="105dd-106">Parameters</span></span>  

 `fIsJMCStepper`  
 <span data-ttu-id="105dd-107">から `true` アプリケーションの開発者によって作成されたコードのみをステップ実行するには、をに設定します。それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="105dd-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="105dd-108">要件</span><span class="sxs-lookup"><span data-stu-id="105dd-108">Requirements</span></span>  

 <span data-ttu-id="105dd-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="105dd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="105dd-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="105dd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="105dd-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="105dd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="105dd-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="105dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
