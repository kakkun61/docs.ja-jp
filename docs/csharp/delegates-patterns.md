---
title: デリゲートの一般的なパターン
description: コンポーネント間の密接な結合を避けるための、コードでのデリゲートの一般的な使用パターンについて説明します。
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 22ab88e5b139381e3a8921baa20df035f1405146
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223685"
---
# <a name="common-patterns-for-delegates"></a><span data-ttu-id="f7dbb-103">デリゲートの一般的なパターン</span><span class="sxs-lookup"><span data-stu-id="f7dbb-103">Common Patterns for Delegates</span></span>

<span data-ttu-id="f7dbb-104">[[戻る]](delegates-strongly-typed.md)</span><span class="sxs-lookup"><span data-stu-id="f7dbb-104">[Previous](delegates-strongly-typed.md)</span></span>

<span data-ttu-id="f7dbb-105">デリゲートは、コンポーネント間の結合度を最小限にしたソフトウェア設計を可能にするメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-105">Delegates provide a mechanism that enables software designs involving minimal coupling between components.</span></span>

<span data-ttu-id="f7dbb-106">この種の設計の代表的な例が LINQ です。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-106">One excellent example for this kind of design is LINQ.</span></span> <span data-ttu-id="f7dbb-107">LINQ のクエリ式パターンは、そのすべての機能がデリゲートによって支えられています。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-107">The LINQ Query Expression Pattern relies on delegates for all of its features.</span></span> <span data-ttu-id="f7dbb-108">簡単な例を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-108">Consider this simple example:</span></span>

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

<span data-ttu-id="f7dbb-109">このコードは、一連の数値から値が 10 未満である数値のみを抽出するものです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-109">This filters the sequence of numbers to only those less than the value 10.</span></span>
<span data-ttu-id="f7dbb-110">`Where` メソッドは、デリゲートを使って、どの要素を抽出するかを判断しています。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-110">The `Where` method uses a delegate that determines which elements of a sequence pass the filter.</span></span> <span data-ttu-id="f7dbb-111">LINQ クエリを作成するとき、その具体的な目的に合ったデリゲートの機能は、皆さんが実装することになります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-111">When you create a LINQ query, you supply the implementation of the delegate for this specific purpose.</span></span>

<span data-ttu-id="f7dbb-112">Where メソッドのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-112">The prototype for the Where method is:</span></span>

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

<span data-ttu-id="f7dbb-113">この例は、LINQ のすべてのメソッドに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-113">This example is repeated with all the methods that are part of LINQ.</span></span> <span data-ttu-id="f7dbb-114">具体的なクエリを扱うコードには、すべてデリゲートが使われているのです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-114">They all rely on delegates for the code that manages the specific query.</span></span> <span data-ttu-id="f7dbb-115">きわめて強力な API デザイン パターンなので、しっかり覚えて自分のものにしてください。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-115">This API design pattern is a very powerful one to learn and understand.</span></span>

<span data-ttu-id="f7dbb-116">この単純な例から、コンポーネント間の結合関係がデリゲートにはほとんど必要ないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-116">This simple example illustrates how delegates require very little coupling between components.</span></span> <span data-ttu-id="f7dbb-117">特定の基本クラスから派生したクラスを作成する必要がないのです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-117">You don't need to create a class that derives from a particular base class.</span></span> <span data-ttu-id="f7dbb-118">特定のインターフェイスを実装する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-118">You don't need to implement a specific interface.</span></span>
<span data-ttu-id="f7dbb-119">唯一の要件は、目的のタスクに必要なメソッドの機能を 1 つ、手の届くところに実装するだけです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-119">The only requirement is to provide the implementation of one method that is fundamental to the task at hand.</span></span>

## <a name="building-your-own-components-with-delegates"></a><span data-ttu-id="f7dbb-120">デリゲートを使った独自のコンポーネントを作成する</span><span class="sxs-lookup"><span data-stu-id="f7dbb-120">Building Your Own Components with Delegates</span></span>

<span data-ttu-id="f7dbb-121">この例を踏まえて、デリゲートを利用した設計を使ってコンポーネントを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-121">Let's build on that example by creating a component using a design that relies on delegates.</span></span>

