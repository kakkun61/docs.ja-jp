---
title: ICorDebugManagedCallback2::ChangeConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 4ba04b1a4815587b40d03819fdac795dcc7f2c4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697273"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="a933d-102">ICorDebugManagedCallback2::ChangeConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="a933d-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>

<span data-ttu-id="a933d-103">指定した接続に関連付けられたタスクのセットが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a933d-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a933d-104">構文</span><span class="sxs-lookup"><span data-stu-id="a933d-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a933d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a933d-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="a933d-106">から変更された接続を格納しているプロセスを表す "いいプロセス" オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a933d-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="a933d-107">から変更された接続の ID。</span><span class="sxs-lookup"><span data-stu-id="a933d-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a933d-108">注釈</span><span class="sxs-lookup"><span data-stu-id="a933d-108">Remarks</span></span>  

 <span data-ttu-id="a933d-109">`ChangeConnection`コールバックは、次のいずれかの場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a933d-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="a933d-110">デバッガーが接続を含むプロセスにアタッチする場合。</span><span class="sxs-lookup"><span data-stu-id="a933d-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="a933d-111">この場合、ランタイムは、プロセス内の各接続に対して [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) イベントとイベントを生成してディスパッチし `ChangeConnection` ます。</span><span class="sxs-lookup"><span data-stu-id="a933d-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="a933d-112">`ChangeConnection`接続のタスクセットが作成後に変更されたかどうかに関係なく、既存のすべての接続に対してイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a933d-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="a933d-113">ホストが[ホスティング API](../hosting/index.md)で[ICLRDebugManager:: setconnectiontasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md)を呼び出すとき。</span><span class="sxs-lookup"><span data-stu-id="a933d-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
 <span data-ttu-id="a933d-114">デバッガーは、新しい変更を取得するために、プロセス内のすべてのスレッドをスキャンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a933d-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a933d-115">要件</span><span class="sxs-lookup"><span data-stu-id="a933d-115">Requirements</span></span>  

 <span data-ttu-id="a933d-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a933d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a933d-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a933d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a933d-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a933d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a933d-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a933d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a933d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a933d-120">See also</span></span>

- [<span data-ttu-id="a933d-121">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a933d-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="a933d-122">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a933d-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
