---
title: 破壊的変更:HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c51b1dd9d708c04bc1bbcfb65ea2e9daea5330b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759420"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="afd0b-103">HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました</span><span class="sxs-lookup"><span data-stu-id="afd0b-103">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="afd0b-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は非推奨となっており、`Microsoft.AspNetCore.Http.BadHttpRequestException` から誘導するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="afd0b-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="afd0b-105">Kestrel サーバーと IIS サーバーでは、下位互換性のために、今後も以前の例外型がスローされます。</span><span class="sxs-lookup"><span data-stu-id="afd0b-105">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="afd0b-106">非推奨になった型は、将来のリリースで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="afd0b-106">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="afd0b-107">ディスカッションについては、[dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afd0b-107">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="afd0b-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="afd0b-108">Version introduced</span></span>

<span data-ttu-id="afd0b-109">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="afd0b-109">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="afd0b-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="afd0b-110">Old behavior</span></span>

<span data-ttu-id="afd0b-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と`Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は <xref:System.IO.IOException?displayProperty=nameWithType> から派生しています。</span><span class="sxs-lookup"><span data-stu-id="afd0b-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="afd0b-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="afd0b-112">New behavior</span></span>

<span data-ttu-id="afd0b-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="afd0b-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="afd0b-114">型は、`System.IO.IOException` の派生型である `Microsoft.AspNetCore.Http.BadHttpRequestException` からも派生します。</span><span class="sxs-lookup"><span data-stu-id="afd0b-114">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="afd0b-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="afd0b-115">Reason for change</span></span>

<span data-ttu-id="afd0b-116">次の変更が行われました。</span><span class="sxs-lookup"><span data-stu-id="afd0b-116">The change was made to:</span></span>

* <span data-ttu-id="afd0b-117">重複する型を統合します。</span><span class="sxs-lookup"><span data-stu-id="afd0b-117">Consolidate duplicate types.</span></span>
* <span data-ttu-id="afd0b-118">異なるサーバー実装間で動作を統一します。</span><span class="sxs-lookup"><span data-stu-id="afd0b-118">Unify behavior across server implementations.</span></span>

<span data-ttu-id="afd0b-119">Kestrel または IIS の使用時、アプリで基本例外 `Microsoft.AspNetCore.Http.BadHttpRequestException` をキャッチできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="afd0b-119">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="afd0b-120">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="afd0b-120">Recommended action</span></span>

<span data-ttu-id="afd0b-121">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` の使用状況を `Microsoft.AspNetCore.Http.BadHttpRequestException` に置換します。</span><span class="sxs-lookup"><span data-stu-id="afd0b-121">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="afd0b-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="afd0b-122">Affected APIs</span></span>

- [<span data-ttu-id="afd0b-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="afd0b-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="afd0b-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="afd0b-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
