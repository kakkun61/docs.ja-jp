---
title: サービスメッシュ-WCF 開発者向け gRPC
description: サービスメッシュを使用して、Kubernetes クラスター内の gRPC サービスに要求をルーティングおよび分散します。
ms.date: 12/15/2020
ms.openlocfilehash: a1c72a4facf1c133af912bbee242328653a051b6
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938131"
---
# <a name="service-meshes"></a><span data-ttu-id="adcdf-103">サービス メッシュ</span><span class="sxs-lookup"><span data-stu-id="adcdf-103">Service meshes</span></span>

<span data-ttu-id="adcdf-104">サービスメッシュは、ネットワーク内のルーティングサービス要求を制御するインフラストラクチャコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="adcdf-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="adcdf-105">サービスメッシュは、Kubernetes クラスター内のあらゆる種類のネットワークレベルの問題を処理できます。これには次のものが含まれる。</span><span class="sxs-lookup"><span data-stu-id="adcdf-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="adcdf-106">サービス検出</span><span class="sxs-lookup"><span data-stu-id="adcdf-106">Service discovery</span></span>
- <span data-ttu-id="adcdf-107">負荷分散</span><span class="sxs-lookup"><span data-stu-id="adcdf-107">Load balancing</span></span>
- <span data-ttu-id="adcdf-108">フォールト トレランス</span><span class="sxs-lookup"><span data-stu-id="adcdf-108">Fault tolerance</span></span>
- <span data-ttu-id="adcdf-109">暗号化</span><span class="sxs-lookup"><span data-stu-id="adcdf-109">Encryption</span></span>
- <span data-ttu-id="adcdf-110">監視</span><span class="sxs-lookup"><span data-stu-id="adcdf-110">Monitoring</span></span>

