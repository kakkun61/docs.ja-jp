---
title: Wcf 開発者向けの gRPC-gRPC への WCF 双方向サービスの移行
description: さまざまな形式の WCF 双方向サービスを gRPC streaming services に移行する方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 4741e5ad5c12fa358853381d4f2c286add14f8f5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938027"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="c3064-103">WCF 双方向サービスを gRPC に移行する</span><span class="sxs-lookup"><span data-stu-id="c3064-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="c3064-104">ここでは、基本的な概念を理解しました。このセクションでは、より複雑な *ストリーミング* grpc サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c3064-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="c3064-105">Windows Communication Foundation (WCF) で双方向サービスを使用するには、複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="c3064-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c3064-106">一部のサービスはクライアントによって開始され、サーバーからデータをストリーミングします。</span><span class="sxs-lookup"><span data-stu-id="c3064-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="c3064-107">その他の全二重サービスには、WCF ドキュメントにある従来の電卓の例のように、継続的な双方向通信が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c3064-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="c3064-108">この章では、2つの WCF stock ティッカー実装を実行し、gRPC に移行します。1つはサーバーストリーミング RPC を使用し、もう1つは双方向ストリーミング RPC を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3064-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="c3064-109">サーバーストリーミング RPC</span><span class="sxs-lookup"><span data-stu-id="c3064-109">Server streaming RPC</span></span>

<span data-ttu-id="c3064-110">SimpleStockPriceTicker の [サンプル SimpleStockTicker WCF ソリューション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)では、クライアントが株価記号の一覧を使用して接続を開始する双方向サービスがあり、サーバーは *コールバックインターフェイス* を使用して更新プログラムが使用可能になったときにそれらを送信します。</span><span class="sxs-lookup"><span data-stu-id="c3064-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="c3064-111">クライアントは、サーバーからの呼び出しに応答するために、そのインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="c3064-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="c3064-112">WCF ソリューション</span><span class="sxs-lookup"><span data-stu-id="c3064-112">The WCF solution</span></span>

<span data-ttu-id="c3064-113">WCF ソリューションは、自己ホスト型の Net.tcp サーバーとして .NET Framework 4 に実装されています。*x* コンソールアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c3064-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="c3064-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="c3064-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="c3064-115">サービスには、コールバックインターフェイスを使用して `ISimpleStockTickerCallback` リアルタイムでクライアントにデータを送信するため、戻り値の型のない1つのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="c3064-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="c3064-116">コールバックインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3064-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="c3064-117">これらのインターフェイスの実装と、フェイク外部依存関係を使用してテストデータを提供できます。</span><span class="sxs-lookup"><span data-stu-id="c3064-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="c3064-118">gRPC ストリーミング</span><span class="sxs-lookup"><span data-stu-id="c3064-118">gRPC streaming</span></span>

<span data-ttu-id="c3064-119">リアルタイムデータを処理するための gRPC プロセスは、WCF プロセスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="c3064-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="c3064-120">クライアントからサーバーへの呼び出しでは、永続的なストリームを作成できます。このストリームは、非同期的に到着するメッセージを監視できます。</span><span class="sxs-lookup"><span data-stu-id="c3064-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="c3064-121">違いにかかわらず、ストリームは、このデータを処理するためのより直観的な方法であり、LINQ、リアクティブストリーム、関数型プログラミングなどを重視する最新のプログラミングにおいてさらに関連性があります。</span><span class="sxs-lookup"><span data-stu-id="c3064-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="c3064-122">サービス定義には2つのメッセージが必要です。1つは要求用で、もう1つはストリーム用です。</span><span class="sxs-lookup"><span data-stu-id="c3064-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="c3064-123">サービスは、 `StockTickerUpdate` 宣言にキーワードを含むメッセージのストリームを返し `stream` `return` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="c3064-124">`Timestamp`価格変更の正確な時間を表示するには、更新プログラムにを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c3064-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="c3064-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="c3064-125">simple_stock_ticker.proto</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-simplestockticker"></a><span data-ttu-id="c3064-126">SimpleStockTicker を実装する</span><span class="sxs-lookup"><span data-stu-id="c3064-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="c3064-127">`StockPriceSubscriber` `TraderSys.StockMarket` クラスライブラリからターゲットソリューションの新しい .NET Standard クラスライブラリに3つのクラスをコピーして、WCF プロジェクトのフェイクを再利用します。</span><span class="sxs-lookup"><span data-stu-id="c3064-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="c3064-128">ベストプラクティスに従うには、型を追加 `Factory` してインスタンスを作成し、を `IStockPriceSubscriberFactory` ASP.NET Core 依存関係挿入サービスに登録します。</span><span class="sxs-lookup"><span data-stu-id="c3064-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="c3064-129">ファクトリ実装</span><span class="sxs-lookup"><span data-stu-id="c3064-129">The factory implementation</span></span>

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="register-the-factory"></a><span data-ttu-id="c3064-130">ファクトリの登録</span><span class="sxs-lookup"><span data-stu-id="c3064-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="c3064-131">これで、このクラスを使用して gRPC を実装できるようになりました `StockTickerService` 。</span><span class="sxs-lookup"><span data-stu-id="c3064-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="c3064-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="c3064-132">StockTickerService.cs</span></span>

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors caused by broken connection, etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

