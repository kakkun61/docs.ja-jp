---
title: '方法 : イベントベースの非同期パターンをサポートするコンポーネントを実装する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
ms.openlocfilehash: 2294379d37d4cd9e7fae494a6548561258743d74
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888881"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a><span data-ttu-id="839fc-102">方法 : イベントベースの非同期パターンをサポートするコンポーネントを実装する</span><span class="sxs-lookup"><span data-stu-id="839fc-102">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="839fc-103">顕著な遅延が発生する可能性がある操作を伴うクラスを作成する場合は、[イベント ベースの非同期パターン](event-based-asynchronous-pattern-overview.md)を実装することによって、非同期機能を与えることを検討します。</span><span class="sxs-lookup"><span data-stu-id="839fc-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="839fc-104">このチュートリアルでは、イベント ベースの非同期パターンを実装するコンポーネントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="839fc-104">This walkthrough illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="839fc-105">これは、<xref:System.ComponentModel?displayProperty=nameWithType> 名前空間のヘルパー クラスを使用して実装します。これにより、コンポーネントは任意のアプリケーション モデルで正常に動作します (ASP.NET、コンソール アプリケーション、Windows フォーム アプリケーションなど)。</span><span class="sxs-lookup"><span data-stu-id="839fc-105">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model, including ASP.NET, Console applications and Windows Forms applications.</span></span> <span data-ttu-id="839fc-106">また、このコンポーネントは、<xref:System.Windows.Forms.PropertyGrid> コントロールや独自のカスタム デザイナーで設計可能です。</span><span class="sxs-lookup"><span data-stu-id="839fc-106">This component is also designable with a <xref:System.Windows.Forms.PropertyGrid> control and your own custom designers.</span></span>  
  
 <span data-ttu-id="839fc-107">このチュートリアルを完了すると、素数を非同期に計算するアプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-107">When you are through, you will have an application that computes prime numbers asynchronously.</span></span> <span data-ttu-id="839fc-108">アプリケーションには、メイン ユーザー インターフェイス (UI) スレッドと各素数の計算用のスレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="839fc-108">Your application will have a main user interface (UI) thread and a thread for each prime number calculation.</span></span> <span data-ttu-id="839fc-109">大きな数が素数かどうかを調べるにはかなりの時間がかかることがありますが、この遅延によってメイン UI スレッドが中断されることはなく、計算中もフォームは応答性を維持します。</span><span class="sxs-lookup"><span data-stu-id="839fc-109">Although testing whether a large number is prime can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculations.</span></span> <span data-ttu-id="839fc-110">いくつでも好きなだけ計算を同時に実行し、保留中の計算を選択的に取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="839fc-110">You will be able to run as many calculations as you like concurrently and selectively cancel pending calculations.</span></span>  
  
 <span data-ttu-id="839fc-111">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="839fc-111">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="839fc-112">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="839fc-112">Creating the Component</span></span>  
  
- <span data-ttu-id="839fc-113">パブリックの非同期イベントとデリゲートの定義</span><span class="sxs-lookup"><span data-stu-id="839fc-113">Defining Public Asynchronous Events and Delegates</span></span>  
  
- <span data-ttu-id="839fc-114">プライベート デリゲートの定義</span><span class="sxs-lookup"><span data-stu-id="839fc-114">Defining Private Delegates</span></span>  
  
- <span data-ttu-id="839fc-115">パブリック イベントの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-115">Implementing Public Events</span></span>  
  
- <span data-ttu-id="839fc-116">完了メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-116">Implementing the Completion Method</span></span>  
  
- <span data-ttu-id="839fc-117">ワーカー メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-117">Implementing the Worker Methods</span></span>  
  
