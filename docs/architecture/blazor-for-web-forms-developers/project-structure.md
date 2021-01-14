---
title: アプリのプロジェクト構造 Blazor
description: ASP.NET Web フォームおよびプロジェクトのプロジェクト構造を比較する方法について説明 Blazor します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: ba7113c88db728f30812821deaf7c06a80663d1f
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189090"
---
# <a name="project-structure-for-no-locblazor-apps"></a><span data-ttu-id="5ef00-103">アプリのプロジェクト構造 Blazor</span><span class="sxs-lookup"><span data-stu-id="5ef00-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="5ef00-104">大きなプロジェクト構造の違いにもかかわらず、ASP.NET の Web フォームは、 Blazor さまざまな概念を共有しています。</span><span class="sxs-lookup"><span data-stu-id="5ef00-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="5ef00-105">ここでは、プロジェクトの構造を見 Blazor て、それを ASP.NET の Web フォームプロジェクトと比較します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="5ef00-106">最初のアプリを作成するには、 Blazor 「 [ Blazor 作業の開始](/aspnet/core/blazor/get-started)」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="5ef00-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="5ef00-107">指示に従って、 Blazor ASP.NET Core でホストされているサーバーアプリまたはアプリを作成でき Blazor WebAssembly ます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="5ef00-108">ホスティングモデル固有のロジックを除き、両方のプロジェクトのコードのほとんどは同じです。</span><span class="sxs-lookup"><span data-stu-id="5ef00-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="5ef00-109">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="5ef00-109">Project file</span></span>

