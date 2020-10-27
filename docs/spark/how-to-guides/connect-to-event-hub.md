---
title: .NET for Apache Spark を Azure Event Hubs に接続する
description: ローカルの .NET for Apache Spark インスタンスから Azure Event Hub に接続する方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c8fd10992e63674032af4148e0673a5330d9086c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223966"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="74f59-103">.NET for Apache Spark を Azure Event Hubs に接続する</span><span class="sxs-lookup"><span data-stu-id="74f59-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="74f59-104">この記事では、[.NET for Apache Spark](https://github.com/dotnet/spark) アプリケーションを Azure Event Hubs に接続して Apache Kafka ストリームの読み取りと書き込みを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74f59-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74f59-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="74f59-105">Prerequisites</span></span>

<span data-ttu-id="74f59-106">イベント ハブについて Event Hubs 名前空間を準備します。</span><span class="sxs-lookup"><span data-stu-id="74f59-106">Have an Event Hubs Namespace ready with an event hub.</span></span> <span data-ttu-id="74f59-107">ステップ バイ ステップ ガイドについては、「[クイックスタート: Azure portal を使用してイベント ハブを作成する](/azure/event-hubs/event-hubs-create)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74f59-107">For a step-by-step guide, refer to [Quickstart: Create an event hub using Azure portal](/azure/event-hubs/event-hubs-create).</span></span> <span data-ttu-id="74f59-108">イベント ハブの名前空間を作成するときは、必ず Standard 価格レベルを選択してください。</span><span class="sxs-lookup"><span data-stu-id="74f59-108">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="74f59-109">Azure Event Hubs とは</span><span class="sxs-lookup"><span data-stu-id="74f59-109">What is Azure Event Hubs</span></span>

<span data-ttu-id="74f59-110">[Azure Event Hubs](/azure/event-hubs/event-hubs-about) は、ビッグ データのストリーミング プラットフォームとなるイベント インジェスト サービスです。</span><span class="sxs-lookup"><span data-stu-id="74f59-110">[Azure Event Hubs](/azure/event-hubs/event-hubs-about) is a big-data streaming platform and event-ingestion service.</span></span> <span data-ttu-id="74f59-111">これは、フル マネージドのサービスとしてのプラットフォーム (PaaS) であり、[Apache Kafka](https://kafka.apache.org/) と簡単に統合できます。これにより、独自のクラスターを管理、構成、または実行しなくても、PaaS Kafka エクスペリエンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="74f59-111">It is a fully managed Platform-as-a-Service (PaaS) that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure, or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="74f59-112">アプリケーションを Azure Event Hubs に接続する</span><span class="sxs-lookup"><span data-stu-id="74f59-112">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="74f59-113">Event Hubs の接続文字列と完全修飾ドメイン名 (FQDN) を、後で使用するために取得します。</span><span class="sxs-lookup"><span data-stu-id="74f59-113">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="74f59-114">手順については、「[Get an Event Hubs connection string (Event Hubs の接続文字列を取得する)](/azure/event-hubs/event-hubs-get-connection-string)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74f59-114">For instructions, see [Get an Event Hubs connection string](/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="74f59-115">Kafka 用 Event Hubs からの読み取りを開始するには、コード内の名前空間の詳細を使用して次の構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="74f59-115">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="74f59-116">次のように、アプリケーションで **BOOTSTRAP_SERVERS** と **EH_SASL** を更新します。</span><span class="sxs-lookup"><span data-stu-id="74f59-116">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="74f59-117">Azure Event Hub ストリームから読み取る</span><span class="sxs-lookup"><span data-stu-id="74f59-117">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="74f59-118">これで、Kafka の場合と同様に Event Hubs でストリーミングを開始できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="74f59-118">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="74f59-119">サンプル コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="74f59-119">Sample code as shown below:</span></span>

```csharp
SparkSession spark = SparkSession
    .Builder()
    .AppName("Connect Event Hub")
    .GetOrCreate();

DataFrame df = spark
    .ReadStream()
    .Format("kafka")
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("subscribe", "spark-test")
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("kafka.request.timeout.ms", "60000")
    .Option("kafka.session.timeout.ms", "60000")
    .Option("failOnDataLoss", "false")
    .Load();

DataFrame dfWrite = df
    .WriteStream()
    .OutputMode("append")
    .Format("console")
    .Start();
```

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="74f59-120">Azure Event Hub ストリームに書き込む</span><span class="sxs-lookup"><span data-stu-id="74f59-120">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="74f59-121">次に示すように、同じ方法で Event Hubs に書き込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="74f59-121">You can also write to Event Hubs in the same way, as shown below:</span></span>

```csharp
// df is the DataFrame to write

df.WriteStream()
    .Format("kafka")
    .Option("topic", topics)
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("checkpointLocation", "./checkpoint")
    .Start();
```

## <a name="run-your-application"></a><span data-ttu-id="74f59-122">アプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="74f59-122">Run your application</span></span>

<span data-ttu-id="74f59-123">.NET for Apache Spark アプリケーションを実行するには、sbt プロジェクトの `build.sbt` で `libraryDependency` を使用して、Spark プロジェクトのビルド定義の一環として `spark-sql-kafka-0-10` モジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="74f59-123">In order to run your .NET for Apache Spark application, define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="74f59-124">`spark-submit` (または `spark-shell`) などの Spark 環境では、次のように `--packages` コマンドライン オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="74f59-124">For Spark environments such as `spark-submit` (or `spark-shell`), use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="74f59-125">実行する Spark のバージョンに合わせて、パッケージのバージョンを必ず含めてください。</span><span class="sxs-lookup"><span data-stu-id="74f59-125">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
