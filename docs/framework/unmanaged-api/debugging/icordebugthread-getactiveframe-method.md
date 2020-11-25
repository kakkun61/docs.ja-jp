---
title: ICorDebugThread::GetActiveFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
ms.openlocfilehash: 6ca4c1ad5ef575db075a5066146bacb6d1e59ea2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728083"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="7f1d7-102">ICorDebugThread::GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="7f1d7-102">ICorDebugThread::GetActiveFrame Method</span></span>

<span data-ttu-id="7f1d7-103">このテキストスレッドオブジェクトのアクティブな (最新の) フレームへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7f1d7-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f1d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f1d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f1d7-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="7f1d7-106">入出力フレームを表す、テキストフレームインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7f1d7-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f1d7-107">注釈</span><span class="sxs-lookup"><span data-stu-id="7f1d7-107">Remarks</span></span>  

 <span data-ttu-id="7f1d7-108">`ppFrame`現在アクティブなフレームがない場合、パラメーターは null になります。</span><span class="sxs-lookup"><span data-stu-id="7f1d7-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1d7-109">要件</span><span class="sxs-lookup"><span data-stu-id="7f1d7-109">Requirements</span></span>  

 <span data-ttu-id="7f1d7-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f1d7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1d7-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f1d7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f1d7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f1d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f1d7-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f1d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