<span data-ttu-id="5ef00-110">Blazor サーバーアプリは .NET プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="5ef00-110">Blazor Server apps are .NET projects.</span></span> <span data-ttu-id="5ef00-111">サーバーアプリのプロジェクトファイル Blazor は、次のように簡単に取得できます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="5ef00-112">アプリのプロジェクトファイルは Blazor WebAssembly 少し複雑になります (正確なバージョン番号は異なる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="5ef00-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="5ef00-113">BlazorWebAssembly `Microsoft.NET.Sdk.BlazorWebAssembly` `Microsoft.NET.Sdk.Web` ベースの .net ランタイムでブラウザーで実行されるため、sdk ではなくプロジェクトターゲット WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="5ef00-113">Blazor WebAssembly project targets `Microsoft.NET.Sdk.BlazorWebAssembly` instead of `Microsoft.NET.Sdk.Web` sdk because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="5ef00-114">サーバーや開発者のコンピューターで使用できるように、web ブラウザーに .NET をインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="5ef00-115">その結果、プロジェクトは Blazor 個別のパッケージ参照を使用してフレームワークを参照します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="5ef00-116">これに対し、既定の ASP.NET Web フォームプロジェクトでは、 *.csproj* ファイルに約300行の XML が含まれています。そのほとんどは、プロジェクト内のさまざまなコードおよびコンテンツファイルを明示的に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="5ef00-117">とアプリのリリースでは、 `.NET 5` `Blazor Server` 統合された `Blazor WebAssembly` 1 つのランタイムを簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-117">With the release of `.NET 5` both `Blazor Server` and `Blazor WebAssembly` app can easily share one unified runtime.</span></span>

<span data-ttu-id="5ef00-118">これらはサポートされていますが、個々のアセンブリ参照は .NET プロジェクトではあまり一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-118">Although they're supported, individual assembly references are less common in .NET projects.</span></span> <span data-ttu-id="5ef00-119">ほとんどのプロジェクトの依存関係は、NuGet パッケージ参照として処理されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-119">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="5ef00-120">.NET プロジェクトでは、最上位レベルのパッケージの依存関係を参照するだけです。</span><span class="sxs-lookup"><span data-stu-id="5ef00-120">You only need to reference top-level package dependencies in .NET projects.</span></span> <span data-ttu-id="5ef00-121">推移的な依存関係は自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-121">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="5ef00-122">ASP.NET Web フォームプロジェクトでよく見られる *packages.config* ファイルを使用してパッケージを参照するのではなく、要素を使用してパッケージ参照をプロジェクトファイルに追加し `<PackageReference>` ます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-122">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="5ef00-123">エントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="5ef00-123">Entry point</span></span>

<span data-ttu-id="5ef00-124">Blazorサーバーアプリのエントリポイントは、コンソールアプリで見られるように、 *Program.cs* ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-124">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="5ef00-125">アプリを実行すると、web アプリ固有の既定値を使用して web ホストインスタンスが作成され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-125">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="5ef00-126">Web ホストは、 Blazor サーバーアプリのライフサイクルを管理し、ホストレベルのサービスを設定します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-126">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="5ef00-127">このようなサービスの例としては、構成、ログ記録、依存関係の注入、HTTP サーバーなどがあります。</span><span class="sxs-lookup"><span data-stu-id="5ef00-127">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="5ef00-128">このコードはほとんどが定型であり、変更されることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-128">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

<span data-ttu-id="5ef00-129">BlazorWebAssemblyアプリでは、 *Program.cs* にエントリポイントを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-129">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="5ef00-130">コードは少し異なります。</span><span class="sxs-lookup"><span data-stu-id="5ef00-130">The code looks slightly different.</span></span> <span data-ttu-id="5ef00-131">コードは、同じホストレベルのサービスをアプリに提供するようにアプリホストを設定するという点で似ています。</span><span class="sxs-lookup"><span data-stu-id="5ef00-131">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="5ef00-132">WebAssemblyただし、アプリホストは、ブラウザーで直接実行されるため、HTTP サーバーを設定しません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-132">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="5ef00-133">Blazor アプリには、 `Startup` アプリのスタートアップロジックを定義するための、 *global.asax* ファイルではなくクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="5ef00-133">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="5ef00-134">クラスは、 `Startup` アプリとアプリ固有のサービスを構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-134">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="5ef00-135">Blazorサーバーアプリで `Startup` は、クラスを使用して、クライアントブラウザーとサーバーの間で使用されるリアルタイム接続のエンドポイントを設定し Blazor ます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-135">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="5ef00-136">アプリでは、クラスによって、 Blazor WebAssembly `Startup` アプリのルートコンポーネントと、それらをレンダリングする場所が定義されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-136">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="5ef00-137">このクラスについては `Startup` 、「 [アプリのスタートアップ](./app-startup.md) 」セクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-137">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="5ef00-138">静的ファイル</span><span class="sxs-lookup"><span data-stu-id="5ef00-138">Static files</span></span>

<span data-ttu-id="5ef00-139">ASP.NET Web フォームプロジェクトとは異なり、プロジェクト内のすべてのファイルを Blazor 静的ファイルとして要求することはできません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-139">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="5ef00-140">*Wwwroot* フォルダー内のファイルのみが web アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-140">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="5ef00-141">このフォルダーは、アプリの "web ルート" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-141">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="5ef00-142">アプリの web ルート以外のものは、web アドレスを指定でき *ません* 。</span><span class="sxs-lookup"><span data-stu-id="5ef00-142">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="5ef00-143">このセットアップでは、web 経由でプロジェクトファイルが誤って公開されないようにするための追加のセキュリティレベルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-143">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="5ef00-144">構成</span><span class="sxs-lookup"><span data-stu-id="5ef00-144">Configuration</span></span>

<span data-ttu-id="5ef00-145">ASP.NET Web フォームアプリの構成は、通常、1つ以上の *web.config* ファイルを使用して処理されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-145">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="5ef00-146">Blazor 通常、アプリには *web.config* ファイルがありません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-146">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="5ef00-147">ファイルがある場合は、IIS でホストされている場合にのみ、ファイルが IIS 固有の設定を構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-147">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="5ef00-148">代わりに、 Blazor サーバーアプリは ASP.NET Core 構成の抽象化を使用し Blazor WebAssembly ます (現在、アプリでは同じ構成の抽象化はサポートされていませんが、将来追加される機能である可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="5ef00-148">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="5ef00-149">たとえば、既定のサーバーアプリでは、 Blazor 一部の設定が *appsettings.js* に格納されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-149">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="5ef00-150">構成の詳細については、 [構成](./config.md) セクションの ASP.NET Core プロジェクトに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef00-150">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="5ef00-151">Razor のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="5ef00-151">Razor components</span></span>

<span data-ttu-id="5ef00-152">プロジェクト内のほとんどのファイル Blazor は、 *razor* ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5ef00-152">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="5ef00-153">Razor は、web UI を動的に生成するために使用される HTML および C# に基づくテンプレート言語です。</span><span class="sxs-lookup"><span data-stu-id="5ef00-153">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="5ef00-154">この *razor* ファイルは、アプリの UI を構成するコンポーネントを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-154">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="5ef00-155">ほとんどの場合、コンポーネントはサーバーとアプリの両方で同一です Blazor Blazor WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="5ef00-155">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="5ef00-156">のコンポーネント Blazor は、ASP.NET Web フォームのユーザーコントロールに似ています。</span><span class="sxs-lookup"><span data-stu-id="5ef00-156">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="5ef00-157">各 Razor コンポーネントファイルは、プロジェクトのビルド時に .NET クラスにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-157">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="5ef00-158">生成されたクラスは、コンポーネントの状態、レンダリングロジック、ライフサイクルメソッド、イベントハンドラー、およびその他のロジックをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="5ef00-158">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="5ef00-159">「[再利用可能な UI コンポーネントの構築 Blazor ](./components.md) 」セクションの「コンポーネントの作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef00-159">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="5ef00-160">*_Imports razor* ファイルは razor コンポーネントファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-160">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="5ef00-161">代わりに、同じフォルダーおよびそのサブフォルダー内の他の *razor* ファイルにインポートする razor ディレクティブのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-161">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="5ef00-162">たとえば、_Imports の *razor* ファイルは、 `using` 一般的に使用される名前空間のディレクティブを追加する従来の方法です。</span><span class="sxs-lookup"><span data-stu-id="5ef00-162">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="5ef00-163">Pages</span><span class="sxs-lookup"><span data-stu-id="5ef00-163">Pages</span></span>

<span data-ttu-id="5ef00-164">アプリ内のページはどこにあり Blazor ますか。</span><span class="sxs-lookup"><span data-stu-id="5ef00-164">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="5ef00-165">Blazor では、ASP.NET Web フォームアプリの *.aspx* ファイルのように、アドレス指定可能なページに対して個別のファイル拡張子は定義されません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-165">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="5ef00-166">代わりに、ページはコンポーネントにルートを割り当てることによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-166">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="5ef00-167">ルートは通常、Razor ディレクティブを使用して割り当てられ `@page` ます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-167">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="5ef00-168">たとえば、 `Counter` *Pages/Counter. razor* ファイルで作成されたコンポーネントは、次のルートを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-168">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="5ef00-169">でのルーティング Blazor は、サーバー上ではなく、クライアント側で処理されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-169">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="5ef00-170">ユーザーがブラウザーで移動すると、はナビゲーションをインターセプトし、 Blazor 一致するルートを使用してコンポーネントをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="5ef00-170">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="5ef00-171">コンポーネントのルートは、現在、 *.aspx* ページのようなコンポーネントのファイルの場所によって推測されていません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-171">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="5ef00-172">この機能は今後追加される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ef00-172">This feature may be added in the future.</span></span> <span data-ttu-id="5ef00-173">各ルートは、コンポーネントに対して明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ef00-173">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="5ef00-174">ルーティング可能なコンポーネントを *Pages* フォルダーに格納することは、特別な意味を持たず、純粋に規則です。</span><span class="sxs-lookup"><span data-stu-id="5ef00-174">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="5ef00-175">詳細につい Blazor ては、「 [ページ、ルーティング、およびレイアウト](./pages-routing-layouts.md) 」セクションの「ルーティング」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef00-175">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="5ef00-176">Layout</span><span class="sxs-lookup"><span data-stu-id="5ef00-176">Layout</span></span>

<span data-ttu-id="5ef00-177">ASP.NET Web フォームアプリでは、共通ページレイアウトはマスターページ (*.master*) を使用して処理されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-177">In ASP.NET Web Forms apps, a common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="5ef00-178">Blazorアプリでは、ページレイアウトはレイアウトコンポーネント (*Shared/mainlayout. razor*) を使用して処理されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-178">In Blazor apps, the page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="5ef00-179">レイアウトコンポーネントの詳細につい [ては、「ページ、ルーティング、レイアウト](./pages-routing-layouts.md) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef00-179">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-no-locblazor"></a><span data-ttu-id="5ef00-180">ブートストラップ Blazor</span><span class="sxs-lookup"><span data-stu-id="5ef00-180">Bootstrap Blazor</span></span>

<span data-ttu-id="5ef00-181">ブートストラップの Blazor 場合、アプリは次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ef00-181">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="5ef00-182">ページ上のルートコンポーネント (*app.xaml*) を表示する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-182">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="5ef00-183">対応する Blazor フレームワークスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-183">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="5ef00-184">Blazorサーバーアプリでは、ルートコンポーネントのホストページは *_Host* ファイルに定義されています。</span><span class="sxs-lookup"><span data-stu-id="5ef00-184">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="5ef00-185">このファイルは、コンポーネントではなく Razor ページを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-185">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="5ef00-186">Razor 構文 Razor Pages 使用して、サーバーアドレス指定可能なページを定義し *ます。* これは .aspx ページとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="5ef00-186">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="5ef00-187">`Html.RenderComponentAsync<TComponent>(RenderMode)`メソッドは、ルートレベルのコンポーネントを表示する場所を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-187">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="5ef00-188">オプションは、 `RenderMode` コンポーネントを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-188">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="5ef00-189">次の表に、サポートされるオプションの概要を示し `RenderMode` ます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-189">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="5ef00-190">オプション</span><span class="sxs-lookup"><span data-stu-id="5ef00-190">Option</span></span>                        |<span data-ttu-id="5ef00-191">説明</span><span class="sxs-lookup"><span data-stu-id="5ef00-191">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="5ef00-192">ブラウザーとの接続が確立されると、対話形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-192">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="5ef00-193">最初の prerendered してから対話形式で表示する</span><span class="sxs-lookup"><span data-stu-id="5ef00-193">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="5ef00-194">静的コンテンツとしてレンダリング</span><span class="sxs-lookup"><span data-stu-id="5ef00-194">Rendered as static content</span></span>|

<span data-ttu-id="5ef00-195">*_Framework/blazor.server.js* へのスクリプト参照は、サーバーとのリアルタイム接続を確立し、すべてのユーザー操作と UI 更新を処理します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-195">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="5ef00-196">アプリで Blazor WebAssembly は、ホストページは *wwwroot/index.html* の下の単純な静的 HTML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5ef00-196">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="5ef00-197">`<div>`という id を持つ要素 `app` は、ルートコンポーネントのレンダリング先を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-197">The `<div>` element with id named `app` is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

<span data-ttu-id="5ef00-198">レンダリングするルートコンポーネントは、アプリのメソッドで指定され、 `Program.Main` 依存関係の挿入によってサービスを登録する柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="5ef00-198">The root component to render is specified in the app's `Program.Main` method with the flexibility to register services through dependency injection.</span></span> <span data-ttu-id="5ef00-199">詳細については、「 [ASP.NET Core Blazor 依存関係の挿入](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef00-199">For more information, see [ASP.NET Core Blazor dependency injection](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).</span></span>

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a><span data-ttu-id="5ef00-200">ビルド出力</span><span class="sxs-lookup"><span data-stu-id="5ef00-200">Build output</span></span>

<span data-ttu-id="5ef00-201">プロジェクトを Blazor ビルドすると、すべての Razor コンポーネントとコードファイルが1つのアセンブリにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-201">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="5ef00-202">ASP.NET Web フォームプロジェクトとは異なり、は Blazor UI ロジックのランタイムコンパイルをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-202">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="5ef00-203">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="5ef00-203">Run the app</span></span>

<span data-ttu-id="5ef00-204">サーバーアプリを実行するには Blazor 、 `F5` Visual Studio でを押します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-204">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="5ef00-205">Blazor アプリはランタイムコンパイルをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5ef00-205">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="5ef00-206">コードとコンポーネントのマークアップの変更結果を表示するには、デバッガーがアタッチされた状態でアプリをリビルドして再起動します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-206">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="5ef00-207">デバッガーがアタッチされていない状態でを実行した場合 ( `Ctrl+F5` )、Visual Studio はファイルの変更を監視し、変更が加えられるとアプリを再起動します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-207">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="5ef00-208">変更が行われると、ブラウザーが手動で更新されます。</span><span class="sxs-lookup"><span data-stu-id="5ef00-208">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="5ef00-209">アプリを実行するには Blazor WebAssembly 、次のいずれかの方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-209">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="5ef00-210">開発サーバーを使用して、クライアントプロジェクトを直接実行します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-210">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="5ef00-211">ASP.NET Core を使用してアプリをホストするときに、サーバープロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="5ef00-211">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="5ef00-212">BlazorWebAssemblyアプリは、ブラウザーと Visual Studio の両方でデバッグできます。詳細については、[デバッグ ASP.NET Core Blazor WebAssembly ](/aspnet/core/blazor/debug)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef00-212">Blazor WebAssembly apps can be debugged in both browser and Visual Studio.See [Debug ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5ef00-213">[前へ](hosting-models.md)
>[次へ](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="5ef00-213">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