- <span data-ttu-id="839fc-118">開始メソッドとキャンセル メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-118">Implementing Start and Cancel Methods</span></span>  
  
 <span data-ttu-id="839fc-119">このトピックのコードを単一のリストとしてコピーするには、「[方法 : イベントベースの非同期パターンのクライアントを実装する](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="839fc-119">To copy the code in this topic as a single listing, see [How to: Implement a Client of the Event-based Asynchronous Pattern](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="creating-the-component"></a><span data-ttu-id="839fc-120">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="839fc-120">Creating the Component</span></span>  
 <span data-ttu-id="839fc-121">最初に、イベント ベースの非同期パターンを実装するコンポーネントを作成します。</span><span class="sxs-lookup"><span data-stu-id="839fc-121">The first step is to create the component that will implement the Event-based Asynchronous Pattern.</span></span>  
  
### <a name="to-create-the-component"></a><span data-ttu-id="839fc-122">コンポーネントを作成するには</span><span class="sxs-lookup"><span data-stu-id="839fc-122">To create the component</span></span>  
  
- <span data-ttu-id="839fc-123"><xref:System.ComponentModel.Component> を継承する `PrimeNumberCalculator` というクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="839fc-123">Create a class called `PrimeNumberCalculator` that inherits from <xref:System.ComponentModel.Component>.</span></span>  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a><span data-ttu-id="839fc-124">パブリックの非同期イベントとデリゲートの定義</span><span class="sxs-lookup"><span data-stu-id="839fc-124">Defining Public Asynchronous Events and Delegates</span></span>  
 <span data-ttu-id="839fc-125">コンポーネントは、イベントを使ってクライアントと通信します。</span><span class="sxs-lookup"><span data-stu-id="839fc-125">Your component communicates to clients using events.</span></span> <span data-ttu-id="839fc-126">_MethodName_**Completed** イベントは非同期タスクの完了をクライアントに通知し、 _MethodName_**ProgressChanged** イベントは非同期タスクの進行状況をクライアントに通知します。</span><span class="sxs-lookup"><span data-stu-id="839fc-126">The _MethodName_**Completed** event alerts clients to the completion of an asynchronous task, and the _MethodName_**ProgressChanged** event informs clients of the progress of an asynchronous task.</span></span>  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a><span data-ttu-id="839fc-127">コンポーネントのクライアント用の非同期イベントを定義するには:</span><span class="sxs-lookup"><span data-stu-id="839fc-127">To define asynchronous events for clients of your component:</span></span>  
  
1. <span data-ttu-id="839fc-128">ファイルの先頭で <xref:System.Threading?displayProperty=nameWithType> および <xref:System.Collections.Specialized?displayProperty=nameWithType> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="839fc-128">Import the <xref:System.Threading?displayProperty=nameWithType> and <xref:System.Collections.Specialized?displayProperty=nameWithType> namespaces at the top of your file.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#11)]  
  
2. <span data-ttu-id="839fc-129">`PrimeNumberCalculator` クラスの定義の前で、進行状況イベントと完了イベントのデリゲートを宣言します。</span><span class="sxs-lookup"><span data-stu-id="839fc-129">Before the `PrimeNumberCalculator` class definition, declare delegates for progress and completion events.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#7)]  
  
3. <span data-ttu-id="839fc-130">`PrimeNumberCalculator` クラスの定義で、進行状況と完了をクライアントに報告するイベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="839fc-130">In the `PrimeNumberCalculator` class definition, declare events for reporting progress and completion to clients.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#8)]  
  
4. <span data-ttu-id="839fc-131">`PrimeNumberCalculator` クラスの定義の後で、`CalculatePrimeCompleted` イベントに対するクライアントのイベント ハンドラーに各計算の結果を報告するための `CalculatePrimeCompletedEventArgs` クラスを派生します。</span><span class="sxs-lookup"><span data-stu-id="839fc-131">After the `PrimeNumberCalculator` class definition, derive the `CalculatePrimeCompletedEventArgs` class for reporting the outcome of each calculation to the client's event handler for the `CalculatePrimeCompleted`.event.</span></span> <span data-ttu-id="839fc-132">`AsyncCompletedEventArgs` プロパティに加えて、このクラスにより、クライアントはテストされた値、その値が素数かどうか、素数でない場合は最初の約数を知ることができます。</span><span class="sxs-lookup"><span data-stu-id="839fc-132">In addition to the `AsyncCompletedEventArgs` properties, this class enables the client to determine what number was tested, whether it is prime, and what the first divisor is if it is not prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a><span data-ttu-id="839fc-133">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="839fc-133">Checkpoint</span></span>  
 <span data-ttu-id="839fc-134">この段階で、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="839fc-134">At this point, you can build the component.</span></span>  
  
### <a name="to-test-your-component"></a><span data-ttu-id="839fc-135">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="839fc-135">To test your component</span></span>  
  
- <span data-ttu-id="839fc-136">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="839fc-136">Compile the component.</span></span>  
  
     <span data-ttu-id="839fc-137">コンパイラの警告が 2 つ表示されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-137">You will receive two compiler warnings:</span></span>  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     <span data-ttu-id="839fc-138">これらの警告は次のセクションでなくなります。</span><span class="sxs-lookup"><span data-stu-id="839fc-138">These warnings will be cleared in the next section.</span></span>  
  
## <a name="defining-private-delegates"></a><span data-ttu-id="839fc-139">プライベート デリゲートの定義</span><span class="sxs-lookup"><span data-stu-id="839fc-139">Defining Private Delegates</span></span>  
 <span data-ttu-id="839fc-140">`PrimeNumberCalculator` コンポーネントの非同期の側面は、<xref:System.Threading.SendOrPostCallback> と呼ばれる特別なデリゲートを使って内部的に実装されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-140">The asynchronous aspects of the `PrimeNumberCalculator` component are implemented internally with a special delegate known as a <xref:System.Threading.SendOrPostCallback>.</span></span> <span data-ttu-id="839fc-141"><xref:System.Threading.SendOrPostCallback> は、<xref:System.Threading.ThreadPool> スレッドで実行するコールバック メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="839fc-141">A <xref:System.Threading.SendOrPostCallback> represents a callback method that executes on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="839fc-142">コールバック メソッドは、<xref:System.Object> 型のパラメーターを 1 つ受け取るシグネチャを持つ必要があります。つまり、ラッパー クラスでデリゲートに状態を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="839fc-142">The callback method must have a signature that takes a single parameter of type <xref:System.Object>, which means you will need to pass state among delegates in a wrapper class.</span></span> <span data-ttu-id="839fc-143">詳細については、<xref:System.Threading.SendOrPostCallback> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="839fc-143">For more information, see <xref:System.Threading.SendOrPostCallback>.</span></span>  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a><span data-ttu-id="839fc-144">コンポーネントの内部非同期動作を実装するには:</span><span class="sxs-lookup"><span data-stu-id="839fc-144">To implement your component's internal asynchronous behavior:</span></span>  
  
1. <span data-ttu-id="839fc-145">`PrimeNumberCalculator` クラスで <xref:System.Threading.SendOrPostCallback> デリゲートを宣言して作成します。</span><span class="sxs-lookup"><span data-stu-id="839fc-145">Declare and create the <xref:System.Threading.SendOrPostCallback> delegates in the `PrimeNumberCalculator` class.</span></span> <span data-ttu-id="839fc-146">`InitializeDelegates` という名前のユーティリティ メソッドで <xref:System.Threading.SendOrPostCallback> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="839fc-146">Create the <xref:System.Threading.SendOrPostCallback> objects in a utility method called `InitializeDelegates`.</span></span>  
  
     <span data-ttu-id="839fc-147">2 つのデリゲートが必要です。1 つはクライアントに進行状況を報告するためのもので、もう 1 つはクライアントに完了を報告するためのものです。</span><span class="sxs-lookup"><span data-stu-id="839fc-147">You will need two delegates: one for reporting progress to the client, and one for reporting completion to the client.</span></span>  

     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#20)]  
  
2. <span data-ttu-id="839fc-148">コンポーネントのコンストラクターで `InitializeDelegates` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="839fc-148">Call the `InitializeDelegates` method in your component's constructor.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#21)]  
  
3. <span data-ttu-id="839fc-149">実際の処理を非同期に行う `PrimeNumberCalculator` クラスのデリゲートを宣言します。</span><span class="sxs-lookup"><span data-stu-id="839fc-149">Declare a delegate in the `PrimeNumberCalculator` class that handles the actual work to be done asynchronously.</span></span> <span data-ttu-id="839fc-150">このデリゲートは、数値が素数かどうかをテストするワーカー メソッドをラップします。</span><span class="sxs-lookup"><span data-stu-id="839fc-150">This delegate wraps the worker method that tests whether a number is prime.</span></span> <span data-ttu-id="839fc-151">デリゲートは <xref:System.ComponentModel.AsyncOperation> パラメーターを受け取ります。このパラメーターは、非同期操作の有効期間を追跡するために使われます。</span><span class="sxs-lookup"><span data-stu-id="839fc-151">The delegate takes an <xref:System.ComponentModel.AsyncOperation> parameter, which will be used to track the lifetime of the asynchronous operation.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#22)]  
  
4. <span data-ttu-id="839fc-152">保留中の非同期操作の有効期間を管理するためのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="839fc-152">Create a collection for managing lifetimes of pending asynchronous operations.</span></span> <span data-ttu-id="839fc-153">クライアントは操作の実行と完了を追跡する手段が必要であり、この追跡は、クライアントが非同期メソッドを呼び出すときに渡す必要のある一意のトークン (タスク ID) を使って行われます。</span><span class="sxs-lookup"><span data-stu-id="839fc-153">The client needs a way to track operations as they are executed and completed, and this tracking is done by requiring the client to pass a unique token, or task ID, when the client makes the call to the asynchronous method.</span></span> <span data-ttu-id="839fc-154">`PrimeNumberCalculator` コンポーネントは、タスク ID を対応する呼び出しと関連付けることによって、各呼び出しの追跡を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="839fc-154">The `PrimeNumberCalculator` component must keep track of each call by associating the task ID with its corresponding invocation.</span></span> <span data-ttu-id="839fc-155">クライアントが一意でないタスク ID を渡した場合、`PrimeNumberCalculator` コンポーネントは例外を生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="839fc-155">If the client passes a task ID that is not unique, the `PrimeNumberCalculator` component must raise an exception.</span></span>  
  
     <span data-ttu-id="839fc-156">`PrimeNumberCalculator` コンポーネントは、<xref:System.Collections.Specialized.HybridDictionary> という特別なコレクション クラスを使ってタスク ID を追跡します。</span><span class="sxs-lookup"><span data-stu-id="839fc-156">The `PrimeNumberCalculator` component keeps track of task ID by using a special collection class called a <xref:System.Collections.Specialized.HybridDictionary>.</span></span> <span data-ttu-id="839fc-157">クラスの定義で、`userTokenToLifetime` という名前の <xref:System.Collections.Specialized.HybridDictionary> を作成します。</span><span class="sxs-lookup"><span data-stu-id="839fc-157">In the class definition, create a <xref:System.Collections.Specialized.HybridDictionary> called `userTokenToLifetime`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a><span data-ttu-id="839fc-158">パブリック イベントの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-158">Implementing Public Events</span></span>  
 <span data-ttu-id="839fc-159">イベント ベースの非同期パターンを実装するコンポーネントは、イベントを使ってクライアントに通信します。</span><span class="sxs-lookup"><span data-stu-id="839fc-159">Components that implement the Event-based Asynchronous Pattern communicate to clients using events.</span></span> <span data-ttu-id="839fc-160">これらのイベントは、<xref:System.ComponentModel.AsyncOperation> クラスを使って適切なスレッドで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-160">These events are invoked on the proper thread with the help of the <xref:System.ComponentModel.AsyncOperation> class.</span></span>  
  
### <a name="to-raise-events-to-your-components-clients"></a><span data-ttu-id="839fc-161">コンポーネントのクライアントに対するイベントを生成するには:</span><span class="sxs-lookup"><span data-stu-id="839fc-161">To raise events to your component's clients:</span></span>  
  
1. <span data-ttu-id="839fc-162">クライアントに報告するためのパブリック イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-162">Implement public events for reporting to clients.</span></span> <span data-ttu-id="839fc-163">進行状況報告用のイベントと、完了報告用のイベントが必要です。</span><span class="sxs-lookup"><span data-stu-id="839fc-163">You will need an event for reporting progress and one for reporting completion.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a><span data-ttu-id="839fc-164">完了メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-164">Implementing the Completion Method</span></span>  
 <span data-ttu-id="839fc-165">完了デリゲートは、非同期操作が正常完了、エラー、またはキャンセルで終了すると、基になっているフリー スレッドの非同期動作が呼び出すメソッドです。</span><span class="sxs-lookup"><span data-stu-id="839fc-165">The completion delegate is the method that the underlying, free-threaded asynchronous behavior will invoke when the asynchronous operation ends by successful completion, error, or cancellation.</span></span> <span data-ttu-id="839fc-166">この呼び出しは、任意のスレッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="839fc-166">This invocation happens on an arbitrary thread.</span></span>  
  
 <span data-ttu-id="839fc-167">このメソッドでは、クライアントのタスク ID が一意のクライアント トークンの内部コレクションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-167">This method is where the client's task ID is removed from the internal collection of unique client tokens.</span></span> <span data-ttu-id="839fc-168">また、このメソッドは、対応する <xref:System.ComponentModel.AsyncOperation> で <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> メソッドを呼び出すことにより、特定の非同期操作の有効期間を終了させます。</span><span class="sxs-lookup"><span data-stu-id="839fc-168">This method also ends the lifetime of a particular asynchronous operation by calling the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method on the corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="839fc-169">この呼び出しでは、アプリケーション モデルの適切なスレッドで完了イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="839fc-169">This call raises the completion event on the thread that is appropriate for the application model.</span></span> <span data-ttu-id="839fc-170"><xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> メソッドが呼び出された後、<xref:System.ComponentModel.AsyncOperation> のこのインスタンスは使えなくなり、それ以降にこれを使おうとするとすべて例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="839fc-170">After the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method is called, this instance of <xref:System.ComponentModel.AsyncOperation> can no longer be used, and any subsequent attempts to use it will throw an exception.</span></span>  
  
 <span data-ttu-id="839fc-171">`CompletionMethod` のシグネチャは、非同期操作の結果を記述するために必要なすべての状態を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="839fc-171">The `CompletionMethod` signature must hold all state necessary to describe the outcome of the asynchronous operation.</span></span> <span data-ttu-id="839fc-172">この特定の非同期操作によってテストされた値の状態、その値が素数かどうか、素数の場合は最初の約数を保持しています。</span><span class="sxs-lookup"><span data-stu-id="839fc-172">It holds state for the number that was tested by this particular asynchronous operation, whether the number is prime, and the value of its first divisor if it is not a prime number.</span></span> <span data-ttu-id="839fc-173">また、発生した例外を記述する状態、およびこの特定のタスクに対応する <xref:System.ComponentModel.AsyncOperation> も保持します。</span><span class="sxs-lookup"><span data-stu-id="839fc-173">It also holds state describing any exception that occurred, and the <xref:System.ComponentModel.AsyncOperation> corresponding to this particular task.</span></span>  
  
### <a name="to-complete-an-asynchronous-operation"></a><span data-ttu-id="839fc-174">非同期操作を完了するには:</span><span class="sxs-lookup"><span data-stu-id="839fc-174">To complete an asynchronous operation:</span></span>  
  
- <span data-ttu-id="839fc-175">完了メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-175">Implement the completion method.</span></span> <span data-ttu-id="839fc-176">このメソッドは 6 つのパラメーターを受け取り、それを使って、クライアントの `CalculatePrimeCompletedEventHandler` によってクライアントに返される `CalculatePrimeCompletedEventArgs` を設定します。</span><span class="sxs-lookup"><span data-stu-id="839fc-176">It takes six parameters, which it uses to populate a `CalculatePrimeCompletedEventArgs` that is returned to the client through the client's `CalculatePrimeCompletedEventHandler`.</span></span> <span data-ttu-id="839fc-177">また、クライアントのタスク ID トークンを内部コレクションから削除し、<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> を呼び出して非同期操作の有効期間を終了します。</span><span class="sxs-lookup"><span data-stu-id="839fc-177">It removes the client's task ID token from the internal collection, and it ends the asynchronous operation's lifetime with a call to <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>.</span></span> <span data-ttu-id="839fc-178"><xref:System.ComponentModel.AsyncOperation> は、アプリケーション モデルに適したスレッドまたはコンテキストへの呼び出しをマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="839fc-178">The <xref:System.ComponentModel.AsyncOperation> marshals the call to the thread or context that is appropriate for the application model.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a><span data-ttu-id="839fc-179">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="839fc-179">Checkpoint</span></span>  
 <span data-ttu-id="839fc-180">この段階で、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="839fc-180">At this point, you can build the component.</span></span>  
  
### <a name="to-test-your-component"></a><span data-ttu-id="839fc-181">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="839fc-181">To test your component</span></span>  
  
- <span data-ttu-id="839fc-182">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="839fc-182">Compile the component.</span></span>  
  
     <span data-ttu-id="839fc-183">コンパイラの警告が 1 つ表示されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-183">You will receive one compiler warning:</span></span>  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     <span data-ttu-id="839fc-184">この警告は次のセクションで解決されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-184">This warning will be resolved in the next section.</span></span>  
  
## <a name="implementing-the-worker-methods"></a><span data-ttu-id="839fc-185">ワーカー メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-185">Implementing the Worker Methods</span></span>  
 <span data-ttu-id="839fc-186">ここまでで、`PrimeNumberCalculator` コンポーネントをサポートする非同期コードを実装できました。</span><span class="sxs-lookup"><span data-stu-id="839fc-186">So far, you have implemented the supporting asynchronous code for the `PrimeNumberCalculator` component.</span></span> <span data-ttu-id="839fc-187">次に、実際の処理を行うコードを実装できます。</span><span class="sxs-lookup"><span data-stu-id="839fc-187">Now you can implement the code that does the actual work.</span></span> <span data-ttu-id="839fc-188">3 つのメソッド `CalculateWorker`、`BuildPrimeNumberList`、`IsPrime` を実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-188">You will implement three methods: `CalculateWorker`, `BuildPrimeNumberList`, and `IsPrime`.</span></span> <span data-ttu-id="839fc-189">また、`BuildPrimeNumberList` と `IsPrime` は、Sieve of Eratosthenes と呼ばれるよく知られたアルゴリズムを構成します。これは、テストする数値の平方根までのすべての素数を調べることで、その数値が素数かどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="839fc-189">Together, `BuildPrimeNumberList` and `IsPrime` comprise a well-known algorithm called the Sieve of Eratosthenes, which determines if a number is prime by finding all the prime numbers up to the square root of the test number.</span></span> <span data-ttu-id="839fc-190">平方根までに約数が見つからない場合、テスト対象の値は素数です。</span><span class="sxs-lookup"><span data-stu-id="839fc-190">If no divisors are found by that point, the test number is prime.</span></span>  
  
 <span data-ttu-id="839fc-191">このコンポーネントが最大限の効率性で作成されているとしたら、異なるテスト数値のさまざまな呼び出しによって検出されたすべての素数を記憶しています。</span><span class="sxs-lookup"><span data-stu-id="839fc-191">If this component were written for maximum efficiency, it would remember all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="839fc-192">また、2、3、5 などの自明の約数もチェックします。</span><span class="sxs-lookup"><span data-stu-id="839fc-192">It would also check for trivial divisors like 2, 3, and 5.</span></span> <span data-ttu-id="839fc-193">ただし、この例の目的は時間のかかる操作を非同期に実行する方法を示すことなので、これらの最適化は自習のために残しておきます。</span><span class="sxs-lookup"><span data-stu-id="839fc-193">The intent of this example is to demonstrate how time-consuming operations can be executed asynchronously, however, so these optimizations are left as an exercise for you.</span></span>  
  
 <span data-ttu-id="839fc-194">`CalculateWorker` メソッドはデリゲートにラップされており、`BeginInvoke` の呼び出しとは非同期に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-194">The `CalculateWorker` method is wrapped in a delegate and is invoked asynchronously with a call to `BeginInvoke`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="839fc-195">進行状況の報告は、`BuildPrimeNumberList` メソッドで実装されています。</span><span class="sxs-lookup"><span data-stu-id="839fc-195">Progress reporting is implemented in the `BuildPrimeNumberList` method.</span></span> <span data-ttu-id="839fc-196">高速なコンピューターでは、`ProgressChanged` イベントが立て続けに発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="839fc-196">On fast computers, `ProgressChanged` events can be raised in rapid succession.</span></span> <span data-ttu-id="839fc-197">これらのイベントが生成されるクライアント スレッドは、このような状況を処理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="839fc-197">The client thread, on which these events are raised, must be able to handle this situation.</span></span> <span data-ttu-id="839fc-198">ユーザー インターフェイスのコードがメッセージであふれ、処理が追いつかなくなり、応答しなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="839fc-198">User interface code may be flooded with messages and unable to keep up, resulting in unresponsiveness.</span></span> <span data-ttu-id="839fc-199">この状況を処理するユーザー インターフェイスの例については、「[方法: イベントベースの非同期パターンのクライアントを実装する](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="839fc-199">For an example user interface that handles this situation, see [How to: Implement a Client of the Event-based Asynchronous Pattern](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a><span data-ttu-id="839fc-200">素数の計算を非同期に実行するには:</span><span class="sxs-lookup"><span data-stu-id="839fc-200">To execute the prime number calculation asynchronously:</span></span>  
  
1. <span data-ttu-id="839fc-201">`TaskCanceled` ユーティリティ メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-201">Implement the `TaskCanceled` utility method.</span></span> <span data-ttu-id="839fc-202">このメソッドは、タスク有効期間コレクションで指定されたタスク ID をチェックし、タスク ID が見つからない場合は `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="839fc-202">This checks the task lifetime collection for the given task ID, and returns `true` if the task ID is not found.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#32)]  
  
2. <span data-ttu-id="839fc-203">`CalculateWorker` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-203">Implement the `CalculateWorker` method.</span></span> <span data-ttu-id="839fc-204">このメソッドは、テストする数と <xref:System.ComponentModel.AsyncOperation> の 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="839fc-204">It takes two parameters: a number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#27)]  
  
3. <span data-ttu-id="839fc-205">`BuildPrimeNumberList`を実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-205">Implement `BuildPrimeNumberList`.</span></span> <span data-ttu-id="839fc-206">このメソッドは、テストする数と <xref:System.ComponentModel.AsyncOperation> の 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="839fc-206">It takes two parameters: the number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="839fc-207"><xref:System.ComponentModel.AsyncOperation> を使って、進行状況とインクリメンタルな結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="839fc-207">It uses the <xref:System.ComponentModel.AsyncOperation> to report progress and incremental results.</span></span> <span data-ttu-id="839fc-208">これにより、アプリケーション モデルの適切なスレッドまたはコンテキストで、クライアントのイベント ハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-208">This assures that the client's event handlers are called on the proper thread or context for the application model.</span></span> <span data-ttu-id="839fc-209">`BuildPrimeNumberList` は、素数を見つけると、`ProgressChanged` イベントに対するクライアントのイベント ハンドラーに、インクリメンタルな結果としてこれを報告します。</span><span class="sxs-lookup"><span data-stu-id="839fc-209">When `BuildPrimeNumberList` finds a prime number, it reports this as an incremental result to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="839fc-210">これには <xref:System.ComponentModel.ProgressChangedEventArgs> から派生した `CalculatePrimeProgressChangedEventArgs` という名前のクラスが必要であり、このクラスには `LatestPrimeNumber` という名前の追加プロパティが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="839fc-210">This requires a class derived from <xref:System.ComponentModel.ProgressChangedEventArgs>, called `CalculatePrimeProgressChangedEventArgs`, which has one added property called `LatestPrimeNumber`.</span></span>  
  
     <span data-ttu-id="839fc-211">`BuildPrimeNumberList` メソッドは `TaskCanceled` メソッドも定期的に呼び出し、このメソッドが `true` を返すと終了します。</span><span class="sxs-lookup"><span data-stu-id="839fc-211">The `BuildPrimeNumberList` method also periodically calls the `TaskCanceled` method and exits if the method returns `true`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#5)]  
  
4. <span data-ttu-id="839fc-212">`IsPrime`を実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-212">Implement `IsPrime`.</span></span> <span data-ttu-id="839fc-213">このメソッドは、既知の素数のリスト、テスト対象の数、および見つかった最初の約数の出力パラメーターの、3 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="839fc-213">It takes three parameters: a list of known prime numbers, the number to test, and an output parameter for the first divisor found.</span></span> <span data-ttu-id="839fc-214">素数のリストを基に、テスト対象の数が素数かどうかを特定します。</span><span class="sxs-lookup"><span data-stu-id="839fc-214">Given the list of prime numbers, it determines if the test number is prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#28)]  
  
5. <span data-ttu-id="839fc-215"><xref:System.ComponentModel.ProgressChangedEventArgs> から `CalculatePrimeProgressChangedEventArgs` を派生します。</span><span class="sxs-lookup"><span data-stu-id="839fc-215">Derive `CalculatePrimeProgressChangedEventArgs` from <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span> <span data-ttu-id="839fc-216">このクラスは、`ProgressChanged` イベントに対するクライアントのイベント ハンドラーにインクリメンタルな結果を報告するために必要です。</span><span class="sxs-lookup"><span data-stu-id="839fc-216">This class is necessary for reporting incremental results to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="839fc-217">`LatestPrimeNumber` という名前の追加プロパティが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="839fc-217">It has one added property called `LatestPrimeNumber`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a><span data-ttu-id="839fc-218">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="839fc-218">Checkpoint</span></span>  
 <span data-ttu-id="839fc-219">この段階で、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="839fc-219">At this point, you can build the component.</span></span>  
  
### <a name="to-test-your-component"></a><span data-ttu-id="839fc-220">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="839fc-220">To test your component</span></span>  
  
- <span data-ttu-id="839fc-221">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="839fc-221">Compile the component.</span></span>  
  
     <span data-ttu-id="839fc-222">残っているのは、非同期操作を開始およびキャンセルするメソッドである `CalculatePrimeAsync` と `CancelAsync` です。</span><span class="sxs-lookup"><span data-stu-id="839fc-222">All that remains to be written are the methods to start and cancel asynchronous operations, `CalculatePrimeAsync` and `CancelAsync`.</span></span>  
  
## <a name="implementing-the-start-and-cancel-methods"></a><span data-ttu-id="839fc-223">開始メソッドとキャンセル メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="839fc-223">Implementing the Start and Cancel Methods</span></span>  
 <span data-ttu-id="839fc-224">ラップするデリゲートで `BeginInvoke` を呼び出すことにより、専用のスレッドでワーカー メソッドを開始します。</span><span class="sxs-lookup"><span data-stu-id="839fc-224">You start the worker method on its own thread by calling `BeginInvoke` on the delegate that wraps it.</span></span> <span data-ttu-id="839fc-225">特定の非同期操作の有効期間を管理するには、<xref:System.ComponentModel.AsyncOperationManager> ヘルパー クラスの <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="839fc-225">To manage the lifetime of a particular asynchronous operation, you call the <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> method on the <xref:System.ComponentModel.AsyncOperationManager> helper class.</span></span> <span data-ttu-id="839fc-226">このメソッドが返す <xref:System.ComponentModel.AsyncOperation> は、クライアントのイベント ハンドラーに対する呼び出しを適切なスレッドまたはコンテキストにマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="839fc-226">This returns an <xref:System.ComponentModel.AsyncOperation>, which marshals calls on the client's event handlers to the proper thread or context.</span></span>  
  
 <span data-ttu-id="839fc-227">特定の保留中操作を取り消すには、対応する <xref:System.ComponentModel.AsyncOperation> で <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="839fc-227">You cancel a particular pending operation by calling <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> on its corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="839fc-228">このメソッドはその操作を終了するので、それ以降に <xref:System.ComponentModel.AsyncOperation> を呼び出すと例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="839fc-228">This ends that operation, and any subsequent calls to its <xref:System.ComponentModel.AsyncOperation> will throw an exception.</span></span>  
  
### <a name="to-implement-start-and-cancel-functionality"></a><span data-ttu-id="839fc-229">開始とキャンセルの機能を実装するには:</span><span class="sxs-lookup"><span data-stu-id="839fc-229">To implement Start and Cancel functionality:</span></span>  
  
1. <span data-ttu-id="839fc-230">`CalculatePrimeAsync` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-230">Implement the `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="839fc-231">クライアントが提供したトークン (タスク ID) が、現在保留中のタスクを表すすべてのトークンの間で一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="839fc-231">Make sure the client-supplied token (task ID) is unique with respect to all the tokens representing currently pending tasks.</span></span> <span data-ttu-id="839fc-232">クライアントが一意ではないトークンを渡した場合、`CalculatePrimeAsync` は例外を生成します。</span><span class="sxs-lookup"><span data-stu-id="839fc-232">If the client passes in a non-unique token, `CalculatePrimeAsync` raises an exception.</span></span> <span data-ttu-id="839fc-233">一意の場合は、トークンはタスク ID のコレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-233">Otherwise, the token is added to the task ID collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#3)]  
  
2. <span data-ttu-id="839fc-234">`CancelAsync` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="839fc-234">Implement the `CancelAsync` method.</span></span> <span data-ttu-id="839fc-235">トークン コレクションに `taskId` パラメーターが存在する場合は、削除されます。</span><span class="sxs-lookup"><span data-stu-id="839fc-235">If the `taskId` parameter exists in the token collection, it is removed.</span></span> <span data-ttu-id="839fc-236">これにより、開始する前に取り消されたタスクが実行するのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="839fc-236">This prevents canceled tasks that have not started from running.</span></span> <span data-ttu-id="839fc-237">タスクが実行中の場合、`BuildPrimeNumberList` メソッドは、タスク ID が有効期間コレクションから削除されたことを検出すると終了します。</span><span class="sxs-lookup"><span data-stu-id="839fc-237">If the task is running, the `BuildPrimeNumberList` method exits when it detects that the task ID has been removed from the lifetime collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a><span data-ttu-id="839fc-238">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="839fc-238">Checkpoint</span></span>  
 <span data-ttu-id="839fc-239">この段階で、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="839fc-239">At this point, you can build the component.</span></span>  
  
### <a name="to-test-your-component"></a><span data-ttu-id="839fc-240">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="839fc-240">To test your component</span></span>  
  
- <span data-ttu-id="839fc-241">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="839fc-241">Compile the component.</span></span>  
  
 <span data-ttu-id="839fc-242">`PrimeNumberCalculator` コンポーネントが完全して使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="839fc-242">The `PrimeNumberCalculator` component is now complete and ready to use.</span></span>  
  
 <span data-ttu-id="839fc-243">`PrimeNumberCalculator` コンポーネントを使うクライアントの例については、「[方法: イベントベースの非同期パターンのクライアントを実装する](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="839fc-243">For an example client that uses the `PrimeNumberCalculator` component, see [How to: Implement a Client of the Event-based Asynchronous Pattern](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="839fc-244">次の手順</span><span class="sxs-lookup"><span data-stu-id="839fc-244">Next Steps</span></span>  
 <span data-ttu-id="839fc-245">`CalculatePrimeAsync` メソッドに相当する同期メソッドである `CalculatePrime` を作成して、この例を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="839fc-245">You can fill out this example by writing `CalculatePrime`, the synchronous equivalent of `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="839fc-246">このようにすると、`PrimeNumberCalculator` コンポーネントはイベント ベースの非同期パターンに完全に準拠するようになります。</span><span class="sxs-lookup"><span data-stu-id="839fc-246">This will make the `PrimeNumberCalculator` component fully compliant with the Event-based Asynchronous Pattern.</span></span>  
  
 <span data-ttu-id="839fc-247">異なるテスト対象の数に対するさまざまな呼び出しによって検出されたすべての素数のリストを保持することで、この例を改良できます。</span><span class="sxs-lookup"><span data-stu-id="839fc-247">You can improve this example by retaining the list of all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="839fc-248">この方法を使うと、各タスクはそれより前のタスクで行われた作業の結果を流用できます。</span><span class="sxs-lookup"><span data-stu-id="839fc-248">Using this approach, each task will benefit from the work done by previous tasks.</span></span> <span data-ttu-id="839fc-249">異なるスレッドによるリストへのアクセスがシリアル化されるように、このリストを `lock` 領域で保護することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="839fc-249">Be careful to protect this list with `lock` regions, so access to the list by different threads is serialized.</span></span>  
  
 <span data-ttu-id="839fc-250">2、3、5 などの自明の約数をテストすることにより、この例を改良することもできます。</span><span class="sxs-lookup"><span data-stu-id="839fc-250">You can also improve this example by testing for trivial divisors, like 2, 3, and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839fc-251">参照</span><span class="sxs-lookup"><span data-stu-id="839fc-251">See also</span></span>

- [<span data-ttu-id="839fc-252">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="839fc-252">How to: Run an Operation in the Background</span></span>](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [<span data-ttu-id="839fc-253">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="839fc-253">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="839fc-254">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="839fc-254">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
