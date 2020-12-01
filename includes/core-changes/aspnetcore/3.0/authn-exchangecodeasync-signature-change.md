---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032458"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="9d954-101">認証:OAuthHandler ExchangeCodeAsync 署名が変更されました</span><span class="sxs-lookup"><span data-stu-id="9d954-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="9d954-102">ASP.NET Core 3.0 では、`OAuthHandler.ExchangeCodeAsync` の署名が次のように変更されました。</span><span class="sxs-lookup"><span data-stu-id="9d954-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="9d954-103">移動先:</span><span class="sxs-lookup"><span data-stu-id="9d954-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="9d954-104">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9d954-104">Version introduced</span></span>

<span data-ttu-id="9d954-105">3.0</span><span class="sxs-lookup"><span data-stu-id="9d954-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9d954-106">以前の動作</span><span class="sxs-lookup"><span data-stu-id="9d954-106">Old behavior</span></span>

<span data-ttu-id="9d954-107">`code` と `redirectUri` の文字列が個別の引数として渡されました。</span><span class="sxs-lookup"><span data-stu-id="9d954-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9d954-108">新しい動作</span><span class="sxs-lookup"><span data-stu-id="9d954-108">New behavior</span></span>

<span data-ttu-id="9d954-109">`Code` と `RedirectUri` は、`OAuthCodeExchangeContext` コンストラクターを使用して設定できる `OAuthCodeExchangeContext` のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="9d954-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="9d954-110">新しい `OAuthCodeExchangeContext` 型は、`OAuthHandler.ExchangeCodeAsync` に渡される唯一の引数です。</span><span class="sxs-lookup"><span data-stu-id="9d954-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9d954-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="9d954-111">Reason for change</span></span>

<span data-ttu-id="9d954-112">この変更により、追加のパラメーターを中断することなく提供できます。</span><span class="sxs-lookup"><span data-stu-id="9d954-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="9d954-113">新しい `ExchangeCodeAsync` オーバーロードを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9d954-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9d954-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="9d954-114">Recommended action</span></span>

<span data-ttu-id="9d954-115">適切な `code` と `redirectUri` の値を使用して、`OAuthCodeExchangeContext` を作成します。</span><span class="sxs-lookup"><span data-stu-id="9d954-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="9d954-116"><xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> インスタンスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d954-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="9d954-117">この 1 つの `OAuthCodeExchangeContext` インスタンスは、複数の引数ではなく、`OAuthHandler.ExchangeCodeAsync` に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9d954-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="9d954-118">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9d954-118">Category</span></span>

<span data-ttu-id="9d954-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9d954-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9d954-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9d954-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
