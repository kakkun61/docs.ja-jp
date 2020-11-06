---
title: 同期メソッドの非同期呼び出し
description: BeginInvoke メソッドと EndInvoke メソッドを使用して、.NET で同期メソッドを非同期的に呼び出す方法について説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
ms.openlocfilehash: d518e5f64096fde5c9b14222dc4fe0634e6bb7b1
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888894"
---
# <a name="calling-synchronous-methods-asynchronously"></a><span data-ttu-id="09e74-103">同期メソッドの非同期呼び出し</span><span class="sxs-lookup"><span data-stu-id="09e74-103">Calling Synchronous Methods Asynchronously</span></span>

<span data-ttu-id="09e74-104">.NET では、すべてのメソッドを非同期的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="09e74-104">.NET enables you to call any method asynchronously.</span></span> <span data-ttu-id="09e74-105">これを行うには、呼び出すメソッドと同じシグネチャを持つデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="09e74-105">To do this, you define a delegate with the same signature as the method you want to call.</span></span> <span data-ttu-id="09e74-106">このデリゲートには、共通言語ランタイムにより、適切なシグネチャが使用された `BeginInvoke` および `EndInvoke` メソッドが自動的に定義されます。</span><span class="sxs-lookup"><span data-stu-id="09e74-106">The common language runtime automatically defines `BeginInvoke` and `EndInvoke` methods for this delegate, with the appropriate signatures.</span></span>

> [!NOTE]
> <span data-ttu-id="09e74-107">非同期デリゲート (具体的には `BeginInvoke` メソッドと `EndInvoke` メソッド) は、.NET Compact Framework ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="09e74-107">Asynchronous delegate calls, specifically the `BeginInvoke` and `EndInvoke` methods, are not supported in the .NET Compact Framework.</span></span>

<span data-ttu-id="09e74-108">`BeginInvoke` メソッドは、非同期呼び出しを開始します。</span><span class="sxs-lookup"><span data-stu-id="09e74-108">The `BeginInvoke` method initiates the asynchronous call.</span></span> <span data-ttu-id="09e74-109">このメソッドは、非同期的に実行するメソッドと同じパラメーターと共に、2 つの省略可能な追加パラメーターを持っています。</span><span class="sxs-lookup"><span data-stu-id="09e74-109">It has the same parameters as the method that you want to execute asynchronously, plus two additional optional parameters.</span></span> <span data-ttu-id="09e74-110">最初のパラメーターは、同期呼び出しが完了したときに呼び出されるメソッドを参照する <xref:System.AsyncCallback> デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="09e74-110">The first parameter is an <xref:System.AsyncCallback> delegate that references a method to be called when the asynchronous call completes.</span></span> <span data-ttu-id="09e74-111">2 番目のパラメーターは、コールバック メソッドに情報を渡すユーザー定義オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="09e74-111">The second parameter is a user-defined object that passes information into the callback method.</span></span> <span data-ttu-id="09e74-112">`BeginInvoke` からは制御がすぐに戻り、非同期呼び出しが完了するまで待機しません。</span><span class="sxs-lookup"><span data-stu-id="09e74-112">`BeginInvoke` returns immediately and does not wait for the asynchronous call to complete.</span></span> <span data-ttu-id="09e74-113">`BeginInvoke` は <xref:System.IAsyncResult>を返します。これを使用して非同期呼び出しの進捗状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="09e74-113">`BeginInvoke` returns an <xref:System.IAsyncResult>, which can be used to monitor the progress of the asynchronous call.</span></span>

