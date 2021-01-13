---
title: 非同期プログラミング - C#
description: .NET Core で提供される、C# 言語レベルの非同期プログラミング モデルについて説明します。
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 58f650e7932d4f5862d545429376b3e417bb433c
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512243"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="fc891-103">非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="fc891-103">Asynchronous programming</span></span>

<span data-ttu-id="fc891-104">I/O バインドのニーズ (ネットワークからのデータの要求、データベースへのアクセス、ファイル システムの読み書きなど) がある場合、非同期プログラミングを利用できます。</span><span class="sxs-lookup"><span data-stu-id="fc891-104">If you have any I/O-bound needs (such as requesting data from a network, accessing a database, or reading and writing to a file system), you'll want to utilize asynchronous programming.</span></span> <span data-ttu-id="fc891-105">CPU バインドのコードにも、コストのかかる計算の実行など、非同期コードに適したシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="fc891-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="fc891-106">C# は言語レベルで非同期プログラミング モデルを備えており、コールバックに苦労したり、非同期処理をサポートするライブラリに従ったりしなくても、非同期コードを簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="fc891-106">C# has a language-level asynchronous programming model, which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library that supports asynchrony.</span></span> <span data-ttu-id="fc891-107">C# は、[タスク ベースの非同期パターン (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) と呼ばれるものに従います。</span><span class="sxs-lookup"><span data-stu-id="fc891-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="overview-of-the-asynchronous-model"></a><span data-ttu-id="fc891-108">非同期モデルの概要</span><span class="sxs-lookup"><span data-stu-id="fc891-108">Overview of the asynchronous model</span></span>

<span data-ttu-id="fc891-109">非同期プログラミングの中心になるのは `Task` オブジェクトと `Task<T>` オブジェクトであり、非同期操作をモデル化します。</span><span class="sxs-lookup"><span data-stu-id="fc891-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span> <span data-ttu-id="fc891-110">これらは、`async` および `await` キーワードによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fc891-110">They are supported by the `async` and `await` keywords.</span></span> <span data-ttu-id="fc891-111">ほとんどの場合、モデルは非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="fc891-111">The model is fairly simple in most cases:</span></span>

- <span data-ttu-id="fc891-112">I/O バインドのコードでは、`async` メソッドの内部で、`Task` または `Task<T>` を返す操作を待機します。</span><span class="sxs-lookup"><span data-stu-id="fc891-112">For I/O-bound code, you await an operation that returns a `Task` or `Task<T>` inside of an `async` method.</span></span>
- <span data-ttu-id="fc891-113">CPU バインドのコードでは、<xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> メソッドによってバックグラウンド スレッドで開始された操作を待機します。</span><span class="sxs-lookup"><span data-stu-id="fc891-113">For CPU-bound code, you await an operation that is started on a background thread with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="fc891-114">`await` キーワードはマジックが行われる場所であり、</span><span class="sxs-lookup"><span data-stu-id="fc891-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="fc891-115">`await` を実行したメソッドの呼び出し元に制御が委譲されます。これによって最終的に、UI は応答できるようになり、サービスは柔軟性を持つようになります。</span><span class="sxs-lookup"><span data-stu-id="fc891-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span> <span data-ttu-id="fc891-116">`async` と `await` 以外にも非同期コードを実現する[方法はあります](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)が、この記事では言語レベルのコンストラクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fc891-116">While [there are ways](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) to approach async code other than `async` and `await`, this article focuses on the language-level constructs.</span></span>

### <a name="io-bound-example-download-data-from-a-web-service"></a><span data-ttu-id="fc891-117">I/O バインドの例: Web サービスからデータをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="fc891-117">I/O-bound example: Download data from a web service</span></span>

<span data-ttu-id="fc891-118">ボタンがクリックされたら Web サービスからデータをダウンロードする必要がありますが UI スレッドはブロックしたくない、といった場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-118">You may need to download some data from a web service when a button is pressed but don't want to block the UI thread.</span></span> <span data-ttu-id="fc891-119">これは、次のようにして実現できます。</span><span class="sxs-lookup"><span data-stu-id="fc891-119">It can be accomplished like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="fc891-120">コードでは、`Task` オブジェクトとの対話に煩わされることなく意図すること (データを非同期的にダウンロードする) が表されています。</span><span class="sxs-lookup"><span data-stu-id="fc891-120">The code expresses the intent (downloading data asynchronously) without getting bogged down in interacting with `Task` objects.</span></span>

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a><span data-ttu-id="fc891-121">CPU バインドの例: ゲームの計算を実行する</span><span class="sxs-lookup"><span data-stu-id="fc891-121">CPU-bound example: Perform a calculation for a game</span></span>

