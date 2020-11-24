---
title: ICorDebugFrame::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: b52499e509bf172b03b5e4d2b1e4c677dc800281
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690474"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="5dab8-102">ICorDebugFrame::GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="5dab8-102">ICorDebugFrame::GetCaller Method</span></span>

<span data-ttu-id="5dab8-103">このフレームを呼び出した現在のチェーン内のテキストボックスオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5dab8-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dab8-104">構文</span><span class="sxs-lookup"><span data-stu-id="5dab8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dab8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5dab8-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="5dab8-106">入出力呼び出し元のフレームを表すオブジェクトのアドレスへのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="5dab8-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="5dab8-107">呼び出されたフレームが現在のチェーンの最も外側のフレームである場合、この値は null になります。</span><span class="sxs-lookup"><span data-stu-id="5dab8-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dab8-108">要件</span><span class="sxs-lookup"><span data-stu-id="5dab8-108">Requirements</span></span>  

 <span data-ttu-id="5dab8-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dab8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dab8-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dab8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dab8-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dab8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dab8-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dab8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