<span data-ttu-id="09e74-114">`EndInvoke` メソッドは、非同期呼び出しの結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="09e74-114">The `EndInvoke` method retrieves the results of the asynchronous call.</span></span> <span data-ttu-id="09e74-115">このメソッドは、 `BeginInvoke`の後であればいつでも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="09e74-115">It can be called any time after `BeginInvoke`.</span></span> <span data-ttu-id="09e74-116">非同期呼び出しがまだ完了していない場合は、 `EndInvoke` は非同期呼び出しが完了するまで呼び出し元スレッドをブロックします。</span><span class="sxs-lookup"><span data-stu-id="09e74-116">If the asynchronous call has not completed, `EndInvoke` blocks the calling thread until it completes.</span></span> <span data-ttu-id="09e74-117">`EndInvoke` のパラメーターには、非同期実行するメソッドの `out` パラメーターと `ref` パラメーター (Visual Basic では `<Out>` `ByRef` と `ByRef`) と、`BeginInvoke` によって返された <xref:System.IAsyncResult> が含まれます。</span><span class="sxs-lookup"><span data-stu-id="09e74-117">The parameters of `EndInvoke` include the `out` and `ref` parameters (`<Out>` `ByRef` and `ByRef` in Visual Basic) of the method that you want to execute asynchronously, plus the <xref:System.IAsyncResult> returned by `BeginInvoke`.</span></span>

> [!NOTE]
> <span data-ttu-id="09e74-118">Visual Studio の IntelliSense 機能によって `BeginInvoke` と `EndInvoke` のパラメーターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="09e74-118">The IntelliSense feature in Visual Studio displays the parameters of `BeginInvoke` and `EndInvoke`.</span></span> <span data-ttu-id="09e74-119">Visual Studio や類似のツールを使っていない場合や、Visual Studio で C# を使っている場合、これらのメソッドについて定義されているパラメーターについては、「[非同期プログラミング モデル (APM)](asynchronous-programming-model-apm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09e74-119">If you're not using Visual Studio or a similar tool, or if you're using C# with Visual Studio, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) for a description of the parameters defined for these methods.</span></span>

<span data-ttu-id="09e74-120">このトピックのコード例では、 `BeginInvoke` と `EndInvoke` を使用して非同期呼び出しを行う 4 つの一般的な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09e74-120">The code examples in this topic demonstrate four common ways to use `BeginInvoke` and `EndInvoke` to make asynchronous calls.</span></span> <span data-ttu-id="09e74-121">`BeginInvoke` を呼び出した後、次の処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="09e74-121">After calling `BeginInvoke` you can do the following:</span></span>

- <span data-ttu-id="09e74-122">何か処理を実行した後、呼び出しが完了するまでブロックする `EndInvoke` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="09e74-122">Do some work and then call `EndInvoke` to block until the call completes.</span></span>

- <span data-ttu-id="09e74-123"><xref:System.Threading.WaitHandle> プロパティを使用して <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> を取得し、その <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドを使用して <xref:System.Threading.WaitHandle> が通知されるまで実行をブロックし、 `EndInvoke`を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="09e74-123">Obtain a <xref:System.Threading.WaitHandle> using the <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> property, use its <xref:System.Threading.WaitHandle.WaitOne%2A> method to block execution until the <xref:System.Threading.WaitHandle> is signaled, and then call `EndInvoke`.</span></span>

- <span data-ttu-id="09e74-124"><xref:System.IAsyncResult> によって返される `BeginInvoke` をポーリングして非同期呼び出しが完了したかどうかを確認した後、 `EndInvoke`を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="09e74-124">Poll the <xref:System.IAsyncResult> returned by `BeginInvoke` to determine when the asynchronous call has completed, and then call `EndInvoke`.</span></span>

- <span data-ttu-id="09e74-125">コールバック メソッドのデリゲートを `BeginInvoke`に渡します。</span><span class="sxs-lookup"><span data-stu-id="09e74-125">Pass a delegate for a callback method to `BeginInvoke`.</span></span> <span data-ttu-id="09e74-126">このメソッドは、非同期呼び出しが完了すると、 <xref:System.Threading.ThreadPool> スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="09e74-126">The method is executed on a <xref:System.Threading.ThreadPool> thread when the asynchronous call completes.</span></span> <span data-ttu-id="09e74-127">コールバック メソッドは `EndInvoke`を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="09e74-127">The callback method calls `EndInvoke`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09e74-128">どの手法を使用する場合でも、常に `EndInvoke` を呼び出して、非同期呼び出しを完了します。</span><span class="sxs-lookup"><span data-stu-id="09e74-128">No matter which technique you use, always call `EndInvoke` to complete your asynchronous call.</span></span>

