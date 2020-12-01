---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032488"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="4a87d-101">認証:HttpContext.Authentication プロパティが削除されました</span><span class="sxs-lookup"><span data-stu-id="4a87d-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="4a87d-102">`HttpContext` の非推奨の `Authentication` プロパティが削除されました。</span><span class="sxs-lookup"><span data-stu-id="4a87d-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4a87d-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="4a87d-103">Change description</span></span>

<span data-ttu-id="4a87d-104">[dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504) の一部として、`HttpContext` の非推奨の `Authentication` プロパティが削除されました。</span><span class="sxs-lookup"><span data-stu-id="4a87d-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="4a87d-105">2\.0 以降、`Authentication` プロパティは非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="4a87d-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="4a87d-106">この非推奨のプロパティを使用して新しい置換 API にコードを移行するために、[移行ガイド](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)が発行されました。</span><span class="sxs-lookup"><span data-stu-id="4a87d-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="4a87d-107">古い ASP.NET Core 1.x 認証スタックに関連する残りの未使用のクラス/API が、コミット [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65) で削除されました。</span><span class="sxs-lookup"><span data-stu-id="4a87d-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="4a87d-108">ディスカッションについては、[dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a87d-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4a87d-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="4a87d-109">Version introduced</span></span>

<span data-ttu-id="4a87d-110">3.0</span><span class="sxs-lookup"><span data-stu-id="4a87d-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4a87d-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="4a87d-111">Reason for change</span></span>

<span data-ttu-id="4a87d-112">ASP.NET Core 1.0 API が <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName> の拡張メソッドに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="4a87d-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a87d-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="4a87d-113">Recommended action</span></span>

<span data-ttu-id="4a87d-114">[移行ガイド](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a87d-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="4a87d-115">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="4a87d-115">Category</span></span>

<span data-ttu-id="4a87d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a87d-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a87d-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="4a87d-117">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpContext.Authentication?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler`
- `P:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext`
- `P:Microsoft.AspNetCore.Http.HttpContext.Authentication`

-->
