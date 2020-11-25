---
title: ICorDebugFrameEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 76b96dfd9d22c7e770671dcc01cb421430df729f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728187"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="e9d07-102">ICorDebugFrameEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="e9d07-102">ICorDebugFrameEnum::Next Method</span></span>

<span data-ttu-id="e9d07-103">現在の位置から開始して、指定された数の表示フレームインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e9d07-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9d07-104">構文</span><span class="sxs-lookup"><span data-stu-id="e9d07-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9d07-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9d07-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="e9d07-106">から `ICorDebugFrame` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="e9d07-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="e9d07-107">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="e9d07-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e9d07-108">入出力実際に返されたインスタンスの数へのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="e9d07-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="e9d07-109">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="e9d07-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9d07-110">要件</span><span class="sxs-lookup"><span data-stu-id="e9d07-110">Requirements</span></span>  

 <span data-ttu-id="e9d07-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9d07-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9d07-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9d07-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9d07-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9d07-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9d07-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9d07-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
