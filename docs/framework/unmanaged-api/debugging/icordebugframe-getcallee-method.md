---
title: ICorDebugFrame::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 6347e0109f256dc46eb0140ffd1f51977c205b51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678806"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="83180-102">ICorDebugFrame::GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="83180-102">ICorDebugFrame::GetCallee Method</span></span>

<span data-ttu-id="83180-103">このフレームが呼び出された現在のチェーン内のテキストボックスオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="83180-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83180-104">構文</span><span class="sxs-lookup"><span data-stu-id="83180-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83180-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83180-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="83180-106">入出力呼び出されたフレームを表すオブジェクトのアドレスへのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="83180-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="83180-107">呼び出し元のフレームが現在のチェーンの最も内側のフレームである場合、この値は null になります。</span><span class="sxs-lookup"><span data-stu-id="83180-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83180-108">要件</span><span class="sxs-lookup"><span data-stu-id="83180-108">Requirements</span></span>  

 <span data-ttu-id="83180-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83180-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83180-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83180-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83180-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83180-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83180-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83180-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
