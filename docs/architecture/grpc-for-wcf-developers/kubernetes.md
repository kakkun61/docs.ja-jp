---
title: WCF 開発者向け Kubernetes-gRPC
description: Kubernetes クラスターで ASP.NET Core gRPC サービスを実行しています。
ms.date: 12/15/2020
ms.openlocfilehash: 0b457d6fa982b5f5b983194d4aedbff0eb782f36
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938061"
---
# <a name="kubernetes"></a><span data-ttu-id="026de-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="026de-103">Kubernetes</span></span>

<span data-ttu-id="026de-104">Docker ホストでコンテナーを手動で実行することもできますが、信頼性の高い運用システムの場合は、コンテナーオーケストレーションエンジンを使用して、クラスター内の複数のサーバーで実行されている複数のインスタンスを管理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="026de-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's better to use a container orchestration engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="026de-105">さまざまなコンテナーオーケストレーションエンジンが用意されています。これには、Kubernetes、Docker の群れ、Apache のシステムなどがあります。</span><span class="sxs-lookup"><span data-stu-id="026de-105">There are various container orchestration engines available, including Kubernetes, Docker Swarm, and Apache Mesos.</span></span> <span data-ttu-id="026de-106">しかし、これらのエンジンでは、Kubernetes ははるかに広く使用されているので、この章で重点的に説明します。</span><span class="sxs-lookup"><span data-stu-id="026de-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="026de-107">Kubernetes には、次の機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="026de-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="026de-108">**スケジュール設定** では、クラスター内の複数のノードでコンテナーを実行し、使用可能なリソースのバランスの取れた使用状況を確保し、障害が発生した場合はコンテナーを実行したままにして、新しいバージョンのイメージまたは新しい構成へのローリング更新を処理します。</span><span class="sxs-lookup"><span data-stu-id="026de-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="026de-109">**正常性チェック** は、コンテナーを監視してサービスを継続的に確認します。</span><span class="sxs-lookup"><span data-stu-id="026de-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="026de-110">**DNS & サービス検出** は、クラスター内のサービス間のルーティングを処理します。</span><span class="sxs-lookup"><span data-stu-id="026de-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="026de-111">受信は、選択したサービスを外部 **に公開し**、一般にこれらのサービスのインスタンス間で負荷分散を行います。</span><span class="sxs-lookup"><span data-stu-id="026de-111">**Ingress** exposes selected services externally and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="026de-112">**リソース管理** は、ストレージなどの外部リソースをコンテナーにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="026de-112">**Resource management** attaches external resources like storage to containers.</span></span>

<span data-ttu-id="026de-113">この章では、ASP.NET Core gRPC サービスと、サービスを使用する web サイトを Kubernetes クラスターにデプロイする方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="026de-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="026de-114">使用されるサンプルアプリケーションは、GitHub の [dotnet/grpc-wcf 開発者](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) リポジトリで入手できます。</span><span class="sxs-lookup"><span data-stu-id="026de-114">The sample application used is available in the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="026de-115">Kubernetes の用語</span><span class="sxs-lookup"><span data-stu-id="026de-115">Kubernetes terminology</span></span>

<span data-ttu-id="026de-116">Kubernetes は *desired state configuration* を使用します。この API は *ポッド*、*デプロイ*、*サービス* などのオブジェクトを表すために使用され、*コントロールプレーン* は *クラスター* 内のすべての *ノード* で目的の状態を実装します。</span><span class="sxs-lookup"><span data-stu-id="026de-116">Kubernetes uses *desired state configuration*: the API is used to describe objects like *Pods*, *Deployments*, and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="026de-117">Kubernetes クラスターには、 *KUBERNETES API* を実行する *マスター* ノードがあります。このノードは、プログラムによって、またはコマンドラインツールを使用して通信できます `kubectl` 。</span><span class="sxs-lookup"><span data-stu-id="026de-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which you can communicate with programmatically or by using the `kubectl` command-line tool.</span></span> <span data-ttu-id="026de-118">`kubectl` では、コマンドライン引数を使用してオブジェクトを作成および管理できますが、Kubernetes オブジェクトの宣言データを含む YAML ファイルで最適に動作します。</span><span class="sxs-lookup"><span data-stu-id="026de-118">`kubectl` can create and manage objects through command-line arguments, but it works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="026de-119">Kubernetes YAML ファイル</span><span class="sxs-lookup"><span data-stu-id="026de-119">Kubernetes YAML files</span></span>

