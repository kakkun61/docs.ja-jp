---
ms.openlocfilehash: 14d80f25c34465caa6dec10e5704fe0a3cbccc71
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96478376"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="43565-101">認証:Google+ が非推奨になり、置き換えられました</span><span class="sxs-lookup"><span data-stu-id="43565-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="43565-102">Google では、早ければ 2019 年 1 月 28 日をもってアプリ向け Google+ Sign-in の[サービスが終了](https://developers.google.com/+/api-shutdown)します。</span><span class="sxs-lookup"><span data-stu-id="43565-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="43565-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="43565-103">Change description</span></span>

<span data-ttu-id="43565-104">ASP.NET 4.x と ASP.NET Core では、Google+ Sign-in API を使用して、Web アプリで Google アカウント ユーザーを認証しています。</span><span class="sxs-lookup"><span data-stu-id="43565-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="43565-105">影響を受ける NuGet パッケージは、ASP.NET Core の場合は [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/)、ASP.NET Web Forms および MVC での `Microsoft.Owin` の場合は [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) です。</span><span class="sxs-lookup"><span data-stu-id="43565-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="43565-106">代わりとなる Google の API では、別のデータ ソースと形式が使用されています。</span><span class="sxs-lookup"><span data-stu-id="43565-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="43565-107">構造的な変更については、以下に示す軽減策と解決策を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43565-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="43565-108">データ自体が要件を満たしているかどうかをアプリで確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43565-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="43565-109">たとえば、名前、電子メール アドレス、プロファイル リンク、プロファイル写真では、以前とは微妙に異なる値が提供される場合があります。</span><span class="sxs-lookup"><span data-stu-id="43565-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="43565-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="43565-110">Version introduced</span></span>

<span data-ttu-id="43565-111">すべてのバージョン。</span><span class="sxs-lookup"><span data-stu-id="43565-111">All versions.</span></span> <span data-ttu-id="43565-112">この変更は、ASP.NET Core の外部での変更です。</span><span class="sxs-lookup"><span data-stu-id="43565-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="43565-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="43565-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="43565-114">ASP.NET Web Forms および MVC での Owin</span><span class="sxs-lookup"><span data-stu-id="43565-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="43565-115">`Microsoft.Owin` 3.1.0 以降については、一時的な軽減策の概要が[こちら](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)にあります。</span><span class="sxs-lookup"><span data-stu-id="43565-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="43565-116">アプリでは、データ形式の変更を確認するために、軽減策を使用してテストを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43565-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="43565-117">`Microsoft.Owin` 4.0.1 と修正プログラムをリリースする計画があります。</span><span class="sxs-lookup"><span data-stu-id="43565-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="43565-118">以前のバージョンを使用しているアプリは、バージョン 4.0.1 に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43565-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="43565-119">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="43565-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="43565-120">[ASP.NET Web Forms および MVC での Owin](#owin-with-aspnet-web-forms-and-mvc) の軽減策は、ASP.NET Core 1.x に適応できます。</span><span class="sxs-lookup"><span data-stu-id="43565-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="43565-121">1\.x は[有効期間の終了](https://dotnet.microsoft.com/platform/support-policy)状態に達したため、NuGet パッケージの修正プログラムは計画されていません。</span><span class="sxs-lookup"><span data-stu-id="43565-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="43565-122">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="43565-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="43565-123">`Microsoft.AspNetCore.Authentication.Google` バージョン 2.x の場合は、`Startup.ConfigureServices` での `AddGoogle` の既存の呼び出しを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="43565-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="43565-124">2 月の 2.1 と 2.2 の修正プログラムには、先行の再構成が新しい既定値として組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="43565-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="43565-125">ASP.NET Core 2.0 は[有効期間の終了](https://dotnet.microsoft.com/platform/support-policy)に達したため、修正プログラムは計画されていません。</span><span class="sxs-lookup"><span data-stu-id="43565-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="43565-126">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="43565-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="43565-127">ASP.NET Core 2.x 用に提供されている軽減策は、ASP.NET Core 3.0 にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="43565-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="43565-128">今後の 3.0 のプレビューにおいて、`Microsoft.AspNetCore.Authentication.Google` パッケージが削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43565-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="43565-129">ユーザーは、代わりに `Microsoft.AspNetCore.Authentication.OpenIdConnect` に誘導されます。</span><span class="sxs-lookup"><span data-stu-id="43565-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="43565-130">`Startup.ConfigureServices` 内の `AddGoogle` を `AddOpenIdConnect` に置き換える方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="43565-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="43565-131">この置き換えは ASP.NET Core 2.0 以降で使用でき、必要に応じて ASP.NET Core 1.x にも適応できます。</span><span class="sxs-lookup"><span data-stu-id="43565-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/signin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="43565-132">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="43565-132">Category</span></span>

<span data-ttu-id="43565-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43565-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="43565-134">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="43565-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