<span data-ttu-id="fc891-122">ボタンをクリックすると画面上の多くの敵にダメージを与えることができるモバイル ゲームを作っています。</span><span class="sxs-lookup"><span data-stu-id="fc891-122">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span> <span data-ttu-id="fc891-123">ダメージ計算の実行は負荷が大きく、UI スレッドで実行すると計算の実行中はゲームが停止しているように見えます。</span><span class="sxs-lookup"><span data-stu-id="fc891-123">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="fc891-124">これを処理する最善の方法は、バックグラウンド スレッドを開始して、その中で `Task.Run` を使って処理を実行し、`await` を使用して結果を大気することです。</span><span class="sxs-lookup"><span data-stu-id="fc891-124">The best way to handle this is to start a background thread, which does the work using `Task.Run`, and await its result using `await`.</span></span> <span data-ttu-id="fc891-125">このようにすると、処理が行われている間も UI が停止することはありません。</span><span class="sxs-lookup"><span data-stu-id="fc891-125">This allows the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="fc891-126">このコードでは、ボタンのクリック イベントの意図が明らかに表されています。バックグラウンド スレッドを手動で管理する必要はなく、ブロッキングが発生しない方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="fc891-126">This code clearly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="fc891-127">内部での処理</span><span class="sxs-lookup"><span data-stu-id="fc891-127">What happens under the covers</span></span>

