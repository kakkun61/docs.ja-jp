---
title: ICorDebugChain::GetNext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: 75b97f4333f3e81533b1f10b8c3c7ba6197ac94a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730085"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="cc79d-102">ICorDebugChain::GetNext メソッド</span><span class="sxs-lookup"><span data-stu-id="cc79d-102">ICorDebugChain::GetNext Method</span></span>

<span data-ttu-id="cc79d-103">スレッドの次のフレームのチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc79d-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc79d-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc79d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc79d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc79d-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="cc79d-106">入出力スレッドの次のフレームのチェーンを表す、テキストチェーンオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cc79d-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="cc79d-107">このチェーンが最後のチェーンの場合、 `ppChain` は null です。</span><span class="sxs-lookup"><span data-stu-id="cc79d-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc79d-108">要件</span><span class="sxs-lookup"><span data-stu-id="cc79d-108">Requirements</span></span>  

 <span data-ttu-id="cc79d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc79d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc79d-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc79d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc79d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc79d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc79d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc79d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
