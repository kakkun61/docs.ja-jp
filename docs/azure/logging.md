---
title: Azure SDK for .NET を使用したログ記録
description: Azure SDK for .NET クライアント ライブラリを使用してログ記録を有効にする方法について説明します。
ms.date: 03/20/2020
ms.custom: devx-track-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: 6adc485867e9bad401a15da19e6cb4424d2ddb13
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700711"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="efc5d-103">Azure SDK for .NET を使用したログ記録</span><span class="sxs-lookup"><span data-stu-id="efc5d-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="efc5d-104">[Azure SDK](https://azure.microsoft.com/downloads/) for .NET クライアント ライブラリには、クライアント ライブラリの操作をログに記録する機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="efc5d-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="efc5d-105">これにより、クライアント ライブラリが Azure サービスに対して行う I/O 要求と応答を監視できます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="efc5d-106">通常、このログは、通信の問題をデバッグまたは診断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="efc5d-107">この記事では、Azure SDK for .NET を使用してログ記録を有効にする 3 つの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="efc5d-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="efc5d-108">コンソール ウィンドウにログを記録する</span><span class="sxs-lookup"><span data-stu-id="efc5d-108">Log to the console window</span></span>
- <span data-ttu-id="efc5d-109">.NET 診断トレースにログを記録する</span><span class="sxs-lookup"><span data-stu-id="efc5d-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="efc5d-110">カスタム ログ記録を構成する</span><span class="sxs-lookup"><span data-stu-id="efc5d-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efc5d-111">この記事は、最新バージョンの Azure SDK for .NET を使用するクライアント ライブラリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="efc5d-112">ライブラリがサポートされているかどうかを確認するには、「[Azure SDK の最新リリース](https://azure.github.io/azure-sdk/releases/latest/index.html)」の一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efc5d-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="efc5d-113">Azure SDK クライアント ライブラリの古いバージョンをアプリケーションで使用している場合は、該当するサービスのドキュメントで具体的な手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efc5d-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="efc5d-114">ログ情報</span><span class="sxs-lookup"><span data-stu-id="efc5d-114">Log information</span></span>

<span data-ttu-id="efc5d-115">SDK では、次の情報がログに記録されます。パラメーター クエリとヘッダー値はサニタイズされ、個人データが削除されます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="efc5d-116">HTTP 要求ログ エントリ:</span><span class="sxs-lookup"><span data-stu-id="efc5d-116">HTTP request log entry:</span></span>

- <span data-ttu-id="efc5d-117">一意の ID</span><span class="sxs-lookup"><span data-stu-id="efc5d-117">Unique ID</span></span>
- <span data-ttu-id="efc5d-118">HTTP メソッド</span><span class="sxs-lookup"><span data-stu-id="efc5d-118">HTTP method</span></span>
- <span data-ttu-id="efc5d-119">URI</span><span class="sxs-lookup"><span data-stu-id="efc5d-119">URI</span></span>
- <span data-ttu-id="efc5d-120">送信要求ヘッダー</span><span class="sxs-lookup"><span data-stu-id="efc5d-120">Outgoing request headers</span></span>

<span data-ttu-id="efc5d-121">HTTP 応答ログ エントリ:</span><span class="sxs-lookup"><span data-stu-id="efc5d-121">HTTP response log entry:</span></span>

- <span data-ttu-id="efc5d-122">I/O 操作の実行時間 (時間経過)</span><span class="sxs-lookup"><span data-stu-id="efc5d-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="efc5d-123">要求 ID</span><span class="sxs-lookup"><span data-stu-id="efc5d-123">Request ID</span></span>
- <span data-ttu-id="efc5d-124">HTTP 状態コード</span><span class="sxs-lookup"><span data-stu-id="efc5d-124">HTTP status code</span></span>
- <span data-ttu-id="efc5d-125">HTTP 理由語句</span><span class="sxs-lookup"><span data-stu-id="efc5d-125">HTTP reason phrase</span></span>
- <span data-ttu-id="efc5d-126">応答ヘッダー</span><span class="sxs-lookup"><span data-stu-id="efc5d-126">Response headers</span></span>
- <span data-ttu-id="efc5d-127">エラー情報 (該当する場合)</span><span class="sxs-lookup"><span data-stu-id="efc5d-127">Error information, when applicable</span></span>

<span data-ttu-id="efc5d-128">要求と応答のコンテンツの場合:</span><span class="sxs-lookup"><span data-stu-id="efc5d-128">For request and response content:</span></span>

- <span data-ttu-id="efc5d-129">Content-type ヘッダーに応じて、コンテンツ ストリームはテキストまたはバイトになります。</span><span class="sxs-lookup"><span data-stu-id="efc5d-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="efc5d-130">[!メモ} コンテンツ ログは既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="efc5d-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="efc5d-131">有効にするには、`ClientOptions` で `Diagnostics.IsLoggingContentEnabled` を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="efc5d-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="efc5d-132">イベント ログは通常、次の 3 つのレベルのいずれかで出力されます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="efc5d-133">要求と応答イベントの情報</span><span class="sxs-lookup"><span data-stu-id="efc5d-133">Informational for request and response events</span></span>
- <span data-ttu-id="efc5d-134">エラーの警告</span><span class="sxs-lookup"><span data-stu-id="efc5d-134">Warning for errors</span></span>
- <span data-ttu-id="efc5d-135">詳細なメッセージとコンテンツ ログの詳細</span><span class="sxs-lookup"><span data-stu-id="efc5d-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="efc5d-136">組み込みメソッドを使用してログ記録を有効にする</span><span class="sxs-lookup"><span data-stu-id="efc5d-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="efc5d-137">Azure SDK for .NET クライアント ライブラリは、[`EventSource` クラス](/dotnet/api/system.diagnostics.tracing.eventsource)を使用して Windows イベント トレーシング (ETW) にイベントを記録します。これは、.NET では一般的です。</span><span class="sxs-lookup"><span data-stu-id="efc5d-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="efc5d-138">イベント ソースを使用すると、パフォーマンスのオーバーヘッドを最小限に抑えながら、アプリケーション コードで構造化されたログを使用できます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="efc5d-139">これらのイベン トログにアクセスするには、イベント リスナーを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efc5d-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="efc5d-140">SDK には `Azure.Core.Diagnostics.AzureEventSourceListener` クラス (Azure.Core NuGet パッケージで定義されています) が含まれています。これには、.NET アプリケーションの包括的なログ記録を簡略化する 2 つの静的メソッド (`CreateConsoleLogger` と `CreateTraceLogger`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="efc5d-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="efc5d-141">これらのメソッドでは、ログ レベルを指定する省略可能なパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="efc5d-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="efc5d-142">コンソール ウィンドウにログを記録する</span><span class="sxs-lookup"><span data-stu-id="efc5d-142">Log to the console window</span></span>

<span data-ttu-id="efc5d-143">Azure SDK for .NET クライアント ライブラリの主な原則は、包括的なログをリアルタイムで簡単に表示できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="efc5d-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="efc5d-144">`CreateConsoleLogger` メソッドを使用すると、1 行のコードでログをコンソール ウィンドウに送信できます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="efc5d-145">診断トレースにログを記録する</span><span class="sxs-lookup"><span data-stu-id="efc5d-145">Log to diagnostic traces</span></span>

<span data-ttu-id="efc5d-146">トレース リスナーを実装する場合は、`CreateTraceLogger` メソッドを使用して、標準の .NET イベント トレース機構 ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)) にログを記録できます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="efc5d-147">.NET でのイベント トレースの詳細については、「[トレース リスナー](../framework/debug-trace-profile/trace-listeners.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efc5d-147">For more information on event tracing in .NET, see [Trace Listeners](../framework/debug-trace-profile/trace-listeners.md).</span></span> <span data-ttu-id="efc5d-148">この例では、詳細レベルのログ記録を指定します。</span><span class="sxs-lookup"><span data-stu-id="efc5d-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="efc5d-149">カスタム ログ記録を構成する</span><span class="sxs-lookup"><span data-stu-id="efc5d-149">Configure custom logging</span></span>

<span data-ttu-id="efc5d-150">前述のように、Azure SDK for .NET からログ メッセージを受信するには、イベント リスナーを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efc5d-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="efc5d-151">包括的なログを実装する際に上記の簡略化されたメソッドを使用しない場合は、`AzureEventSourceListener` クラスのインスタンスを作成して、作成したコールバック関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="efc5d-152">このメソッドでは、必要に応じて好きに処理できるログ メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="efc5d-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="efc5d-153">また、インスタンスを構築するときに、含めるログ レベルを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="efc5d-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="efc5d-154">次の例では、カスタム メッセージを使用してコンソールにログを記録するイベント リスナーを作成し、それを詳細レベルの Azure コア イベントでフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="efc5d-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a><span data-ttu-id="efc5d-155">次の手順</span><span class="sxs-lookup"><span data-stu-id="efc5d-155">Next steps</span></span>

- [<span data-ttu-id="efc5d-156">Azure App Service のアプリの診断ログの有効化</span><span class="sxs-lookup"><span data-stu-id="efc5d-156">Enable diagnostics logging for apps in Azure App Service</span></span>](/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="efc5d-157">[Azure のセキュリティ ログと監査のオプション](/azure/security/fundamentals/log-audit)を確認する</span><span class="sxs-lookup"><span data-stu-id="efc5d-157">Review [Azure security logging and auditing](/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="efc5d-158">[Azure プラットフォーム ログ](/azure/azure-monitor/platform/platform-logs-overview)を操作する方法を確認する</span><span class="sxs-lookup"><span data-stu-id="efc5d-158">Learn how to work with [Azure platform logs](/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="efc5d-159">[.NET Core のログ記録とトレース](../core/diagnostics/logging-tracing.md)の詳細について読む</span><span class="sxs-lookup"><span data-stu-id="efc5d-159">Read more about [.NET Core logging and tracing](../core/diagnostics/logging-tracing.md)</span></span>