<span data-ttu-id="fc891-128">非同期操作には多数の動作要素が関係します。</span><span class="sxs-lookup"><span data-stu-id="fc891-128">There are many moving pieces where asynchronous operations are concerned.</span></span> <span data-ttu-id="fc891-129">`Task` と `Task<T>` の内部処理について詳しくは、「[非同期の詳細](../standard/async-in-depth.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fc891-129">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, see the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="fc891-130">C# 側では、コンパイラによってコードがステート マシンに変換されます。ステート マシンでは、`await` に達したときの実行の委譲や、バックグラウンド ジョブが終了したときの実行の再開などが追跡されます。</span><span class="sxs-lookup"><span data-stu-id="fc891-130">On the C# side of things, the compiler transforms your code into a state machine that keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="fc891-131">理論的には、これは[非同期処理の約束モデル](https://en.wikipedia.org/wiki/Futures_and_promises)の実装です。</span><span class="sxs-lookup"><span data-stu-id="fc891-131">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="fc891-132">理解すべき重要事項</span><span class="sxs-lookup"><span data-stu-id="fc891-132">Key pieces to understand</span></span>

* <span data-ttu-id="fc891-133">非同期コードは I/O バインドと CPU バインドの両方のコードで使うことができますが、使い方はシナリオにより異なります。</span><span class="sxs-lookup"><span data-stu-id="fc891-133">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="fc891-134">非同期コードで使われる `Task<T>` と `Task` は、バックグラウンドで行われる処理のモデル化に使われる構成要素です。</span><span class="sxs-lookup"><span data-stu-id="fc891-134">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="fc891-135">キーワード `async` はメソッドを非同期メソッドに変換し、メソッドの本体で `await` キーワードを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fc891-135">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="fc891-136">適用された `await` キーワードは、呼び出しメソッドを中断し、待機中のタスクが完了するまで呼び出し元に制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="fc891-136">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="fc891-137">`await` は、非同期メソッドの中でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc891-137">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="fc891-138">CPU バインドと I/O バインドの処理</span><span class="sxs-lookup"><span data-stu-id="fc891-138">Recognize CPU-bound and I/O-bound work</span></span>

<span data-ttu-id="fc891-139">このガイドの最初の 2 つの例では、CPU バインドと I/O バインドの処理に対して `async` および `await` を使う方法を示しました。</span><span class="sxs-lookup"><span data-stu-id="fc891-139">The first two examples of this guide showed how you could use `async` and `await` for I/O-bound and CPU-bound work.</span></span> <span data-ttu-id="fc891-140">行う必要のあるジョブが I/O バインドか CPU バインドかを識別できることが重要です。これは、コードのパフォーマンスに大きく影響し、特定の構成の誤った使用につながるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="fc891-140">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="fc891-141">コードを記述する前に次の 2 点について考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-141">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="fc891-142">コードは何か (データベースのデータなど) を "待機" していますか。</span><span class="sxs-lookup"><span data-stu-id="fc891-142">Will your code be "waiting" for something, such as data from a database?</span></span>

   <span data-ttu-id="fc891-143">答えが "はい" の場合、その処理は **I/O バインド** です。</span><span class="sxs-lookup"><span data-stu-id="fc891-143">If your answer is "yes", then your work is **I/O-bound**.</span></span>

1. <span data-ttu-id="fc891-144">コードでは、負荷の大きい計算が実行されますか。</span><span class="sxs-lookup"><span data-stu-id="fc891-144">Will your code be performing an expensive computation?</span></span>

   <span data-ttu-id="fc891-145">答えが "はい" の場合、その処理は **CPU バインド** です。</span><span class="sxs-lookup"><span data-stu-id="fc891-145">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="fc891-146">処理が **I/O バインド** の場合は、`async` と `await` を使いますが、`Task.Run` は "*使いません*"。</span><span class="sxs-lookup"><span data-stu-id="fc891-146">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span> <span data-ttu-id="fc891-147">タスク並列ライブラリは "*使わないでください*"。</span><span class="sxs-lookup"><span data-stu-id="fc891-147">You *should not* use the Task Parallel Library.</span></span> <span data-ttu-id="fc891-148">その理由について詳しくは、「[非同期の詳細](../standard/async-in-depth.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fc891-148">The reason for this is outlined in [Async in Depth](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="fc891-149">処理が **CPU バインド** であり、応答性が重要な場合は、`async` と `await` を使い、`Task.Run` を "*使って*" 別のスレッドで処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="fc891-149">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await`, but spawn off the work on another thread *with* `Task.Run`.</span></span> <span data-ttu-id="fc891-150">処理がコンカレンシーと並列処理に適している場合は、[タスク並列ライブラリ](../standard/parallel-programming/task-parallel-library-tpl.md)を使うことも考慮します。</span><span class="sxs-lookup"><span data-stu-id="fc891-150">If the work is appropriate for concurrency and parallelism, also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="fc891-151">さらに、常にコードの実行を測定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-151">Additionally, you should always measure the execution of your code.</span></span> <span data-ttu-id="fc891-152">たとえば、マルチスレッドでのコンテキスト切り替えのオーバーヘッドと比較して、CPU バインドの処理の負荷がそれほど大きくないことがわかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-152">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span> <span data-ttu-id="fc891-153">すべての選択肢にはトレードオフがあり、状況に合った適切なトレードオフを選ぶ必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-153">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="fc891-154">その他の例</span><span class="sxs-lookup"><span data-stu-id="fc891-154">More examples</span></span>

<span data-ttu-id="fc891-155">以下では、C# で非同期コードを記述するさまざまな方法がわかる例を示します。</span><span class="sxs-lookup"><span data-stu-id="fc891-155">The following examples demonstrate various ways you can write async code in C#.</span></span> <span data-ttu-id="fc891-156">実際に遭遇する可能性があるいくつかの異なるシナリオを使います。</span><span class="sxs-lookup"><span data-stu-id="fc891-156">They cover a few different scenarios you may come across.</span></span>

### <a name="extract-data-from-a-network"></a><span data-ttu-id="fc891-157">ネットワークからデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="fc891-157">Extract data from a network</span></span>

<span data-ttu-id="fc891-158">このスニペットでは、<https://dotnetfoundation.org> にあるホームページから HTML がダウンロードされ、HTML に文字列 ".NET" が出現する回数が数えられます。</span><span class="sxs-lookup"><span data-stu-id="fc891-158">This snippet downloads the HTML from the homepage at <https://dotnetfoundation.org> and counts the number of times the string ".NET" occurs in the HTML.</span></span> <span data-ttu-id="fc891-159">ASP.NET を使用して Web API コントローラー メソッドが定義され、そのメソッドによってこのタスクが実行されて、値が返されます。</span><span class="sxs-lookup"><span data-stu-id="fc891-159">It uses ASP.NET to define a Web API controller method, which performs this task and returns the number.</span></span>

> [!NOTE]
> <span data-ttu-id="fc891-160">運用コードで HTML の解析の実行を計画している場合は、正規表現を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc891-160">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="fc891-161">代わりに解析ライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc891-161">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="fc891-162">次に示すのはユニバーサル Windows アプリ用に記述された同じシナリオであり、ボタンがクリックされたら同じタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="fc891-162">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a><span data-ttu-id="fc891-163">複数タスクの完了を待機する</span><span class="sxs-lookup"><span data-stu-id="fc891-163">Wait for multiple tasks to complete</span></span>

<span data-ttu-id="fc891-164">複数のデータを同時に取得することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-164">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span> <span data-ttu-id="fc891-165">`Task` API には 2 つのメソッド <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> と <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> が含まれており、これらを使用して、複数のバックグラウンド ジョブで非ブロッキング待機を実行する非同期コードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="fc891-165">The `Task` API contains two methods, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, that allow you to write asynchronous code that performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="fc891-166">次の例では、一連の `userId` に対する `User` データを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fc891-166">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="fc891-167">LINQ を使ってさらに簡潔に記述する別の方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fc891-167">Here's another way to write this more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="fc891-168">コードは少ないですが、LINQ と非同期コードを併用するときは注意してください。</span><span class="sxs-lookup"><span data-stu-id="fc891-168">Although it's less code, use caution when mixing LINQ with asynchronous code.</span></span> <span data-ttu-id="fc891-169">LINQ は遅延実行を使うので、生成されたシーケンスを `.ToList()` または `.ToArray()` の呼び出しで強制的に反復処理させない限り、`foreach` ループ内で行われた非同期呼び出しはすぐに実行されません。</span><span class="sxs-lookup"><span data-stu-id="fc891-169">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="fc891-170">重要な情報とアドバイス</span><span class="sxs-lookup"><span data-stu-id="fc891-170">Important info and advice</span></span>

<span data-ttu-id="fc891-171">非同期プログラミングには、留意することで予期しない動作を防ぐことができる細かい事柄がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="fc891-171">With async programming, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="fc891-172">`async` **メソッドの本体に** `await` **キーワードが含まれないと、何も行われません。**</span><span class="sxs-lookup"><span data-stu-id="fc891-172">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

  <span data-ttu-id="fc891-173">これは、忘れてはならない重要なことです。</span><span class="sxs-lookup"><span data-stu-id="fc891-173">This is important to keep in mind.</span></span> <span data-ttu-id="fc891-174">`await` が `async` メソッドの本体で使用されていない場合、C# コンパイラでは警告が生成されますが、コードは通常のメソッドと同様にコンパイルされて実行されます。</span><span class="sxs-lookup"><span data-stu-id="fc891-174">If `await` is not used in the body of an `async` method, the C# compiler generates a warning, but the code compiles and runs as if it were a normal method.</span></span> <span data-ttu-id="fc891-175">非同期メソッドに対して C# コンパイラによって生成されるステート マシンでは何も行われないため、これは非常に非効率的です。</span><span class="sxs-lookup"><span data-stu-id="fc891-175">This is incredibly inefficient, as the state machine generated by the C# compiler for the async method is not accomplishing anything.</span></span>

* <span data-ttu-id="fc891-176">**記述するすべての非同期メソッド名のサフィックスとして、"Async" を追加する必要があります**</span><span class="sxs-lookup"><span data-stu-id="fc891-176">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="fc891-177">これは、同期メソッドと非同期メソッドの区別をより簡単にするために、.NET で使われる規則です。</span><span class="sxs-lookup"><span data-stu-id="fc891-177">This is the convention used in .NET to more easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="fc891-178">コードによって明示的に呼び出されない一部のメソッド (イベント ハンドラーや Web コントローラー メソッドなど) には、必ずしも当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="fc891-178">Certain methods that aren't explicitly called by your code (such as event handlers or web controller methods) don't necessarily apply.</span></span> <span data-ttu-id="fc891-179">そのようなメソッドはコードでは明示的に呼び出されないため、明示的な命名はそれほど重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="fc891-179">Because they are not explicitly called by your code, being explicit about their naming isn't as important.</span></span>

* <span data-ttu-id="fc891-180">`async void` **はイベント ハンドラーに対してのみ使う必要があります。**</span><span class="sxs-lookup"><span data-stu-id="fc891-180">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="fc891-181">イベントには戻り値の型がないため、`async void` は非同期イベント ハンドラーの動作を可能にする唯一の方法です (したがって、`Task` と `Task<T>` を使うことはできません)。</span><span class="sxs-lookup"><span data-stu-id="fc891-181">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="fc891-182">`async void` のその他の使用はすべて TAP モデルに従わないので、使うのが難しい場合があります。以下はその例です。</span><span class="sxs-lookup"><span data-stu-id="fc891-182">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="fc891-183">`async void` メソッドでスローされた例外を、そのメソッドの外部でキャッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fc891-183">Exceptions thrown in an `async void` method can't be caught outside of that method.</span></span>
* <span data-ttu-id="fc891-184">`async void` メソッドをテストするのは困難です。</span><span class="sxs-lookup"><span data-stu-id="fc891-184">`async void` methods are difficult to test.</span></span>
* <span data-ttu-id="fc891-185">`async void` メソッドでは、呼び出し元がそれを非同期と予期していないと、悪い副作用が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-185">`async void` methods can cause bad side effects if the caller isn't expecting them to be async.</span></span>

* <span data-ttu-id="fc891-186">**LINQ 式での非同期ラムダの使用は慎重に行う必要があります**</span><span class="sxs-lookup"><span data-stu-id="fc891-186">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="fc891-187">LINQ 内のラムダ式では、遅延実行が使用されます。つまり、予期していないときにコードが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-187">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you're not expecting it to.</span></span> <span data-ttu-id="fc891-188">これにブロッキング タスクを組み込んだ場合、正しく作成されていないと、簡単にデッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="fc891-188">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="fc891-189">さらに、このように非同期コードを入れ子にすると、コードの実行についての推論も難しくなります。</span><span class="sxs-lookup"><span data-stu-id="fc891-189">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="fc891-190">非同期と LINQ は強力ですが、併用するときは可能な限り慎重かつ明確にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-190">Async and LINQ are powerful but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="fc891-191">**タスクを待機するコードは非ブロッキング方式で作成します**</span><span class="sxs-lookup"><span data-stu-id="fc891-191">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="fc891-192">`Task` が完了するのを待機するための手段として現在のスレッドをブロックすると、デッドロックおよびコンテキスト スレッドのブロックが発生するおそれがあり、複雑なエラー処理が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="fc891-192">Blocking the current thread as a means to wait for a `Task` to complete can result in deadlocks and blocked context threads and can require more complex error-handling.</span></span> <span data-ttu-id="fc891-193">次の表では、非ブロッキング方式でタスクの待機に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fc891-193">The following table provides guidance on how to deal with waiting for tasks in a non-blocking way:</span></span>

| <span data-ttu-id="fc891-194">これを使う</span><span class="sxs-lookup"><span data-stu-id="fc891-194">Use this...</span></span>          | <span data-ttu-id="fc891-195">これは使わない</span><span class="sxs-lookup"><span data-stu-id="fc891-195">Instead of this...</span></span>           | <span data-ttu-id="fc891-196">行う処理</span><span class="sxs-lookup"><span data-stu-id="fc891-196">When wishing to do this...</span></span>                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | <span data-ttu-id="fc891-197">`Task.Wait` または `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="fc891-197">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="fc891-198">バックグラウンド タスクの結果の取得</span><span class="sxs-lookup"><span data-stu-id="fc891-198">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny`               | <span data-ttu-id="fc891-199">任意のタスクの完了の待機</span><span class="sxs-lookup"><span data-stu-id="fc891-199">Waiting for any task to complete</span></span>           |
| `await Task.WhenAll` | `Task.WaitAll`               | <span data-ttu-id="fc891-200">すべてのタスクの完了の待機</span><span class="sxs-lookup"><span data-stu-id="fc891-200">Waiting for all tasks to complete</span></span>          |
| `await Task.Delay`   | `Thread.Sleep`               | <span data-ttu-id="fc891-201">一定期間の待機</span><span class="sxs-lookup"><span data-stu-id="fc891-201">Waiting for a period of time</span></span>               |

* <span data-ttu-id="fc891-202">**可能な場合は** `ValueTask` **の使用を検討する**</span><span class="sxs-lookup"><span data-stu-id="fc891-202">**Consider using** `ValueTask` **where possible**</span></span>

<span data-ttu-id="fc891-203">非同期メソッドから `Task` オブジェクトを返すと、特定のパスでパフォーマンスのボトルネックが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-203">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="fc891-204">`Task` は参照型です。したがって、これを使うことは、オブジェクトを割り当てることを意味します。</span><span class="sxs-lookup"><span data-stu-id="fc891-204">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="fc891-205">`async` 修飾子で宣言されたメソッドがキャッシュされた結果を返すか、同期的に完了する場合、追加の割り当ては、コードのパフォーマンスが重要なセクションにおいて大きな時間コストにつながります。</span><span class="sxs-lookup"><span data-stu-id="fc891-205">In cases where a method declared with the `async` modifier returns a cached result or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="fc891-206">厳密なループ処理でこのような割り当てが発生した場合、コストがかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-206">It can become costly if those allocations occur in tight loops.</span></span> <span data-ttu-id="fc891-207">詳しくは、「[一般化された async の戻り値の型](whats-new/csharp-7.md#generalized-async-return-types)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fc891-207">For more information, see [generalized async return types](whats-new/csharp-7.md#generalized-async-return-types).</span></span>

* <span data-ttu-id="fc891-208">`ConfigureAwait(false)` **の使用を検討する**</span><span class="sxs-lookup"><span data-stu-id="fc891-208">**Consider using** `ConfigureAwait(false)`</span></span>

<span data-ttu-id="fc891-209">"どのような場合に <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> メソッドを使用する必要があるか" ということが問題になることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="fc891-209">A common question is, "when should I use the <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> method?".</span></span> <span data-ttu-id="fc891-210">このメソッドを使用すると、`Task` インスタンスでその awaiter を構成できます。</span><span class="sxs-lookup"><span data-stu-id="fc891-210">The method allows for a `Task` instance to configure its awaiter.</span></span> <span data-ttu-id="fc891-211">これは重要な考慮事項であり、それを正しく設定しないと、パフォーマンスに影響し、デッドロックが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fc891-211">This is an important consideration and setting it incorrectly could potentially have performance implications and even deadlocks.</span></span> <span data-ttu-id="fc891-212">`ConfigureAwait` の詳細については、「[ConfigureAwait の FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc891-212">For more information on `ConfigureAwait`, see the [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span></span>

* <span data-ttu-id="fc891-213">**ステートフル性の低いコードを記述します**</span><span class="sxs-lookup"><span data-stu-id="fc891-213">**Write less stateful code**</span></span>

<span data-ttu-id="fc891-214">グローバル オブジェクトの状態または特定のメソッドの実行に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc891-214">Don't depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="fc891-215">代わりに、メソッドの戻り値のみに依存するようにします。</span><span class="sxs-lookup"><span data-stu-id="fc891-215">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="fc891-216">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="fc891-216">Why?</span></span>

* <span data-ttu-id="fc891-217">コードを理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="fc891-217">Code will be easier to reason about.</span></span>
* <span data-ttu-id="fc891-218">コードをテストしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="fc891-218">Code will be easier to test.</span></span>
* <span data-ttu-id="fc891-219">非同期コードと同期コードの混在がはるかに簡単になります。</span><span class="sxs-lookup"><span data-stu-id="fc891-219">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="fc891-220">一般には、競合状態を完全に回避できます。</span><span class="sxs-lookup"><span data-stu-id="fc891-220">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="fc891-221">戻り値に依存すると、非同期コードの調整が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="fc891-221">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="fc891-222">(ボーナス) 依存関係の挿入で問題なく動作します。</span><span class="sxs-lookup"><span data-stu-id="fc891-222">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="fc891-223">推奨される目標は、完全またはほぼ完全な[参照の透過性](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29)をコードで実現することです。</span><span class="sxs-lookup"><span data-stu-id="fc891-223">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="fc891-224">そうすることで、予測、テスト、保守が非常に容易なコードベースになります。</span><span class="sxs-lookup"><span data-stu-id="fc891-224">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="fc891-225">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="fc891-225">Other resources</span></span>

* <span data-ttu-id="fc891-226">「[非同期の詳細](../standard/async-in-depth.md)」では、タスクの動作方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="fc891-226">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="fc891-227">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="fc891-227">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="fc891-228">Lucian Wischik の「[Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async)」(非同期に関する 6 つの重要なヒント) は、非同期プログラミングのためのすばらしいリソースです。</span><span class="sxs-lookup"><span data-stu-id="fc891-228">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