<span data-ttu-id="f7dbb-122">たとえば大規模なシステムのログ メッセージに使われるコンポーネントとは、どのようなものでしょうか。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-122">Let's define a component that could be used for log messages in a large system.</span></span> <span data-ttu-id="f7dbb-123">そのライブラリ コンポーネントは、各種プラットフォーム上のさまざまな環境で使われることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-123">The library components could be used in many different environments, on multiple different platforms.</span></span> <span data-ttu-id="f7dbb-124">ログを扱うコンポーネントには、共通する機能が多数存在します。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-124">There are a lot of common features in the component that manages the logs.</span></span> <span data-ttu-id="f7dbb-125">まず、システム内のコンポーネントからメッセージを受け取らなければなりません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-125">It will need to accept messages from any component in the system.</span></span> <span data-ttu-id="f7dbb-126">それらのメッセージには、さまざまな優先度が割り当てられ、中心となるコンポーネントがそれらの優先度を管理できるようになっていることでしょう。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-126">Those messages will have different priorities, which the core component can manage.</span></span> <span data-ttu-id="f7dbb-127">最終的にアーカイブされるメッセージの形式には、タイムスタンプが記録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-127">The messages should have timestamps in their final archived form.</span></span> <span data-ttu-id="f7dbb-128">さらに高度な用途としては、ログの発生元のコンポーネントごとにメッセージをフィルタリングすることも考えられます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-128">For more advanced scenarios, you could filter messages by the source component.</span></span>

<span data-ttu-id="f7dbb-129">この機能には、不確定要素が 1 つあります。メッセージがどこに出力されるかです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-129">There is one aspect of the feature that will change often: where messages are written.</span></span> <span data-ttu-id="f7dbb-130">メッセージがエラー コンソールに出力されるか、</span><span class="sxs-lookup"><span data-stu-id="f7dbb-130">In some environments, they may be written to the error console.</span></span> <span data-ttu-id="f7dbb-131">ファイルに出力されるかは、環境によってさまざまです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-131">In others, a file.</span></span> <span data-ttu-id="f7dbb-132">データベース ストレージや OS のイベント ログのほか、ドキュメント ストレージに出力される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-132">Other possibilities include database storage, OS event logs, or other document storage.</span></span>

<span data-ttu-id="f7dbb-133">また複数の場所に出力して、それぞれ異なる用途に使われるようなケースもあります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-133">There are also combinations of output that might be used in different scenarios.</span></span> <span data-ttu-id="f7dbb-134">たとえばコンソールとファイルにメッセージを出力したい場合もあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-134">You may want to write messages to the console and to a file.</span></span>

<span data-ttu-id="f7dbb-135">デリゲートを使った設計なら運用の幅が大きく広がり、将来追加される可能性のあるストレージ メカニズムへの対応が容易になります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-135">A design based on delegates will provide a great deal of flexibility, and make it easy to support storage mechanisms that may be added in the future.</span></span>

<span data-ttu-id="f7dbb-136">この設計の下では、主要なログ コンポーネントが必ずしも仮想クラスである必要はなく、シール クラスであってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-136">Under this design, the primary log component can be a non-virtual, even sealed class.</span></span> <span data-ttu-id="f7dbb-137">一連のデリゲートを組み込めば、さまざまなストレージ メディアにメッセージを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-137">You can plug in any set of delegates to write the messages to different storage media.</span></span> <span data-ttu-id="f7dbb-138">マルチキャスト デリゲートがネイティブでサポートされているため、メッセージを複数の場所 (ファイルとコンソールなど) に出力する必要のある状況にも簡単に対応することができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-138">The built in support for multicast delegates makes it easy to support scenarios where messages must be written to multiple locations (a file, and a console).</span></span>

## <a name="a-first-implementation"></a><span data-ttu-id="f7dbb-139">初めての実装</span><span class="sxs-lookup"><span data-stu-id="f7dbb-139">A First Implementation</span></span>

