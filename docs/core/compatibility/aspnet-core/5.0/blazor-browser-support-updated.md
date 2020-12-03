---
title: '破壊的変更: Blazor: ブラウザー サポートの更新'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:ブラウザー サポートの更新'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 63b35aa8cb73bfb82c565007704375bac3737299
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759987"
---
# <a name="blazor-updated-browser-support"></a><span data-ttu-id="0c567-103">Blazor: ブラウザー サポートの更新</span><span class="sxs-lookup"><span data-stu-id="0c567-103">Blazor: Updated browser support</span></span>

<span data-ttu-id="0c567-104">ASP.NET Core 5.0 には、[新しい Blazor 機能](https://github.com/dotnet/aspnetcore/issues/21514)が導入されていますが、その一部は古いブラウザーと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="0c567-104">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="0c567-105">ASP.NET Core 5.0 の Blazor でサポートされているブラウザーのリストが、それに従って更新されています。</span><span class="sxs-lookup"><span data-stu-id="0c567-105">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="0c567-106">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c567-106">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0c567-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="0c567-107">Version introduced</span></span>

<span data-ttu-id="0c567-108">5.0</span><span class="sxs-lookup"><span data-stu-id="0c567-108">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="0c567-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="0c567-109">Old behavior</span></span>

<span data-ttu-id="0c567-110">Blazor Server は、十分なポリフィルを備えた Microsoft Internet Explorer 11 をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0c567-110">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="0c567-111">Blazor Server と Blazor WebAssembly は、[Microsoft Edge レガシ](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)でも機能します。</span><span class="sxs-lookup"><span data-stu-id="0c567-111">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="0c567-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="0c567-112">New behavior</span></span>

<span data-ttu-id="0c567-113">ASP.NET Core 5.0 の Blazor Server は、Microsoft Internet Explorer 11 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="0c567-113">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="0c567-114">Blazor Server と Blazor WebAssembly は、Microsoft Edge レガシでは完全には機能しません。</span><span class="sxs-lookup"><span data-stu-id="0c567-114">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0c567-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="0c567-115">Reason for change</span></span>

<span data-ttu-id="0c567-116">ASP.NET Core 5.0 の新しい Blazor 機能は、これらの古いブラウザーと互換性がなく、これらの古いブラウザーの使用は減少しています。</span><span class="sxs-lookup"><span data-stu-id="0c567-116">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="0c567-117">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c567-117">For more information, see the following resources:</span></span>

* [<span data-ttu-id="0c567-118">Microsoft Edge レガシの Windows サポートも、2021 年 3 月 9 日に終了します</span><span class="sxs-lookup"><span data-stu-id="0c567-118">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="0c567-119">Microsoft 365 のアプリとサービスでの Microsoft Internet Explorer 11 のサポートは、2021 年 8 月 17 日までに終了します</span><span class="sxs-lookup"><span data-stu-id="0c567-119">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a><span data-ttu-id="0c567-120">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="0c567-120">Recommended action</span></span>

<span data-ttu-id="0c567-121">これらの古いブラウザーから[新しい Chromium ベースの Microsoft Edge](https://www.microsoft.com/edge) にアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="0c567-121">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="0c567-122">これらの古いブラウザーをサポートする必要がある Blazor アプリの場合は、ASP.NET Core 3.1 を使用してください。</span><span class="sxs-lookup"><span data-stu-id="0c567-122">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="0c567-123">ASP.NET Core 3.1 の Blazor でサポートされているブラウザーのリストは変更されておらず、[サポートされているプラットフォーム](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1)に記載されています。</span><span class="sxs-lookup"><span data-stu-id="0c567-123">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0c567-124">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="0c567-124">Affected APIs</span></span>

<span data-ttu-id="0c567-125">なし</span><span class="sxs-lookup"><span data-stu-id="0c567-125">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