## <a name="defining-the-test-method-and-asynchronous-delegate"></a><span data-ttu-id="09e74-129">テスト メソッドと非同期デリゲートの定義</span><span class="sxs-lookup"><span data-stu-id="09e74-129">Defining the Test Method and Asynchronous Delegate</span></span>
 <span data-ttu-id="09e74-130">次のコード例は、長時間実行される `TestMethod`メソッドの非同期呼び出しを行うさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09e74-130">The code examples that follow demonstrate various ways of calling the same long-running method, `TestMethod`, asynchronously.</span></span> <span data-ttu-id="09e74-131">`TestMethod` メソッドはコンソール メッセージを表示して処理が開始されたことを示し、しばらくスリープした後、終了します。</span><span class="sxs-lookup"><span data-stu-id="09e74-131">The `TestMethod` method displays a console message to show that it has begun processing, sleeps for a few seconds, and then ends.</span></span> <span data-ttu-id="09e74-132">`TestMethod` には `out` パラメーターがあり、 `BeginInvoke` および `EndInvoke`のシグネチャへのそのようなパラメーターの追加方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09e74-132">`TestMethod` has an `out` parameter to demonstrate the way such parameters are added to the signatures of `BeginInvoke` and `EndInvoke`.</span></span> <span data-ttu-id="09e74-133">`ref` パラメーターは同様に処理できます。</span><span class="sxs-lookup"><span data-stu-id="09e74-133">You can handle `ref` parameters similarly.</span></span>

 <span data-ttu-id="09e74-134">次のコード例は、 `TestMethod` と、 `AsyncMethodCaller` の非同期呼び出しに使用できる `TestMethod` という名前のデリゲートの定義を示します。</span><span class="sxs-lookup"><span data-stu-id="09e74-134">The following code example shows the definition of `TestMethod` and the delegate named `AsyncMethodCaller` that can be used to call `TestMethod` asynchronously.</span></span> <span data-ttu-id="09e74-135">コード例をコンパイルするには、 `TestMethod` および `AsyncMethodCaller` デリゲートの定義を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e74-135">To compile the code examples, you must include the definitions for `TestMethod` and the `AsyncMethodCaller` delegate.</span></span>

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a><span data-ttu-id="09e74-136">EndInvoke による非同期呼び出しの待機</span><span class="sxs-lookup"><span data-stu-id="09e74-136">Waiting for an Asynchronous Call with EndInvoke</span></span>
 <span data-ttu-id="09e74-137">メソッドを非同期実行する最も簡単な方法は、デリゲートの `BeginInvoke` メソッドを呼び出してメソッドの実行を開始し、メイン スレッドで何かの処理を実行した後、デリゲートの `EndInvoke` メソッドを呼び出す方法です。</span><span class="sxs-lookup"><span data-stu-id="09e74-137">The simplest way to execute a method asynchronously is to start executing the method by calling the delegate's `BeginInvoke` method, do some work on the main thread, and then call the delegate's `EndInvoke` method.</span></span> <span data-ttu-id="09e74-138">`EndInvoke` は非同期呼び出しが完了するまで戻らないので、呼び出し元スレッドがブロックされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="09e74-138">`EndInvoke` might block the calling thread because it does not return until the asynchronous call completes.</span></span> <span data-ttu-id="09e74-139">この手法はファイルやネットワーク操作を使用するときに適しています。</span><span class="sxs-lookup"><span data-stu-id="09e74-139">This is a good technique to use with file or network operations.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09e74-140">`EndInvoke` でブロックするため、ユーザー インターフェイスにサービスを提供するスレッドからは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="09e74-140">Because `EndInvoke` might block, you should never call it from threads that service the user interface.</span></span>

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a><span data-ttu-id="09e74-141">WaitHandle による非同期呼び出しの待機</span><span class="sxs-lookup"><span data-stu-id="09e74-141">Waiting for an Asynchronous Call with WaitHandle</span></span>
 <span data-ttu-id="09e74-142"><xref:System.Threading.WaitHandle> を取得するには、 <xref:System.IAsyncResult.AsyncWaitHandle%2A> によって返される <xref:System.IAsyncResult> の `BeginInvoke`プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="09e74-142">You can obtain a <xref:System.Threading.WaitHandle> by using the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by `BeginInvoke`.</span></span> <span data-ttu-id="09e74-143"><xref:System.Threading.WaitHandle> は非同期呼び出しが完了すると通知され、 <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドを呼び出すことによってこれを待機できます。</span><span class="sxs-lookup"><span data-stu-id="09e74-143">The <xref:System.Threading.WaitHandle> is signaled when the asynchronous call completes, and you can wait for it by calling the <xref:System.Threading.WaitHandle.WaitOne%2A> method.</span></span>

 <span data-ttu-id="09e74-144"><xref:System.Threading.WaitHandle>を使用する場合は、非同期呼び出しの完了前または完了後、 `EndInvoke` を呼び出して結果を取得する前に、追加の処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="09e74-144">If you use a <xref:System.Threading.WaitHandle>, you can perform additional processing before or after the asynchronous call completes, but before calling `EndInvoke` to retrieve the results.</span></span>

