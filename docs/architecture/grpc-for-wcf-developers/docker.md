---
title: WCF 開発者向け Docker-gRPC
description: ASP.NET Core gRPC アプリケーション用の Docker イメージの作成
ms.date: 09/02/2019
ms.openlocfilehash: 0a680d0918868829042e521506fa8c1a1628bf5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688446"
---
# <a name="create-docker-images"></a><span data-ttu-id="0199f-103">Docker イメージを作成する</span><span class="sxs-lookup"><span data-stu-id="0199f-103">Create Docker images</span></span>

<span data-ttu-id="0199f-104">このセクションでは、ASP.NET Core gRPC アプリケーション用の Docker イメージを作成する方法について説明します。 Docker、Kubernetes、またはその他のコンテナー環境で実行できます。</span><span class="sxs-lookup"><span data-stu-id="0199f-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="0199f-105">ASP.NET Core MVC web アプリおよび gRPC サービスと共に使用されるサンプルアプリケーションは、GitHub の [dotnet/grpc-wcf 開発者](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) リポジトリで入手できます。</span><span class="sxs-lookup"><span data-stu-id="0199f-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="0199f-106">ASP.NET Core アプリケーション用の Microsoft 基本イメージ</span><span class="sxs-lookup"><span data-stu-id="0199f-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="0199f-107">Microsoft では、.NET Core アプリケーションをビルドして実行するためのさまざまな基本イメージを提供しています。</span><span class="sxs-lookup"><span data-stu-id="0199f-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="0199f-108">ASP.NET Core 3.0 イメージを作成するには、次の2つの基本イメージを使用します。</span><span class="sxs-lookup"><span data-stu-id="0199f-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="0199f-109">アプリケーションをビルドして発行するための SDK イメージ。</span><span class="sxs-lookup"><span data-stu-id="0199f-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="0199f-110">配置のランタイムイメージ。</span><span class="sxs-lookup"><span data-stu-id="0199f-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="0199f-111">Image</span><span class="sxs-lookup"><span data-stu-id="0199f-111">Image</span></span> | <span data-ttu-id="0199f-112">説明</span><span class="sxs-lookup"><span data-stu-id="0199f-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="0199f-113">mcr.microsoft.com/dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="0199f-113">mcr.microsoft.com/dotnet/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-sdk/) | <span data-ttu-id="0199f-114">を使用してアプリケーションをビルド `docker build` します。</span><span class="sxs-lookup"><span data-stu-id="0199f-114">For building applications with `docker build`.</span></span> <span data-ttu-id="0199f-115">運用環境では使用されません。</span><span class="sxs-lookup"><span data-stu-id="0199f-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="0199f-116">mcr.microsoft.com/dotnet/aspnet</span><span class="sxs-lookup"><span data-stu-id="0199f-116">mcr.microsoft.com/dotnet/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | <span data-ttu-id="0199f-117">ランタイムと ASP.NET Core の依存関係を含みます。</span><span class="sxs-lookup"><span data-stu-id="0199f-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="0199f-118">運用環境向け。</span><span class="sxs-lookup"><span data-stu-id="0199f-118">For production.</span></span> |

<span data-ttu-id="0199f-119">各イメージには、タグによって識別される、異なる Linux ディストリビューションに基づく4つのバリエーションがあります。</span><span class="sxs-lookup"><span data-stu-id="0199f-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="0199f-120">イメージタグ</span><span class="sxs-lookup"><span data-stu-id="0199f-120">Image tag(s)</span></span> | <span data-ttu-id="0199f-121">Linux</span><span class="sxs-lookup"><span data-stu-id="0199f-121">Linux</span></span> | <span data-ttu-id="0199f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="0199f-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="0199f-123">3.0-buster、3.0</span><span class="sxs-lookup"><span data-stu-id="0199f-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="0199f-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="0199f-124">Debian 10</span></span> | <span data-ttu-id="0199f-125">OS バリアントが指定されていない場合の既定のイメージ。</span><span class="sxs-lookup"><span data-stu-id="0199f-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="0199f-126">3.0-アルペン</span><span class="sxs-lookup"><span data-stu-id="0199f-126">3.0-alpine</span></span> | <span data-ttu-id="0199f-127">Alpine 3.9</span><span class="sxs-lookup"><span data-stu-id="0199f-127">Alpine 3.9</span></span> | <span data-ttu-id="0199f-128">Alpine base イメージは Debian または Ubuntu よりもはるかに小さいものです。</span><span class="sxs-lookup"><span data-stu-id="0199f-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="0199f-129">3.0-disco</span><span class="sxs-lookup"><span data-stu-id="0199f-129">3.0-disco</span></span> | <span data-ttu-id="0199f-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="0199f-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="0199f-131">3.0-bionic</span><span class="sxs-lookup"><span data-stu-id="0199f-131">3.0-bionic</span></span> | <span data-ttu-id="0199f-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0199f-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="0199f-133">Alpine base イメージは約 100 MB であり、Debian および Ubuntu イメージでは 200 MB と比較しています。</span><span class="sxs-lookup"><span data-stu-id="0199f-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="0199f-134">一部のソフトウェアパッケージまたはライブラリは、アルペンのパッケージ管理では利用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0199f-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="0199f-135">使用するイメージがわからない場合は、既定の Debian を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0199f-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0199f-136">ビルドとランタイムに同じ形式の Linux を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0199f-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="0199f-137">1つのバリアントでビルドおよび発行されたアプリケーションが、別のバリアントで動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0199f-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="0199f-138">Docker イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="0199f-138">Create a Docker image</span></span>

