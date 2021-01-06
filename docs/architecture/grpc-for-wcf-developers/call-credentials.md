---
title: 資格情報の呼び出し-WCF 開発者向けの gRPC
description: ASP.NET Core 3.0 で gRPC 通話資格情報を実装して使用する方法。
ms.date: 12/15/2020
ms.openlocfilehash: 66394c75929bf068f83d631e022b467386e59ec5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938443"
---
# <a name="call-credentials"></a><span data-ttu-id="0b79c-103">資格情報を呼び出す</span><span class="sxs-lookup"><span data-stu-id="0b79c-103">Call credentials</span></span>

<span data-ttu-id="0b79c-104">呼び出し資格情報は、すべての要求に対してメタデータで渡されたトークンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="0b79c-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="0b79c-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="0b79c-105">WS-Federation</span></span>

<span data-ttu-id="0b79c-106">ASP.NET Core は、 [Wsfederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet パッケージを使用した WS-Federation をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0b79c-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="0b79c-107">WS-Federation は、HTTP/2 でサポートされていない Windows 認証の代替手段として最も近いものです。</span><span class="sxs-lookup"><span data-stu-id="0b79c-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="0b79c-108">ユーザーは Active Directory フェデレーションサービス (AD FS) (AD FS) を使用して認証されます。これにより、ASP.NET Core での認証に使用できるトークンが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0b79c-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="0b79c-109">この認証方法の使用を開始する方法の詳細については、「 [ASP.NET Core での WS-Federation を使用したユーザーの認証](/aspnet/core/security/authentication/ws-federation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b79c-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="0b79c-110">JWT ベアラートークン</span><span class="sxs-lookup"><span data-stu-id="0b79c-110">JWT Bearer tokens</span></span>

<span data-ttu-id="0b79c-111">[JSON Web Token](https://jwt.io) (JWT) 標準は、エンコードされた文字列でユーザーとそのクレームに関する情報をエンコードする手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="0b79c-112">また、公開キー暗号化を使用して、コンシューマーがトークンの整合性を検証できるように、そのトークンに署名する方法も提供します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="0b79c-113">IdentityServer4 などのさまざまなサービスを使用して、ユーザーを認証し、gRPC と HTTP Api で使用する OpenID Connect (OIDC) トークンを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="0b79c-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="0b79c-114">ASP.NET Core 5.0 は JWT ベアラーパッケージを使用して JWTs を処理できます。</span><span class="sxs-lookup"><span data-stu-id="0b79c-114">ASP.NET Core 5.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="0b79c-115">GRPC アプリケーションの構成は、ASP.NET Core MVC アプリケーションの場合とまったく同じです。</span><span class="sxs-lookup"><span data-stu-id="0b79c-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="0b79c-116">ここでは、JWT ベアラートークンに焦点を絞って説明します。これは、WS-FEDERATION を使用した開発が簡単であるためです。</span><span class="sxs-lookup"><span data-stu-id="0b79c-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="0b79c-117">サーバーに認証と承認を追加する</span><span class="sxs-lookup"><span data-stu-id="0b79c-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="0b79c-118">JWT ベアラーパッケージは、既定では ASP.NET Core 5.0 には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="0b79c-118">The JWT Bearer package isn't included in ASP.NET Core 5.0 by default.</span></span> <span data-ttu-id="0b79c-119">アプリに [AspNetCore JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0b79c-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="0b79c-120">スタートアップクラスに認証サービスを追加し、JWT ベアラーハンドラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="0b79c-121">プロパティは、 `IssuerSigningKey` 署名され `Microsoft.IdentityModels.Tokens.SecurityKey` たトークンを検証するために必要な暗号化データを使用して、の実装を必要とします。</span><span class="sxs-lookup"><span data-stu-id="0b79c-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="0b79c-122">このトークンは、Azure Key Vault などの *シークレットサーバー* に安全に格納します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="0b79c-123">次に、承認サービスを追加します。これにより、システムへのアクセスが制御されます。</span><span class="sxs-lookup"><span data-stu-id="0b79c-123">Next, add the Authorization service, which controls access to the system:</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="0b79c-124">認証と承認は、2つの別個の手順です。</span><span class="sxs-lookup"><span data-stu-id="0b79c-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="0b79c-125">認証を使用して、ユーザーの id を決定します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="0b79c-126">承認を使用して、ユーザーがシステムのさまざまな部分へのアクセスを許可されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="0b79c-127">次に、認証と承認のミドルウェアをメソッドの ASP.NET Core パイプラインに追加し `Configure` ます。</span><span class="sxs-lookup"><span data-stu-id="0b79c-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="0b79c-128">最後に、 `[Authorize]` セキュリティで保護されるすべてのサービスまたはメソッドに属性を適用し、 `User` 基になっているのプロパティを使用し `HttpContext` てアクセス許可を確認します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="0b79c-129">クライアントアプリケーションに呼び出し資格情報を提供する</span><span class="sxs-lookup"><span data-stu-id="0b79c-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="0b79c-130">Id サーバーから JWT トークンを取得したら、それを使用してクライアントからの gRPC 呼び出しを認証できます。その際、次のように呼び出しのメタデータヘッダーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="0b79c-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="0b79c-131">これで、JWT ベアラートークンを呼び出し資格情報として使用して、gRPC サービスをセキュリティで保護しました。</span><span class="sxs-lookup"><span data-stu-id="0b79c-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="0b79c-132">[認証と承認を追加したポートフォリオサンプル gRPC アプリケーション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth)のバージョンは、GitHub にあります。</span><span class="sxs-lookup"><span data-stu-id="0b79c-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0b79c-133">[前へ](security.md)
>[次へ](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="0b79c-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
