---
title: '方法: 初回例外通知を受け取る'
description: CLR が例外ハンドラーを検索する前に、AppDomain クラスの FirstChanceException イベントを使用して、.NET で初回例外通知を取得します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
ms.openlocfilehash: 0b3150a52a68e078d1052a9894bb652ad35027d0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242566"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a><span data-ttu-id="74370-103">方法: 初回例外通知を受け取る</span><span class="sxs-lookup"><span data-stu-id="74370-103">How to: Receive First-Chance Exception Notifications</span></span>

<span data-ttu-id="74370-104"><xref:System.AppDomain> クラスの <xref:System.AppDomain.FirstChanceException>イベントを使用すると、共通言語ランタイムが例外ハンドラーの検索を開始する前に、例外がスローされたことを知らせる通知を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="74370-104">The <xref:System.AppDomain.FirstChanceException> event of the <xref:System.AppDomain> class lets you receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>

 <span data-ttu-id="74370-105">このイベントは、アプリケーション ドメイン レベルで発生します。</span><span class="sxs-lookup"><span data-stu-id="74370-105">The event is raised at the application domain level.</span></span> <span data-ttu-id="74370-106">実行スレッドは複数のアプリケーション ドメインを通過する可能性があるため、あるアプリケーション ドメインでハンドルされない例外が別のアプリケーション ドメインでハンドルされることもあります。</span><span class="sxs-lookup"><span data-stu-id="74370-106">A thread of execution can pass through multiple application domains, so an exception that is unhandled in one application domain could be handled in another application domain.</span></span> <span data-ttu-id="74370-107">通知は、イベントのハンドラーを追加した各アプリケーション ドメインで発生し、いずれかのアプリケーション ドメインで例外がハンドルされるまで続行されます。</span><span class="sxs-lookup"><span data-stu-id="74370-107">The notification occurs in each application domain that has added a handler for the event, until an application domain handles the exception.</span></span>

 <span data-ttu-id="74370-108">ここで紹介するプロシージャと例では、1 つのアプリケーション ドメインを実装する単純なプログラムで初回例外通知を受け取る方法と、作成したアプリケーション ドメインで初回例外通知を受け取る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74370-108">The procedures and examples in this article show how to receive first-chance exception notifications in a simple program that has one application domain, and in an application domain that you create.</span></span>

 <span data-ttu-id="74370-109">複数のアプリケーション ドメインにわたる複雑な例については、<xref:System.AppDomain.FirstChanceException> イベントの例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74370-109">For a more complex example that spans several application domains, see the example for the <xref:System.AppDomain.FirstChanceException> event.</span></span>

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a><span data-ttu-id="74370-110">既定のアプリケーション ドメインで初回例外通知を受け取る</span><span class="sxs-lookup"><span data-stu-id="74370-110">Receiving First-Chance Exception Notifications in the Default Application Domain</span></span>

 <span data-ttu-id="74370-111">次のプロシージャでは、アプリケーションのエントリ ポイントである `Main()`メソッドが既定のアプリケーション ドメインで実行されます。</span><span class="sxs-lookup"><span data-stu-id="74370-111">In the following procedure, the entry point for the application, the `Main()` method, runs in the default application domain.</span></span>

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a><span data-ttu-id="74370-112">既定のアプリケーション ドメインで初回例外通知の動作を確認するには</span><span class="sxs-lookup"><span data-stu-id="74370-112">To demonstrate first-chance exception notifications in the default application domain</span></span>