<span data-ttu-id="026de-120">すべての Kubernetes YAML ファイルには、少なくとも3つの最上位レベルのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="026de-120">Every Kubernetes YAML file will have at least three top-level properties:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="026de-121">プロパティは、 `apiVersion` ファイルの対象となるバージョン (および API) を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="026de-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="026de-122">プロパティは、 `kind` YAML が表すオブジェクトの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="026de-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="026de-123">プロパティには `metadata` 、、、などのオブジェクトプロパティが含まれてい `name` `namespace` `labels` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-123">The `metadata` property contains object properties like `name`, `namespace`, and `labels`.</span></span>

<span data-ttu-id="026de-124">ほとんどの Kubernetes YAML ファイルには、 `spec` オブジェクトの作成に必要なリソースと構成を説明するセクションもあります。</span><span class="sxs-lookup"><span data-stu-id="026de-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="026de-125">ポッド</span><span class="sxs-lookup"><span data-stu-id="026de-125">Pods</span></span>

<span data-ttu-id="026de-126">ポッドは、Kubernetes での実行の基本単位です。</span><span class="sxs-lookup"><span data-stu-id="026de-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="026de-127">複数のコンテナーを実行できますが、1つのコンテナーを実行するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="026de-127">They can run multiple containers, but they're also used to run single containers.</span></span> <span data-ttu-id="026de-128">ポッドには、コンテナーに必要なすべてのストレージリソースと、ネットワークの IP アドレスも含まれています。</span><span class="sxs-lookup"><span data-stu-id="026de-128">The pod also includes any storage resources required by the containers, and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="026de-129">サービス</span><span class="sxs-lookup"><span data-stu-id="026de-129">Services</span></span>

