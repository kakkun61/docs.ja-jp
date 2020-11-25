---
title: ICorDebugThread3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 015d0061e5be5bbc212243ca06f1d165abe4496a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729305"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="cf5fa-102">ICorDebugThread3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf5fa-102">ICorDebugThread3 Interface</span></span>

<span data-ttu-id="cf5fa-103">とそれに対応するインターフェイス [へのエントリ](icordebugstackwalk-interface.md) ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="cf5fa-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf5fa-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5fa-104">Methods</span></span>  
  
|<span data-ttu-id="cf5fa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5fa-105">Method</span></span>|<span data-ttu-id="cf5fa-106">説明</span><span class="sxs-lookup"><span data-stu-id="cf5fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf5fa-107">CreateStackWalk メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5fa-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="cf5fa-108">スタックをアンワインドするスレッドに対し [て、このオブジェクトを](icordebugstackwalk-interface.md) 作成します。</span><span class="sxs-lookup"><span data-stu-id="cf5fa-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="cf5fa-109">GetActiveInternalFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5fa-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="cf5fa-110">スタック上の内部フレーム ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="cf5fa-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf5fa-111">注釈</span><span class="sxs-lookup"><span data-stu-id="cf5fa-111">Remarks</span></span>  

 <span data-ttu-id="cf5fa-112">`ICorDebugThread3` は、のように、の論理上の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="cf5fa-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf5fa-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cf5fa-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf5fa-114">要件</span><span class="sxs-lookup"><span data-stu-id="cf5fa-114">Requirements</span></span>  

 <span data-ttu-id="cf5fa-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf5fa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf5fa-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf5fa-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf5fa-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf5fa-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf5fa-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf5fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5fa-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf5fa-119">See also</span></span>

- [<span data-ttu-id="cf5fa-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf5fa-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cf5fa-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="cf5fa-121">Debugging</span></span>](index.md)
