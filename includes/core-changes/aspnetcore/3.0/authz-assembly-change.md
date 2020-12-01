---
ms.openlocfilehash: 2819fb3857fa6d40a2b2e42eeaec2d9c6e50eef0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96299354"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="a46fe-101">承認:AddAuthorization のオーバーロードが別のアセンブリに移動した</span><span class="sxs-lookup"><span data-stu-id="a46fe-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="a46fe-102">`Microsoft.AspNetCore.Authorization` に以前あったコア `AddAuthorization` メソッドが `AddAuthorizationCore` に名前変更されました。</span><span class="sxs-lookup"><span data-stu-id="a46fe-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="a46fe-103">古い `AddAuthorization` メソッドはまだありますが、代わりに `Microsoft.AspNetCore.Authorization.Policy` アセンブリに含まれています。</span><span class="sxs-lookup"><span data-stu-id="a46fe-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="a46fe-104">両方のメソッドを使用するアプリには影響はありません。</span><span class="sxs-lookup"><span data-stu-id="a46fe-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="a46fe-105">`Microsoft.AspNetCore.Authorization.Policy` は、「[共有フレームワーク: Microsoft.AspNetCore.App から削除されたアセンブリ](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)」に説明されているスタンドアロン パッケージではなく共有フレームワークで出荷されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a46fe-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a46fe-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a46fe-106">Version introduced</span></span>

<span data-ttu-id="a46fe-107">3.0</span><span class="sxs-lookup"><span data-stu-id="a46fe-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a46fe-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="a46fe-108">Old behavior</span></span>

<span data-ttu-id="a46fe-109">`AddAuthorization` メソッドは `Microsoft.AspNetCore.Authorization` にありました。</span><span class="sxs-lookup"><span data-stu-id="a46fe-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a46fe-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="a46fe-110">New behavior</span></span>

<span data-ttu-id="a46fe-111">`AddAuthorization` メソッドは `Microsoft.AspNetCore.Authorization.Policy` にあります。</span><span class="sxs-lookup"><span data-stu-id="a46fe-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="a46fe-112">`AddAuthorizationCore` は、古いメソッドの新しい名前です。</span><span class="sxs-lookup"><span data-stu-id="a46fe-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a46fe-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="a46fe-113">Reason for change</span></span>

<span data-ttu-id="a46fe-114">`AddAuthorization` は、承認に必要な一般的なすべてのサービスを追加するのにより適切なメソッド名です。</span><span class="sxs-lookup"><span data-stu-id="a46fe-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a46fe-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a46fe-115">Recommended action</span></span>

<span data-ttu-id="a46fe-116">`Microsoft.AspNetCore.Authorization.Policy` に参照を追加するか、代わりに `AddAuthorizationCore` を使用します。</span><span class="sxs-lookup"><span data-stu-id="a46fe-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="a46fe-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="a46fe-117">Category</span></span>

<span data-ttu-id="a46fe-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a46fe-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a46fe-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a46fe-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
