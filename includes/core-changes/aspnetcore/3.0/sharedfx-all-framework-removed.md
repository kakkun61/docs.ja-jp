---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032648"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="f53f1-101">共有フレームワーク: Microsoft.AspNetCore.All を削除</span><span class="sxs-lookup"><span data-stu-id="f53f1-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="f53f1-102">ASP.NET Core 3.0 以降では、`Microsoft.AspNetCore.All` メタパッケージと、対応する `Microsoft.AspNetCore.All` 共有フレームワークが生成されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f53f1-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="f53f1-103">このパッケージは ASP.NET Core 2.2 で使用することができ、ASP.NET Core 2.1 でサービス更新プログラムを引き続き受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="f53f1-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f53f1-104">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f53f1-104">Version introduced</span></span>

<span data-ttu-id="f53f1-105">3.0</span><span class="sxs-lookup"><span data-stu-id="f53f1-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f53f1-106">以前の動作</span><span class="sxs-lookup"><span data-stu-id="f53f1-106">Old behavior</span></span>

<span data-ttu-id="f53f1-107">アプリでは `Microsoft.AspNetCore.All` メタパッケージを使用して、.NET Core 上の `Microsoft.AspNetCore.All` 共有フレームワークをターゲットにすることができました。</span><span class="sxs-lookup"><span data-stu-id="f53f1-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f53f1-108">新しい動作</span><span class="sxs-lookup"><span data-stu-id="f53f1-108">New behavior</span></span>

<span data-ttu-id="f53f1-109">.NET Core 3.0 には、`Microsoft.AspNetCore.All` 共有フレームワークは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="f53f1-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f53f1-110">変更理由</span><span class="sxs-lookup"><span data-stu-id="f53f1-110">Reason for change</span></span>

<span data-ttu-id="f53f1-111">`Microsoft.AspNetCore.All` メタパッケージには、多数の外部依存関係が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="f53f1-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f53f1-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f53f1-112">Recommended action</span></span>

<span data-ttu-id="f53f1-113">プロジェクトを移行して、`Microsoft.AspNetCore.App` フレームワークを使用します。</span><span class="sxs-lookup"><span data-stu-id="f53f1-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="f53f1-114">`Microsoft.AspNetCore.All` でこれまで提供されていたコンポーネントは、NuGet で引き続き利用できます。</span><span class="sxs-lookup"><span data-stu-id="f53f1-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="f53f1-115">これらのコンポーネントは、共有フレームワークに含まれるのではなく、アプリと共にデプロイされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f53f1-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="f53f1-116">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="f53f1-116">Category</span></span>

<span data-ttu-id="f53f1-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f53f1-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f53f1-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f53f1-118">Affected APIs</span></span>

<span data-ttu-id="f53f1-119">None</span><span class="sxs-lookup"><span data-stu-id="f53f1-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
