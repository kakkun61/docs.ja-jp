---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032538"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="9a0e1-101">HTTP:DefaultHttpContext の機能拡張の削除</span><span class="sxs-lookup"><span data-stu-id="9a0e1-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="9a0e1-102">ASP.NET Core 3.0 のパフォーマンスの改善の一環として、`DefaultHttpContext` の機能拡張が削除されました。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="9a0e1-103">クラスは `sealed` になりました。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-103">The class is now `sealed`.</span></span> <span data-ttu-id="9a0e1-104">詳細については、[dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="9a0e1-105">単体テストで `Mock<DefaultHttpContext>` を使用する場合は、代わりに `Mock<HttpContext>` または `new DefaultHttpContext()` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="9a0e1-106">ディスカッションについては、[dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9a0e1-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9a0e1-107">Version introduced</span></span>

<span data-ttu-id="9a0e1-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9a0e1-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9a0e1-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="9a0e1-109">Old behavior</span></span>

<span data-ttu-id="9a0e1-110">クラスは `DefaultHttpContext` から派生できます。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9a0e1-111">新しい動作</span><span class="sxs-lookup"><span data-stu-id="9a0e1-111">New behavior</span></span>

<span data-ttu-id="9a0e1-112">クラスは `DefaultHttpContext` から派生できません。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9a0e1-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="9a0e1-113">Reason for change</span></span>

<span data-ttu-id="9a0e1-114">機能拡張は `HttpContext` のプーリングを可能にするために当初提供されていましたが、不要な複雑さをもたらし、他の最適化の妨げとなっていました。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9a0e1-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="9a0e1-115">Recommended action</span></span>

<span data-ttu-id="9a0e1-116">単体テストで `Mock<DefaultHttpContext>` を使用する場合、今後は代わりに `Mock<HttpContext>` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9a0e1-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="9a0e1-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9a0e1-117">Category</span></span>

<span data-ttu-id="9a0e1-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9a0e1-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a0e1-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9a0e1-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
