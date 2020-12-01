---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032578"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="56063-101">Kestrel: 接続アダプターが削除されました</span><span class="sxs-lookup"><span data-stu-id="56063-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="56063-102">"pubternal" API を `public` に移すための移行の一環として、`IConnectionAdapter` の概念が Kestrel から削除されました。</span><span class="sxs-lookup"><span data-stu-id="56063-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="56063-103">接続アダプターは、接続ミドルウェア (ASP.NET Core パイプラインの HTTP ミドルウェアに似ていますが、下位レベルの接続用) で置き換えられつつあります。</span><span class="sxs-lookup"><span data-stu-id="56063-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="56063-104">HTTPS および接続のログ記録は接続アダプターから接続ミドルウェアに移されました。</span><span class="sxs-lookup"><span data-stu-id="56063-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="56063-105">それらの拡張メソッドは引き続きシームレスに動作しますが、実装の詳細が変更されています。</span><span class="sxs-lookup"><span data-stu-id="56063-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="56063-106">詳細については、[dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56063-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="56063-107">ディスカッションについては、[dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56063-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56063-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="56063-108">Version introduced</span></span>

<span data-ttu-id="56063-109">3.0</span><span class="sxs-lookup"><span data-stu-id="56063-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="56063-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="56063-110">Old behavior</span></span>

<span data-ttu-id="56063-111">Kestrel 拡張コンポーネントは `IConnectionAdapter` を使用して作成されていました。</span><span class="sxs-lookup"><span data-stu-id="56063-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="56063-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="56063-112">New behavior</span></span>

<span data-ttu-id="56063-113">Kestrel 拡張コンポーネントは、[ミドルウェア](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)として作成されます。</span><span class="sxs-lookup"><span data-stu-id="56063-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="56063-114">変更理由</span><span class="sxs-lookup"><span data-stu-id="56063-114">Reason for change</span></span>

<span data-ttu-id="56063-115">この変更は、より柔軟な拡張性アーキテクチャを提供することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="56063-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56063-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="56063-116">Recommended action</span></span>

<span data-ttu-id="56063-117">[ここに](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)示すように、`IConnectionAdapter` のすべての実装を、新しいミドルウェア パターンを使用するように変換します。</span><span class="sxs-lookup"><span data-stu-id="56063-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="56063-118">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="56063-118">Category</span></span>

<span data-ttu-id="56063-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="56063-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56063-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="56063-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
