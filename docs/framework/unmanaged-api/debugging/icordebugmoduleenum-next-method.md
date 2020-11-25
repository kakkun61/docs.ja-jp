---
title: ICorDebugModuleEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: a4bdac42c584d5d34b072354de65ed20c6a80609
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709493"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="c82fe-102">ICorDebugModuleEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="c82fe-102">ICorDebugModuleEnum::Next Method</span></span>

<span data-ttu-id="c82fe-103">によって指定された "のモジュール" インスタンスの数を列挙から取得します。この数は `celt` 、現在の位置から開始します。</span><span class="sxs-lookup"><span data-stu-id="c82fe-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c82fe-104">構文</span><span class="sxs-lookup"><span data-stu-id="c82fe-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c82fe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c82fe-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="c82fe-106">から `ICorDebugModule` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="c82fe-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="c82fe-107">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugModule` ます。</span><span class="sxs-lookup"><span data-stu-id="c82fe-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c82fe-108">入出力実際に返されたインスタンスの数へのポインター `ICorDebugModule` 。</span><span class="sxs-lookup"><span data-stu-id="c82fe-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="c82fe-109">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="c82fe-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c82fe-110">要件</span><span class="sxs-lookup"><span data-stu-id="c82fe-110">Requirements</span></span>  

 <span data-ttu-id="c82fe-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c82fe-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c82fe-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c82fe-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c82fe-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c82fe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c82fe-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c82fe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82fe-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c82fe-115">See also</span></span>
