---
title: .NET CLI を使用してライブラリを開発する
description: .NET CLI を使用して .NET ライブラリを作成する方法について説明します。 複数のフレームワークをサポートするライブラリを作成します。
author: cartermp
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: 6f4c1feac7630a6a0250e4b0b39ef01152f5a400
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633677"
---
# <a name="develop-libraries-with-the-net-cli"></a><span data-ttu-id="9392b-104">.NET CLI を使用してライブラリを開発する</span><span class="sxs-lookup"><span data-stu-id="9392b-104">Develop libraries with the .NET CLI</span></span>

<span data-ttu-id="9392b-105">この記事では、.NET CLI を使用して .NET 用ライブラリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9392b-105">This article covers how to write libraries for .NET using the .NET CLI.</span></span> <span data-ttu-id="9392b-106">CLI は、サポートされる任意の OS で動作する効率的で低レベルのエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9392b-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="9392b-107">Visual Studio でライブラリを構築することもできます。Visual Studio で構築する場合は、[Visual Studio ガイドを参照](library-with-visual-studio.md)してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9392b-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="9392b-108">Prerequisites</span></span>

<span data-ttu-id="9392b-109">[.NET SDK と CLI](https://dotnet.microsoft.com/download) がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9392b-109">You need [the .NET SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="9392b-110">このドキュメントで [.NET Framework](https://dotnet.microsoft.com) バージョンについて扱うセクションでは、.NET Framework が Windows コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9392b-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="9392b-111">また、古い .NET Framework ターゲットをサポートする場合、[.NET ダウンロードのアーカイブ ページ](https://dotnet.microsoft.com/download/archives)から Targeting Pack または Developer Pack をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9392b-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="9392b-112">次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-112">Refer to this table:</span></span>

| <span data-ttu-id="9392b-113">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="9392b-113">.NET Framework version</span></span> | <span data-ttu-id="9392b-114">ダウンロードするもの</span><span class="sxs-lookup"><span data-stu-id="9392b-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="9392b-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="9392b-115">4.6.1</span></span>                  | <span data-ttu-id="9392b-116">.NET Framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="9392b-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="9392b-117">4.6</span><span class="sxs-lookup"><span data-stu-id="9392b-117">4.6</span></span>                    | <span data-ttu-id="9392b-118">.NET Framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="9392b-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="9392b-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9392b-119">4.5.2</span></span>                  | <span data-ttu-id="9392b-120">.NET Framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="9392b-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="9392b-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="9392b-121">4.5.1</span></span>                  | <span data-ttu-id="9392b-122">.NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="9392b-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="9392b-123">4.5</span><span class="sxs-lookup"><span data-stu-id="9392b-123">4.5</span></span>                    | <span data-ttu-id="9392b-124">Windows 8 用 Windows ソフトウェア開発キット</span><span class="sxs-lookup"><span data-stu-id="9392b-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="9392b-125">4.0</span><span class="sxs-lookup"><span data-stu-id="9392b-125">4.0</span></span>                    | <span data-ttu-id="9392b-126">Windows SDK for Windows 7 および .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="9392b-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="9392b-127">2.0、3.0、および 3.5</span><span class="sxs-lookup"><span data-stu-id="9392b-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="9392b-128">.NET Framework 3.5 SP1 Runtime (または Windows 8 以降のバージョン)</span><span class="sxs-lookup"><span data-stu-id="9392b-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-net-50-or-net-standard"></a><span data-ttu-id="9392b-129">.NET 5.0 または .NET Standard をターゲットにする方法</span><span class="sxs-lookup"><span data-stu-id="9392b-129">How to target .NET 5.0 or .NET Standard</span></span>

<span data-ttu-id="9392b-130">プロジェクト ファイル ( *.csproj* または *.fsproj*) に追加することでプロジェクトのターゲット フレームワークを制御します。</span><span class="sxs-lookup"><span data-stu-id="9392b-130">You control your project's target framework by adding it to your project file (*.csproj* or *.fsproj*).</span></span> <span data-ttu-id="9392b-131">ターゲットとして .NET 5.0 と .NET Standard のいずれを選択するかについては、「[.NET 5 と .NET Standard](../../standard/net-standard.md#net-5-and-net-standard)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-131">For guidance on how to choose between targeting .NET 5.0 or .NET Standard see [.NET 5 and .NET Standard](../../standard/net-standard.md#net-5-and-net-standard).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9392b-132">.NET Framework バージョン 4.0 以前をターゲットにする場合、または .NET Framework では利用できて .NET Standard では利用できない API (`System.Drawing` など) を使用する場合は、マルチターゲットの方法について次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-132">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="9392b-133">.NET Framework をターゲット設定する方法</span><span class="sxs-lookup"><span data-stu-id="9392b-133">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="9392b-134">次の手順では、お使いのマシンに .NET Framework がインストールされていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="9392b-134">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="9392b-135">依存関係のインストールについては、「[前提条件](#prerequisites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-135">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="9392b-136">ここで使用されている .NET Framework バージョンには、現在サポートされていないものもあります。</span><span class="sxs-lookup"><span data-stu-id="9392b-136">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="9392b-137">サポートされないバージョンについては、「[.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us)」(.NET Framework のサポート ライフサイクル ポリシーについてよく寄せられる質問) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-137">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="9392b-138">最大数の開発者とプロジェクトを対象にしたい場合、基準となるターゲットは .NET Framework 4.0 です。</span><span class="sxs-lookup"><span data-stu-id="9392b-138">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="9392b-139">.NET Framework をターゲット設定するには、まず、サポートしたい .NET Framework バージョンに対応する正しいターゲット フレームワーク モニカー (TFM) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9392b-139">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="9392b-140">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="9392b-140">.NET Framework version</span></span> | <span data-ttu-id="9392b-141">TFM</span><span class="sxs-lookup"><span data-stu-id="9392b-141">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="9392b-142">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="9392b-142">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="9392b-143">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="9392b-143">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="9392b-144">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="9392b-144">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="9392b-145">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="9392b-145">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="9392b-146">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9392b-146">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="9392b-147">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="9392b-147">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="9392b-148">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="9392b-148">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="9392b-149">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="9392b-149">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="9392b-150">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="9392b-150">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="9392b-151">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="9392b-151">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="9392b-152">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9392b-152">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="9392b-153">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="9392b-153">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="9392b-154">この TFM をプロジェクト ファイルの `TargetFramework` セクションに挿入します。</span><span class="sxs-lookup"><span data-stu-id="9392b-154">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="9392b-155">.NET Framework 4.0 をターゲットとするライブラリを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9392b-155">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9392b-156">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="9392b-156">And that's it!</span></span> <span data-ttu-id="9392b-157">これは .NET Framework 4 向けにのみコンパイルされていますが、新しいバージョンの .NET Framework のライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9392b-157">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="9392b-158">マルチターゲットを設定する方法</span><span class="sxs-lookup"><span data-stu-id="9392b-158">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="9392b-159">次の手順では、.NET Framework がコンピューターにインストールされている想定です。</span><span class="sxs-lookup"><span data-stu-id="9392b-159">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="9392b-160">インストールする必要がある依存関係と、そのダウンロードできる場所については、「[前提条件](#prerequisites)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-160">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="9392b-161">プロジェクトが .NET Framework と .NET の両方をサポートしている場合、状況によっては古いバージョンの .NET Framework をターゲットにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9392b-161">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET.</span></span> <span data-ttu-id="9392b-162">このシナリオで、新しい API と新しいターゲット向けの言語構成を使用する場合、コードで `#if` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="9392b-162">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="9392b-163">また、必要に応じて、ターゲットにする各プラットフォームに応じて異なるパッケージと依存関係追加して、それぞれに異なる必要な API を含めます。</span><span class="sxs-lookup"><span data-stu-id="9392b-163">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="9392b-164">たとえば、HTTP 上でネットワークキング操作を行うライブラリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="9392b-164">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="9392b-165">.NET Standard と .NET Framework バージョン 4.5 以降の場合、`System.Net.Http` 名前空間の `HttpClient` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9392b-165">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="9392b-166">ただし、それより前のバージョンの .NET Framework に `HttpClient` クラスはないので、代わりに `System.Net` 名前空間の `WebClient` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9392b-166">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="9392b-167">プロジェクト ファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9392b-167">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard2.0;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="9392b-168">主な変更点が 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="9392b-168">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="9392b-169">`TargetFramework` ノードは `TargetFrameworks` で置き換えられ、3 つの TFM が内部に表現されています。</span><span class="sxs-lookup"><span data-stu-id="9392b-169">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="9392b-170">1 つの .NET Framework 参照を取り込む `net40` ターゲットの `<ItemGroup>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="9392b-170">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="9392b-171">.NET Framework の参照 2 に取り込む `net45` ターゲットの `<ItemGroup>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="9392b-171">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="9392b-172">ビルド システムは `#if` ディレクティブで使用される次のプリプロセッサ シンボルを認識します。</span><span class="sxs-lookup"><span data-stu-id="9392b-172">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="9392b-173">次に、ターゲットごとに条件付きコンパイルを利用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="9392b-173">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET Framework 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="9392b-174">`dotnet build` を使用してこのプロジェクトをビルドすると、`bin/` フォルダー以下に 3 つのディレクトリがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="9392b-174">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard2.0/
```

<span data-ttu-id="9392b-175">それぞれに各ターゲットの `.dll` ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9392b-175">Each of these contains the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net"></a><span data-ttu-id="9392b-176">.NET でライブラリをテストする方法</span><span class="sxs-lookup"><span data-stu-id="9392b-176">How to test libraries on .NET</span></span>

<span data-ttu-id="9392b-177">プラットフォーム全体でテストできることが重要です。</span><span class="sxs-lookup"><span data-stu-id="9392b-177">It's important to be able to test across platforms.</span></span> <span data-ttu-id="9392b-178">[xUnit](https://xunit.net/) または MSTest はそのまま利用できます。</span><span class="sxs-lookup"><span data-stu-id="9392b-178">You can use either [xUnit](https://xunit.net/) or MSTest out of the box.</span></span> <span data-ttu-id="9392b-179">どちらも、.NET 上のライブラリの単体テストに最適です。</span><span class="sxs-lookup"><span data-stu-id="9392b-179">Both are perfectly suitable for unit testing your library on .NET.</span></span> <span data-ttu-id="9392b-180">テスト プロジェクトでソリューションをセットアップする方法は、[ソリューションの構造](#structuring-a-solution)によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9392b-180">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="9392b-181">次の例は、テスト ディレクトリとソース ディレクトリが同じ最上位ディレクトリにある場合です。</span><span class="sxs-lookup"><span data-stu-id="9392b-181">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9392b-182">この例ではいくつかの [.NET CLI コマンド](../tools/index.md)を使用しています。</span><span class="sxs-lookup"><span data-stu-id="9392b-182">This uses some [.NET CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="9392b-183">詳細については、「[dotnet new](../tools/dotnet-new.md)」と「[dotnet sln](../tools/dotnet-sln.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9392b-183">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="9392b-184">ソリューションを設定します。</span><span class="sxs-lookup"><span data-stu-id="9392b-184">Set up your solution.</span></span> <span data-ttu-id="9392b-185">次のコマンドで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="9392b-185">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="9392b-186">これでプロジェクトが作成され、ソリューション内のプロジェクトがリンクされます。</span><span class="sxs-lookup"><span data-stu-id="9392b-186">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="9392b-187">`SolutionWithSrcAndTest` のディレクトリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9392b-187">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="9392b-188">テスト プロジェクトのディレクトリに移動し、`MyProject` から `MyProject.Test` への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9392b-188">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="9392b-189">パッケージを復元し、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9392b-189">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

1. <span data-ttu-id="9392b-190">`dotnet test` コマンドを実行して、xUnit が実行されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9392b-190">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="9392b-191">MSTest を使用する場合は、MSTest コンソール実行ツールが実行されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9392b-191">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="9392b-192">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="9392b-192">And that's it!</span></span> <span data-ttu-id="9392b-193">コマンド ライン ツールを使用して、すべてのプラットフォームでライブラリをテストできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9392b-193">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="9392b-194">すべてをセットアップしてテストに進む場合、ライブラリのテストはとても単純です。</span><span class="sxs-lookup"><span data-stu-id="9392b-194">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="9392b-195">ライブラリに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="9392b-195">Make changes to your library.</span></span>
1. <span data-ttu-id="9392b-196">コマンド ラインから、`dotnet test` コマンドを使用してテスト ディレクトリでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="9392b-196">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="9392b-197">`dotnet test` コマンドを呼び出すと、コードは自動的にリビルドされます。</span><span class="sxs-lookup"><span data-stu-id="9392b-197">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="9392b-198">複数のプロジェクトを使用する方法</span><span class="sxs-lookup"><span data-stu-id="9392b-198">How to use multiple projects</span></span>

<span data-ttu-id="9392b-199">大規模なライブラリで一般的なニーズは、複数のプロジェクトに機能を配置することです。</span><span class="sxs-lookup"><span data-stu-id="9392b-199">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="9392b-200">たとえば、慣用的な C# や F# で使用できるライブラリをビルドするとします。</span><span class="sxs-lookup"><span data-stu-id="9392b-200">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="9392b-201">これは、ライブラリのユーザーは、C# または F# に対して自然な方法で使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="9392b-201">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="9392b-202">たとえば、C# の場合、次のようにライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9392b-202">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="9392b-203">F# の場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9392b-203">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="9392b-204">このような使用シナリオは、アクセスされる API が C# と F# 用に異なる構造を持つ必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="9392b-204">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="9392b-205">これを実現する一般的なアプローチとして、ライブラリのすべてのロジックをコア プロジェクトに取り入れ、C# および F# プロジェクトでコア プロジェクトに呼び出す API レイヤーを定義する方法があります。</span><span class="sxs-lookup"><span data-stu-id="9392b-205">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="9392b-206">以降のセクションでは、次の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="9392b-206">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="9392b-207">**AwesomeLibrary.Core** - ライブラリのすべてのロジックを含むコア プロジェクト</span><span class="sxs-lookup"><span data-stu-id="9392b-207">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="9392b-208">**AwesomeLibrary.CSharp** - C# で使用するためのパブリック API を含むプロジェクト</span><span class="sxs-lookup"><span data-stu-id="9392b-208">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="9392b-209">**AwesomeLibrary.FSharp** - F# で使用するためのパブリック API を含むプロジェクト</span><span class="sxs-lookup"><span data-stu-id="9392b-209">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="9392b-210">自分の端末で次のコマンドを実行し、このガイドと同じ構造を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="9392b-210">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="9392b-211">これで上記の 3 つのプロジェクトと、それらをリンクするソリューション ファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="9392b-211">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="9392b-212">ソリューション ファイルとリンク プロジェクトを作成すると、最上位レベルからプロジェクトを復元し、ビルドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="9392b-212">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="9392b-213">プロジェクト間参照</span><span class="sxs-lookup"><span data-stu-id="9392b-213">Project-to-project referencing</span></span>

<span data-ttu-id="9392b-214">プロジェクトを参照するには、.NET CLI を使用してプロジェクト参照を追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9392b-214">The best way to reference a project is to use the .NET CLI to add a project reference.</span></span> <span data-ttu-id="9392b-215">**AwesomeLibrary.CSharp** と **AwesomeLibrary.FSharp** のプロジェクト ディレクトリから、次のコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9392b-215">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="9392b-216">**AwesomeLibrary.CSharp** と **AwesomeLibrary.FSharp** の両方のプロジェクト ファイルは、`ProjectReference` ターゲットとして **AwesomeLibrary.Core** を参照するようになります。</span><span class="sxs-lookup"><span data-stu-id="9392b-216">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="9392b-217">この参照を確認するには、プロジェクト ファイルに以下の行があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9392b-217">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="9392b-218">この.NET CLI を使用しない場合は、このセクションを各プロジェクト ファイルに手動で追加します。</span><span class="sxs-lookup"><span data-stu-id="9392b-218">You can add this section to each project file manually if you prefer not to use the .NET CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="9392b-219">ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="9392b-219">Structuring a solution</span></span>

<span data-ttu-id="9392b-220">マルチプロジェクト ソリューションのもう 1 つの重要な側面は、全体のプロジェクト構造を適切に構築することです。</span><span class="sxs-lookup"><span data-stu-id="9392b-220">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="9392b-221">ただし、`dotnet sln add` でソリューション ファイルに各プロジェクト ファイルがリンクされ、ソリューション レベルで `dotnet restore` と `dotnet build` を実行できる限り、好みに応じてコードを整理することができます。</span><span class="sxs-lookup"><span data-stu-id="9392b-221">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
