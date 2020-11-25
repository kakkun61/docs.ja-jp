---
title: ICorDebugBreakpointEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
ms.openlocfilehash: 14c89e808ea8e41bbee46a59a60bc1876f3800d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730189"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="4026d-102">ICorDebugBreakpointEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="4026d-102">ICorDebugBreakpointEnum::Next Method</span></span>

<span data-ttu-id="4026d-103">現在の位置から開始して、指定した数の ICorDebugBreakpoint インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="4026d-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4026d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4026d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4026d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4026d-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="4026d-106">から `ICorDebugBreakpoint` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="4026d-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="4026d-107">入出力ポインターの配列。各ポインターは、 `ICorDebugBreakpoint` ブレークポイントを表すオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="4026d-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4026d-108">入出力実際に返されたインスタンスの数へのポインター `ICorDebugBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="4026d-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="4026d-109">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="4026d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4026d-110">要件</span><span class="sxs-lookup"><span data-stu-id="4026d-110">Requirements</span></span>  

 <span data-ttu-id="4026d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4026d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4026d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4026d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4026d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4026d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4026d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4026d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
