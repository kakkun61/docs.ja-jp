---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032521"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="4b64e-101">ホスティング:ObjectPoolProvider が WebHostBuilder 依存関係から削除されました</span><span class="sxs-lookup"><span data-stu-id="4b64e-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="4b64e-102">ASP.NET Core の定額課金を増やすために、`ObjectPoolProvider` が主な依存関係のセットから削除されました。</span><span class="sxs-lookup"><span data-stu-id="4b64e-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="4b64e-103">`ObjectPoolProvider` に依存する特定のコンポーネント自体で、それが追加されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4b64e-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="4b64e-104">ディスカッションについては、[dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b64e-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4b64e-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="4b64e-105">Version introduced</span></span>

<span data-ttu-id="4b64e-106">3.0</span><span class="sxs-lookup"><span data-stu-id="4b64e-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4b64e-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="4b64e-107">Old behavior</span></span>

<span data-ttu-id="4b64e-108">`WebHostBuilder` によって、DI コンテナーに既定で `ObjectPoolProvider` が提供されます。</span><span class="sxs-lookup"><span data-stu-id="4b64e-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4b64e-109">新しい動作</span><span class="sxs-lookup"><span data-stu-id="4b64e-109">New behavior</span></span>

<span data-ttu-id="4b64e-110">`WebHostBuilder` によって、DI コンテナーに既定で `ObjectPoolProvider` が提供されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4b64e-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4b64e-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="4b64e-111">Reason for change</span></span>

<span data-ttu-id="4b64e-112">この変更は、ASP.NET Core の定額課金を増やすために行われました。</span><span class="sxs-lookup"><span data-stu-id="4b64e-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4b64e-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="4b64e-113">Recommended action</span></span>

<span data-ttu-id="4b64e-114">コンポーネントに `ObjectPoolProvider` が必要な場合は、`IServiceCollection` を介して依存関係に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b64e-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="4b64e-115">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="4b64e-115">Category</span></span>

<span data-ttu-id="4b64e-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4b64e-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4b64e-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="4b64e-117">Affected APIs</span></span>

<span data-ttu-id="4b64e-118">None</span><span class="sxs-lookup"><span data-stu-id="4b64e-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
