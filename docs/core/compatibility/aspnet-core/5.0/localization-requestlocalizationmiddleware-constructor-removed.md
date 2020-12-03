---
title: 破壊的変更:ローカリゼーション:ローカライズ ミドルウェア要求で古いコンストラクターを削除
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: ローカリゼーション:ローカライズ ミドルウェア要求で古いコンストラクターを削除'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 53dd0f25078dae140d34d6d21d66983f78b8bdb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759957"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="512ca-103">ローカリゼーション:ローカライズ ミドルウェア要求で古いコンストラクターを削除</span><span class="sxs-lookup"><span data-stu-id="512ca-103">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="512ca-104"><xref:Microsoft.Extensions.Logging.ILoggerFactory> パラメーターのない <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> コンストラクターは[このコミットで](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="512ca-104">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="512ca-105">ASP.NET Core 5.0 では、非推奨コンストラクターが削除されました。</span><span class="sxs-lookup"><span data-stu-id="512ca-105">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="512ca-106">ディスカッションについては、[dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="512ca-106">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="512ca-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="512ca-107">Version introduced</span></span>

<span data-ttu-id="512ca-108">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="512ca-108">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="512ca-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="512ca-109">Old behavior</span></span>

<span data-ttu-id="512ca-110">非推奨 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` コンストラクターが存在します。</span><span class="sxs-lookup"><span data-stu-id="512ca-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="512ca-111">新しい動作</span><span class="sxs-lookup"><span data-stu-id="512ca-111">New behavior</span></span>

<span data-ttu-id="512ca-112">非推奨 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` コンストラクターが存在しません。</span><span class="sxs-lookup"><span data-stu-id="512ca-112">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="512ca-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="512ca-113">Reason for change</span></span>

<span data-ttu-id="512ca-114">この変更により、ローカライズ ミドルウェア要求で常にロガーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="512ca-114">This change ensures that the request localization middleware always has access to a logger.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="512ca-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="512ca-115">Recommended action</span></span>

<span data-ttu-id="512ca-116">`RequestLocalizationMiddleware` のインスタンスを手動で構築するとき、コンストラクターで `ILoggerFactory` インスタンスを渡します。</span><span class="sxs-lookup"><span data-stu-id="512ca-116">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="512ca-117">そのコンテキストで有効な `ILoggerFactory` インスタンスが利用できない場合、ミドルウェア コンストラクターに <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> インスタンスを渡すことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="512ca-117">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="512ca-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="512ca-118">Affected APIs</span></span>

[<span data-ttu-id="512ca-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span><span class="sxs-lookup"><span data-stu-id="512ca-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
