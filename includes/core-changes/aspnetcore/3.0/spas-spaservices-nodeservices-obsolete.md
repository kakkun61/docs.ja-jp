---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032679"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="87e20-101">SPA: SpaServices および NodeServices が古いものとしてマークされた</span><span class="sxs-lookup"><span data-stu-id="87e20-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="87e20-102">以下の NuGet パッケージの内容は、ASP.NET Core 2.1 以降ではすべて不要になりました。</span><span class="sxs-lookup"><span data-stu-id="87e20-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="87e20-103">その結果、以下のパッケージは古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="87e20-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="87e20-104">Microsoft.AspNetCore.SpaServices</span><span class="sxs-lookup"><span data-stu-id="87e20-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="87e20-105">Microsoft.AspNetCore.NodeServices</span><span class="sxs-lookup"><span data-stu-id="87e20-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="87e20-106">同じ理由から、以下の npm モジュールは非推奨としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="87e20-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="87e20-107">aspnet-angular</span><span class="sxs-lookup"><span data-stu-id="87e20-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="87e20-108">aspnet-prerendering</span><span class="sxs-lookup"><span data-stu-id="87e20-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="87e20-109">aspnet-webpack</span><span class="sxs-lookup"><span data-stu-id="87e20-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="87e20-110">aspnet-webpack-react</span><span class="sxs-lookup"><span data-stu-id="87e20-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="87e20-111">domain-task</span><span class="sxs-lookup"><span data-stu-id="87e20-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="87e20-112">上記のパッケージと npm モジュールは、今後 .NET 5 で削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="87e20-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="87e20-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="87e20-113">Version introduced</span></span>

<span data-ttu-id="87e20-114">3.0</span><span class="sxs-lookup"><span data-stu-id="87e20-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="87e20-115">以前の動作</span><span class="sxs-lookup"><span data-stu-id="87e20-115">Old behavior</span></span>

<span data-ttu-id="87e20-116">非推奨のパッケージと npm モジュールは、ASP.NET Core をさまざまなシングルページ アプリ (SPA) フレームワークと統合するためのものでした。</span><span class="sxs-lookup"><span data-stu-id="87e20-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="87e20-117">そのようなフレームワークとしては、Angular、React、React with Redux などがあります。</span><span class="sxs-lookup"><span data-stu-id="87e20-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="87e20-118">新しい動作</span><span class="sxs-lookup"><span data-stu-id="87e20-118">New behavior</span></span>

<span data-ttu-id="87e20-119">[Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet パッケージには新しい統合メカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="87e20-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="87e20-120">そのパッケージは、ASP.NET Core 2.1 以降、Angular および React プロジェクト テンプレートの基礎になっています。</span><span class="sxs-lookup"><span data-stu-id="87e20-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="87e20-121">変更理由</span><span class="sxs-lookup"><span data-stu-id="87e20-121">Reason for change</span></span>

<span data-ttu-id="87e20-122">ASP.NET Core では、Angular、React、React with Redux など、さまざまなシングルページ アプリ (SPA) フレームワークとの統合がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="87e20-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="87e20-123">当初、これらのフレームワークとの統合は、サーバー側プリレンダリングや Webpack との統合などのシナリオを処理する ASP.NET Core 固有のコンポーネントを使用して行われていました。</span><span class="sxs-lookup"><span data-stu-id="87e20-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="87e20-124">時間と共に、業界標準は変化しました。</span><span class="sxs-lookup"><span data-stu-id="87e20-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="87e20-125">各 SPA フレームワークにおいて、独自の標準コマンドライン インターフェイスがリリースされました。</span><span class="sxs-lookup"><span data-stu-id="87e20-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="87e20-126">たとえば、Angular CLI や create-react-app などです。</span><span class="sxs-lookup"><span data-stu-id="87e20-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="87e20-127">2018 年 5 月に ASP.NET Core 2.1 がリリースされたとき、チームは標準の変更に対応しました。</span><span class="sxs-lookup"><span data-stu-id="87e20-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="87e20-128">SPA フレームワーク独自のツールチェーンと統合するための、より新しくて簡単な方法が提供されました。</span><span class="sxs-lookup"><span data-stu-id="87e20-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="87e20-129">その新しい統合メカニズムはパッケージ `Microsoft.AspNetCore.SpaServices.Extensions` に存在しており、ASP.NET Core 2.1 以降、Angular および React プロジェクト テンプレートの基礎になっています。</span><span class="sxs-lookup"><span data-stu-id="87e20-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="87e20-130">古い ASP.NET Core 固有のコンポーネントは不適切であり、推奨されないことを明確にするために、次のようにしました。</span><span class="sxs-lookup"><span data-stu-id="87e20-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="87e20-131">2\.1 より前の統合メカニズムは、旧式とマークされています。</span><span class="sxs-lookup"><span data-stu-id="87e20-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="87e20-132">npm パッケージのサポートは非推奨とマークされています。</span><span class="sxs-lookup"><span data-stu-id="87e20-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87e20-133">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="87e20-133">Recommended action</span></span>

<span data-ttu-id="87e20-134">これらのパッケージを使用している場合は、次の機能を使用するようにアプリを更新してください。</span><span class="sxs-lookup"><span data-stu-id="87e20-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="87e20-135">`Microsoft.AspNetCore.SpaServices.Extensions` パッケージ内のもの。</span><span class="sxs-lookup"><span data-stu-id="87e20-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="87e20-136">使用している SPA フレームワークによって提供されるもの</span><span class="sxs-lookup"><span data-stu-id="87e20-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="87e20-137">サーバー側プリレンダリングやホット モジュール リロードなどの機能を有効にするには、対応する SPA フレームワークのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87e20-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="87e20-138">`Microsoft.AspNetCore.SpaServices.Extensions` の機能は古くなって "*おらず*"、引き続きサポートされます。</span><span class="sxs-lookup"><span data-stu-id="87e20-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="87e20-139">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="87e20-139">Category</span></span>

<span data-ttu-id="87e20-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="87e20-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87e20-141">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="87e20-141">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
