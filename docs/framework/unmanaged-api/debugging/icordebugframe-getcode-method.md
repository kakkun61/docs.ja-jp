---
title: ICorDebugFrame::GetCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
ms.openlocfilehash: 29dc87bf465fc9751b5af795f7640b095e535e63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690396"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="d9475-102">ICorDebugFrame::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="d9475-102">ICorDebugFrame::GetCode Method</span></span>

<span data-ttu-id="d9475-103">このスタックフレームに関連付けられているコードへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d9475-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9475-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9475-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9475-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9475-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="d9475-106">入出力このフレームに関連付けられているコードを表す、コードオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d9475-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9475-107">要件</span><span class="sxs-lookup"><span data-stu-id="d9475-107">Requirements</span></span>  

 <span data-ttu-id="d9475-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9475-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9475-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9475-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9475-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9475-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9475-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9475-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
