---
title: ICorDebugFrame::GetFunctionToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
ms.openlocfilehash: 3430c5062bd5633e1178226974b7358783192e51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675985"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="6cdab-102">ICorDebugFrame::GetFunctionToken メソッド</span><span class="sxs-lookup"><span data-stu-id="6cdab-102">ICorDebugFrame::GetFunctionToken Method</span></span>

<span data-ttu-id="6cdab-103">このスタックフレームに関連付けられているコードを含む関数のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="6cdab-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cdab-104">構文</span><span class="sxs-lookup"><span data-stu-id="6cdab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cdab-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6cdab-105">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="6cdab-106">入出力 `mdMethodDef` 関数のメタデータを参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6cdab-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cdab-107">要件</span><span class="sxs-lookup"><span data-stu-id="6cdab-107">Requirements</span></span>  

 <span data-ttu-id="6cdab-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cdab-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cdab-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cdab-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cdab-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cdab-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cdab-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cdab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