> [!NOTE]
> <span data-ttu-id="09e74-145">`EndInvoke`を呼び出す場合、待機ハンドルは自動的に閉じられません。</span><span class="sxs-lookup"><span data-stu-id="09e74-145">The wait handle is not closed automatically when you call `EndInvoke`.</span></span> <span data-ttu-id="09e74-146">待機ハンドルへのすべての参照を解放すると、ガベージ コレクションが待機ハンドルをクリアするときにシステム リソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="09e74-146">If you release all references to the wait handle, system resources are freed when garbage collection reclaims the wait handle.</span></span> <span data-ttu-id="09e74-147">待機ハンドルの使用が終了すると同時にシステム リソースを解放するには、 <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> メソッドを呼び出して破棄します。</span><span class="sxs-lookup"><span data-stu-id="09e74-147">To free the system resources as soon as you are finished using the wait handle, dispose of it by calling the <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="09e74-148">破棄可能なオブジェクトが明示的に破棄されると、ガベージ コレクションはより効率的に動作します。</span><span class="sxs-lookup"><span data-stu-id="09e74-148">Garbage collection works more efficiently when disposable objects are explicitly disposed.</span></span>

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a><span data-ttu-id="09e74-149">非同期呼び出し完了のポーリング</span><span class="sxs-lookup"><span data-stu-id="09e74-149">Polling for Asynchronous Call Completion</span></span>
 <span data-ttu-id="09e74-150"><xref:System.IAsyncResult.IsCompleted%2A> によって返された <xref:System.IAsyncResult> の `BeginInvoke` プロパティを使用して、非同期呼び出しが完了したことを検出できます。</span><span class="sxs-lookup"><span data-stu-id="09e74-150">You can use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by `BeginInvoke` to discover when the asynchronous call completes.</span></span> <span data-ttu-id="09e74-151">この方法は、ユーザー インターフェイスにサービスを提供するスレッドから非同期呼び出しを行う場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="09e74-151">You might do this when making the asynchronous call from a thread that services the user interface.</span></span> <span data-ttu-id="09e74-152">完了をポーリングすると、呼び出し元スレッドは、 <xref:System.Threading.ThreadPool> スレッドで非同期呼び出しを実行しながら、実行を継続できます。</span><span class="sxs-lookup"><span data-stu-id="09e74-152">Polling for completion allows the calling thread to continue executing while the asynchronous call executes on a <xref:System.Threading.ThreadPool> thread.</span></span>

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a><span data-ttu-id="09e74-153">非同期呼び出し完了時のコールバック メソッドの実行</span><span class="sxs-lookup"><span data-stu-id="09e74-153">Executing a Callback Method When an Asynchronous Call Completes</span></span>
 <span data-ttu-id="09e74-154">非同期呼び出しを開始したスレッドが結果を処理するスレッドである必要がない場合は、呼び出しが完了したときにコールバック メソッドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="09e74-154">If the thread that initiates the asynchronous call does not need to be the thread that processes the results, you can execute a callback method when the call completes.</span></span> <span data-ttu-id="09e74-155">コールバック メソッドは <xref:System.Threading.ThreadPool> スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="09e74-155">The callback method is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

 <span data-ttu-id="09e74-156">コールバック メソッドを使用するには、コールバック メソッドを表す `BeginInvoke` デリゲートを <xref:System.AsyncCallback> に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e74-156">To use a callback method, you must pass `BeginInvoke` an <xref:System.AsyncCallback> delegate that represents the callback method.</span></span> <span data-ttu-id="09e74-157">コールバック メソッドで使用される情報を含むオブジェクトを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="09e74-157">You can also pass an object that contains information to be used by the callback method.</span></span> <span data-ttu-id="09e74-158">コールバック メソッドでは、唯一のパラメーターである <xref:System.IAsyncResult>を <xref:System.Runtime.Remoting.Messaging.AsyncResult> オブジェクトにキャストします。</span><span class="sxs-lookup"><span data-stu-id="09e74-158">In the callback method, you can cast the <xref:System.IAsyncResult>, which is the only parameter of the callback method, to an <xref:System.Runtime.Remoting.Messaging.AsyncResult> object.</span></span> <span data-ttu-id="09e74-159">こうすると、 <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> プロパティを使用して、呼び出しを開始するために使用したデリゲートを取得し、 `EndInvoke`を呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="09e74-159">You can then use the <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> property to get the delegate that was used to initiate the call so that you can call `EndInvoke`.</span></span>

 <span data-ttu-id="09e74-160">例に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="09e74-160">Notes on the example:</span></span>

