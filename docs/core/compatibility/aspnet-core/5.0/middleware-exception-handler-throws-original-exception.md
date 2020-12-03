---
title: 破壊的変更:ミドルウェア:ハンドラーが見つからない場合、例外ハンドラー ミドルウェアから元の例外がスローされる
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: ミドルウェア:ハンドラーが見つからない場合、例外ハンドラー ミドルウェアから元の例外がスローされる'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8801d3e6950d66fd9f24e051fd8729c50eb0b282
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759980"
---
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="70357-103">ミドルウェア:ハンドラーが見つからない場合、例外ハンドラー ミドルウェアから元の例外がスローされる</span><span class="sxs-lookup"><span data-stu-id="70357-103">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="70357-104">ASP.NET Core 5.0 より前では、例外が発生したときに、[Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) によって構成済みの例外ハンドラーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="70357-104">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="70357-105"><xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> で構成された例外ハンドラーが見つからない場合は、HTTP 404 応答が生成されます。</span><span class="sxs-lookup"><span data-stu-id="70357-105">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="70357-106">この応答は、次のような誤解を招きます。</span><span class="sxs-lookup"><span data-stu-id="70357-106">The response is misleading in that it:</span></span>

* <span data-ttu-id="70357-107">ユーザー エラーのように見える。</span><span class="sxs-lookup"><span data-stu-id="70357-107">Seems to be a user error.</span></span>
* <span data-ttu-id="70357-108">サーバーで例外が発生したという事実がわからなくなる。</span><span class="sxs-lookup"><span data-stu-id="70357-108">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="70357-109">ASP.NET Core 5.0 のこの誤解を招くエラーに対処するために、例外ハンドラーが見つからない場合、`ExceptionHandlerMiddleware` からは元の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="70357-109">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="70357-110">その結果、サーバーによって HTTP 500 応答が生成されます。</span><span class="sxs-lookup"><span data-stu-id="70357-110">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="70357-111">この応答であれば、発生したエラーをデバッグするときにサーバー ログで簡単に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="70357-111">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="70357-112">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70357-112">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="70357-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="70357-113">Version introduced</span></span>

<span data-ttu-id="70357-114">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="70357-114">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="70357-115">以前の動作</span><span class="sxs-lookup"><span data-stu-id="70357-115">Old behavior</span></span>

<span data-ttu-id="70357-116">構成された例外ハンドラーが見つからない場合は、Exception Handler Middleware によって HTTP 404 応答が生成されます。</span><span class="sxs-lookup"><span data-stu-id="70357-116">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="70357-117">新しい動作</span><span class="sxs-lookup"><span data-stu-id="70357-117">New behavior</span></span>

<span data-ttu-id="70357-118">構成された例外ハンドラーが見つからない場合は、Exception Handler Middleware からは元の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="70357-118">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="70357-119">変更理由</span><span class="sxs-lookup"><span data-stu-id="70357-119">Reason for change</span></span>

<span data-ttu-id="70357-120">HTTP 404 エラーを受け取っても、サーバーで例外が発生したことが明らかにはなりません。</span><span class="sxs-lookup"><span data-stu-id="70357-120">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="70357-121">この変更により、HTTP 500 エラーが生成され、次のことが明らかになります。</span><span class="sxs-lookup"><span data-stu-id="70357-121">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="70357-122">問題の原因はユーザー エラーではない。</span><span class="sxs-lookup"><span data-stu-id="70357-122">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="70357-123">サーバー上で例外が発生した。</span><span class="sxs-lookup"><span data-stu-id="70357-123">An exception was encountered on the server.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="70357-124">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="70357-124">Recommended action</span></span>

<span data-ttu-id="70357-125">API の変更はありません。</span><span class="sxs-lookup"><span data-stu-id="70357-125">There are no API changes.</span></span> <span data-ttu-id="70357-126">既存のすべてのアプリは引き続きコンパイルされ、実行されます。</span><span class="sxs-lookup"><span data-stu-id="70357-126">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="70357-127">スローされた例外は、サーバーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="70357-127">The exception thrown is handled by the server.</span></span> <span data-ttu-id="70357-128">たとえば、例外は [Kestrel](/aspnet/core/fundamentals/servers/kestrel) または [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys) によって HTTP 500 エラー応答に変換されます。</span><span class="sxs-lookup"><span data-stu-id="70357-128">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="70357-129">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="70357-129">Affected APIs</span></span>

<span data-ttu-id="70357-130">なし</span><span class="sxs-lookup"><span data-stu-id="70357-130">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
