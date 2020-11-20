---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440425"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a><span data-ttu-id="d885c-101">データの保護: DataProtection.Blobs では新しい Azure Storage API が使用されます</span><span class="sxs-lookup"><span data-stu-id="d885c-101">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>

<span data-ttu-id="d885c-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` は [Azure Storage ライブラリ](https://github.com/Azure/azure-storage-net)に依存します。</span><span class="sxs-lookup"><span data-stu-id="d885c-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="d885c-103">これらのライブラリで、アセンブリ、パッケージ、名前空間の名前が変更されました。</span><span class="sxs-lookup"><span data-stu-id="d885c-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="d885c-104">ASP.NET Core 3.0 以降、`Azure.Extensions.AspNetCore.DataProtection.Blobs` では `Azure.Storage.` というプレフィックスが付いた新しい API およびパッケージが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d885c-104">Starting in ASP.NET Core 3.0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` uses the new `Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="d885c-105">Azure Storage API に関する質問については、<https://github.com/Azure/azure-storage-net> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d885c-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="d885c-106">この問題に関するディスカッションについては、[dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d885c-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d885c-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="d885c-107">Version introduced</span></span>

<span data-ttu-id="d885c-108">3.0</span><span class="sxs-lookup"><span data-stu-id="d885c-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d885c-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="d885c-109">Old behavior</span></span>

<span data-ttu-id="d885c-110">パッケージでは `WindowsAzure.Storage` NuGet パッケージが参照されていました。</span><span class="sxs-lookup"><span data-stu-id="d885c-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>
<span data-ttu-id="d885c-111">パッケージでは `Microsoft.Azure.Storage.Blob` NuGet パッケージが参照されています。</span><span class="sxs-lookup"><span data-stu-id="d885c-111">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d885c-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="d885c-112">New behavior</span></span>

<span data-ttu-id="d885c-113">パッケージでは `Azure.Storage.Blob` NuGet パッケージが参照されています。</span><span class="sxs-lookup"><span data-stu-id="d885c-113">The package references the `Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d885c-114">変更理由</span><span class="sxs-lookup"><span data-stu-id="d885c-114">Reason for change</span></span>

<span data-ttu-id="d885c-115">この変更により、`Azure.Extensions.AspNetCore.DataProtection.Blobs` は推奨される Azure Storage パッケージに移行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d885c-115">This change allows `Azure.Extensions.AspNetCore.DataProtection.Blobs` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d885c-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="d885c-116">Recommended action</span></span>

<span data-ttu-id="d885c-117">ASP.NET Core 3.0 で古い Azure Storage API をまだ使用する必要がある場合は、パッケージ [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) または [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/) に対する直接的な依存関係を追加してください。</span><span class="sxs-lookup"><span data-stu-id="d885c-117">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the package [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) or [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span></span> <span data-ttu-id="d885c-118">このパッケージは、新しい `Azure.Storage` API と共にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d885c-118">This package can be installed alongside the new `Azure.Storage` APIs.</span></span>

<span data-ttu-id="d885c-119">多くの場合、アップグレードで必要なのは、新しい名前空間を使用するように `using` ステートメントを変更することだけです。</span><span class="sxs-lookup"><span data-stu-id="d885c-119">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a><span data-ttu-id="d885c-120">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="d885c-120">Category</span></span>

<span data-ttu-id="d885c-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d885c-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d885c-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="d885c-122">Affected APIs</span></span>

<span data-ttu-id="d885c-123">なし</span><span class="sxs-lookup"><span data-stu-id="d885c-123">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