- <span data-ttu-id="09e74-161">`TestMethod` の `threadId` パラメーターは `out` パラメーター (Visual Basic では [`<Out>` `ByRef`) であるため、その入力値が `TestMethod` で使用されることはありません。</span><span class="sxs-lookup"><span data-stu-id="09e74-161">The `threadId` parameter of `TestMethod` is an `out` parameter ([`<Out>` `ByRef` in Visual Basic), so its input value is never used by `TestMethod`.</span></span> <span data-ttu-id="09e74-162">`BeginInvoke` 呼び出しにはダミー変数が渡されます。</span><span class="sxs-lookup"><span data-stu-id="09e74-162">A dummy variable is passed to the `BeginInvoke` call.</span></span> <span data-ttu-id="09e74-163">`threadId` パラメーターが `ref` パラメーター (Visual Basic では`ByRef` ) であった場合、 `BeginInvoke` と `EndInvoke`の両方に渡すことができるように、変数はクラス レベルのフィールドであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="09e74-163">If the `threadId` parameter were a `ref` parameter (`ByRef` in Visual Basic), the variable would have to be a class-level field so that it could be passed to both `BeginInvoke` and `EndInvoke`.</span></span>

- <span data-ttu-id="09e74-164">`BeginInvoke` に渡される状態情報は、コールバック メソッドが出力メッセージを書式指定するために使用する書式指定文字列です。</span><span class="sxs-lookup"><span data-stu-id="09e74-164">The state information that is passed to `BeginInvoke` is a format string, which the callback method uses to format an output message.</span></span> <span data-ttu-id="09e74-165">型 <xref:System.Object>として渡されるため、状態情報を使用するには適切な型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e74-165">Because it is passed as type <xref:System.Object>, the state information must be cast to its proper type before it can be used.</span></span>

- <span data-ttu-id="09e74-166">コールバックは <xref:System.Threading.ThreadPool> スレッドで作成されます。</span><span class="sxs-lookup"><span data-stu-id="09e74-166">The callback is made on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="09e74-167"><xref:System.Threading.ThreadPool> スレッドは、メイン スレッドが終了した場合はアプリケーションの実行を継続しないバックグラウンド スレッドであるため、例で使用するメイン スレッドは、コールバックが終了できるまでスリープする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e74-167"><xref:System.Threading.ThreadPool> threads are background threads, which do not keep the application running if the main thread ends, so the main thread of the example has to sleep long enough for the callback to finish.</span></span>

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a><span data-ttu-id="09e74-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="09e74-168">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="09e74-169">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="09e74-169">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
