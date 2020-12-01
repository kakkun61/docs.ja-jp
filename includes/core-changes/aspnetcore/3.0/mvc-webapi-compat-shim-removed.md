---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032628"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="dea30-101">MVC: Web API 互換性 shim を削除</span><span class="sxs-lookup"><span data-stu-id="dea30-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="dea30-102">ASP.NET Core 3.0 以降、`Microsoft.AspNetCore.Mvc.WebApiCompatShim` パッケージは使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="dea30-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dea30-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="dea30-103">Change description</span></span>

<span data-ttu-id="dea30-104">`Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) パッケージは、ASP.NET Core への既存の Web API 実装の移行を簡素化するために、ASP.NET Core と ASP.NET 4.x Web API 2 の部分的な互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="dea30-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="dea30-105">ただし、WebApiCompatShim を使用するアプリでは、ASP.NET Core の最近のリリースで提供される API 関連の機能の利点が得られません。</span><span class="sxs-lookup"><span data-stu-id="dea30-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="dea30-106">このような機能として、改善された Open API 仕様の生成、標準化されたエラー処理、クライアント コードの生成などがあります。</span><span class="sxs-lookup"><span data-stu-id="dea30-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="dea30-107">3\.0 での API の取り組みに重点を置くために、WebApiCompatShim が削除されました。</span><span class="sxs-lookup"><span data-stu-id="dea30-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="dea30-108">WebApiCompatShim を使用する既存のアプリは、新しい `[ApiController]` モデルに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dea30-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dea30-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="dea30-109">Version introduced</span></span>

<span data-ttu-id="dea30-110">3.0</span><span class="sxs-lookup"><span data-stu-id="dea30-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dea30-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="dea30-111">Reason for change</span></span>

<span data-ttu-id="dea30-112">Web API 互換性 shim は移行ツールでした。</span><span class="sxs-lookup"><span data-stu-id="dea30-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="dea30-113">このツールにより、ASP.NET Core に追加された新しい機能へのユーザー アクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="dea30-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dea30-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="dea30-114">Recommended action</span></span>

<span data-ttu-id="dea30-115">この shim の使用を削除し、ASP.NET Core 自体の同様の機能に直接移行します。</span><span class="sxs-lookup"><span data-stu-id="dea30-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="dea30-116">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="dea30-116">Category</span></span>

<span data-ttu-id="dea30-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dea30-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dea30-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="dea30-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
