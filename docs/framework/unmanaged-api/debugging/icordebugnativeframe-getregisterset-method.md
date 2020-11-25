---
title: ICorDebugNativeFrame::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
ms.openlocfilehash: 945a398d32b50efc81ba45e705ed9d4161ed1524
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709272"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="42423-102">ICorDebugNativeFrame::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="42423-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>

<span data-ttu-id="42423-103">このスタックフレームのレジスタセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="42423-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42423-104">構文</span><span class="sxs-lookup"><span data-stu-id="42423-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42423-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42423-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="42423-106">入出力このスタックフレームの [レジスタセットを表す、オブジェクトの](icordebugregisterset-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="42423-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42423-107">要件</span><span class="sxs-lookup"><span data-stu-id="42423-107">Requirements</span></span>  

 <span data-ttu-id="42423-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42423-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42423-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42423-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42423-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42423-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42423-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42423-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42423-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="42423-112">See also</span></span>
