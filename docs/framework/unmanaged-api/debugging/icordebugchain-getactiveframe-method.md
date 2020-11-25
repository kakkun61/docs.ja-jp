---
title: ICorDebugChain::GetActiveFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: daecd216b4d7e9c23336b8956c13735549be901b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730137"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="6e64e-102">ICorDebugChain::GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="6e64e-102">ICorDebugChain::GetActiveFrame Method</span></span>

<span data-ttu-id="6e64e-103">チェーンのアクティブな (つまり、最新の) フレームを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e64e-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e64e-104">構文</span><span class="sxs-lookup"><span data-stu-id="6e64e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e64e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e64e-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="6e64e-106">入出力チェーン上のアクティブな (つまり、最新の) フレームを表す、の各フレームオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6e64e-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e64e-107">注釈</span><span class="sxs-lookup"><span data-stu-id="6e64e-107">Remarks</span></span>  

 <span data-ttu-id="6e64e-108">使用できるマネージスタックフレームがない場合、 `ppFrame` は null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6e64e-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="6e64e-109">アクティブなフレームが使用できない場合、呼び出しは成功し、 `ppFrame` は null になります。</span><span class="sxs-lookup"><span data-stu-id="6e64e-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="6e64e-110">CHAIN_ENTER_UNMANAGED によって開始されるチェーンと、CHAIN_CLASS_INIT によって開始されるチェーンに対して、アクティブなフレームは使用できません。</span><span class="sxs-lookup"><span data-stu-id="6e64e-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="6e64e-111">CorDebugChainReason 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e64e-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e64e-112">要件</span><span class="sxs-lookup"><span data-stu-id="6e64e-112">Requirements</span></span>  

 <span data-ttu-id="6e64e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e64e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e64e-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e64e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e64e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e64e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e64e-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e64e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
