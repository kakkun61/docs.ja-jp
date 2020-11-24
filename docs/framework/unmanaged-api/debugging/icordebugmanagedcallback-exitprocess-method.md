---
title: ICorDebugManagedCallback::ExitProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 67f3e63b58e08a4b9ccfbd555e6edcdef0d00d90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688944"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="8b87a-102">ICorDebugManagedCallback::ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="8b87a-102">ICorDebugManagedCallback::ExitProcess Method</span></span>

<span data-ttu-id="8b87a-103">プロセスが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8b87a-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b87a-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b87a-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b87a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b87a-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="8b87a-106">からプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b87a-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b87a-107">注釈</span><span class="sxs-lookup"><span data-stu-id="8b87a-107">Remarks</span></span>  

 <span data-ttu-id="8b87a-108">イベントから続行することはできません `ExitProcess` 。</span><span class="sxs-lookup"><span data-stu-id="8b87a-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="8b87a-109">このイベントは、プロセスの停止中に、他のイベントに非同期に発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8b87a-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="8b87a-110">これは、プロセスが停止中に終了した場合に発生する可能性があります。通常は、何らかの外部強制が原因です。</span><span class="sxs-lookup"><span data-stu-id="8b87a-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="8b87a-111">共通言語ランタイム (CLR) がマネージコールバックのディスパッチを既に行っている場合、このイベントは、そのコールバックが返されるまで遅延されます。</span><span class="sxs-lookup"><span data-stu-id="8b87a-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="8b87a-112">`ExitProcess`イベントは、シャットダウン時に呼び出されることが保証されている唯一の終了/アンロードイベントです。</span><span class="sxs-lookup"><span data-stu-id="8b87a-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b87a-113">要件</span><span class="sxs-lookup"><span data-stu-id="8b87a-113">Requirements</span></span>  

 <span data-ttu-id="8b87a-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b87a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b87a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b87a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b87a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b87a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b87a-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b87a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b87a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b87a-118">See also</span></span>

- [<span data-ttu-id="8b87a-119">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b87a-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
