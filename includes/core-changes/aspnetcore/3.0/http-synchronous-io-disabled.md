---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032548"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="8f2f2-101">HTTP:すべてのサーバーで同期 IO が無効になっています</span><span class="sxs-lookup"><span data-stu-id="8f2f2-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="8f2f2-102">ASP.NET Core 3.0 以降では、同期サーバー操作は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8f2f2-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="8f2f2-103">Change description</span></span>

<span data-ttu-id="8f2f2-104">`AllowSynchronousIO` は、`HttpRequest.Body.Read`、`HttpResponse.Body.Write`、`Stream.Flush` などの同期 IO API を有効または無効にする各サーバーのオプションです。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="8f2f2-105">これらの API は長い間、スレッドの枯渇とアプリのハングの原因になっていました。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="8f2f2-106">ASP.NET Core 3.0 Preview 3 以降では、これらの同期操作は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="8f2f2-107">影響を受けるサーバー:</span><span class="sxs-lookup"><span data-stu-id="8f2f2-107">Affected servers:</span></span>

- <span data-ttu-id="8f2f2-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="8f2f2-108">Kestrel</span></span>
- <span data-ttu-id="8f2f2-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="8f2f2-109">HttpSys</span></span>
- <span data-ttu-id="8f2f2-110">IIS インプロセス</span><span class="sxs-lookup"><span data-stu-id="8f2f2-110">IIS in-process</span></span>
- <span data-ttu-id="8f2f2-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="8f2f2-111">TestServer</span></span>

<span data-ttu-id="8f2f2-112">次のようなエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="8f2f2-113">各サーバーには、この動作を制御する `AllowSynchronousIO` オプションがあり、そのすべての既定値は現在、`false` です。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="8f2f2-114">この動作は、一時的な軽減策として、要求ごとにオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="8f2f2-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="8f2f2-116">`TextWriter`、または `Dispose` で同期 API を呼び出す別のストリームで問題が発生した場合は、代わりに新しい `DisposeAsync` API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="8f2f2-117">ディスカッションについては、[dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8f2f2-118">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8f2f2-118">Version introduced</span></span>

<span data-ttu-id="8f2f2-119">3.0</span><span class="sxs-lookup"><span data-stu-id="8f2f2-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8f2f2-120">以前の動作</span><span class="sxs-lookup"><span data-stu-id="8f2f2-120">Old behavior</span></span>

<span data-ttu-id="8f2f2-121">`HttpRequest.Body.Read`、`HttpResponse.Body.Write`、および `Stream.Flush` が既定で許可されていました。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8f2f2-122">新しい動作</span><span class="sxs-lookup"><span data-stu-id="8f2f2-122">New behavior</span></span>

<span data-ttu-id="8f2f2-123">これらの同期 API は、既定では許可されません。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="8f2f2-124">次のようなエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="8f2f2-125">変更理由</span><span class="sxs-lookup"><span data-stu-id="8f2f2-125">Reason for change</span></span>

<span data-ttu-id="8f2f2-126">これらの同期 API は長い間、スレッドの枯渇とアプリのハングの原因になっていました。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="8f2f2-127">ASP.NET Core 3.0 Preview 3 以降では、同期操作は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8f2f2-128">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="8f2f2-128">Recommended action</span></span>

<span data-ttu-id="8f2f2-129">非同期バージョンのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="8f2f2-130">この動作は、一時的な軽減策として、要求ごとにオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8f2f2-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="8f2f2-131">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="8f2f2-131">Category</span></span>

<span data-ttu-id="8f2f2-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8f2f2-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8f2f2-133">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8f2f2-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
