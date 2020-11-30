---
title: .NET Core CLI を使用したライブラリの開発
description: .NET Core CLI を使用して .NET Core ライブラリを作成する方法について説明します。 複数のフレームワークをサポートするライブラリを作成します。
author: cartermp
ms.topic: how-to
ms.date: 05/01/2017
ms.openlocfilehash: 8a0b1c5645f41a256bfb9d0e5dac74f8706d84e6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725080"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="4300e-104">.NET Core CLI を使用したライブラリの開発</span><span class="sxs-lookup"><span data-stu-id="4300e-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="4300e-105">この記事では、.NET Core CLI を使用して .NET 用ライブラリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4300e-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="4300e-106">CLI は、サポートされる任意の OS で動作する効率的で低レベルのエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4300e-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="4300e-107">Visual Studio でライブラリを構築することもできます。Visual Studio で構築する場合は、[Visual Studio ガイドを参照](library-with-visual-studio.md)してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4300e-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="4300e-108">Prerequisites</span></span>

<span data-ttu-id="4300e-109">[.NET Core SDK と CLI](https://dotnet.microsoft.com/download) がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4300e-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="4300e-110">このドキュメントで [.NET Framework](https://dotnet.microsoft.com) バージョンについて扱うセクションでは、.NET Framework が Windows コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4300e-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="4300e-111">また、古い .NET Framework ターゲットをサポートする場合、[.NET ダウンロードのアーカイブ ページ](https://dotnet.microsoft.com/download/archives)から Targeting Pack または Developer Pack をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4300e-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="4300e-112">次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-112">Refer to this table:</span></span>

| <span data-ttu-id="4300e-113">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="4300e-113">.NET Framework version</span></span> | <span data-ttu-id="4300e-114">ダウンロードするもの</span><span class="sxs-lookup"><span data-stu-id="4300e-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="4300e-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="4300e-115">4.6.1</span></span>                  | <span data-ttu-id="4300e-116">.NET Framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="4300e-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="4300e-117">4.6</span><span class="sxs-lookup"><span data-stu-id="4300e-117">4.6</span></span>                    | <span data-ttu-id="4300e-118">.NET Framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="4300e-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="4300e-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="4300e-119">4.5.2</span></span>                  | <span data-ttu-id="4300e-120">.NET Framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="4300e-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="4300e-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="4300e-121">4.5.1</span></span>                  | <span data-ttu-id="4300e-122">.NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="4300e-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="4300e-123">4.5</span><span class="sxs-lookup"><span data-stu-id="4300e-123">4.5</span></span>                    | <span data-ttu-id="4300e-124">Windows 8 用 Windows ソフトウェア開発キット</span><span class="sxs-lookup"><span data-stu-id="4300e-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="4300e-125">4.0</span><span class="sxs-lookup"><span data-stu-id="4300e-125">4.0</span></span>                    | <span data-ttu-id="4300e-126">Windows SDK for Windows 7 および .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="4300e-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="4300e-127">2.0、3.0、および 3.5</span><span class="sxs-lookup"><span data-stu-id="4300e-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="4300e-128">.NET Framework 3.5 SP1 Runtime (または Windows 8 以降のバージョン)</span><span class="sxs-lookup"><span data-stu-id="4300e-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-net-standard"></a><span data-ttu-id="4300e-129">.NET Standard をターゲット設定する方法</span><span class="sxs-lookup"><span data-stu-id="4300e-129">How to target .NET Standard</span></span>

<span data-ttu-id="4300e-130">.NET Standard にあまりなじみがない場合、詳細については、「[.NET Standard](../../standard/net-standard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4300e-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="4300e-131">この記事には、.NET Standard バージョンを多様な実装にマップする表が掲載されています。</span><span class="sxs-lookup"><span data-stu-id="4300e-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="4300e-132">ライブラリを作成する目的でこの表の意味について説明します。</span><span class="sxs-lookup"><span data-stu-id="4300e-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="4300e-133">選択する .NET Standard のバージョンは、最新の API にアクセスできることと、より多くの .NET 実装と .NET Standard バージョンをターゲット設定できることのトレードオフで決まります。</span><span class="sxs-lookup"><span data-stu-id="4300e-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="4300e-134">ターゲット設定可能なプラットフォームとバージョンの範囲は、`netstandardX.X` のバージョンを選択し (`X.X` はバージョン番号です)、プロジェクト ファイル (`.csproj` または `.fsproj`) に追加することで制御します。</span><span class="sxs-lookup"><span data-stu-id="4300e-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="4300e-135">.NET Standard をターゲット設定する場合、ニーズに応じて 3 つの主要なオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="4300e-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="4300e-136">テンプレートで提供されている既定のバージョンの .NET Standard (`netstandard1.4`) を使用できます。これにより、UWP、.NET Framework 4.6.1、.NET Standard 2.0 との互換性を保ちながら、.NET Standard 上のほとんどの API にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4300e-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="4300e-137">プロジェクト ファイルの `TargetFramework` ノードの値を変更することで、.NET Standard の下位または上位バージョンを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4300e-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="4300e-138">.NET Standard バージョンは下位互換性があります。</span><span class="sxs-lookup"><span data-stu-id="4300e-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="4300e-139">つまり、`netstandard1.0` ライブラリは、`netstandard1.1` プラットフォーム以降で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4300e-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="4300e-140">ただし、上位互換性はありません。</span><span class="sxs-lookup"><span data-stu-id="4300e-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="4300e-141">下位の .NET Standard プラットフォームは、上位のものを参照できません。</span><span class="sxs-lookup"><span data-stu-id="4300e-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="4300e-142">つまり、`netstandard1.0` ライブラリは、`netstandard1.1` 以降をターゲットとするライブラリを参照できません。</span><span class="sxs-lookup"><span data-stu-id="4300e-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="4300e-143">API とプラットフォームを適切に組み合わせ、ニーズに対応できる Standard バージョンを選択してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="4300e-144">現時点では `netstandard1.4` が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="4300e-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="4300e-145">.NET Framework バージョン 4.0 以前をターゲットにする場合、または .NET Framework では利用できて .NET Standard では利用できない API (`System.Drawing` など) を使用する場合は、マルチターゲットの方法について次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="4300e-146">.NET Framework をターゲット設定する方法</span><span class="sxs-lookup"><span data-stu-id="4300e-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="4300e-147">次の手順では、お使いのマシンに .NET Framework がインストールされていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="4300e-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="4300e-148">依存関係のインストールについては、「[前提条件](#prerequisites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="4300e-149">ここで使用されている .NET Framework バージョンには、現在サポートされていないものもあります。</span><span class="sxs-lookup"><span data-stu-id="4300e-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="4300e-150">サポートされないバージョンについては、「[.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us)」(.NET Framework のサポート ライフサイクル ポリシーについてよく寄せられる質問) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="4300e-151">最大数の開発者とプロジェクトを対象にしたい場合、基準となるターゲットは .NET Framework 4.0 です。</span><span class="sxs-lookup"><span data-stu-id="4300e-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="4300e-152">.NET Framework をターゲット設定するには、まず、サポートしたい .NET Framework バージョンに対応する正しいターゲット フレームワーク モニカー (TFM) を使用します。</span><span class="sxs-lookup"><span data-stu-id="4300e-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="4300e-153">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="4300e-153">.NET Framework version</span></span> | <span data-ttu-id="4300e-154">TFM</span><span class="sxs-lookup"><span data-stu-id="4300e-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="4300e-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="4300e-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="4300e-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="4300e-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="4300e-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="4300e-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="4300e-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="4300e-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="4300e-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="4300e-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="4300e-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="4300e-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="4300e-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="4300e-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="4300e-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="4300e-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="4300e-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="4300e-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="4300e-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="4300e-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="4300e-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="4300e-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="4300e-166">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="4300e-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="4300e-167">この TFM をプロジェクト ファイルの `TargetFramework` セクションに挿入します。</span><span class="sxs-lookup"><span data-stu-id="4300e-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="4300e-168">.NET Framework 4.0 をターゲットとするライブラリを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4300e-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="4300e-169">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="4300e-169">And that's it!</span></span> <span data-ttu-id="4300e-170">これは .NET Framework 4 向けにのみコンパイルされていますが、新しいバージョンの .NET Framework のライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4300e-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="4300e-171">マルチターゲットを設定する方法</span><span class="sxs-lookup"><span data-stu-id="4300e-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="4300e-172">次の手順では、.NET Framework がコンピューターにインストールされている想定です。</span><span class="sxs-lookup"><span data-stu-id="4300e-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="4300e-173">インストールする必要がある依存関係と、そのダウンロードできる場所については、「[前提条件](#prerequisites)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="4300e-174">プロジェクトが .NET Framework と .NET Core の両方をサポートしている場合、状況によっては古いバージョンの .NET Framework をターゲットにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4300e-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="4300e-175">このシナリオで、新しい API と新しいターゲット向けの言語構成を使用する場合、コードで `#if` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="4300e-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="4300e-176">また、必要に応じて、ターゲットにする各プラットフォームに応じて異なるパッケージと依存関係追加して、それぞれに異なる必要な API を含めます。</span><span class="sxs-lookup"><span data-stu-id="4300e-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="4300e-177">たとえば、HTTP 上でネットワークキング操作を行うライブラリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="4300e-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="4300e-178">.NET Standard と .NET Framework バージョン 4.5 以降の場合、`System.Net.Http` 名前空間の `HttpClient` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4300e-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="4300e-179">ただし、それより前のバージョンの .NET Framework に `HttpClient` クラスはないので、代わりに `System.Net` 名前空間の `WebClient` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4300e-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="4300e-180">プロジェクト ファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4300e-180">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
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

<span data-ttu-id="4300e-181">主な変更点が 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="4300e-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="4300e-182">`TargetFramework` ノードは `TargetFrameworks` で置き換えられ、3 つの TFM が内部に表現されています。</span><span class="sxs-lookup"><span data-stu-id="4300e-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="4300e-183">1 つの .NET Framework 参照を取り込む `net40` ターゲットの `<ItemGroup>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="4300e-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="4300e-184">.NET Framework の参照 2 に取り込む `net45` ターゲットの `<ItemGroup>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="4300e-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="4300e-185">ビルド システムは `#if` ディレクティブで使用される次のプリプロセッサ シンボルを認識します。</span><span class="sxs-lookup"><span data-stu-id="4300e-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="4300e-186">次に、ターゲットごとに条件付きコンパイルを利用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="4300e-186">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="4300e-187">`dotnet build` を使用してこのプロジェクトをビルドすると、`bin/` フォルダー以下に 3 つのディレクトリがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4300e-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="4300e-188">各ディレクトリには、各ターゲットの `.dll` ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="4300e-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="4300e-189">.NET Core でライブラリをテストする方法</span><span class="sxs-lookup"><span data-stu-id="4300e-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="4300e-190">プラットフォーム全体でテストできることが重要です。</span><span class="sxs-lookup"><span data-stu-id="4300e-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="4300e-191">[xUnit](https://xunit.github.io/) または MSTest はそのまま利用できます。</span><span class="sxs-lookup"><span data-stu-id="4300e-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="4300e-192">どちらも、.NET Core 上のライブラリの単体テストに最適です。</span><span class="sxs-lookup"><span data-stu-id="4300e-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="4300e-193">テスト プロジェクトでソリューションをセットアップする方法は、[ソリューションの構造](#structuring-a-solution)によって異なります。</span><span class="sxs-lookup"><span data-stu-id="4300e-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="4300e-194">次の例は、テスト ディレクトリとソース ディレクトリが同じ最上位ディレクトリにある場合です。</span><span class="sxs-lookup"><span data-stu-id="4300e-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="4300e-195">ここでは、いくつかの [.NET Core CLI](../tools/index.md) コマンドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4300e-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="4300e-196">詳細については、「[dotnet new](../tools/dotnet-new.md)」と「[dotnet sln](../tools/dotnet-sln.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4300e-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="4300e-197">ソリューションを設定します。</span><span class="sxs-lookup"><span data-stu-id="4300e-197">Set up your solution.</span></span> <span data-ttu-id="4300e-198">次のコマンドで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="4300e-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="4300e-199">これでプロジェクトが作成され、ソリューション内のプロジェクトがリンクされます。</span><span class="sxs-lookup"><span data-stu-id="4300e-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="4300e-200">`SolutionWithSrcAndTest` のディレクトリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4300e-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="4300e-201">テスト プロジェクトのディレクトリに移動し、`MyProject` から `MyProject.Test` への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="4300e-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="4300e-202">パッケージを復元し、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="4300e-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="4300e-203">`dotnet test` コマンドを実行して、xUnit が実行されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4300e-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="4300e-204">MSTest を使用する場合は、MSTest コンソール実行ツールが実行されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4300e-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="4300e-205">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="4300e-205">And that's it!</span></span> <span data-ttu-id="4300e-206">コマンド ライン ツールを使用して、すべてのプラットフォームでライブラリをテストできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4300e-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="4300e-207">すべてをセットアップしてテストに進む場合、ライブラリのテストはとても単純です。</span><span class="sxs-lookup"><span data-stu-id="4300e-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="4300e-208">ライブラリに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="4300e-208">Make changes to your library.</span></span>
1. <span data-ttu-id="4300e-209">コマンド ラインから、`dotnet test` コマンドを使用してテスト ディレクトリでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4300e-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="4300e-210">`dotnet test` コマンドを呼び出すと、コードは自動的にリビルドされます。</span><span class="sxs-lookup"><span data-stu-id="4300e-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="4300e-211">複数のプロジェクトを使用する方法</span><span class="sxs-lookup"><span data-stu-id="4300e-211">How to use multiple projects</span></span>

<span data-ttu-id="4300e-212">大規模なライブラリで一般的なニーズは、複数のプロジェクトに機能を配置することです。</span><span class="sxs-lookup"><span data-stu-id="4300e-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="4300e-213">たとえば、慣用的な C# や F# で使用できるライブラリをビルドするとします。</span><span class="sxs-lookup"><span data-stu-id="4300e-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="4300e-214">これは、ライブラリのユーザーは、C# または F# に対して自然な方法で使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="4300e-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="4300e-215">たとえば、C# の場合、次のようにライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4300e-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="4300e-216">F# の場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4300e-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="4300e-217">このような使用シナリオは、アクセスされる API が C# と F# 用に異なる構造を持つ必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="4300e-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="4300e-218">これを実現する一般的なアプローチとして、ライブラリのすべてのロジックをコア プロジェクトに取り入れ、C# および F# プロジェクトでコア プロジェクトに呼び出す API レイヤーを定義する方法があります。</span><span class="sxs-lookup"><span data-stu-id="4300e-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="4300e-219">以降のセクションでは、次の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="4300e-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="4300e-220">**AwesomeLibrary.Core** - ライブラリのすべてのロジックを含むコア プロジェクト</span><span class="sxs-lookup"><span data-stu-id="4300e-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="4300e-221">**AwesomeLibrary.CSharp** - C# で使用するためのパブリック API を含むプロジェクト</span><span class="sxs-lookup"><span data-stu-id="4300e-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="4300e-222">**AwesomeLibrary.FSharp** - F# で使用するためのパブリック API を含むプロジェクト</span><span class="sxs-lookup"><span data-stu-id="4300e-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="4300e-223">自分の端末で次のコマンドを実行し、このガイドと同じ構造を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="4300e-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="4300e-224">これで上記の 3 つのプロジェクトと、それらをリンクするソリューション ファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="4300e-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="4300e-225">ソリューション ファイルとリンク プロジェクトを作成すると、最上位レベルからプロジェクトを復元し、ビルドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="4300e-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="4300e-226">プロジェクト間参照</span><span class="sxs-lookup"><span data-stu-id="4300e-226">Project-to-project referencing</span></span>

<span data-ttu-id="4300e-227">プロジェクトを参照するには、.NET Core CLI を使用してプロジェクト参照を追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4300e-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="4300e-228">**AwesomeLibrary.CSharp** と **AwesomeLibrary.FSharp** のプロジェクト ディレクトリから、次のコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4300e-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="4300e-229">**AwesomeLibrary.CSharp** と **AwesomeLibrary.FSharp** の両方のプロジェクト ファイルは、`ProjectReference` ターゲットとして **AwesomeLibrary.Core** を参照するようになります。</span><span class="sxs-lookup"><span data-stu-id="4300e-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="4300e-230">この参照を確認するには、プロジェクト ファイルに以下の行があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4300e-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="4300e-231">この .NET Core CLI を使用しない場合は、このセクションを各プロジェクト ファイルに手動で追加します。</span><span class="sxs-lookup"><span data-stu-id="4300e-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="4300e-232">ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="4300e-232">Structuring a solution</span></span>

<span data-ttu-id="4300e-233">マルチプロジェクト ソリューションのもう 1 つの重要な側面は、全体のプロジェクト構造を適切に構築することです。</span><span class="sxs-lookup"><span data-stu-id="4300e-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="4300e-234">ただし、`dotnet sln add` でソリューション ファイルに各プロジェクト ファイルがリンクされ、ソリューション レベルで `dotnet restore` と `dotnet build` を実行できる限り、好みに応じてコードを整理することができます。</span><span class="sxs-lookup"><span data-stu-id="4300e-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
