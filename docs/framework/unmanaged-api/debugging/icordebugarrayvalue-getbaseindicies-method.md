---
title: ICorDebugArrayValue::GetBaseIndicies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: ea5c5a728afb9ac90f8599c833caab11fd0c65fe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731463"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="50309-102">ICorDebugArrayValue::GetBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="50309-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>

<span data-ttu-id="50309-103">配列内の各次元のベースインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="50309-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50309-104">構文</span><span class="sxs-lookup"><span data-stu-id="50309-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50309-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50309-105">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="50309-106">からこのオブジェクトの次元数 `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="50309-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="50309-107">この値は、 `indicies` 配列のサイズがオブジェクトの次元数と同じであるため、配列のサイズでも `ICorDebugArrayValue` あります。</span><span class="sxs-lookup"><span data-stu-id="50309-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="50309-108">入出力整数の配列。各整数は、このオブジェクトの次元のベースインデックス (つまり開始インデックス) です `ICorDebugArrayValue` 。</span><span class="sxs-lookup"><span data-stu-id="50309-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50309-109">要件</span><span class="sxs-lookup"><span data-stu-id="50309-109">Requirements</span></span>  

 <span data-ttu-id="50309-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50309-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50309-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50309-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50309-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50309-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50309-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50309-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