<span data-ttu-id="0199f-139">Docker イメージは、 *Dockerfile* によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="0199f-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="0199f-140">これは、アプリケーションを構築するために必要なすべてのコマンドを含むテキストファイルで、アプリケーションをビルドまたは実行するために必要なすべての依存関係をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0199f-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="0199f-141">次の例は、ASP.NET Core 3.0 アプリケーションの最も単純な Dockerfile を示しています。</span><span class="sxs-lookup"><span data-stu-id="0199f-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="0199f-142">Dockerfile には、2つの部分があります。1つ目は基本イメージを使用してアプリケーションをビルドし、発行します。 `sdk` 2 つ目はベースからランタイムイメージを作成します。 `aspnet`</span><span class="sxs-lookup"><span data-stu-id="0199f-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="0199f-143">これは、 `sdk` イメージは約 900 mb で、ランタイムイメージでは約 200 mb であり、ほとんどの内容は実行時には不要であるためです。</span><span class="sxs-lookup"><span data-stu-id="0199f-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="0199f-144">ビルドステップ</span><span class="sxs-lookup"><span data-stu-id="0199f-144">The build steps</span></span>

| <span data-ttu-id="0199f-145">手順</span><span class="sxs-lookup"><span data-stu-id="0199f-145">Step</span></span> | <span data-ttu-id="0199f-146">説明</span><span class="sxs-lookup"><span data-stu-id="0199f-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="0199f-147">基本イメージを宣言し、エイリアスを割り当て `builder` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="0199f-148">ディレクトリを作成 `/src` し、現在の作業ディレクトリとして設定します。</span><span class="sxs-lookup"><span data-stu-id="0199f-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="0199f-149">ホスト上の現在のディレクトリの下にあるものをすべて、イメージの現在のディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0199f-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="0199f-150">外部パッケージを復元します (ASP.NET Core 3.0 framework は SDK と共にプレインストールされています)。</span><span class="sxs-lookup"><span data-stu-id="0199f-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="0199f-151">リリースビルドをビルドして発行します。</span><span class="sxs-lookup"><span data-stu-id="0199f-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="0199f-152">フラグは必須ではないことに注意 `--runtime` してください。</span><span class="sxs-lookup"><span data-stu-id="0199f-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="0199f-153">ランタイムイメージの手順</span><span class="sxs-lookup"><span data-stu-id="0199f-153">The runtime image steps</span></span>

| <span data-ttu-id="0199f-154">手順</span><span class="sxs-lookup"><span data-stu-id="0199f-154">Step</span></span> | <span data-ttu-id="0199f-155">説明</span><span class="sxs-lookup"><span data-stu-id="0199f-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="0199f-156">新しい基本イメージを宣言します。</span><span class="sxs-lookup"><span data-stu-id="0199f-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="0199f-157">ディレクトリを作成 `/app` し、現在の作業ディレクトリとして設定します。</span><span class="sxs-lookup"><span data-stu-id="0199f-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="0199f-158">最初の行のエイリアスを使用して、発行されたアプリケーションを前のイメージからコピーし `builder` `FROM` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="0199f-159">コンテナーの起動時に実行するコマンドを設定します。</span><span class="sxs-lookup"><span data-stu-id="0199f-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="0199f-160">`dotnet`ランタイムイメージ内のコマンドは、DLL ファイルのみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0199f-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="0199f-161">Docker での HTTPS</span><span class="sxs-lookup"><span data-stu-id="0199f-161">HTTPS in Docker</span></span>

<span data-ttu-id="0199f-162">Docker 用の Microsoft 基本イメージは `ASPNETCORE_URLS` 、環境変数をに設定し `http://+:80` ます。これは、Kestrel が HTTPS を使用せずにそのポートで実行されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0199f-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="0199f-163">( [自己ホスト型 gRPC アプリケーション](self-hosted.md)で説明されているように) カスタム証明書と共に HTTPS を使用している場合は、これをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0199f-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="0199f-164">Dockerfile のランタイムイメージ作成部分で環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="0199f-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="0199f-165">Dockerignore ファイル</span><span class="sxs-lookup"><span data-stu-id="0199f-165">The .dockerignore file</span></span>