<span data-ttu-id="c3064-133">ご覧のように、ファイル内の宣言では、 `.proto` メソッドがメッセージのストリームを返すことが示されて `StockTickerUpdate` いますが、実際にはを返し `Task` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="c3064-134">ストリームを作成するジョブは、生成されたコードと、応答ストリームを提供する gRPC ランタイムライブラリによって処理され、 `IServerStreamWriter<StockTickerUpdate>` 使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c3064-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="c3064-135">接続が開いている間にサービスクラスのインスタンスが保持されている WCF 双方向サービスとは異なり、gRPC サービスは返されたタスクを使用してサービスを維持します。</span><span class="sxs-lookup"><span data-stu-id="c3064-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="c3064-136">接続が閉じられるまで、タスクは完了しません。</span><span class="sxs-lookup"><span data-stu-id="c3064-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="c3064-137">サービスは、からのを使用して、クライアントが接続を閉じたことを通知でき `CancellationToken` `ServerCallContext` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="c3064-138">単純な静的メソッドである `AwaitCancellation` は、トークンが取り消されたときに完了するタスクを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3064-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="c3064-139">メソッドで、を `Subscribe` 取得 `StockPriceSubscriber` し、応答ストリームに書き込むイベントハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="c3064-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="c3064-140">次に、接続が閉じられるのを待って `subscriber` から、閉じたストリームにデータを書き込むことができないようにを直ちに破棄します。</span><span class="sxs-lookup"><span data-stu-id="c3064-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="c3064-141">`WriteUpdateAsync`メソッドには、 `try` / `catch` ストリームにメッセージが書き込まれたときに発生する可能性のあるエラーを処理するブロックがあります。</span><span class="sxs-lookup"><span data-stu-id="c3064-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="c3064-142">この考慮事項は、意図的に、またはどこかの障害が原因で、任意のミリ秒で中断される可能性があるネットワーク経由の永続的な接続において重要です。</span><span class="sxs-lookup"><span data-stu-id="c3064-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="c3064-143">クライアントアプリケーションからの Stockkerservice の使用</span><span class="sxs-lookup"><span data-stu-id="c3064-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="c3064-144">ファイルから共有可能なクライアントクラスライブラリを作成するには、前のセクションと同じ手順に従い `.proto` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="c3064-145">このサンプルには、クライアントの使用方法を示す .NET コンソールアプリケーションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c3064-145">In the sample, there's a .NET console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="c3064-146">Program.cs の例</span><span class="sxs-lookup"><span data-stu-id="c3064-146">Example Program.cs</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

<span data-ttu-id="c3064-147">この場合、 `Subscribe` 生成されたクライアントのメソッドは非同期ではありません。</span><span class="sxs-lookup"><span data-stu-id="c3064-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="c3064-148">ストリームが作成され、そのメソッドが非同期であるため、すぐに使用できるようになり `MoveNext` ます。最初に呼び出されたときは、接続が有効になるまで完了しません。</span><span class="sxs-lookup"><span data-stu-id="c3064-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="c3064-149">ストリームは、非同期メソッドに渡され `DisplayAsync` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="c3064-150">アプリケーションは、ユーザーがキーを押すまで待機してから、メソッドをキャンセル `DisplayAsync` し、タスクが完了するのを待ってから終了します。</span><span class="sxs-lookup"><span data-stu-id="c3064-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="c3064-151">このコードでは、新しい C# 8 宣言構文を使用して、 `using` メソッドの終了時にストリームとチャネルを破棄し `Main` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="c3064-152">これは小さな変更ですが、インデントや空の線を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="c3064-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="c3064-153">ストリームを使用する</span><span class="sxs-lookup"><span data-stu-id="c3064-153">Consume the stream</span></span>

