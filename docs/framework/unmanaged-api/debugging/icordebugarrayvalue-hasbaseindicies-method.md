---
title: ICorDebugArrayValue::HasBaseIndicies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
ms.openlocfilehash: a9d1faf5a834cb5d9be19f995aaa3eee1202171b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727446"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="1d3cf-102">ICorDebugArrayValue::HasBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="1d3cf-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>

<span data-ttu-id="1d3cf-103">この配列のどの次元にも0以外のベースインデックスがあるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1d3cf-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d3cf-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d3cf-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d3cf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1d3cf-105">Parameters</span></span>  

 `pbHasBaseIndicies`  
 <span data-ttu-id="1d3cf-106">入出力 `true` このオブジェクトの1つ以上の次元に0以外のベースインデックスがある場合は、ブール値へのポインター。それ以外の場合は、 `ICorDebugArrayValue` ブール値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="1d3cf-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d3cf-107">要件</span><span class="sxs-lookup"><span data-stu-id="1d3cf-107">Requirements</span></span>  

 <span data-ttu-id="1d3cf-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d3cf-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d3cf-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d3cf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d3cf-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d3cf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d3cf-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d3cf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
