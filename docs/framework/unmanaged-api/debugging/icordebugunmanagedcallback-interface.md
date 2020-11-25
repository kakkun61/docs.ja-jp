---
title: ICorDebugUnmanagedCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
ms.openlocfilehash: 73722c9fbc1571496159c32b0106f25bc05dbe65
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703019"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="b531b-102">ICorDebugUnmanagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b531b-102">ICorDebugUnmanagedCallback Interface</span></span>

<span data-ttu-id="b531b-103">共通言語ランタイム (CLR) に直接関連しないネイティブイベントの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="b531b-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b531b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b531b-104">Methods</span></span>  
  
|<span data-ttu-id="b531b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b531b-105">Method</span></span>|<span data-ttu-id="b531b-106">説明</span><span class="sxs-lookup"><span data-stu-id="b531b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b531b-107">DebugEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="b531b-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="b531b-108">ネイティブイベントが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b531b-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b531b-109">注釈</span><span class="sxs-lookup"><span data-stu-id="b531b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b531b-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b531b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b531b-111">要件</span><span class="sxs-lookup"><span data-stu-id="b531b-111">Requirements</span></span>  

 <span data-ttu-id="b531b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b531b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b531b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b531b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b531b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b531b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b531b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b531b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b531b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b531b-116">See also</span></span>

- [<span data-ttu-id="b531b-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b531b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