1. <span data-ttu-id="74370-113">ラムダ関数を使用して <xref:System.AppDomain.FirstChanceException> イベントのイベント ハンドラーを定義し、それをイベントにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="74370-113">Define an event handler for the <xref:System.AppDomain.FirstChanceException> event, using a lambda function, and attach it to the event.</span></span> <span data-ttu-id="74370-114">この例では、イベント ハンドラーによって、イベントが処理されたアプリケーション ドメインの名前と、例外の <xref:System.Exception.Message%2A> プロパティを出力します。</span><span class="sxs-lookup"><span data-stu-id="74370-114">In this example, the event handler prints the name of the application domain where the event was handled and the exception's <xref:System.Exception.Message%2A> property.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2. <span data-ttu-id="74370-115">例外をスローし、それをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="74370-115">Throw an exception and catch it.</span></span> <span data-ttu-id="74370-116">ランタイムが例外ハンドラーを見つける前に、<xref:System.AppDomain.FirstChanceException> イベントが発生し、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="74370-116">Before the runtime locates the exception handler, the <xref:System.AppDomain.FirstChanceException> event is raised and displays a message.</span></span> <span data-ttu-id="74370-117">このメッセージの後に、例外ハンドラーによるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="74370-117">This message is followed by the message that is displayed by the exception handler.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3. <span data-ttu-id="74370-118">例外をスローしますが、それをキャッチしません。</span><span class="sxs-lookup"><span data-stu-id="74370-118">Throw an exception, but do not catch it.</span></span> <span data-ttu-id="74370-119">ランタイムが例外ハンドラーを検索する前に、<xref:System.AppDomain.FirstChanceException> イベントが発生し、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="74370-119">Before the runtime looks for an exception handler, the <xref:System.AppDomain.FirstChanceException> event is raised and displays a message.</span></span> <span data-ttu-id="74370-120">例外ハンドラーがないため、アプリケーションは終了します。</span><span class="sxs-lookup"><span data-stu-id="74370-120">There is no exception handler, so the application terminates.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     <span data-ttu-id="74370-121">このプロシージャの最初の 3 つのステップに示されているコードは、完全なコンソール アプリケーションを形成します。</span><span class="sxs-lookup"><span data-stu-id="74370-121">The code that is shown in the first three steps of this procedure forms a complete console application.</span></span> <span data-ttu-id="74370-122">既定のアプリケーション ドメインの名前は .exe ファイルの名前と拡張子から構成されるため、アプリケーションからの出力は .exe ファイルの名前によって異なります。</span><span class="sxs-lookup"><span data-stu-id="74370-122">The output from the application varies, depending on the name of the .exe file, because the name of the default application domain consists of the name and extension of the .exe file.</span></span> <span data-ttu-id="74370-123">次のサンプル出力を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74370-123">See the following for sample output.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a><span data-ttu-id="74370-124">別のアプリケーション ドメインで初回例外通知を受け取る</span><span class="sxs-lookup"><span data-stu-id="74370-124">Receiving First-Chance Exception Notifications in Another Application Domain</span></span>

 <span data-ttu-id="74370-125">プログラムに複数のアプリケーション ドメインが含まれている場合は、通知を受け取るアプリケーション ドメインを選択できます。</span><span class="sxs-lookup"><span data-stu-id="74370-125">If your program contains more than one application domain, you can choose which application domains receive notifications.</span></span>

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a><span data-ttu-id="74370-126">作成したアプリケーション ドメインで初回例外通知を受け取るには</span><span class="sxs-lookup"><span data-stu-id="74370-126">To receive first-chance exception notifications in an application domain that you create</span></span>

1. <span data-ttu-id="74370-127"><xref:System.AppDomain.FirstChanceException> イベントのイベント ハンドラーを定義します。</span><span class="sxs-lookup"><span data-stu-id="74370-127">Define an event handler for the <xref:System.AppDomain.FirstChanceException> event.</span></span> <span data-ttu-id="74370-128">この例では、`static` メソッド (Visual Basic では `Shared` メソッド) を使用して、イベントが処理されたアプリケーション ドメインの名前と、例外の <xref:System.Exception.Message%2A> プロパティを出力します。</span><span class="sxs-lookup"><span data-stu-id="74370-128">This example uses a `static` method (`Shared` method in Visual Basic) that prints the name of the application domain where the event was handled and the exception's <xref:System.Exception.Message%2A> property.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2. <span data-ttu-id="74370-129">アプリケーション ドメインを作成し、そのアプリケーション ドメインの <xref:System.AppDomain.FirstChanceException> イベントにイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="74370-129">Create an application domain and add the event handler to the <xref:System.AppDomain.FirstChanceException> event for that application domain.</span></span> <span data-ttu-id="74370-130">この例では、アプリケーション ドメインの名前は `AD1` です。</span><span class="sxs-lookup"><span data-stu-id="74370-130">In this example, the application domain is named `AD1`.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     <span data-ttu-id="74370-131">既定のアプリケーション ドメインでも、同じようにこのイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="74370-131">You can handle this event in the default application domain in the same way.</span></span> <span data-ttu-id="74370-132">既定のアプリケーション ドメインへの参照を取得するには、`static` (Visual Basic では `Shared`) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> プロパティを `Main()` で使用します。</span><span class="sxs-lookup"><span data-stu-id="74370-132">Use the `static` (`Shared` in Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property in `Main()` to get a reference to the default application domain.</span></span>

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a><span data-ttu-id="74370-133">アプリケーション ドメインで初回例外通知の動作を確認するには</span><span class="sxs-lookup"><span data-stu-id="74370-133">To demonstrate first-chance exception notifications in the application domain</span></span>

