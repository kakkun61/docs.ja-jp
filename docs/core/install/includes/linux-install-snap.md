---
ms.openlocfilehash: 83808f2f3a05333ed5d9e3809cbc2fd6e230d02c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031772"
---

[<span data-ttu-id="cf788-101">.NET Core は、Snap Store から入手できます。</span><span class="sxs-lookup"><span data-stu-id="cf788-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="cf788-102">Snap は、アプリとその依存関係のバンドルであり、さまざまな Linux ディストリビューション間で変更を加えることなく動作します。</span><span class="sxs-lookup"><span data-stu-id="cf788-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="cf788-103">Snap は、Snap Store で見つけてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="cf788-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="cf788-104">Snap の詳細については、[Snap の概要](https://snapcraft.io/docs/getting-started)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cf788-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="cf788-105">Snap では、サポートされているバージョンの .NET Core のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="cf788-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="cf788-106">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="cf788-106">Install the SDK</span></span>

<span data-ttu-id="cf788-107">.NET SDK の Snap パッケージは、すべて同じ識別子 (`dotnet-sdk`) で公開されます。</span><span class="sxs-lookup"><span data-stu-id="cf788-107">Snap packages for .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="cf788-108">特定のバージョンの SDK は、チャネルを指定することによってインストールできます。</span><span class="sxs-lookup"><span data-stu-id="cf788-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="cf788-109">SDK には、対応するランタイムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf788-109">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="cf788-110">次の表に、チャネルの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="cf788-110">The following table lists the channels:</span></span>

| <span data-ttu-id="cf788-111">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="cf788-111">.NET version</span></span> | <span data-ttu-id="cf788-112">Snap パッケージ</span><span class="sxs-lookup"><span data-stu-id="cf788-112">Snap package</span></span>             |
|--------------|--------------------------|
| <span data-ttu-id="cf788-113">5.0</span><span class="sxs-lookup"><span data-stu-id="cf788-113">5.0</span></span>          | <span data-ttu-id="cf788-114">`5.0` または `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="cf788-114">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="cf788-115">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="cf788-115">3.1 (LTS)</span></span>    | <span data-ttu-id="cf788-116">`3.1` または `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="cf788-116">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="cf788-117">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="cf788-117">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="cf788-118">`snap install` コマンドを使用して、.NET SDK の Snap パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="cf788-118">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="cf788-119">`--channel` パラメーターを使用して、インストールするバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf788-119">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="cf788-120">このパラメーターを省略すると、`latest/stable` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf788-120">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="cf788-121">この例では、`5.0` が指定されています。</span><span class="sxs-lookup"><span data-stu-id="cf788-121">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="cf788-122">次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。</span><span class="sxs-lookup"><span data-stu-id="cf788-122">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="cf788-123">このコマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="cf788-123">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="cf788-124">`{alias}` の名前は自由に選択できます。</span><span class="sxs-lookup"><span data-stu-id="cf788-124">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="cf788-125">たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-sdk.dotnet dotnet50`。</span><span class="sxs-lookup"><span data-stu-id="cf788-125">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="cf788-126">コマンド `dotnet50` を使用すると、この特定のバージョンの .NET が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cf788-126">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="cf788-127">ただし、これはチュートリアルや例のほとんどと互換性がありません。それらでは `dotnet` コマンドが使用可能であることが想定されているためです。</span><span class="sxs-lookup"><span data-stu-id="cf788-127">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="cf788-128">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="cf788-128">Install the runtime</span></span>

<span data-ttu-id="cf788-129">.NET Core ランタイムの Snap パッケージは、それぞれ独自のパッケージ識別子で公開されます。</span><span class="sxs-lookup"><span data-stu-id="cf788-129">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="cf788-130">次の表に、パッケージ識別子の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="cf788-130">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="cf788-131">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="cf788-131">.NET version</span></span>      | <span data-ttu-id="cf788-132">Snap パッケージ</span><span class="sxs-lookup"><span data-stu-id="cf788-132">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="cf788-133">5.0</span><span class="sxs-lookup"><span data-stu-id="cf788-133">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="cf788-134">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="cf788-134">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="cf788-135">3.0</span><span class="sxs-lookup"><span data-stu-id="cf788-135">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="cf788-136">2.2</span><span class="sxs-lookup"><span data-stu-id="cf788-136">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="cf788-137">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="cf788-137">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="cf788-138">`snap install` コマンドを使用して、.NET ランタイムの Snap パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="cf788-138">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="cf788-139">この例では、.NET 5.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="cf788-139">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="cf788-140">次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。</span><span class="sxs-lookup"><span data-stu-id="cf788-140">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="cf788-141">このコマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="cf788-141">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="cf788-142">`{alias}` の名前は自由に選択できます。</span><span class="sxs-lookup"><span data-stu-id="cf788-142">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="cf788-143">たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`。</span><span class="sxs-lookup"><span data-stu-id="cf788-143">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="cf788-144">コマンド `dotnet50` を使用すると、この特定のバージョンの .NET が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cf788-144">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="cf788-145">ただし、これはチュートリアルや例のほとんどと互換性がありません。それらでは `dotnet` コマンドが使用可能であることが想定されているためです。</span><span class="sxs-lookup"><span data-stu-id="cf788-145">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="cf788-146">SSL 証明書のエラー</span><span class="sxs-lookup"><span data-stu-id="cf788-146">SSL Certificate errors</span></span>

<span data-ttu-id="cf788-147">Snap を使用して .NET をインストールする場合、一部のディストリビューションでは .NET の SSL 証明書が見つからないことがあり、`restore` 中に次のようなエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf788-147">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="cf788-148">この問題を解決するには、いくつかの環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="cf788-148">To resolve this issue, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="cf788-149">証明書の場所は、ディストリビューションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="cf788-149">The certificate location will vary by distro.</span></span> <span data-ttu-id="cf788-150">次に、問題が発生したディストリビューションの場所を示します。</span><span class="sxs-lookup"><span data-stu-id="cf788-150">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="cf788-151">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="cf788-151">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="cf788-152">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="cf788-152">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="cf788-153">Solus - `/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="cf788-153">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
