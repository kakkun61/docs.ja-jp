---
title: Snap を使用して Linux に .NET をインストールする - .NET
description: Snap を使用して Linux に .NET SDK または .NET ランタイムをインストールする方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 741933b5ca6f01d73b388675fe7f8a43c4efb0f9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970928"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a><span data-ttu-id="63a43-103">Snap を使用して .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="63a43-103">Install the .NET SDK or the .NET Runtime with Snap</span></span>

<span data-ttu-id="63a43-104">Snap パッケージを使用して、.NET SDK または .NET ランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="63a43-104">Use a Snap package to install the .NET SDK or .NET Runtime.</span></span> <span data-ttu-id="63a43-105">Snap は、Linux ディストリビューションに組み込まれているパッケージ マネージャーに代わる優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="63a43-105">Snaps are a great alternative to the package manager built into your Linux distribution.</span></span> <span data-ttu-id="63a43-106">この記事では、[Snap](https://snapcraft.io/dotnet-sdk) を使用して .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="63a43-106">This article describes how to install .NET through [Snap](https://snapcraft.io/dotnet-sdk).</span></span>

<span data-ttu-id="63a43-107">Snap は、アプリとその依存関係のバンドルであり、さまざまな Linux ディストリビューション間で変更を加えることなく動作します。</span><span class="sxs-lookup"><span data-stu-id="63a43-107">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="63a43-108">Snap は、Snap Store で見つけてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="63a43-108">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="63a43-109">Snap の詳細については、[Snap の概要](https://snapcraft.io/docs/getting-started)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="63a43-109">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

> [!CAUTION]
> <span data-ttu-id="63a43-110">Snap パッケージは、Windows 10 の WSL2 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="63a43-110">Snap packages aren't supported in WSL2 on Windows 10.</span></span> <span data-ttu-id="63a43-111">別の方法としては、[`dotnet-install` スクリプト](linux-scripted-manual.md#scripted-install)または特定の WSL2 ディストリビューション用のパッケージ マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="63a43-111">As an alternative, use the [`dotnet-install` script](linux-scripted-manual.md#scripted-install) or the package manager for the particular WSL2 distribution.</span></span> <span data-ttu-id="63a43-112">推奨されませんが、[snapcraft フォーラムからサポートされていない回避策](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)を使用して Snap を有効にしてみることができます。</span><span class="sxs-lookup"><span data-stu-id="63a43-112">It's not recommended but you can try to enable snap with an [unsupported workaround from the snapcraft forums](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span></span>

## <a name="net-releases"></a><span data-ttu-id="63a43-113">.NET のリリース</span><span class="sxs-lookup"><span data-stu-id="63a43-113">.NET releases</span></span>

<span data-ttu-id="63a43-114">Snap では、✔️ サポートされているバージョンの .NET SDK のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="63a43-114">Only ✔️ supported versions of .NET SDK are available through Snap.</span></span> <span data-ttu-id="63a43-115">.NET ランタイムのすべてのバージョンは、バージョン 2.1 以降の Snap から使用できます。</span><span class="sxs-lookup"><span data-stu-id="63a43-115">All versions of the .NET Runtime are available through snap starting with version 2.1.</span></span> <span data-ttu-id="63a43-116">次の表は、.NET (および .NET Core) のリリースの一覧です。</span><span class="sxs-lookup"><span data-stu-id="63a43-116">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="63a43-117">✔️ Supported</span><span class="sxs-lookup"><span data-stu-id="63a43-117">✔️ Supported</span></span> | <span data-ttu-id="63a43-118">❌ サポートされていない</span><span class="sxs-lookup"><span data-stu-id="63a43-118">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="63a43-119">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-119">5.0</span></span>         | <span data-ttu-id="63a43-120">3.0</span><span class="sxs-lookup"><span data-stu-id="63a43-120">3.0</span></span>           |
| <span data-ttu-id="63a43-121">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="63a43-121">3.1 (LTS)</span></span>   | <span data-ttu-id="63a43-122">2.2</span><span class="sxs-lookup"><span data-stu-id="63a43-122">2.2</span></span>           |
| <span data-ttu-id="63a43-123">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="63a43-123">2.1 (LTS)</span></span>   | <span data-ttu-id="63a43-124">2.0</span><span class="sxs-lookup"><span data-stu-id="63a43-124">2.0</span></span>           |
|             | <span data-ttu-id="63a43-125">1.1</span><span class="sxs-lookup"><span data-stu-id="63a43-125">1.1</span></span>           |
|             | <span data-ttu-id="63a43-126">1.0</span><span class="sxs-lookup"><span data-stu-id="63a43-126">1.0</span></span>           |

<span data-ttu-id="63a43-127">.NET リリースのライフ サイクルの詳細については、「[.NET Core と .NET 5 のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63a43-127">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="sdk-or-runtime"></a><span data-ttu-id="63a43-128">SDK またはランタイム</span><span class="sxs-lookup"><span data-stu-id="63a43-128">SDK or Runtime</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a><span data-ttu-id="63a43-129">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="63a43-129">Install the SDK</span></span>

<span data-ttu-id="63a43-130">.NET SDK 用の Snap パッケージはすべて、同じ識別子 `dotnet-sdk` で公開されます。</span><span class="sxs-lookup"><span data-stu-id="63a43-130">Snap packages for the .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="63a43-131">特定のバージョンの SDK は、チャネルを指定することによってインストールできます。</span><span class="sxs-lookup"><span data-stu-id="63a43-131">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="63a43-132">SDK には、対応するランタイムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="63a43-132">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="63a43-133">次の表に、チャネルの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="63a43-133">The following table lists the channels:</span></span>

| <span data-ttu-id="63a43-134">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="63a43-134">.NET version</span></span> | <span data-ttu-id="63a43-135">Snap パッケージまたはチャネル</span><span class="sxs-lookup"><span data-stu-id="63a43-135">Snap package or channel</span></span>  |
|--------------|--------------------------|
| <span data-ttu-id="63a43-136">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-136">5.0</span></span>          | <span data-ttu-id="63a43-137">`5.0` または `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="63a43-137">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="63a43-138">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="63a43-138">3.1 (LTS)</span></span>    | <span data-ttu-id="63a43-139">`3.1` または `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="63a43-139">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="63a43-140">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="63a43-140">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="63a43-141">`snap install` コマンドを使用して、.NET SDK の Snap パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="63a43-141">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="63a43-142">`--channel` パラメーターを使用して、インストールするバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="63a43-142">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="63a43-143">このパラメーターを省略すると、`latest/stable` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="63a43-143">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="63a43-144">この例では、`5.0` が指定されています。</span><span class="sxs-lookup"><span data-stu-id="63a43-144">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="63a43-145">次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。</span><span class="sxs-lookup"><span data-stu-id="63a43-145">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="63a43-146">このコマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="63a43-146">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="63a43-147">`{alias}` の名前は自由に選択できます。</span><span class="sxs-lookup"><span data-stu-id="63a43-147">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="63a43-148">たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-sdk.dotnet dotnet50`。</span><span class="sxs-lookup"><span data-stu-id="63a43-148">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="63a43-149">コマンド `dotnet50` を使用すると、この特定のバージョンの .NET が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="63a43-149">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="63a43-150">ただし、異なるエイリアスの選択は、ほとんどのチュートリアルや例と互換性がありません。それらでは、`dotnet` コマンドを使用することが想定されているためです。</span><span class="sxs-lookup"><span data-stu-id="63a43-150">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be used.</span></span>

## <a name="install-the-runtime"></a><span data-ttu-id="63a43-151">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="63a43-151">Install the runtime</span></span>

<span data-ttu-id="63a43-152">.NET ランタイム用の Snap パッケージはそれぞれ、独自のパッケージ識別子で公開されます。</span><span class="sxs-lookup"><span data-stu-id="63a43-152">Snap packages for the .NET Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="63a43-153">次の表に、パッケージ識別子の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="63a43-153">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="63a43-154">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="63a43-154">.NET version</span></span>      | <span data-ttu-id="63a43-155">Snap パッケージ</span><span class="sxs-lookup"><span data-stu-id="63a43-155">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="63a43-156">5.0</span><span class="sxs-lookup"><span data-stu-id="63a43-156">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="63a43-157">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="63a43-157">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="63a43-158">3.0</span><span class="sxs-lookup"><span data-stu-id="63a43-158">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="63a43-159">2.2</span><span class="sxs-lookup"><span data-stu-id="63a43-159">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="63a43-160">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="63a43-160">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="63a43-161">`snap install` コマンドを使用して、.NET ランタイムの Snap パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="63a43-161">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="63a43-162">この例では、.NET 5.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="63a43-162">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="63a43-163">次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。</span><span class="sxs-lookup"><span data-stu-id="63a43-163">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="63a43-164">コマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="63a43-164">The command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="63a43-165">`{alias}` の名前は自由に選択できます。</span><span class="sxs-lookup"><span data-stu-id="63a43-165">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="63a43-166">たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`。</span><span class="sxs-lookup"><span data-stu-id="63a43-166">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="63a43-167">コマンド `dotnet50` を使用すると、特定のバージョンの .NET が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="63a43-167">When you use the command `dotnet50`, you'll invoke a specific version of .NET.</span></span> <span data-ttu-id="63a43-168">ただし、異なるエイリアスの選択は、ほとんどのチュートリアルや例と互換性がありません。それらでは、`dotnet` コマンドを使用できることが想定されているためです。</span><span class="sxs-lookup"><span data-stu-id="63a43-168">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

## <a name="tlsssl-certificate-errors"></a><span data-ttu-id="63a43-169">TLS/SSL 証明書のエラー</span><span class="sxs-lookup"><span data-stu-id="63a43-169">TLS/SSL Certificate errors</span></span>

<span data-ttu-id="63a43-170">Snap を使用して .NET をインストールする場合、一部のディストリビューションでは .NET の TLS/SSL 証明書が見つからないことがあり、`restore` の間にエラーが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="63a43-170">When .NET is installed through Snap, it's possible that on some distros the .NET TLS/SSL certificates may not be found and you may receive an error during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="63a43-171">この問題を解決するには、いくつかの環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="63a43-171">To resolve this problem, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="63a43-172">証明書の場所は、ディストリビューションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="63a43-172">The certificate location will vary by distro.</span></span> <span data-ttu-id="63a43-173">次に、問題が発生したディストリビューションの場所を示します。</span><span class="sxs-lookup"><span data-stu-id="63a43-173">Here are the locations for the distros where the issue has been experienced.</span></span>

| <span data-ttu-id="63a43-174">Distribution</span><span class="sxs-lookup"><span data-stu-id="63a43-174">Distribution</span></span> | <span data-ttu-id="63a43-175">場所</span><span class="sxs-lookup"><span data-stu-id="63a43-175">Location</span></span>                                            |
|--------------|-----------------------------------------------------|
| <span data-ttu-id="63a43-176">**Fedora**</span><span class="sxs-lookup"><span data-stu-id="63a43-176">**Fedora**</span></span>   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| <span data-ttu-id="63a43-177">**OpenSUSE**</span><span class="sxs-lookup"><span data-stu-id="63a43-177">**OpenSUSE**</span></span> | `/etc/ssl/ca-bundle.pem`                            |
| <span data-ttu-id="63a43-178">**Solus**</span><span class="sxs-lookup"><span data-stu-id="63a43-178">**Solus**</span></span>    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a><span data-ttu-id="63a43-179">次のステップ</span><span class="sxs-lookup"><span data-stu-id="63a43-179">Next steps</span></span>

- [<span data-ttu-id="63a43-180">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="63a43-180">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="63a43-181">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="63a43-181">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