1. <span data-ttu-id="74370-134">前のプロシージャで作成したアプリケーション ドメインに `Worker` オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="74370-134">Create a `Worker` object in the application domain that you created in the previous procedure.</span></span> <span data-ttu-id="74370-135">`Worker` クラスは、パブリックで、<xref:System.MarshalByRefObject> から派生する必要があります。この記事の最後にある完全な例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74370-135">The `Worker` class must be public, and must derive from <xref:System.MarshalByRefObject>, as shown in the complete example at the end of this article.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2. <span data-ttu-id="74370-136">例外をスローする `Worker` オブジェクトのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="74370-136">Call a method of the `Worker` object that throws an exception.</span></span> <span data-ttu-id="74370-137">この例では、`Thrower` メソッドが 2 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="74370-137">In this example, the `Thrower` method is called twice.</span></span> <span data-ttu-id="74370-138">1 回目のメソッド引数は `true` であるため、メソッドは自身の例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="74370-138">The first time, the method argument is `true`, which causes the method to catch its own exception.</span></span> <span data-ttu-id="74370-139">2 回目の引数は `false` です。この場合、`Main()` メソッドが既定のアプリケーション ドメインで例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="74370-139">The second time, the argument is `false`, and the `Main()` method catches the exception in the default application domain.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3. <span data-ttu-id="74370-140">`Thrower` メソッドにコードを追加して、メソッドが自身の例外をハンドルするかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="74370-140">Place code in the `Thrower` method to control whether the method handles its own exception.</span></span>

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a><span data-ttu-id="74370-141">例</span><span class="sxs-lookup"><span data-stu-id="74370-141">Example</span></span>

 <span data-ttu-id="74370-142">次の例では、`AD1` という名前のアプリケーション ドメインを作成し、このアプリケーション ドメインの <xref:System.AppDomain.FirstChanceException> イベントにイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="74370-142">The following example creates an application domain named `AD1` and adds an event handler to the application domain's <xref:System.AppDomain.FirstChanceException> event.</span></span> <span data-ttu-id="74370-143">この例では、アプリケーション ドメインに `Worker` クラスのインスタンスを作成し、`Thrower` という名前のメソッドを呼び出します。このメソッドにより、<xref:System.ArgumentException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="74370-143">The example creates an instance of the `Worker` class in the application domain, and calls a method named `Thrower` that throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="74370-144">メソッドは、引数の値に応じて、例外をキャッチするか、例外のハンドルに失敗します。</span><span class="sxs-lookup"><span data-stu-id="74370-144">Depending on the value of its argument, the method either catches the exception or fails to handle it.</span></span>

 <span data-ttu-id="74370-145">`Thrower` メソッドが `AD1` で例外をスローするたびに、`AD1` で <xref:System.AppDomain.FirstChanceException> イベントが発生し、イベント ハンドラーによりメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="74370-145">Each time the `Thrower` method throws an exception in `AD1`, the <xref:System.AppDomain.FirstChanceException> event is raised in `AD1`, and the event handler displays a message.</span></span> <span data-ttu-id="74370-146">次に、ランタイムによって例外ハンドラーが検索されます。</span><span class="sxs-lookup"><span data-stu-id="74370-146">The runtime then looks for an exception handler.</span></span> <span data-ttu-id="74370-147">最初のケースでは、例外ハンドラーは `AD1` で見つかります。</span><span class="sxs-lookup"><span data-stu-id="74370-147">In the first case, the exception handler is found in `AD1`.</span></span> <span data-ttu-id="74370-148">2 番目のケースでは、例外は `AD1` でハンドルされず、代わりに既定のアプリケーション ドメインでキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="74370-148">In the second case, the exception is unhandled in `AD1`, and instead is caught in the default application domain.</span></span>

> [!NOTE]
> <span data-ttu-id="74370-149">既定のアプリケーション ドメインの名前は、実行可能ファイルの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="74370-149">The name of the default application domain is the same as the name of the executable.</span></span>

 <span data-ttu-id="74370-150">既定のアプリケーション ドメインに <xref:System.AppDomain.FirstChanceException> イベントのハンドラーを追加すると、既定のアプリケーション ドメインが例外をハンドルする前に、イベントが発生して処理されます。</span><span class="sxs-lookup"><span data-stu-id="74370-150">If you add a handler for the <xref:System.AppDomain.FirstChanceException> event to the default application domain, the event is raised and handled before the default application domain handles the exception.</span></span> <span data-ttu-id="74370-151">これを確認するには、`Main()` の先頭に C# コード `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (Visual Basic では `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="74370-151">To see this, add the C# code `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (in Visual Basic, `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) at the beginning of `Main()`.</span></span>

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="see-also"></a><span data-ttu-id="74370-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="74370-152">See also</span></span>

- <xref:System.AppDomain.FirstChanceException>
