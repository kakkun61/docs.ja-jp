---
title: ICorDebugArrayValue::GetRank メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
ms.openlocfilehash: 9fddee70e34ba9bf7c1860c1a160db369e45fb5e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698163"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="c6430-102">ICorDebugArrayValue::GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="c6430-102">ICorDebugArrayValue::GetRank Method</span></span>

<span data-ttu-id="c6430-103">配列のディメンションの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="c6430-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6430-104">構文</span><span class="sxs-lookup"><span data-stu-id="c6430-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6430-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6430-105">Parameters</span></span>  

 `pnRank`  
 <span data-ttu-id="c6430-106">入出力このオブジェクトの次元数へのポインター `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="c6430-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6430-107">要件</span><span class="sxs-lookup"><span data-stu-id="c6430-107">Requirements</span></span>  

 <span data-ttu-id="c6430-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6430-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6430-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6430-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6430-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6430-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6430-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6430-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
