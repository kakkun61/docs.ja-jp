---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032680"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="479db-101">SPA:SpaServices と NodeServices は今後、コンソール ロガーにフォールバックしません。</span><span class="sxs-lookup"><span data-stu-id="479db-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="479db-102">ログ記録が構成されていない限り、<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> と <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> にはコンソール ログが表示されません。</span><span class="sxs-lookup"><span data-stu-id="479db-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="479db-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="479db-103">Version introduced</span></span>

<span data-ttu-id="479db-104">3.0</span><span class="sxs-lookup"><span data-stu-id="479db-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="479db-105">以前の動作</span><span class="sxs-lookup"><span data-stu-id="479db-105">Old behavior</span></span>

<span data-ttu-id="479db-106">ログ記録が構成されていないとき、コンソール ロガーを自動作成する目的で `Microsoft.AspNetCore.SpaServices` と `Microsoft.AspNetCore.NodeServices` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="479db-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="479db-107">新しい動作</span><span class="sxs-lookup"><span data-stu-id="479db-107">New behavior</span></span>

<span data-ttu-id="479db-108">ログ記録が構成されていない限り、`Microsoft.AspNetCore.SpaServices` と `Microsoft.AspNetCore.NodeServices` にはコンソール ログが表示されません。</span><span class="sxs-lookup"><span data-stu-id="479db-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="479db-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="479db-109">Reason for change</span></span>

<span data-ttu-id="479db-110">他の ASP.NET Core パッケージでのログ記録の実装方法に合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="479db-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="479db-111">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="479db-111">Recommended action</span></span>

<span data-ttu-id="479db-112">以前の動作が必要な場合、コンソール ログ記録を構成するために、`services.AddLogging(builder => builder.AddConsole())` を `Setup.ConfigureServices` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="479db-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="479db-113">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="479db-113">Category</span></span>

<span data-ttu-id="479db-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="479db-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="479db-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="479db-115">Affected APIs</span></span>

<span data-ttu-id="479db-116">None</span><span class="sxs-lookup"><span data-stu-id="479db-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
