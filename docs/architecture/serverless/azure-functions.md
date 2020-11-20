---
title: Azure Functions - サーバーレス アプリ
description: Azure Functions には、イベント ドリブンのインスタント スケール コードを提供する、複数の言語 (C#、JavaScript、Java) とプラットフォーム向けのサーバーレス機能が用意されています。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 08e1aaecdee753dc25cca0d6356caaafae1ad510
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557117"
---
# <a name="azure-functions"></a><span data-ttu-id="22d0d-103">Azure Functions </span><span class="sxs-lookup"><span data-stu-id="22d0d-103">Azure Functions</span></span>

<span data-ttu-id="22d0d-104">Azure Functions では、サーバーレスのコンピューティング エクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-104">Azure Functions provide a serverless compute experience.</span></span> <span data-ttu-id="22d0d-105">*トリガー* (HTTP エンドポイントへのアクセスやタイマーなど) によって呼び出される関数によって、コードまたはビジネス ロジックのブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="22d0d-106">ストレージやキューなどのリソースに接続する特別な "*バインド*" も Functions でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="22d0d-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure Functions のロゴ](./media/azure-functions-logo.png)

<span data-ttu-id="22d0d-108">現在のランタイム バージョン3.0 では、クロスプラットフォームの .NET Core 3.1 アプリケーションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="22d0d-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="22d0d-109">C# 以外に、JavaScript、F#、Java などのその他の言語がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="22d0d-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="22d0d-110">ポータルで作成する関数には、豊富なスクリプト構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="22d0d-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="22d0d-111">スタンドアロン プロジェクトとして作成した関数を、完全なプラットフォームのサポートと機能を使用して展開できます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="22d0d-112">詳細については、「[Azure Functions のドキュメント](/azure/azure-functions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d0d-112">For more information, see [Azure Functions documentation](/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="22d0d-113">プログラミング言語のサポート</span><span class="sxs-lookup"><span data-stu-id="22d0d-113">Programming language support</span></span>

<span data-ttu-id="22d0d-114">一般提供 (GA) では、以下の言語がすべてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="22d0d-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="22d0d-115">言語</span><span class="sxs-lookup"><span data-stu-id="22d0d-115">Language</span></span>      |<span data-ttu-id="22d0d-116">サポートされているランタイム</span><span class="sxs-lookup"><span data-stu-id="22d0d-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="22d0d-117">**C#**</span><span class="sxs-lookup"><span data-stu-id="22d0d-117">**C#**</span></span>        |<span data-ttu-id="22d0d-118">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="22d0d-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="22d0d-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="22d0d-119">**JavaScript**</span></span>|<span data-ttu-id="22d0d-120">Node 10、12</span><span class="sxs-lookup"><span data-stu-id="22d0d-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="22d0d-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="22d0d-121">**F#**</span></span>        |<span data-ttu-id="22d0d-122">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="22d0d-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="22d0d-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="22d0d-123">**Java**</span></span>      |<span data-ttu-id="22d0d-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="22d0d-124">Java 8</span></span>            |
|<span data-ttu-id="22d0d-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="22d0d-125">**Python**</span></span>    |<span data-ttu-id="22d0d-126">Python 3.6、3.7、3.8</span><span class="sxs-lookup"><span data-stu-id="22d0d-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="22d0d-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="22d0d-127">**TypeScript**</span></span>|<span data-ttu-id="22d0d-128">Node 10、12 (JavaScript を使用)</span><span class="sxs-lookup"><span data-stu-id="22d0d-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="22d0d-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="22d0d-129">**PowerShell**</span></span>|<span data-ttu-id="22d0d-130">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="22d0d-130">PowerShell Core 6</span></span>|

<span data-ttu-id="22d0d-131">詳細については、[サポートされている言語](/azure/azure-functions/supported-languages)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d0d-131">For more information, see [Supported languages](/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="22d0d-132">App Service プラン</span><span class="sxs-lookup"><span data-stu-id="22d0d-132">App service plans</span></span>

<span data-ttu-id="22d0d-133">Functions は "*App Service プラン*" によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="22d0d-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="22d0d-134">このプランでは、関数アプリによって使用されるリソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="22d0d-135">プランをリージョンに割り当て、使用される仮想マシンのサイズと数を決定し、価格レベルを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="22d0d-136">真のサーバーレス アプローチとして、関数アプリで **従量課金** プランを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="22d0d-137">従量課金プランでは、負荷に基づいてバックエンドが自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="22d0d-138">関数アプリのもう 1 つのホスティング オプションは、[Premium プラン](/azure/azure-functions/functions-premium-plan)です。</span><span class="sxs-lookup"><span data-stu-id="22d0d-138">Another hosting option for function apps is the [Premium plan](/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="22d0d-139">このプランでは、コールド スタートの必要がない "常時接続" インスタンスが提供され、VNet 接続などの高度な機能がサポートされて、Premium ハードウェアで実行されます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="22d0d-140">詳細については、[App Service プラン](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d0d-140">For more information, see [App service plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="22d0d-141">最初の関数を作成する</span><span class="sxs-lookup"><span data-stu-id="22d0d-141">Create your first function</span></span>

<span data-ttu-id="22d0d-142">関数アプリを作成するには、3 つの一般的な方法があります。</span><span class="sxs-lookup"><span data-stu-id="22d0d-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="22d0d-143">ポータルで関数をスクリプト化します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-143">Script functions in the portal.</span></span>
- <span data-ttu-id="22d0d-144">Azure CLI を使用して必要なリソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="22d0d-145">お気に入りの IDE を使用してローカルで関数をビルドし、Azure に発行します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="22d0d-146">スクリプト化された関数をポータル上で作成する方法の詳細については、「[Azure portal で初めての関数を作成する](/azure/azure-functions/functions-create-first-azure-function)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d0d-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="22d0d-147">Azure CLI からビルドするには、[Azure CLI を使用して初めての関数を作成する](/azure/azure-functions/functions-create-first-azure-function-azure-cli)方法に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d0d-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="22d0d-148">Visual Studio で関数を作成するには、「[Visual Studio を使用して初めての関数を作成する](/azure/azure-functions/functions-create-your-first-function-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d0d-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="22d0d-149">トリガーとバインドについて</span><span class="sxs-lookup"><span data-stu-id="22d0d-149">Understand triggers and bindings</span></span>

<span data-ttu-id="22d0d-150">関数は "*トリガー*" によって呼び出されます。関数に設定できるトリガーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="22d0d-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="22d0d-151">関数を呼び出すだけでなく、特定のトリガーにはバインドとしての機能もあります。</span><span class="sxs-lookup"><span data-stu-id="22d0d-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="22d0d-152">トリガーに加えて、複数のバインドを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="22d0d-153">"*バインド*" は、宣言によってデータをコードに接続する方法です。</span><span class="sxs-lookup"><span data-stu-id="22d0d-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="22d0d-154">渡される場合 (入力) と、データを受け取る場合 (出力) があります。</span><span class="sxs-lookup"><span data-stu-id="22d0d-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="22d0d-155">トリガーとバインドを使用すると、関数を使用した作業が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="22d0d-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="22d0d-156">バインドによって、データベースまたはファイル システムの接続を手動で作成するオーバーヘッドが解消されます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="22d0d-157">バインドに必要なすべての情報は、*functions.json* というスクリプト用の特別なファイル内に格納されます。または、コード内で属性を使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="22d0d-158">次のような一般的なトリガーがあります。</span><span class="sxs-lookup"><span data-stu-id="22d0d-158">Some common triggers include:</span></span>

- <span data-ttu-id="22d0d-159">Blob Storage: ストレージ内でファイルまたはフォルダーがアップロードまたは変更されたときに、関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="22d0d-160">HTTP: REST API のように関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="22d0d-161">キュー: キューに項目が存在する場合に関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="22d0d-162">タイマー: 関数を定期的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="22d0d-163">バインドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-163">Examples of bindings include:</span></span>

- <span data-ttu-id="22d0d-164">CosmosDB: データベースに簡単に接続して、ファイルを読み込んだり保存したりできます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="22d0d-165">Table Storage: 関数アプリからキー/値のストレージを操作します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="22d0d-166">Queue Storage: キューからの項目の取得、または新しい項目のキューへの配置を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="22d0d-167">次の *functions.json* ファイルの例では、トリガーとバインドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="22d0d-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="22d0d-168">この例では、`images` コンテナー内での BLOB ストレージに対する変更によって関数がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="22d0d-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="22d0d-169">ファイルの情報が渡され、トリガーはバインドとしても機能します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="22d0d-170">`images` という名前のキューに情報を格納するための別のバインドが存在します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="22d0d-171">関数の C# スクリプトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="22d0d-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="22d0d-172">この例は、BLOB ストレージ内の変更またはアップロードされたファイルの名前を取得し、後で処理するためにキューに配置する単純な関数です。</span><span class="sxs-lookup"><span data-stu-id="22d0d-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="22d0d-173">トリガーとバインドの完全な一覧については、「[Azure Functions でのトリガーとバインドの概念](/azure/azure-functions/functions-triggers-bindings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22d0d-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="22d0d-174">[前へ](azure-serverless-platform.md)
>[次へ](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="22d0d-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