<span data-ttu-id="adcdf-111">Kubernetes サービスメッシュは、メッシュに含まれる各ポッドにサイドカー *プロキシ* と呼ばれる追加のコンテナーを追加することによって機能します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="adcdf-112">プロキシは、すべての受信および送信ネットワーク要求の処理を引き継ぎます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="adcdf-113">その後、ネットワークの構成と管理は、アプリケーションコンテナーとは別に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-113">You can then keep the configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="adcdf-114">多くの場合、この分離によってアプリケーションコードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="adcdf-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="adcdf-115">[前の章の例](kubernetes.md#test-the-application)では、web アプリケーションからの grpc 要求はすべて、grpc サービスの1つのインスタンスにルーティングされていました。</span><span class="sxs-lookup"><span data-stu-id="adcdf-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="adcdf-116">これは、サービスのホスト名が IP アドレスに解決され、その IP アドレスがインスタンスの有効期間にわたってキャッシュされているために発生し `HttpClientHandler` ます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="adcdf-117">DNS 参照を手動で処理したり、複数のクライアントを作成したりすることによって、この動作を回避できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="adcdf-117">It might be possible to work around this behavior by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="adcdf-118">ただし、この回避策を使用すると、ビジネスや顧客の価値を追加することなく、アプリケーションコードが複雑になります。</span><span class="sxs-lookup"><span data-stu-id="adcdf-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="adcdf-119">サービスメッシュを使用すると、アプリケーションコンテナーからの要求がサイドカープロキシに送信されます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="adcdf-120">その後、サイドカープロキシは、他のサービスのすべてのインスタンスに対してインテリジェントな配信を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="adcdf-121">メッシュは次のようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-121">The mesh can also:</span></span>

- <span data-ttu-id="adcdf-122">サービスの個々のインスタンスの障害にシームレスに対応できます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="adcdf-123">失敗した呼び出しまたはタイムアウトの再試行セマンティクスを処理します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="adcdf-124">クライアントアプリケーションに戻らずに、別のインスタンスに失敗した要求を再ルーティングします。</span><span class="sxs-lookup"><span data-stu-id="adcdf-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="adcdf-125">次のスクリーンショットは、Linkerd サービスメッシュで実行されている StockWeb アプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="adcdf-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="adcdf-126">アプリケーションコードが変更されていないため、Docker イメージが使用されていません。</span><span class="sxs-lookup"><span data-stu-id="adcdf-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="adcdf-127">必要な変更は、およびサービスの YAML ファイルの配置に注釈を追加することだけでした `stockdata` `stockweb` 。</span><span class="sxs-lookup"><span data-stu-id="adcdf-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![サービスメッシュを使用した StockWeb](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="adcdf-129">アプリケーションコードの1つのインスタンスから送信された場合でも、StockWeb アプリケーションからの要求が Stockweb サービスの両方のレプリカにルーティングされていることを、[ **サーバー** ] 列から確認でき `HttpClient` ます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="adcdf-130">実際には、コードを確認すると、同じインスタンスを使用して、StockData サービスに対する100要求がすべて同時に実行されていることがわかります `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="adcdf-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="adcdf-131">サービスメッシュでは、これらの要求は分散されますが、多くのサービスインスタンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="adcdf-132">サービスメッシュは、クラスター内のトラフィックにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="adcdf-133">外部クライアントの場合は、次の章「 [負荷分散](load-balancing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adcdf-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="adcdf-134">サービスメッシュオプション</span><span class="sxs-lookup"><span data-stu-id="adcdf-134">Service mesh options</span></span>

<span data-ttu-id="adcdf-135">現在、Kubernetes: [iLinkerd o](https://istio.io)、 [](https://linkerd.io)、 [consul Connect](https://consul.io/mesh.html)では、3つの汎用サービスメッシュ実装を使用できます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="adcdf-136">3つすべては、要求のルーティング/プロキシ、トラフィックの暗号化、回復性、ホストからホストへの認証、およびトラフィック制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="adcdf-137">サービスメッシュの選択は、次の複数の要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="adcdf-138">コスト、コンプライアンス、有償サポートプランなどに関する組織固有の要件。</span><span class="sxs-lookup"><span data-stu-id="adcdf-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="adcdf-139">クラスターの特性、サイズ、デプロイされたサービスの数、およびクラスターネットワーク内のトラフィックの量。</span><span class="sxs-lookup"><span data-stu-id="adcdf-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="adcdf-140">メッシュのデプロイと管理を容易にし、サービスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="adcdf-141">例: デプロイへの Linkerd の追加</span><span class="sxs-lookup"><span data-stu-id="adcdf-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="adcdf-142">この例では、[前のセクション](kubernetes.md)の *StockKube* アプリケーションで Linkerd service メッシュを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="adcdf-143">この例を実行するには、 [LINKERD CLI をインストール](https://linkerd.io/2/getting-started/#step-1-install-the-cli)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adcdf-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="adcdf-144">Windows バイナリは、GitHub リリースを一覧にしたセクションからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="adcdf-145">エッジリリースの1つではなく、最新の *安定* したリリースを使用してください。</span><span class="sxs-lookup"><span data-stu-id="adcdf-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="adcdf-146">Linkerd CLI がインストールされている状態で、 [はじめに](https://linkerd.io/2/getting-started/index.html) の指示に従って、Kubernetes クラスターに Linkerd コンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="adcdf-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="adcdf-147">手順は簡単であり、インストールにはローカル Kubernetes インスタンスで数分しかかかることはありません。</span><span class="sxs-lookup"><span data-stu-id="adcdf-147">The instructions are straightforward, and the installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="adcdf-148">Linkerd を Kubernetes デプロイに追加する</span><span class="sxs-lookup"><span data-stu-id="adcdf-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="adcdf-149">Linkerd CLI には、 `inject` 必要なセクションとプロパティを Kubernetes ファイルに追加するコマンドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="adcdf-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="adcdf-150">コマンドを実行し、出力を新しいファイルに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="adcdf-151">新しいファイルを調べて、どのような変更が加えられたかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="adcdf-152">配置オブジェクトの場合、メタデータ注釈が追加され、Linkerd が作成時にサイドカープロキシコンテナーをポッドに挿入するように指示します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="adcdf-153">パイプを使用してコマンドの出力をに直接送ることもでき `linkerd inject` `kubectl` ます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="adcdf-154">次のコマンドは、PowerShell または任意の Linux シェルで動作します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="adcdf-155">Linkerd ダッシュボードでサービスを検査する</span><span class="sxs-lookup"><span data-stu-id="adcdf-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="adcdf-156">CLI を使用して Linkerd ダッシュボードを開き `linkerd` ます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="adcdf-157">ダッシュボードには、メッシュに接続されているすべてのサービスに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adcdf-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![StockKube アプリケーションを示す Linkerd ダッシュボード](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="adcdf-159">次の例に示すように StockData gRPC サービスのレプリカの数を増やした場合、ブラウザーで Stockdata ページを更新すると、[ **サーバー** ] 列に id が混在していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="adcdf-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="adcdf-160">このミックスは、使用可能なすべてのインスタンスが要求を処理していることを示します。</span><span class="sxs-lookup"><span data-stu-id="adcdf-160">This mix indicates that all the available instances are serving requests.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

>[!div class="step-by-step"]
><span data-ttu-id="adcdf-161">[前へ](kubernetes.md)
>[次へ](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="adcdf-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