<span data-ttu-id="026de-130">サービスは、ポッド (またはポッドのセット) を記述し、クラスター内でそれらにアクセスする手段を提供するメタオブジェクトです。たとえば、クラスター DNS サービスを使用して、サービス名をポッド IP アドレスのセットにマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="026de-130">Services are meta-objects that describe Pods (or sets of Pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses by using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="026de-131">デプロイメント</span><span class="sxs-lookup"><span data-stu-id="026de-131">Deployments</span></span>

<span data-ttu-id="026de-132">展開は、ポッドに *必要な状態* オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="026de-132">Deployments are the *desired state* objects for Pods.</span></span> <span data-ttu-id="026de-133">ポッドを手動で作成した場合は、終了時に再起動されません。</span><span class="sxs-lookup"><span data-stu-id="026de-133">If you create a pod manually, it won't be restarted when it terminates.</span></span> <span data-ttu-id="026de-134">デプロイは、現在の時点で実行する必要があるポッド、およびそれらのポッドのレプリカの数をクラスターに伝えるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="026de-134">Deployments are used to tell the cluster which Pods, and how many replicas of those Pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="026de-135">その他のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="026de-135">Other objects</span></span>

<span data-ttu-id="026de-136">ポッド、サービス、および展開は、最も基本的なオブジェクトの種類のうちの3つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="026de-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="026de-137">Kubernetes クラスターによって管理されるオブジェクトの種類は他にも多数あります。</span><span class="sxs-lookup"><span data-stu-id="026de-137">There are dozens of other object types that are managed by Kubernetes clusters.</span></span> <span data-ttu-id="026de-138">詳細については、 [Kubernetes の概念](https://kubernetes.io/docs/concepts/) に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="026de-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="026de-139">名前空間</span><span class="sxs-lookup"><span data-stu-id="026de-139">Namespaces</span></span>

<span data-ttu-id="026de-140">Kubernetes クラスターは、数百または数千のノードに拡張し、同様の数のサービスを実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="026de-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes and to run similar numbers of services.</span></span> <span data-ttu-id="026de-141">オブジェクト名が競合しないようにするために、名前空間を使用して、大きなアプリケーションの一部としてオブジェクトをグループ化します。</span><span class="sxs-lookup"><span data-stu-id="026de-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="026de-142">Kubernetes の独自のサービスは名前空間で実行さ `default` れます。</span><span class="sxs-lookup"><span data-stu-id="026de-142">Kubernetes's own services run in a `default` namespace.</span></span> <span data-ttu-id="026de-143">既定のオブジェクトまたはクラスター内の他のテナントとの潜在的な競合を避けるために、すべてのユーザーオブジェクトを独自の名前空間に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="026de-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="026de-144">Kubernetes の概要</span><span class="sxs-lookup"><span data-stu-id="026de-144">Get started with Kubernetes</span></span>

<span data-ttu-id="026de-145">Windows 用の Docker Desktop または Mac 用 Docker デスクトップを実行している場合、Kubernetes は既に使用可能です。</span><span class="sxs-lookup"><span data-stu-id="026de-145">If you're running Docker Desktop for Windows or Docker Desktop for Mac, Kubernetes is already available.</span></span> <span data-ttu-id="026de-146">[**設定**] ウィンドウの [ **Kubernetes** ] セクションで有効にするだけです。</span><span class="sxs-lookup"><span data-stu-id="026de-146">Just enable it in the **Kubernetes** section of the **Settings** window:</span></span>

![Docker Desktop で Kubernetes を有効にする](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

<span data-ttu-id="026de-148">Linux でローカル Kubernetes クラスターを実行する場合は、Linux ディストリビューションで[スナップ](https://snapcraft.io/)がサポートされている場合は[Minikube](https://github.com/kubernetes/minikube)または[MicroK8s](https://microk8s.io/)を検討してください。</span><span class="sxs-lookup"><span data-stu-id="026de-148">To run a local Kubernetes cluster on Linux, consider [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="026de-149">クラスターが実行されていて、アクセス可能であることを確認するには、次のコマンドを実行し `kubectl version` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-149">To confirm that your cluster is running and accessible, run the `kubectl version` command:</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="026de-150">この例で `kubectl` は、CLI と Kubernetes サーバーの両方でバージョン1.14.6 が実行されています。</span><span class="sxs-lookup"><span data-stu-id="026de-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="026de-151">の各バージョン `kubectl` は、サーバーの以前のバージョンと次のバージョンをサポートすることを想定しているため、 `kubectl` 1.14 はサーバーバージョン1.13 と1.15 でも動作します。</span><span class="sxs-lookup"><span data-stu-id="026de-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="026de-152">Kubernetes でサービスを実行する</span><span class="sxs-lookup"><span data-stu-id="026de-152">Run services on Kubernetes</span></span>

<span data-ttu-id="026de-153">サンプルアプリケーションには、 `kube` 3 つの YAML ファイルを含むディレクトリがあります。</span><span class="sxs-lookup"><span data-stu-id="026de-153">The sample application has a `kube` directory that contains three YAML files.</span></span> <span data-ttu-id="026de-154">ファイルは、 `namespace.yml` カスタム名前空間を宣言 `stocks` します。</span><span class="sxs-lookup"><span data-stu-id="026de-154">The `namespace.yml` file declares a custom namespace: `stocks`.</span></span> <span data-ttu-id="026de-155">`stockdata.yml`ファイルは grpc アプリケーションのデプロイとサービスを宣言し、 `stockweb.yml` ファイルは grpc サービスを使用する ASP.NET CORE 5.0 MVC web アプリケーションのデプロイとサービスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="026de-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 5.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="026de-156">でファイルを使用するには `YAML` `kubectl` 、次のコマンドを実行し `apply -f` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-156">To use a `YAML` file with `kubectl`, run the `apply -f` command:</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="026de-157">コマンドは、 `apply` YAML ファイルの有効性を確認し、API から受信したすべてのエラーを表示しますが、ファイルで宣言されているすべてのオブジェクトが作成されるまで待機しません。これは、この手順に時間がかかることがあるためです。</span><span class="sxs-lookup"><span data-stu-id="026de-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created because this step can take some time.</span></span> <span data-ttu-id="026de-158">コマンドと関連するオブジェクトの種類を使用して、 `kubectl get` クラスターでのオブジェクトの作成を確認します。</span><span class="sxs-lookup"><span data-stu-id="026de-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="026de-159">名前空間の宣言</span><span class="sxs-lookup"><span data-stu-id="026de-159">The namespace declaration</span></span>

<span data-ttu-id="026de-160">名前空間の宣言は単純であり、を割り当てるだけで済み `name` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-160">Namespace declaration is simple and requires only assigning a `name`:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="026de-161">を使用して `kubectl` ファイルを適用 `namespace.yml` し、名前空間が正常に作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="026de-161">Use `kubectl` to apply the `namespace.yml` file and to confirm the namespace is created successfully:</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="026de-162">StockData アプリケーション</span><span class="sxs-lookup"><span data-stu-id="026de-162">The StockData application</span></span>

<span data-ttu-id="026de-163">`stockdata.yml`ファイルは、配置とサービスという2つのオブジェクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="026de-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="026de-164">StockData のデプロイ</span><span class="sxs-lookup"><span data-stu-id="026de-164">The StockData Deployment</span></span>

<span data-ttu-id="026de-165">YAML ファイルの配置部分には、 `spec` 必要なレプリカの数を含む、デプロイ自体のが用意されています。また、は、 `template` 配置によって作成および管理される Pod オブジェクトのを提供します。</span><span class="sxs-lookup"><span data-stu-id="026de-165">The Deployment part of the YAML file provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="026de-166">配置オブジェクトは `apps` `apiVersion` 、メインの Kubernetes api ではなく、で指定された api によって管理されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="026de-166">Note that Deployment objects are managed by the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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
  replicas: 1
  template:
    metadata:
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

<span data-ttu-id="026de-167">`spec.selector`プロパティは、実行中のポッドをデプロイと照合するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="026de-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="026de-168">ポッドのプロパティがプロパティと一致して `metadata.labels` いる必要があります。指定しないと、 `matchLabels` API 呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="026de-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="026de-169">セクションでは、 `template.spec` 実行するコンテナーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="026de-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="026de-170">Docker Desktop によって提供されるものなど、ローカル Kubernetes クラスターを使用している場合は、バージョンタグがある限り、ローカルでビルドされたイメージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="026de-170">When you're working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="026de-171">既定では、Kubernetes は常にを確認し、新しいイメージをプルしようとします。</span><span class="sxs-lookup"><span data-stu-id="026de-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="026de-172">既知のリポジトリにイメージが見つからない場合、ポッドの作成は失敗します。</span><span class="sxs-lookup"><span data-stu-id="026de-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="026de-173">ローカルイメージを操作するには、 `imagePullPolicy` をに設定し `Never` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="026de-174">プロパティは、 `ports` ポッドで公開するコンテナーポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="026de-174">The `ports` property specifies which container ports should be published on the Pod.</span></span> <span data-ttu-id="026de-175">`stockservice`イメージは標準の HTTP ポートでサービスを実行するので、ポート80が公開されます。</span><span class="sxs-lookup"><span data-stu-id="026de-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="026de-176">セクションでは、 `resources` ポッド内で実行されているコンテナーにリソースの制限を適用します。</span><span class="sxs-lookup"><span data-stu-id="026de-176">The `resources` section applies resource limits to the container running within the Pod.</span></span> <span data-ttu-id="026de-177">これは、個々のポッドがノード上の使用可能な CPU またはメモリをすべて消費しないようにするため、この方法が適しています。</span><span class="sxs-lookup"><span data-stu-id="026de-177">This is a good practice because it prevents an individual Pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="026de-178">ASP.NET Core 5.0 は、リソースが制限されたコンテナーで実行するように最適化およびチューニングされています。</span><span class="sxs-lookup"><span data-stu-id="026de-178">ASP.NET Core 5.0 has been optimized and tuned to run in resource-limited containers.</span></span> <span data-ttu-id="026de-179">Docker イメージは、環境変数を設定して、 `dotnet/core/aspnet` `dotnet` それがコンテナー内にあることをランタイムに通知します。</span><span class="sxs-lookup"><span data-stu-id="026de-179">The `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="026de-180">StockData サービス</span><span class="sxs-lookup"><span data-stu-id="026de-180">The StockData Service</span></span>

<span data-ttu-id="026de-181">YAML ファイルのサービス部分では、クラスター内のポッドへのアクセスを提供するサービスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="026de-181">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

<span data-ttu-id="026de-182">サービスは、 `spec` プロパティを使用し `selector` て実行を照合し `Pods` ます。この例では、ラベルを持つポッドを探し `run: stockdata` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-182">The Service `spec` uses the `selector` property to match running `Pods`, in this case looking for Pods that have a label `run: stockdata`.</span></span> <span data-ttu-id="026de-183">一致するポッドに指定されたは、 `port` 名前付きサービスによって発行されます。</span><span class="sxs-lookup"><span data-stu-id="026de-183">The specified `port` on matching Pods is published by the named service.</span></span> <span data-ttu-id="026de-184">名前空間で実行されている他のポッド `stocks` は、アドレスとしてを使用して、このサービスの HTTP にアクセスでき `http://stockdata` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-184">Other Pods running in the `stocks` namespace can access HTTP on this service by using `http://stockdata` as the address.</span></span> <span data-ttu-id="026de-185">他の名前空間で実行されているポッドは、ホスト名を使用でき `http://stockdata.stocks` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-185">Pods running in other namespaces can use the `http://stockdata.stocks` host name.</span></span> <span data-ttu-id="026de-186">[ネットワークポリシー](https://kubernetes.io/docs/concepts/services-networking/network-policies/)を使用して、名前空間間サービスアクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="026de-186">You can control cross-namespace service access by using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="026de-187">StockData アプリケーションをデプロイする</span><span class="sxs-lookup"><span data-stu-id="026de-187">Deploy the StockData application</span></span>

<span data-ttu-id="026de-188">を使用して `kubectl` ファイルを適用 `stockdata.yml` し、展開とサービスが作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="026de-188">Use `kubectl` to apply the `stockdata.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a><span data-ttu-id="026de-189">StockWeb アプリケーション</span><span class="sxs-lookup"><span data-stu-id="026de-189">The StockWeb application</span></span>

<span data-ttu-id="026de-190">ファイルは、 `stockweb.yml` MVC アプリケーションのデプロイとサービスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="026de-190">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a><span data-ttu-id="026de-191">環境変数</span><span class="sxs-lookup"><span data-stu-id="026de-191">Environment variables</span></span>

<span data-ttu-id="026de-192">`env`Deployment オブジェクトのセクションでは、イメージを実行しているコンテナーに設定する環境変数を指定し `stockweb:1.0.0` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-192">The `env` section of the Deployment object specifies environment variables to be set in the container that's running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="026de-193">**`StockData__Address`** 環境変数は、 `StockData:Address` EnvironmentVariables 構成プロバイダーによって構成設定にマップされます。</span><span class="sxs-lookup"><span data-stu-id="026de-193">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="026de-194">この設定では、名前の間に2つのアンダースコアを使用し、セクションを区切ります。</span><span class="sxs-lookup"><span data-stu-id="026de-194">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="026de-195">このアドレスは、 `stockdata` 同じ Kubernetes 名前空間で実行されているサービスのサービス名を使用します。</span><span class="sxs-lookup"><span data-stu-id="026de-195">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="026de-196">**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** 環境変数は、 <xref:System.AppContext> の暗号化されていない HTTP/2 接続を有効にするスイッチを設定し <xref:System.Net.Http.HttpClient> ます。</span><span class="sxs-lookup"><span data-stu-id="026de-196">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="026de-197">この環境変数は、次に示すように、コードでスイッチを設定するのと同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="026de-197">This environment variable does the same thing as setting the switch in code, as shown here:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="026de-198">スイッチに環境変数を使用すると、アプリケーションが実行されているコンテキストに応じてコンテキストを簡単に変更できます。</span><span class="sxs-lookup"><span data-stu-id="026de-198">If you use an environment variable for the switch, you can easily change the context depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="026de-199">サービスの種類</span><span class="sxs-lookup"><span data-stu-id="026de-199">Service types</span></span>

<span data-ttu-id="026de-200">`type: NodePort`プロパティは、クラスターの外部から web アプリケーションにアクセスできるようにするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="026de-200">The `type: NodePort` property is used to make the web application accessible from outside the cluster.</span></span> <span data-ttu-id="026de-201">このプロパティの種類を Kubernetes と、サービスのポート80がクラスターの外部ネットワークソケットの任意のポートに発行されます。</span><span class="sxs-lookup"><span data-stu-id="026de-201">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="026de-202">割り当てられたポートは、コマンドを使用して見つけることができ `kubectl get service` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-202">You can find the assigned port by using the `kubectl get service` command.</span></span>

<span data-ttu-id="026de-203">`stockdata`クラスターの外部からサービスにアクセスできないようにするため、既定の種類のを使用し `ClusterIP` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-203">The `stockdata` Service shouldn't be accessible from outside the cluster, so it uses the default type, `ClusterIP`.</span></span>

<span data-ttu-id="026de-204">実稼働システムでは、通常、統合されたロードバランサーを使用して、パブリックアプリケーションを外部のコンシューマーに公開します。</span><span class="sxs-lookup"><span data-stu-id="026de-204">Production systems will most likely use an integrated load balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="026de-205">この方法で公開されるサービスでは、型を使用する必要があり `LoadBalancer` ます。</span><span class="sxs-lookup"><span data-stu-id="026de-205">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="026de-206">サービスの種類の詳細については、 [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="026de-206">For more information on Service types, see the [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="026de-207">StockWeb アプリケーションをデプロイする</span><span class="sxs-lookup"><span data-stu-id="026de-207">Deploy the StockWeb application</span></span>

<span data-ttu-id="026de-208">を使用して `kubectl` ファイルを適用 `stockweb.yml` し、展開とサービスが作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="026de-208">Use `kubectl` to apply the `stockweb.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

<span data-ttu-id="026de-209">コマンドの出力は、 `get service` HTTP ポートが `32564` 外部ネットワーク上のポートに発行されていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="026de-209">The output of the `get service` command shows that the HTTP port has been published to port `32564` on the external network.</span></span> <span data-ttu-id="026de-210">Docker Desktop の場合、この IP アドレスは localhost になります。</span><span class="sxs-lookup"><span data-stu-id="026de-210">For Docker Desktop, this IP address will be localhost.</span></span> <span data-ttu-id="026de-211">アプリケーションにアクセスするには、を参照 `http://localhost:32564` します。</span><span class="sxs-lookup"><span data-stu-id="026de-211">You can access the application by browsing to `http://localhost:32564`.</span></span>

### <a name="test-the-application"></a><span data-ttu-id="026de-212">アプリケーションをテストする</span><span class="sxs-lookup"><span data-stu-id="026de-212">Test the application</span></span>

<span data-ttu-id="026de-213">StockWeb アプリケーションでは、単純な要求/応答サービスから取得された NASDAQ 株式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="026de-213">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="026de-214">このデモでは、各行には、それを返したサービスインスタンスの一意の ID も表示されます。</span><span class="sxs-lookup"><span data-stu-id="026de-214">For this demonstration, each line also shows the unique ID of the Service instance that returned it.</span></span>

![StockWeb スクリーンショット](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="026de-216">サービスのレプリカの数が増加した場合は、 `stockdata` **サーバー** の値が行ごとに変更されることが予想されますが、実際には、100のすべてのレコードが常に同じインスタンスから返されます。</span><span class="sxs-lookup"><span data-stu-id="026de-216">If the number of replicas of the `stockdata` Service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="026de-217">数秒ごとにページを更新した場合、サーバー ID は変わりません。</span><span class="sxs-lookup"><span data-stu-id="026de-217">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="026de-218">なぜこのようになるのですか?</span><span class="sxs-lookup"><span data-stu-id="026de-218">Why does this happen?</span></span> <span data-ttu-id="026de-219">ここでは2つの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="026de-219">There are two factors at play here.</span></span>

<span data-ttu-id="026de-220">まず、Kubernetes Service discovery システムは、既定でラウンドロビンの負荷分散を使用します。</span><span class="sxs-lookup"><span data-stu-id="026de-220">First, the Kubernetes Service discovery system uses round-robin load balancing by default.</span></span> <span data-ttu-id="026de-221">最初に DNS サーバーにクエリを実行すると、サービスに対して最初に一致する IP アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="026de-221">The first time the DNS server is queried, it will return the first matching IP address for the Service.</span></span> <span data-ttu-id="026de-222">次に、リスト内の次の IP アドレスを返します。これは最後まで続きます。</span><span class="sxs-lookup"><span data-stu-id="026de-222">The next time, it will return the next IP address in the list, and so on, until the end.</span></span> <span data-ttu-id="026de-223">その時点で、start にループバックします。</span><span class="sxs-lookup"><span data-stu-id="026de-223">At that point, it loops back to the start.</span></span>

<span data-ttu-id="026de-224">次に、 `HttpClient` StockWeb アプリケーションの gRPC クライアントに使用されるが [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)によって作成および管理され、このクライアントの1つのインスタンスがページへのすべての呼び出しに使用されます。</span><span class="sxs-lookup"><span data-stu-id="026de-224">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="026de-225">クライアントは DNS 参照を1つだけ行うため、すべての要求が同じ IP アドレスにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="026de-225">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="026de-226">また、はパフォーマンス上の理由でキャッシュされているため、 `HttpClientHandler` 複数の要求が同時に同じ IP アドレスを使用します。キャッシュされた DNS エントリの有効期限が切れるか、何らかの理由でハンドラーインスタンスが破棄さ *れ* ます。</span><span class="sxs-lookup"><span data-stu-id="026de-226">And because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="026de-227">その結果、既定では、gRPC サービスへの要求は、クラスター内のそのサービスのすべてのインスタンスでバランスが取れていないことになります。</span><span class="sxs-lookup"><span data-stu-id="026de-227">The result is that by default requests to a gRPC Service aren't balanced across all instances of that Service in the cluster.</span></span> <span data-ttu-id="026de-228">コンシューマーによって使用されるインスタンスは異なりますが、要求の配布やリソースのバランスの取れた使用は保証されません。</span><span class="sxs-lookup"><span data-stu-id="026de-228">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests or a balanced use of resources.</span></span>

<span data-ttu-id="026de-229">次の章「 [サービスメッシュ](service-mesh.md)」では、この問題に対処します。</span><span class="sxs-lookup"><span data-stu-id="026de-229">The next chapter, [Service meshes](service-mesh.md), will address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="026de-230">[前へ](docker.md)
>[次へ](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="026de-230">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
