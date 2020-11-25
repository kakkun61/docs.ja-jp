---
title: ICorDebugFunction::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 9aee95c554afad5b2ea3cf157fc9e62c9b7e40e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696116"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="5c992-102">ICorDebugFunction::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="5c992-102">ICorDebugFunction::GetToken Method</span></span>

<span data-ttu-id="5c992-103">この関数のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="5c992-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c992-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c992-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c992-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c992-105">Parameters</span></span>  

 `pMethodDef`  
 <span data-ttu-id="5c992-106">入出力 `mdMethodDef` この関数のメタデータを参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c992-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c992-107">要件</span><span class="sxs-lookup"><span data-stu-id="5c992-107">Requirements</span></span>  

 <span data-ttu-id="5c992-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c992-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c992-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c992-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c992-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c992-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c992-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c992-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
