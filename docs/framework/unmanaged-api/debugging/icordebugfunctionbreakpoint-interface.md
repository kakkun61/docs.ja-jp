---
title: ICorDebugFunctionBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
ms.openlocfilehash: 0f1e6bbdf16c953b0dd22d9dfa44bc3585f1269e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726250"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="590fc-102">ICorDebugFunctionBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="590fc-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="590fc-103">ICorDebugBreakpoint インターフェイスを拡張して、関数内のブレークポイントをサポートします。</span><span class="sxs-lookup"><span data-stu-id="590fc-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="590fc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="590fc-104">Methods</span></span>  
  
|<span data-ttu-id="590fc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="590fc-105">Method</span></span>|<span data-ttu-id="590fc-106">説明</span><span class="sxs-lookup"><span data-stu-id="590fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="590fc-107">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="590fc-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="590fc-108">ブレークポイントが設定されている関数を参照する、のオブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="590fc-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="590fc-109">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="590fc-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="590fc-110">関数内のブレークポイントのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="590fc-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="590fc-111">注釈</span><span class="sxs-lookup"><span data-stu-id="590fc-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="590fc-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="590fc-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="590fc-113">要件</span><span class="sxs-lookup"><span data-stu-id="590fc-113">Requirements</span></span>  

 <span data-ttu-id="590fc-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="590fc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="590fc-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="590fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="590fc-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="590fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="590fc-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="590fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590fc-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="590fc-118">See also</span></span>

- [<span data-ttu-id="590fc-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="590fc-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
