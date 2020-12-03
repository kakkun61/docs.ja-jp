---
title: '破壊的変更: 静的ファイル: CSV コンテンツ タイプが標準準拠に変更されました'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: 静的ファイル: CSV コンテンツ タイプが標準準拠に変更されました'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c94a0cf213970d20559b7c061d8be220b43961e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760058"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="c361a-103">静的ファイル: CSV コンテンツ タイプが標準準拠に変更されました</span><span class="sxs-lookup"><span data-stu-id="c361a-103">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="c361a-104">ASP.NET Core 5.0 では、[静的ファイル ミドルウェア](/aspnet/core/fundamentals/static-files) によって *.csv* ファイルに使用される既定の `Content-Type` 応答ヘッダー値が、標準に準拠した値 `text/csv` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="c361a-104">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="c361a-105">この問題に関するディスカッションについては、[dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c361a-105">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c361a-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="c361a-106">Version introduced</span></span>

<span data-ttu-id="c361a-107">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="c361a-107">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c361a-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="c361a-108">Old behavior</span></span>

<span data-ttu-id="c361a-109">`Content-Type` ヘッダー値 `application/octet-stream` が使用されていました。</span><span class="sxs-lookup"><span data-stu-id="c361a-109">The `Content-Type` header value `application/octet-stream` was used.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="c361a-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="c361a-110">New behavior</span></span>

<span data-ttu-id="c361a-111">`Content-Type` ヘッダー値 `text/csv` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c361a-111">The `Content-Type` header value `text/csv` is used.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c361a-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="c361a-112">Reason for change</span></span>

<span data-ttu-id="c361a-113">[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) 標準に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="c361a-113">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c361a-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="c361a-114">Recommended action</span></span>

<span data-ttu-id="c361a-115">この変更によってアプリが影響を受ける場合は、ファイル拡張子と MIME の種類のマッピングをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="c361a-115">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="c361a-116">MIME の種類 `application/octet-stream` に戻すには、`Startup.Configure` でメソッド呼び出し <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> を変更します。</span><span class="sxs-lookup"><span data-stu-id="c361a-116">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="c361a-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c361a-117">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="c361a-118">マッピングのカスタマイズの詳細については、「[FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c361a-118">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c361a-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="c361a-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
