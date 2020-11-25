---
title: ICorDebugChain::GetReason メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 58e40995012d98c1af6a41eb12d898c6b9b1d47b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719672"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="a66d7-102">ICorDebugChain::GetReason メソッド</span><span class="sxs-lookup"><span data-stu-id="a66d7-102">ICorDebugChain::GetReason Method</span></span>

<span data-ttu-id="a66d7-103">この呼び出しチェーンの genesis の理由を取得します。</span><span class="sxs-lookup"><span data-stu-id="a66d7-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="a66d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a66d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a66d7-105">Parameters</span></span>  

 `pReason`  
 <span data-ttu-id="a66d7-106">入出力この呼び出しチェーンの genesis の理由を示す、CorDebugChainReason 列挙体の値 (ビットごとの組み合わせ) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a66d7-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a66d7-107">要件</span><span class="sxs-lookup"><span data-stu-id="a66d7-107">Requirements</span></span>  

 <span data-ttu-id="a66d7-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a66d7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a66d7-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a66d7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a66d7-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a66d7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a66d7-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a66d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