<span data-ttu-id="c3064-154">WCF では、コールバックインターフェイスを使用して、サーバーがクライアント上でメソッドを直接呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c3064-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="c3064-155">gRPC ストリームの動作は異なります。</span><span class="sxs-lookup"><span data-stu-id="c3064-155">gRPC streams work differently.</span></span> <span data-ttu-id="c3064-156">クライアントは、返されたストリームに対して反復処理を行い、を返すローカルメソッドから返された場合と同じように、メッセージを処理し `IEnumerable` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="c3064-157">`IAsyncStreamReader<T>`型は、のように動作 `IEnumerator<T>` します。</span><span class="sxs-lookup"><span data-stu-id="c3064-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="c3064-158">`MoveNext`より多くのデータがある限り true を返すメソッドと、 `Current` 最新の値を返すプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c3064-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="c3064-159">唯一の違いは、メソッドが単にでは `MoveNext` なくを返すことです `Task<bool>` `bool` 。</span><span class="sxs-lookup"><span data-stu-id="c3064-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="c3064-160">`ReadAllAsync`拡張メソッドは、 `IAsyncEnumerable` 新しい構文で使用できる標準の C# 8 でストリームをラップし `await foreach` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> <span data-ttu-id="c3064-161">事後対応型のプログラミングパターンを使用する開発者にとって、この章の最後にある「 [クライアントライブラリ](client-libraries.md#iobservable) 」のセクションでは、でラップする拡張メソッドとクラスを追加する方法を示し `IAsyncStreamReader<T>` `IObservable<T>` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="c3064-162">ここでも、ネットワークエラーが発生する可能性があるため、ここで例外をキャッチしてください。これは、 <xref:System.OperationCanceledException> コードがを使用してループを中断するため、必然的にスローされるためです <xref:System.Threading.CancellationToken> 。</span><span class="sxs-lookup"><span data-stu-id="c3064-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="c3064-163">型には `RpcException` 、などの gRPC ランタイムエラーに関する有用な情報が多数含まれてい `StatusCode` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="c3064-164">詳細については、[第4章の「*エラー処理*](error-handling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3064-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="c3064-165">双方向ストリーミング</span><span class="sxs-lookup"><span data-stu-id="c3064-165">Bidirectional streaming</span></span>

<span data-ttu-id="c3064-166">WCF の全二重サービスを使用すると、非同期のリアルタイムメッセージングを双方向で実現できます。</span><span class="sxs-lookup"><span data-stu-id="c3064-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="c3064-167">サーバーストリーミングの例では、クライアントが要求を開始し、更新のストリームを受信します。</span><span class="sxs-lookup"><span data-stu-id="c3064-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="c3064-168">適切なバージョンのサービスを使用すると、クライアントは、停止して新しいサブスクリプションを作成することなく、一覧に対して株式の追加や削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c3064-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="c3064-169">この機能は、 [Fullstockticker サンプルソリューション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)に実装されています。</span><span class="sxs-lookup"><span data-stu-id="c3064-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="c3064-170">`IFullStockTickerService`インターフェイスには、次の3つのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="c3064-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="c3064-171">`Subscribe` 接続を開始します。</span><span class="sxs-lookup"><span data-stu-id="c3064-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="c3064-172">`AddSymbol` ウォッチするストックシンボルを追加します。</span><span class="sxs-lookup"><span data-stu-id="c3064-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="c3064-173">`RemoveSymbol` ウォッチ対象のリストからシンボルを削除します。</span><span class="sxs-lookup"><span data-stu-id="c3064-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

<span data-ttu-id="c3064-174">コールバックインターフェイスは同じままです。</span><span class="sxs-lookup"><span data-stu-id="c3064-174">The callback interface remains the same.</span></span>

<span data-ttu-id="c3064-175">このパターンを gRPC に実装するのは簡単ではありません。これは、1つはクライアントからサーバー、もう1つはサーバーからクライアントの2つのデータストリームが渡されるためです。</span><span class="sxs-lookup"><span data-stu-id="c3064-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="c3064-176">複数のメソッドを使用して追加と削除の操作を実装することはできませんが、1つのストリームに複数の種類のメッセージを渡すことはできません `Any` 。そのためには、 `oneof` [第3章](protobuf-any-oneof.md)で説明した型またはキーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3064-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="c3064-177">許容される特定の型のセットがある場合は、を使用 `oneof` する方が適切な方法です。</span><span class="sxs-lookup"><span data-stu-id="c3064-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="c3064-178">`ActionMessage`またはのいずれかを保持できるを使用し `AddSymbolRequest` `RemoveSymbolRequest` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

