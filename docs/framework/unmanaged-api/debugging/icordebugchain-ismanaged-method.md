---
title: ICorDebugChain::IsManaged メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: cfe884c3d26e7a52618eb9945f0af9a167132f05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724378"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="31946-102">ICorDebugChain::IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="31946-102">ICorDebugChain::IsManaged Method</span></span>

<span data-ttu-id="31946-103">このチェーンでマネージコードが実行されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="31946-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31946-104">構文</span><span class="sxs-lookup"><span data-stu-id="31946-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31946-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31946-105">Parameters</span></span>  

 `pManaged`  
 <span data-ttu-id="31946-106">[出力] `true` このチェーンでマネージコードが実行されている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="31946-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31946-107">要件</span><span class="sxs-lookup"><span data-stu-id="31946-107">Requirements</span></span>  

 <span data-ttu-id="31946-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31946-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31946-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31946-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31946-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31946-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31946-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31946-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
