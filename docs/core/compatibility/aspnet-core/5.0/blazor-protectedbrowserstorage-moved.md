---
title: '破壊的変更:Blazor: ProtectedBrowserStorage 機能を共有フレームワークに移行'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:ProtectedBrowserStorage 機能を共有フレームワークに移行'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c8058adf8b66aef8dd011ea672cd306ae4de60a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759427"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="20875-103">Blazor: ProtectedBrowserStorage 機能を共有フレームワークに移行</span><span class="sxs-lookup"><span data-stu-id="20875-103">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="20875-104">ASP.NET Core 5.0 RC2 リリースの一部として、`ProtectedBrowserStorage` 機能は ASP.NET Core 共有フレームワークに移行されました。</span><span class="sxs-lookup"><span data-stu-id="20875-104">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="20875-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="20875-105">Version introduced</span></span>

<span data-ttu-id="20875-106">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="20875-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="20875-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="20875-107">Old behavior</span></span>

<span data-ttu-id="20875-108">ASP.NET Core 5.0 Preview 8 では、この機能は [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) パッケージの一部として利用できますが、Blazor WebAssembly でのみ使用可能でした。</span><span class="sxs-lookup"><span data-stu-id="20875-108">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="20875-109">ASP.NET Core 5.0 RC1 では、この機能は `Microsoft.AspNetCore.App` 共有フレームワークが参照される [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) パッケージの一部として利用できます。</span><span class="sxs-lookup"><span data-stu-id="20875-109">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="20875-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="20875-110">New behavior</span></span>

<span data-ttu-id="20875-111">ASP.NET Core 5.0 RC2 では、機能を参照して使用するために NuGet パッケージ参照が不要になりました。</span><span class="sxs-lookup"><span data-stu-id="20875-111">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="20875-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="20875-112">Reason for change</span></span>

<span data-ttu-id="20875-113">共有フレームワークへの移行は、お客様が期待するユーザー エクスペリエンスにより適っています。</span><span class="sxs-lookup"><span data-stu-id="20875-113">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="20875-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="20875-114">Recommended action</span></span>

<span data-ttu-id="20875-115">ASP.NET Core 5.0 RC1 からアップグレードする場合は、次の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="20875-115">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="20875-116">プロジェクトから `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` パッケージ参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="20875-116">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="20875-117">`using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` を `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` で置き換え</span><span class="sxs-lookup"><span data-stu-id="20875-117">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="20875-118">`Startup` クラスから `AddProtectedBrowserStorage` への呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="20875-118">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="20875-119">ASP.NET Core 5.0 Preview 8 からアップグレードする場合は、次の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="20875-119">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="20875-120">プロジェクトから `Microsoft.AspNetCore.Components.Web.Extensions` パッケージ参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="20875-120">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="20875-121">`using Microsoft.AspNetCore.Components.Web.Extensions;` を `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` で置き換え</span><span class="sxs-lookup"><span data-stu-id="20875-121">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="20875-122">`Startup` クラスから `AddProtectedBrowserStorage` への呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="20875-122">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="20875-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="20875-123">Affected APIs</span></span>

<span data-ttu-id="20875-124">なし</span><span class="sxs-lookup"><span data-stu-id="20875-124">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
