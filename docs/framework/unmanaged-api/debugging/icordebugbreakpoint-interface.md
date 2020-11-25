---
title: ICorDebugBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730202"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="9421c-102">ICorDebugBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9421c-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="9421c-103">関数内のブレークポイント、または値のウォッチポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="9421c-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9421c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9421c-104">Methods</span></span>  
  
|<span data-ttu-id="9421c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9421c-105">Method</span></span>|<span data-ttu-id="9421c-106">説明</span><span class="sxs-lookup"><span data-stu-id="9421c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9421c-107">Activate メソッド</span><span class="sxs-lookup"><span data-stu-id="9421c-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="9421c-108">こののアクティブな状態を設定 `ICorDebugBreakpoint` します。</span><span class="sxs-lookup"><span data-stu-id="9421c-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="9421c-109">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="9421c-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="9421c-110">このがアクティブかどうかを示す値を取得し `ICorDebugBreakpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="9421c-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9421c-111">注釈</span><span class="sxs-lookup"><span data-stu-id="9421c-111">Remarks</span></span>  

 <span data-ttu-id="9421c-112">ブレークポイントは、条件式を直接サポートしません。</span><span class="sxs-lookup"><span data-stu-id="9421c-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="9421c-113">このような機能が必要な場合は、デバッガーでを上に実装する必要があり `ICorDebugBreakpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="9421c-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="9421c-114">は、 `ICorDebugBreakpoint` 関数内のブレークポイントをサポートするために、によって拡張されます。</span><span class="sxs-lookup"><span data-stu-id="9421c-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9421c-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9421c-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9421c-116">要件</span><span class="sxs-lookup"><span data-stu-id="9421c-116">Requirements</span></span>  

 <span data-ttu-id="9421c-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9421c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9421c-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9421c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9421c-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9421c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9421c-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9421c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9421c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9421c-121">See also</span></span>

- [<span data-ttu-id="9421c-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9421c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
