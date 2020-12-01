---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032561"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="188db-101">ID: SignInManager コンストラクターは新しいパラメーターを受け入れる</span><span class="sxs-lookup"><span data-stu-id="188db-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="188db-102">ASP.NET Core 3.0 以降、`SignInManager` コンストラクターに新しい `IUserConfirmation<TUser>` パラメーターが追加されました。</span><span class="sxs-lookup"><span data-stu-id="188db-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="188db-103">詳細については、[dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="188db-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="188db-104">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="188db-104">Version introduced</span></span>

<span data-ttu-id="188db-105">3.0</span><span class="sxs-lookup"><span data-stu-id="188db-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="188db-106">変更理由</span><span class="sxs-lookup"><span data-stu-id="188db-106">Reason for change</span></span>

<span data-ttu-id="188db-107">変更の動機は、ID での新しいメール/確認フローのサポートを追加するためでした。</span><span class="sxs-lookup"><span data-stu-id="188db-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="188db-108">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="188db-108">Recommended action</span></span>

<span data-ttu-id="188db-109">手動で `SignInManager` を構築している場合は、`IUserConfirmation` の実装を提供するか、依存関係の挿入から 1 つを取得して提供します。</span><span class="sxs-lookup"><span data-stu-id="188db-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="188db-110">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="188db-110">Category</span></span>

<span data-ttu-id="188db-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="188db-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="188db-112">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="188db-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
