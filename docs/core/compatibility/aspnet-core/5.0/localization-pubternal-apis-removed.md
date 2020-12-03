---
title: 破壊的変更:Pubternal API が削除された
description: ASP.NET Core 5.0 の破壊的変更について学習します。この変更後、一部の Pubternal ローカライズ API が削除されました。
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ae647d66b716175536edb3c978b027ebb7d3ddac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759359"
---
# <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="1fe79-103">ローカリゼーション:"Pubternal" API の削除</span><span class="sxs-lookup"><span data-stu-id="1fe79-103">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="1fe79-104">ASP.NET Core のパブリック API サーフェイスをより適切に維持するために、一部の :::no-loc text="\"pubternal\""::: ローカライズ API を削除しました。</span><span class="sxs-lookup"><span data-stu-id="1fe79-104">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="1fe79-105">:::no-loc text="\"pubternal\""::: API には、`public` のアクセス修飾子があり、[internal](../../../../csharp/language-reference/keywords/internal.md) インテントを意味する名前空間に定義されています。</span><span class="sxs-lookup"><span data-stu-id="1fe79-105">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="1fe79-106">ディスカッションについては、[dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fe79-106">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1fe79-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="1fe79-107">Version introduced</span></span>

<span data-ttu-id="1fe79-108">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="1fe79-108">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="1fe79-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="1fe79-109">Old behavior</span></span>

<span data-ttu-id="1fe79-110">次の API が `public` でした。</span><span class="sxs-lookup"><span data-stu-id="1fe79-110">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="1fe79-111">次のいずれかのパラメーター型を取る `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` コンストラクター オーバーロード。</span><span class="sxs-lookup"><span data-stu-id="1fe79-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a><span data-ttu-id="1fe79-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="1fe79-112">New behavior</span></span>

<span data-ttu-id="1fe79-113">変更一覧の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1fe79-113">The following list outlines the changes:</span></span>

- <span data-ttu-id="1fe79-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` が `Microsoft.Extensions.Localization.AssemblyWrapper` となり、現在 `internal` になりました。</span><span class="sxs-lookup"><span data-stu-id="1fe79-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="1fe79-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` が `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` となり、現在 `internal` になりました。</span><span class="sxs-lookup"><span data-stu-id="1fe79-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="1fe79-116">次のいずれかのパラメーター型を取る `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` コンストラクター オーバーロードは、現在 `internal` になりました。</span><span class="sxs-lookup"><span data-stu-id="1fe79-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a><span data-ttu-id="1fe79-117">変更理由</span><span class="sxs-lookup"><span data-stu-id="1fe79-117">Reason for change</span></span>

<span data-ttu-id="1fe79-118">詳細は、[aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882) で説明していますが、:::no-loc text="\"pubternal\""::: 型が `public` API サーフェイスから削除されました。</span><span class="sxs-lookup"><span data-stu-id="1fe79-118">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="1fe79-119">これらの変更により、その設計判断により多くのクラスを順応させることができます。</span><span class="sxs-lookup"><span data-stu-id="1fe79-119">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="1fe79-120">問題のクラスは、チームの内部テストの拡張ポイントを意味していました。</span><span class="sxs-lookup"><span data-stu-id="1fe79-120">The classes in question were intended as extension points for the team's internal testing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1fe79-121">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="1fe79-121">Recommended action</span></span>

<span data-ttu-id="1fe79-122">可能性は低いですが、一部のアプリが意図的にまたは誤って :::no-loc text="\"pubternal\""::: 型に依存するようになっている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1fe79-122">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="1fe79-123">この型から移行する方法については、「[新しい動作](#new-behavior)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fe79-123">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="1fe79-124">この変更の前にはパブリックとして許可されていた API が、現在では許可されなくなったシナリオを特定した場合は、[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) にイシューを立ててください。</span><span class="sxs-lookup"><span data-stu-id="1fe79-124">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1fe79-125">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="1fe79-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