<span data-ttu-id="c3064-179">メッセージのストリームを受け取る双方向ストリーミングサービスを宣言し `ActionMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="c3064-180">このサービスの実装は、前の例と似ていますが、メソッドの最初のパラメーター `Subscribe` がで、 `IAsyncStreamReader<ActionMessage>` `Add` 要求と要求を処理するために使用できるようになりました `Remove` 。</span><span class="sxs-lookup"><span data-stu-id="c3064-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors caused by broken connection, etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

<span data-ttu-id="c3064-181">GRPC が生成したクラスは、 `ActionMessage` プロパティとプロパティのいずれか1つだけを設定できることを保証し `Add` `Remove` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="c3064-182">どのような種類のメッセージが使用されている `null` かを判断するための有効な方法として、どちらを使用しているかはわかりません。</span><span class="sxs-lookup"><span data-stu-id="c3064-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="c3064-183">また、コード生成によって、クラスにが作成されました `enum ActionOneOfCase` `ActionMessage` 。これは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c3064-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="c3064-184">オブジェクトのプロパティを `ActionCase` `ActionMessage` ステートメントと共に使用して、 `switch` どのフィールドが設定されているかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c3064-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> <span data-ttu-id="c3064-185">`switch`ステートメントには、 `default` 不明な値が検出された場合に警告をログに記録するケースがあり `ActionOneOfCase` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="c3064-186">これは、 `.proto` より多くのアクションが追加された新しいバージョンのファイルをクライアントが使用していることを示す場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c3064-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="c3064-187">これは、を使用すること `switch` が、既知のフィールドでのテストよりも優れている理由の1つです `null` 。</span><span class="sxs-lookup"><span data-stu-id="c3064-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="c3064-188">クライアントアプリケーションからの FullStockTickerService の使用</span><span class="sxs-lookup"><span data-stu-id="c3064-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="c3064-189">この複雑なクライアントの使用方法を示す単純な .NET WPF アプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="c3064-189">There's a simple .NET WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="c3064-190">完全なアプリケーションについては、 [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3064-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="c3064-191">クライアントは、クラスで使用されます `MainWindowViewModel` 。このクラスは、 `FullStockTicker.FullStockTickerClient` 依存関係の挿入から型のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3064-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

<span data-ttu-id="c3064-192">メソッドによって返されるオブジェクト `client.Subscribe()` は、gRPC ライブラリ型のインスタンスになりました。これは、 `AsyncDuplexStreamingCall<TRequest, TResponse>` `RequestStream` サーバーに要求を送信し、応答を処理するためのを提供し `ResponseStream` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="c3064-193">要求ストリームは、 `ICommand` シンボルを追加および削除するために、一部の WPF メソッドから使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3064-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="c3064-194">各操作について、オブジェクトの関連するフィールドを設定し `ActionMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> <span data-ttu-id="c3064-195">`oneof`メッセージにフィールドの値を設定すると、以前に設定されていたすべてのフィールドが自動的にクリアされます。</span><span class="sxs-lookup"><span data-stu-id="c3064-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="c3064-196">応答のストリームは、メソッドで処理され `async` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="c3064-197">返されるは、 `Task` ウィンドウが閉じられたときに破棄されることを保持します。</span><span class="sxs-lookup"><span data-stu-id="c3064-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-cleanup"></a><span data-ttu-id="c3064-198">クライアントのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="c3064-198">Client cleanup</span></span>

<span data-ttu-id="c3064-199">ウィンドウが閉じられ、が `MainWindowViewModel` 破棄されると ( `Closed` のイベントから)、オブジェクトを適切に破棄することをお `MainWindow` 勧めし `AsyncDuplexStreamingCall` ます。</span><span class="sxs-lookup"><span data-stu-id="c3064-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="c3064-200">特に、 `CompleteAsync` `RequestStream` サーバー上のストリームを適切に閉じるには、のメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3064-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="c3064-201">この例は、 `DisposeAsync` サンプルビューモデルのメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="c3064-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

<span data-ttu-id="c3064-202">要求ストリームを閉じると、サーバーは独自のリソースを適時に破棄できます。</span><span class="sxs-lookup"><span data-stu-id="c3064-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="c3064-203">これにより、サービスの効率とスケーラビリティが向上し、例外が回避されます。</span><span class="sxs-lookup"><span data-stu-id="c3064-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c3064-204">[前へ](migrate-request-reply.md)
>[次へ](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="c3064-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
