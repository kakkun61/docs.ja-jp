---
title: ICorDebugManagedCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: 937a2fb322eb63461d90e215635e1b10ab6afd09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689785"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="cea0b-102">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cea0b-102">ICorDebugManagedCallback2 Interface</span></span>

<span data-ttu-id="cea0b-103">デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="cea0b-104">`ICorDebugManagedCallback2` は [、のように、の](icordebugmanagedcallback-interface.md) 論理上の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="cea0b-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cea0b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-105">Methods</span></span>  
  
|<span data-ttu-id="cea0b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-106">Method</span></span>|<span data-ttu-id="cea0b-107">説明</span><span class="sxs-lookup"><span data-stu-id="cea0b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cea0b-108">ChangeConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-108">ChangeConnection Method</span></span>](icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="cea0b-109">指定した接続に関連付けられたタスクのセットが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="cea0b-110">CreateConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-110">CreateConnection Method</span></span>](icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="cea0b-111">新しい接続が作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="cea0b-112">DestroyConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-112">DestroyConnection Method</span></span>](icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="cea0b-113">指定された接続が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="cea0b-114">Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-114">Exception Method</span></span>](icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="cea0b-115">例外ハンドラーの検索が開始されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="cea0b-116">ExceptionUnwind メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-116">ExceptionUnwind Method</span></span>](icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="cea0b-117">例外アンワインド処理中の状態通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="cea0b-118">FunctionRemapComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-118">FunctionRemapComplete Method</span></span>](icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="cea0b-119">コードの実行が編集された関数の新しいバージョンに切り替わったことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="cea0b-120">FunctionRemapOpportunity メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-120">FunctionRemapOpportunity Method</span></span>](icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="cea0b-121">コードの実行が、編集された関数の古いバージョンのシーケンスポイントに達したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="cea0b-122">MDANotification メソッド</span><span class="sxs-lookup"><span data-stu-id="cea0b-122">MDANotification Method</span></span>](icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="cea0b-123">コード実行でマネージデバッグアシスタント (MDA) メッセージが検出されたことを通知します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cea0b-124">注釈</span><span class="sxs-lookup"><span data-stu-id="cea0b-124">Remarks</span></span>  

 <span data-ttu-id="cea0b-125">インターフェイスは、インターフェイスを拡張して、 `ICorDebugManagedCallback2` `ICorDebugManagedCallback` .NET Framework バージョン2.0 で導入された新しいデバッグイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="cea0b-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="cea0b-126">デバッガー `ICorDebugManagedCallback2` が .NET Framework 2.0 アプリケーションをデバッグしている場合は、を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cea0b-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="cea0b-127">またはのインスタンスは、 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` コールバックオブジェクトとして [ICorDebug:: setmanagedhandler](icordebug-setmanagedhandler-method.md)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="cea0b-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cea0b-128">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cea0b-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cea0b-129">要件</span><span class="sxs-lookup"><span data-stu-id="cea0b-129">Requirements</span></span>  

 <span data-ttu-id="cea0b-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cea0b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cea0b-131">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cea0b-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cea0b-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cea0b-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cea0b-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cea0b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea0b-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="cea0b-134">See also</span></span>

- [<span data-ttu-id="cea0b-135">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="cea0b-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cea0b-136">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cea0b-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cea0b-137">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cea0b-137">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