<span data-ttu-id="f7dbb-140">最初は簡単な機能を実装してみましょう。新しいメッセージを受け取ったら、アタッチされたデリゲートを使ってそれらを出力するものです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-140">Let's start small: the initial implementation will accept new messages, and write them using any attached delegate.</span></span> <span data-ttu-id="f7dbb-141">まず、コンソールにメッセージを出力するデリゲートを 1 つ作成します。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-141">You can start with one delegate that writes messages to the console.</span></span>

[!code-csharp[LoggerImplementation](../../samples/snippets/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

<span data-ttu-id="f7dbb-142">上の静的クラスは、ごく簡単なコードですが、きちんと機能します。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-142">The static class above is the simplest thing that can work.</span></span> <span data-ttu-id="f7dbb-143">メッセージをコンソールに出力するメソッドの機能を 1 つ実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-143">We need to write the single implementation for the method that writes messages to the console:</span></span>

[!code-csharp[LogToConsole](../../samples/snippets/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

<span data-ttu-id="f7dbb-144">最後にそのメソッドを、Logger に宣言されている WriteMessage デリゲートにアタッチして接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-144">Finally, you need to hook up the delegate by attaching it to the WriteMessage delegate declared in the logger:</span></span>

[!code-csharp[ConnectDelegate](../../samples/snippets/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a><span data-ttu-id="f7dbb-145">実践</span><span class="sxs-lookup"><span data-stu-id="f7dbb-145">Practices</span></span>

<span data-ttu-id="f7dbb-146">紹介したサンプルはごく簡単なものですが、デリゲートを伴う設計についての重要な指針がいくつか示されています。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-146">Our sample so far is fairly simple, but it still demonstrates some of the important guidelines for designs involving delegates.</span></span>

<span data-ttu-id="f7dbb-147">ユーザーは、Core Framework に定義されているデリゲート型を使うことで、さらに簡単にデリゲートを扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-147">Using the delegate types defined in the Core Framework makes it easier for users to work with the delegates.</span></span> <span data-ttu-id="f7dbb-148">皆さんが新しい型を定義する必要はなく、皆さんのライブラリを利用する開発者も、特別な目的を持ったデリゲート型を新たに覚える必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-148">You don't need to define new types, and developers using your library do not need to learn new, specialized delegate types.</span></span>

<span data-ttu-id="f7dbb-149">使用されているインターフェイスはごくわずかでありながら、最大限の柔軟性が得られるようになっています。つまり新しい出力ロガーを作成するために皆さんがすべきことは、メソッドを 1 つ作成することです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-149">The interfaces used are as minimal and as flexible as possible: To create a new output logger, you must create one method.</span></span> <span data-ttu-id="f7dbb-150">そのメソッドは静的メソッドでも、インスタンス メソッドでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-150">That method may be a static method, or an instance method.</span></span> <span data-ttu-id="f7dbb-151">またアクセス指定も任意です。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-151">It may have any access.</span></span>

## <a name="formatting-output"></a><span data-ttu-id="f7dbb-152">出力の書式設定</span><span class="sxs-lookup"><span data-stu-id="f7dbb-152">Formatting Output</span></span>

<span data-ttu-id="f7dbb-153">最初のコード例にもう少し肉付けしてみましょう。その後、別のログ メカニズムの作成に進みます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-153">Let's make this first version a bit more robust, and then start creating other logging mechanisms.</span></span>

<span data-ttu-id="f7dbb-154">まず、より構造化されたメッセージを作成するために、いくつかの引数を `LogMessage()` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-154">Next, let's add a few arguments to the `LogMessage()` method so that your log class creates more structured messages:</span></span>

[!code-csharp[Severity](../../samples/snippets/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

<span data-ttu-id="f7dbb-155">次に、その `Severity` 引数を利用して、ログ出力に送るメッセージをフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-155">Next, let's make use of that `Severity` argument to filter the messages that are sent to the log's output.</span></span>

[!code-csharp[FinalLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a><span data-ttu-id="f7dbb-156">実践</span><span class="sxs-lookup"><span data-stu-id="f7dbb-156">Practices</span></span>

<span data-ttu-id="f7dbb-157">ログのインフラストラクチャに新しい機能を追加しました。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-157">You've added new features to the logging infrastructure.</span></span> <span data-ttu-id="f7dbb-158">このロガー コンポーネントは、出力メカニズムとの結び付きがきわめて弱いので、このように新しい機能を追加しても、ロガーのデリゲートを実装する側のコードには一切影響が生じません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-158">Because the logger component is very loosely coupled to any output mechanism, these new features can be added with no impact on any of the code implementing the logger delegate.</span></span>

<span data-ttu-id="f7dbb-159">他の部分には変更を加えずに一部分だけをアップデートできるという点に関しては、このプログラム コードを記述していく過程で、結び付きの弱さによって運用の幅が広がる例が他にもたくさん見つかることでしょう。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-159">As you keep building this, you'll see more examples of how this loose coupling enables greater flexibility in updating parts of the site without any changes to other locations.</span></span> <span data-ttu-id="f7dbb-160">実際、大規模なアプリケーションになると、ロガー出力クラスを別のアセンブリに置き、リビルドすら必要ないケースもあります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-160">In fact, in a larger application, the logger output classes might be in a different assembly, and not even need to be rebuilt.</span></span>

## <a name="building-a-second-output-engine"></a><span data-ttu-id="f7dbb-161">2 つ目の出力エンジンの作成</span><span class="sxs-lookup"><span data-stu-id="f7dbb-161">Building a Second Output Engine</span></span>

<span data-ttu-id="f7dbb-162">1 つ目のログ コンポーネントがうまく作成できました。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-162">The Log component is coming along well.</span></span> <span data-ttu-id="f7dbb-163">次は、メッセージをファイルに記録する出力エンジンを追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-163">Let's add one more output engine that logs messages to a file.</span></span> <span data-ttu-id="f7dbb-164">この出力エンジンは、先ほどよりも少し複雑になります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-164">This will be a slightly more involved output engine.</span></span> <span data-ttu-id="f7dbb-165">このクラスにはファイル操作がカプセル化され、毎回出力後に必ずファイルが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-165">It will be a class that encapsulates the file operations, and ensures that the file is always closed after each write.</span></span> <span data-ttu-id="f7dbb-166">これによって、メッセージが生成されるたびにすべてのデータが確実にディスクにフラッシュされます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-166">That ensures that all the data is flushed to disk after each message is generated.</span></span>

<span data-ttu-id="f7dbb-167">このファイル ベースのロガーを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-167">Here is that file based logger:</span></span>

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

<span data-ttu-id="f7dbb-168">このクラスを作成した後、インスタンス化すれば、その LogMessage メソッドを Logger コンポーネントにアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-168">Once you've created this class, you can instantiate it and it attaches its LogMessage method to the Logger component:</span></span>

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

<span data-ttu-id="f7dbb-169">この 2 つは、どちらか一方しか使えないというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-169">These two are not mutually exclusive.</span></span> <span data-ttu-id="f7dbb-170">両方のログ メソッドをアタッチすれば、コンソールとファイルにメッセージを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-170">You could attach both log methods and generate messages to the console and a file:</span></span>

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

<span data-ttu-id="f7dbb-171">後で同じアプリケーションで、片方のデリゲートを削除しても、システムに問題が生じることはありません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-171">Later, even in the same application, you can remove one of the delegates without any other issues to the system:</span></span>

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="f7dbb-172">実践</span><span class="sxs-lookup"><span data-stu-id="f7dbb-172">Practices</span></span>

<span data-ttu-id="f7dbb-173">ログ サブシステム用に 2 つ目の出力ハンドラーを追加しました。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-173">Now, you've added a second output handler for the logging sub-system.</span></span>
<span data-ttu-id="f7dbb-174">こちらは、ファイル システムを正しくサポートするために、もう少しインフラストラクチャを整える必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-174">This one needs a bit more infrastructure to correctly support the file system.</span></span> <span data-ttu-id="f7dbb-175">デリゲートはインスタンス メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-175">The delegate is an instance method.</span></span> <span data-ttu-id="f7dbb-176">プライベート メソッドでもあります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-176">It's also a private method.</span></span>
<span data-ttu-id="f7dbb-177">それより広いアクセス指定は必要ありません。なぜならデリゲートの接続は、デリゲート インフラストラクチャが行ってくれるためです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-177">There's no need for greater accessibility because the delegate infrastructure can connect the delegates.</span></span>

<span data-ttu-id="f7dbb-178">また、デリゲート ベースの設計では、新たにコードを書かなくても複数の出力メソッドを利用することができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-178">Second, the delegate-based design enables multiple output methods without any extra code.</span></span> <span data-ttu-id="f7dbb-179">複数の出力メソッドをサポートするために、別途インフラストラクチャを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-179">You don't need to build any additional infrastructure to support multiple output methods.</span></span> <span data-ttu-id="f7dbb-180">何もしなくても、呼び出しリストの中では、それらが別々のメソッドになるのです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-180">They simply become another method on the invocation list.</span></span>

<span data-ttu-id="f7dbb-181">ファイル ロガーの出力メソッドのコードに注目してください。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-181">Pay special attention to the code in the file logging output method.</span></span> <span data-ttu-id="f7dbb-182">決して例外がスローされないようにコーディングされています。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-182">It is coded to ensure that it does not throw any exceptions.</span></span> <span data-ttu-id="f7dbb-183">厳密には常に必要というわけではありませんが、通常はこのようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-183">While this isn't always strictly necessary, it's often a good practice.</span></span> <span data-ttu-id="f7dbb-184">いずれかのデリゲート メソッドから例外がスローされた場合に、呼び出しリストに残っている他のデリゲートが呼び出されなくなってしまいます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-184">If either of the delegate methods throws an exception, the remaining delegates that are on the invocation won't be invoked.</span></span>

<span data-ttu-id="f7dbb-185">最後の注意点として、ファイル ロガーは、ログ メッセージごとにファイルを開閉することによって、そのリソースを自己管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-185">As a last note, the file logger must manage its resources by opening and closing the file on each log message.</span></span> <span data-ttu-id="f7dbb-186">または、ファイルを開いたままにすることも可能です。つまり IDisposable を実装し、完了した時点でファイルを閉じるようにするのです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-186">You could choose to keep the file open and implement IDisposable to close the file when you are completed.</span></span>
<span data-ttu-id="f7dbb-187">どちらの方法にも長所と短所があります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-187">Either method has its advantages and disadvantages.</span></span> <span data-ttu-id="f7dbb-188">また、どちらの方法も、クラス間の結合度がわずかに増します。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-188">Both do create a bit more coupling between the classes.</span></span>

<span data-ttu-id="f7dbb-189">しかし、どちらのシナリオをサポートするにしても、Logger クラスのコードには一切手を加える必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-189">None of the code in the Logger class would need to be updated in order to support either scenario.</span></span>

## <a name="handling-null-delegates"></a><span data-ttu-id="f7dbb-190">Null デリゲートの処理</span><span class="sxs-lookup"><span data-stu-id="f7dbb-190">Handling Null Delegates</span></span>

<span data-ttu-id="f7dbb-191">最後に、出力メカニズムが選択されなかったケースに備えて、LogMessage メソッドに変更を加えたいと思います。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-191">Finally, let's update the LogMessage method so that it is robust for those cases when no output mechanism is selected.</span></span> <span data-ttu-id="f7dbb-192">現在の実装コードでは、`WriteMessage` デリゲートに呼び出しリストがアタッチされなかった場合、`NullReferenceException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-192">The current implementation will throw a `NullReferenceException` when the `WriteMessage` delegate does not have an invocation list attached.</span></span>
<span data-ttu-id="f7dbb-193">メソッドがアタッチされていなくても、何事もなかったように処理が継続されるような設計の方が望ましい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-193">You may prefer a design that silently continues when no methods have been attached.</span></span> <span data-ttu-id="f7dbb-194">これは、`Delegate.Invoke()` メソッドに null 条件演算子を組み合わせて使えば簡単に実現できます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-194">This is easy using the null conditional operator, combined with the `Delegate.Invoke()` method:</span></span>

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

<span data-ttu-id="f7dbb-195">null 条件演算子 (`?.`) は、左辺オペランド (このケースでは `WriteMessage`) が null のとき、そこで評価が打ち切られます。つまり、メッセージを記録する処理は試行されません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-195">The null conditional operator (`?.`) short-circuits when the left operand (`WriteMessage` in this case) is null, which means no attempt is made to log a message.</span></span>

<span data-ttu-id="f7dbb-196">`System.Delegate` や `System.MulticastDelegate` のドキュメントを探しても、`Invoke()` メソッドは記載されていません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-196">You won't find the `Invoke()` method listed in the documentation for `System.Delegate` or `System.MulticastDelegate`.</span></span> <span data-ttu-id="f7dbb-197">宣言されているデリゲート型には、コンパイラによってタイプ セーフな `Invoke` メソッドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-197">The compiler generates a type safe `Invoke` method for any delegate type declared.</span></span> <span data-ttu-id="f7dbb-198">つまり、この例では、`Invoke` が `string` 引数を 1 つ持ち、戻り値の型が void であるということです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-198">In this example, that means `Invoke` takes a single `string` argument, and has a void return type.</span></span>

## <a name="summary-of-practices"></a><span data-ttu-id="f7dbb-199">実践のまとめ</span><span class="sxs-lookup"><span data-stu-id="f7dbb-199">Summary of Practices</span></span>

<span data-ttu-id="f7dbb-200">ログ コンポーネントの基本的概念を見てきました。この概念は、その他の出力機構や各種機能に応用することができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-200">You've seen the beginnings of a log component that could be expanded with other writers, and other features.</span></span> <span data-ttu-id="f7dbb-201">デリゲートを使った設計では、そうしたコンポーネント間の結びつきを疎に保つことができるのです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-201">By using delegates in the design these different components are very loosely coupled.</span></span> <span data-ttu-id="f7dbb-202">これにはさまざまな利点があります。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-202">This provides several advantages.</span></span> <span data-ttu-id="f7dbb-203">まず、ごくわずかな手間で、新しい出力メカニズムを作成してシステムにアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-203">It's very easy to create new output mechanisms and attach them to the system.</span></span> <span data-ttu-id="f7dbb-204">新たに追加するメカニズムで必要となるのは、1 つのメソッドだけです。ログ メッセージを出力するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-204">These other mechanisms only need one method: the method that writes the log message.</span></span> <span data-ttu-id="f7dbb-205">これは、新しい機能を追加するときに問題がきわめて起きにくい設計といえます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-205">It's a design that is very resilient when new features are added.</span></span> <span data-ttu-id="f7dbb-206">どのような出力機構を追加するにせよ、求められるコントラクトはメソッドを 1 つ実装する、ということです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-206">The contract required for any writer is to implement one method.</span></span> <span data-ttu-id="f7dbb-207">それは静的メソッドでもインスタンス メソッドでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-207">That method could be a static or instance method.</span></span> <span data-ttu-id="f7dbb-208">アクセスできる範囲も、public や private を含め、正当なアクセス指定であれば何でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-208">It could be public, private, or any other legal access.</span></span>

<span data-ttu-id="f7dbb-209">Logger クラスには、これまでの動作を大きく変えることなく何度でも、その機能を強化したり変更を加えたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-209">The Logger class can make any number of enhancements or changes without introducing breaking changes.</span></span> <span data-ttu-id="f7dbb-210">あらゆるクラスに言えることですが、パブリック API の変更には、互換性に影響する変更のリスクが伴います。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-210">Like any class, you cannot modify the public API without the risk of breaking changes.</span></span> <span data-ttu-id="f7dbb-211">しかし、ロガーと出力エンジンとの結合はデリゲートを介してのみ行われるので、他の型 (インターフェイス、基本クラスなど) が関係してくることはありません。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-211">But, because the coupling between the logger and any output engines is only through the delegate, no other types (like interfaces or base classes) are involved.</span></span> <span data-ttu-id="f7dbb-212">その結合度は最小限で済むのです。</span><span class="sxs-lookup"><span data-stu-id="f7dbb-212">The coupling is as small as possible.</span></span>

[<span data-ttu-id="f7dbb-213">次へ</span><span class="sxs-lookup"><span data-stu-id="f7dbb-213">Next</span></span>](events-overview.md)
