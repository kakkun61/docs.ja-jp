---
title: AsyncWaitHandle の使用によるアプリケーション実行のブロック
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
ms.openlocfilehash: 1e7fc71ef5a4a44b2bb4c039305e06c157c65f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716162"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="e73c0-102">AsyncWaitHandle の使用によるアプリケーション実行のブロック</span><span class="sxs-lookup"><span data-stu-id="e73c0-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>

<span data-ttu-id="e73c0-103">非同期操作の結果の待機中に、他の作業を継続できないアプリケーションは、操作が完了するまでブロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e73c0-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="e73c0-104">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、アプリケーションのメイン スレッドをブロックします。</span><span class="sxs-lookup"><span data-stu-id="e73c0-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="e73c0-105">非同期操作の **Begin**_OperationName_ メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.AsyncWaitHandle%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="e73c0-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="e73c0-106">このトピックでは、この方法のデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e73c0-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="e73c0-107">非同期操作の **End**_OperationName_ メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e73c0-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="e73c0-108">この方法をデモの例については、「[非同期操作の終了によるアプリケーション実行のブロック](blocking-application-execution-by-ending-an-async-operation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e73c0-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="e73c0-109">非同期操作が完了するまでブロックする 1 つ以上の <xref:System.Threading.WaitHandle> オブジェクトを使用するアプリケーションは、通常は **Begin**_OperationName_ メソッドを呼び出し、操作の結果なしで実行できるすべての作業を実行し、非同期操作が完了するまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="e73c0-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="e73c0-110">アプリケーションは、<xref:System.IAsyncResult.AsyncWaitHandle%2A> を使用して <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドのいずれかを呼び出し、単一の操作上でブロックできます。</span><span class="sxs-lookup"><span data-stu-id="e73c0-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="e73c0-111">非同期操作のセットが完了するまで待機しながらブロックするには、関連する <xref:System.IAsyncResult.AsyncWaitHandle%2A> オブジェクトを配列に格納し、<xref:System.Threading.WaitHandle.WaitAll%2A> メソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e73c0-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="e73c0-112">非同期操作のいずれかのセットが完了するまで待機しながらブロックするには、関連する <xref:System.IAsyncResult.AsyncWaitHandle%2A> オブジェクトを配列に格納し、<xref:System.Threading.WaitHandle.WaitAny%2A> メソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e73c0-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e73c0-113">例</span><span class="sxs-lookup"><span data-stu-id="e73c0-113">Example</span></span>  

 <span data-ttu-id="e73c0-114">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するために、DNS クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="e73c0-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="e73c0-115">例では、非同期操作に関連付けられた <xref:System.Threading.WaitHandle> を使用して、ブロックのデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="e73c0-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="e73c0-116">この方法を使用する場合は必要ないため、`null` (Visual Basic の場合は `Nothing`) は、<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` と `stateObject` パラメーターに渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e73c0-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e73c0-117">参照</span><span class="sxs-lookup"><span data-stu-id="e73c0-117">See also</span></span>

- [<span data-ttu-id="e73c0-118">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="e73c0-118">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="e73c0-119">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="e73c0-119">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
