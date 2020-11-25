---
title: ICorDebugChain::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: a28da34cd3080826f346b8957aa6ba38258b924f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730124"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="3dcd8-102">ICorDebugChain::GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="3dcd8-102">ICorDebugChain::GetCallee Method</span></span>

<span data-ttu-id="3dcd8-103">このチェーンによって呼び出されたチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dcd8-104">構文</span><span class="sxs-lookup"><span data-stu-id="3dcd8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dcd8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3dcd8-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="3dcd8-106">入出力呼び出されたチェーンを表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="3dcd8-107">このチェーンが現在実行されている場合 (つまり、このチェーンが呼び出されたチェーンがを返すのを待機していない場合)、 `ppChain` は null になります。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dcd8-108">注釈</span><span class="sxs-lookup"><span data-stu-id="3dcd8-108">Remarks</span></span>  

 <span data-ttu-id="3dcd8-109">このチェーンは、呼び出されたチェーンが返されるのを待機してから、実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="3dcd8-110">スレッド間でマーシャリングされた呼び出しの場合、呼び出されたチェーンは別のスレッド上にある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dcd8-111">要件</span><span class="sxs-lookup"><span data-stu-id="3dcd8-111">Requirements</span></span>  

 <span data-ttu-id="3dcd8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dcd8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dcd8-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dcd8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dcd8-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dcd8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dcd8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dcd8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
