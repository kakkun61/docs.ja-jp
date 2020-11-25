---
title: ICorDebugEval::GetThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
ms.openlocfilehash: 0680c47e4390e876c5df99ee7eb200e7d187f0ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722194"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="bf846-102">ICorDebugEval::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="bf846-102">ICorDebugEval::GetThread Method</span></span>

<span data-ttu-id="bf846-103">この評価が実行されている、または実行されるスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf846-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf846-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf846-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf846-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf846-105">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="bf846-106">入出力スレッドを表す、スレッドオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bf846-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf846-107">要件</span><span class="sxs-lookup"><span data-stu-id="bf846-107">Requirements</span></span>  

 <span data-ttu-id="bf846-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf846-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf846-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf846-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf846-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf846-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf846-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf846-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
