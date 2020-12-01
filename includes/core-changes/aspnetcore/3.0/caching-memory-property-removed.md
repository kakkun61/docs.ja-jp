---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032471"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="2c8dc-101">キャッシュ:CompactOnMemoryPressure プロパティが削除された</span><span class="sxs-lookup"><span data-stu-id="2c8dc-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="2c8dc-102">ASP.NET Core 3.0 のリリースでは、[古い MemoryCacheOptions API](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18) が削除されました。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="2c8dc-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="2c8dc-103">Change description</span></span>

<span data-ttu-id="2c8dc-104">この変更は、[aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221) に対するフォローアップです。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="2c8dc-105">ディスカッションについては、[dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2c8dc-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="2c8dc-106">Version introduced</span></span>

<span data-ttu-id="2c8dc-107">3.0</span><span class="sxs-lookup"><span data-stu-id="2c8dc-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2c8dc-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="2c8dc-108">Old behavior</span></span>

<span data-ttu-id="2c8dc-109">`MemoryCacheOptions.CompactOnMemoryPressure` プロパティを使用できました。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2c8dc-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="2c8dc-110">New behavior</span></span>

<span data-ttu-id="2c8dc-111">`MemoryCacheOptions.CompactOnMemoryPressure` プロパティは削除されました。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2c8dc-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="2c8dc-112">Reason for change</span></span>

<span data-ttu-id="2c8dc-113">キャッシュを自動的に圧縮すると、問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="2c8dc-114">予期しない動作を避けるため、キャッシュは必要なときにのみ圧縮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2c8dc-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="2c8dc-115">Recommended action</span></span>

<span data-ttu-id="2c8dc-116">キャッシュを圧縮するには、`MemoryCache` にダウンキャストし、必要に応じて `Compact` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2c8dc-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="2c8dc-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="2c8dc-117">Category</span></span>

<span data-ttu-id="2c8dc-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2c8dc-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2c8dc-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="2c8dc-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
