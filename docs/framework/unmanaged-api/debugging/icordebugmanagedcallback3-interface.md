---
title: ICorDebugManagedCallback3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: e04f5be6d2612b26bf7d71807753d170e6a5a7a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723299"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="9b30f-102">ICorDebugManagedCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b30f-102">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="9b30f-103">有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9b30f-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b30f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9b30f-104">Methods</span></span>  
  
|<span data-ttu-id="9b30f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9b30f-105">Method</span></span>|<span data-ttu-id="9b30f-106">説明</span><span class="sxs-lookup"><span data-stu-id="9b30f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b30f-107">CustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="9b30f-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="9b30f-108">有効なカスタムデバッガー通知が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9b30f-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b30f-109">注釈</span><span class="sxs-lookup"><span data-stu-id="9b30f-109">Remarks</span></span>  

 <span data-ttu-id="9b30f-110">このインターフェイスは、" [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) [" というインターフェイスを論理的](icordebugmanagedcallback-interface.md)に拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="9b30f-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b30f-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9b30f-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b30f-112">要件</span><span class="sxs-lookup"><span data-stu-id="9b30f-112">Requirements</span></span>  

 <span data-ttu-id="9b30f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b30f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b30f-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b30f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b30f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b30f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b30f-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b30f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b30f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b30f-117">See also</span></span>

- [<span data-ttu-id="9b30f-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b30f-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="9b30f-119">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b30f-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="9b30f-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b30f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9b30f-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9b30f-121">Debugging</span></span>](index.md)