<span data-ttu-id="0199f-166">ソース管理から特定のファイルやディレクトリを除外するファイルと同じように、ファイルを使用して、 `.gitignore` `.dockerignore` ビルド中にファイルとディレクトリをイメージにコピーしないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="0199f-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="0199f-167">これにより、時間を節約できるだけでなく、 `obj` PC からのディレクトリがイメージにコピーされた場合に発生するエラーを回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="0199f-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="0199f-168">少なくとも、ファイルにとのエントリを追加する必要があり `bin` `obj` `.dockerignore` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="0199f-169">イメージをビルドする</span><span class="sxs-lookup"><span data-stu-id="0199f-169">Build the image</span></span>

<span data-ttu-id="0199f-170">単一のアプリケーションと1つの Dockerfile を持つソリューションでは、Dockerfile を基本ディレクトリに配置するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="0199f-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="0199f-171">つまり、ファイルと同じディレクトリに配置し `.sln` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="0199f-172">その場合は、イメージをビルドするために、Dockerfile が格納されているディレクトリから次のコマンドを使用し `docker build` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="0199f-173">紛らわしい名前付き `--tag` フラグ (に短縮できます) は、 `-t` 指定されている場合は、イメージの完全な名前 (実際のタグを含む) を指定します。</span><span class="sxs-lookup"><span data-stu-id="0199f-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="0199f-174">`.`末尾のは、ビルドを実行するコンテキストを指定します。 Dockerfile 内のコマンドの現在の作業ディレクトリです `COPY` 。</span><span class="sxs-lookup"><span data-stu-id="0199f-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="0199f-175">1つのソリューション内に複数のアプリケーションがある場合は、各アプリケーションの Dockerfile を、ファイルの横にある独自のフォルダーに保持でき `.csproj` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="0199f-176">引き続き、 `docker build` ベースディレクトリからコマンドを実行して、ソリューションとすべてのプロジェクトがイメージにコピーされるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0199f-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="0199f-177">`--file`(または) フラグを使用して、現在のディレクトリの下に Dockerfile を指定でき `-f` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="0199f-178">コンピューターのコンテナーでイメージを実行する</span><span class="sxs-lookup"><span data-stu-id="0199f-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="0199f-179">ローカルの Docker インスタンスでイメージを実行するには、コマンドを使用し `docker run` ます。</span><span class="sxs-lookup"><span data-stu-id="0199f-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="0199f-180">フラグは、 `-ti` 現在のターミナルをコンテナーのターミナルに接続し、対話モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="0199f-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="0199f-181">は、 `-p 5000:80` コンテナーのポート80を localhost ネットワークインターフェイスのポート5000に発行 (リンク) します。</span><span class="sxs-lookup"><span data-stu-id="0199f-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="0199f-182">イメージをレジストリにプッシュする</span><span class="sxs-lookup"><span data-stu-id="0199f-182">Push the image to a registry</span></span>

<span data-ttu-id="0199f-183">イメージが動作することを確認したら、それを Docker レジストリにプッシュして、他のシステムで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0199f-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="0199f-184">内部ネットワークでは、Docker レジストリをプロビジョニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0199f-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="0199f-185">これは、 [docker の独自の `registry` イメージ](https://docs.docker.com/registry/deploying/) を実行するのと同じように簡単ですが (Docker レジストリは docker コンテナーで実行されます)、さまざまな包括的なソリューションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0199f-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="0199f-186">外部共有とクラウド使用については、 [Azure Container Registry](/azure/container-registry/) や [Docker Hub](https://docs.docker.com/docker-hub/repos/)などのさまざまな管理対象レジストリを利用できます。</span><span class="sxs-lookup"><span data-stu-id="0199f-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="0199f-187">Docker Hub にプッシュするには、イメージ名の前にユーザー名または組織名を付けます。</span><span class="sxs-lookup"><span data-stu-id="0199f-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="0199f-188">プライベートレジストリにプッシュするには、イメージ名の前にレジストリのホスト名と組織名を付けます。</span><span class="sxs-lookup"><span data-stu-id="0199f-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="0199f-189">イメージがレジストリに格納された後、個々の Docker ホスト、または Kubernetes のようなコンテナーオーケストレーションエンジンにイメージを展開できます。</span><span class="sxs-lookup"><span data-stu-id="0199f-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0199f-190">[前へ](self-hosted.md)
>[次へ](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="0199f-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
