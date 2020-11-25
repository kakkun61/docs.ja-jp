---
title: ICorDebugChain::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
ms.openlocfilehash: a3f02af1a0de9fcd7b3db1e49ef0d78af3395d2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719659"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="9ee21-102">ICorDebugChain::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="9ee21-102">ICorDebugChain::GetRegisterSet Method</span></span>

<span data-ttu-id="9ee21-103">このチェーンのアクティブな部分のレジスタセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="9ee21-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee21-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ee21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ee21-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ee21-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="9ee21-106">入出力このチェーンのアクティブな部分のレジスタセットを表す、 [のオブジェクトの](icordebugregisterset-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ee21-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ee21-107">要件</span><span class="sxs-lookup"><span data-stu-id="9ee21-107">Requirements</span></span>  

 <span data-ttu-id="9ee21-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ee21-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ee21-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ee21-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ee21-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ee21-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ee21-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ee21-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
