---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032647"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="8afbd-101">セッション状態: 古い API が削除された</span><span class="sxs-lookup"><span data-stu-id="8afbd-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="8afbd-102">セッション Cookie を構成するための古い API が削除されました。</span><span class="sxs-lookup"><span data-stu-id="8afbd-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="8afbd-103">詳細については、[aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8afbd-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8afbd-104">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8afbd-104">Version introduced</span></span>

<span data-ttu-id="8afbd-105">3.0</span><span class="sxs-lookup"><span data-stu-id="8afbd-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8afbd-106">変更理由</span><span class="sxs-lookup"><span data-stu-id="8afbd-106">Reason for change</span></span>

<span data-ttu-id="8afbd-107">この変更により、Cookie を使用する機能を構成するための API 間の一貫性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="8afbd-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8afbd-108">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="8afbd-108">Recommended action</span></span>

<span data-ttu-id="8afbd-109">削除された API の使用箇所を、置換された新しい API に移行します。</span><span class="sxs-lookup"><span data-stu-id="8afbd-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="8afbd-110">`Startup.ConfigureServices` での次の例を検討してください。</span><span class="sxs-lookup"><span data-stu-id="8afbd-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(ServiceCollection services)
{
    services.AddSession(options =>
    {
        // Removed obsolete APIs
        options.CookieName = "SessionCookie";
        options.CookieDomain = "contoso.com";
        options.CookiePath = "/";
        options.CookieHttpOnly = true;
        options.CookieSecure = CookieSecurePolicy.Always;

        // new API
        options.Cookie.Name = "SessionCookie";
        options.Cookie.Domain = "contoso.com";
        options.Cookie.Path = "/";
        options.Cookie.HttpOnly = true;
        options.Cookie.SecurePolicy = CookieSecurePolicy.Always;
    });
}
```

#### <a name="category"></a><span data-ttu-id="8afbd-111">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="8afbd-111">Category</span></span>

<span data-ttu-id="8afbd-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8afbd-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8afbd-113">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8afbd-113">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieName?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure?displayProperty=fullName>

<!-- 

#### Affected APIs

- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieName`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure`

-->
