---
title: ICorDebugStackWalk インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: b37a89c0a86df49c894dc43676f8feafb80f5c95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687516"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="8d123-102">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d123-102">ICorDebugStackWalk Interface</span></span>

<span data-ttu-id="8d123-103">スレッドのスタック上のマネージド メソッド (フレーム) を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d123-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d123-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8d123-104">Methods</span></span>  
  
|<span data-ttu-id="8d123-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8d123-105">Method</span></span>|<span data-ttu-id="8d123-106">説明</span><span class="sxs-lookup"><span data-stu-id="8d123-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d123-107">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="8d123-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="8d123-108">オブジェクト内の現在のフレームのコンテキストを返し `ICorDebugStackWalk` ます。</span><span class="sxs-lookup"><span data-stu-id="8d123-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="8d123-109">SetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="8d123-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="8d123-110">`ICorDebugStackWalk`オブジェクトの現在のコンテキストをスレッドの有効なコンテキストに設定します。</span><span class="sxs-lookup"><span data-stu-id="8d123-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="8d123-111">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="8d123-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="8d123-112">オブジェクトを `ICorDebugStackWalk` 次のフレームに移動します。</span><span class="sxs-lookup"><span data-stu-id="8d123-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="8d123-113">GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="8d123-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="8d123-114">オブジェクト内の現在のフレームを取得し `ICorDebugStackWalk` ます。</span><span class="sxs-lookup"><span data-stu-id="8d123-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d123-115">注釈</span><span class="sxs-lookup"><span data-stu-id="8d123-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d123-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8d123-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d123-117">要件</span><span class="sxs-lookup"><span data-stu-id="8d123-117">Requirements</span></span>  

 <span data-ttu-id="8d123-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d123-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d123-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d123-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d123-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d123-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d123-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d123-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d123-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d123-122">See also</span></span>

- [<span data-ttu-id="8d123-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d123-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8d123-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8d123-124">Debugging</span></span>](index.md)
