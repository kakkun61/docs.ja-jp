---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366885"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a><span data-ttu-id="56477-101">IEnumerable\<T> を受け取る拡張メソッドに GroupCollection を渡すにはあいまいさが必要</span><span class="sxs-lookup"><span data-stu-id="56477-101">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>

<span data-ttu-id="56477-102"><xref:System.Text.RegularExpressions.GroupCollection> で `IEnumerable<T>` を受け取る拡張メソッドを呼び出す場合は、キャストを使用して型を明確にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56477-102">When calling an extension method that takes an `IEnumerable<T>` on a <xref:System.Text.RegularExpressions.GroupCollection>, you must disambiguate the type using a cast.</span></span>

#### <a name="change-description"></a><span data-ttu-id="56477-103">変更内容</span><span class="sxs-lookup"><span data-stu-id="56477-103">Change description</span></span>

<span data-ttu-id="56477-104">.NET Core 3.0 以降では、<xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> によって `IEnumerable<KeyValuePair<String,Group>>` が実装され、それによって他の型 (`IEnumerable<Group>` など) も加えて実装されます。</span><span class="sxs-lookup"><span data-stu-id="56477-104">Starting in .NET Core 3.0, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> implements `IEnumerable<KeyValuePair<String,Group>>` in addition to the other types it implements, including `IEnumerable<Group>`.</span></span> <span data-ttu-id="56477-105">これは、<xref:System.Collections.Generic.IEnumerable%601> を受け取る拡張メソッドを呼び出す場合には、あいまいな結果となります。</span><span class="sxs-lookup"><span data-stu-id="56477-105">This results in ambiguity when calling an extension method that takes an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="56477-106">たとえば、<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> などの <xref:System.Text.RegularExpressions.GroupCollection> インスタンスでこのような拡張メソッドを呼び出すと、次のコンパイラ エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56477-106">If you call such an extension method on a <xref:System.Text.RegularExpressions.GroupCollection> instance, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType>, you'll see the following compiler error:</span></span>

<span data-ttu-id="56477-107">**CS1061: 'GroupCollection' に 'Count' の定義が含まれておらず、型 'GroupCollection' の最初の引数を受け付ける拡張メソッド 'Count' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が不足しています。)**</span><span class="sxs-lookup"><span data-stu-id="56477-107">**CS1061: 'GroupCollection' does not contain a definition for 'Count' and no accessible extension method 'Count' accepting a first argument of type 'GroupCollection' could be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="56477-108">以前のバージョンの .NET では、あいまいさはなく、コンパイラ エラーもありませんでした。</span><span class="sxs-lookup"><span data-stu-id="56477-108">In previous versions of .NET, there was no ambiguity and no compiler error.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56477-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="56477-109">Version introduced</span></span>

<span data-ttu-id="56477-110">3.0</span><span class="sxs-lookup"><span data-stu-id="56477-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="56477-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="56477-111">Reason for change</span></span>

<span data-ttu-id="56477-112">これは[意図しない破壊的変更](https://github.com/dotnet/corefx/pull/30077)でした。</span><span class="sxs-lookup"><span data-stu-id="56477-112">This was an [unintentional breaking change](https://github.com/dotnet/corefx/pull/30077).</span></span> <span data-ttu-id="56477-113">しばらくの間このようになっているため、元に戻す予定はありません。</span><span class="sxs-lookup"><span data-stu-id="56477-113">Because it has been like this for some time, we don't plan to revert it.</span></span> <span data-ttu-id="56477-114">また、このような変更自体が中断されます。</span><span class="sxs-lookup"><span data-stu-id="56477-114">In addition, such a change would itself be breaking.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56477-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="56477-115">Recommended action</span></span>

<span data-ttu-id="56477-116"><xref:System.Text.RegularExpressions.GroupCollection> インスタンスの場合は、キャストで `IEnumerable<T>` を受け入れる拡張メソッドの呼び出しを明確にします。</span><span class="sxs-lookup"><span data-stu-id="56477-116">For <xref:System.Text.RegularExpressions.GroupCollection> instances, disambiguate calls to extension methods that accept an `IEnumerable<T>` with a cast.</span></span>

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a><span data-ttu-id="56477-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="56477-117">Category</span></span>

<span data-ttu-id="56477-118">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="56477-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56477-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="56477-119">Affected APIs</span></span>

<span data-ttu-id="56477-120"><xref:System.Collections.Generic.IEnumerable%601> を受け入れるすべての拡張メソッドが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="56477-120">Any extension method that accepts an <xref:System.Collections.Generic.IEnumerable%601> is affected.</span></span> <span data-ttu-id="56477-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="56477-121">For example:</span></span>

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- <span data-ttu-id="56477-122">`System.Linq.Enumerable` メソッドの大部分 (<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName> など)</span><span class="sxs-lookup"><span data-stu-id="56477-122">Most of the `System.Linq.Enumerable` methods, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span></span>
- <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>

<!--

#### Affected APIs

- ``M:System.Collections.Immutable.ImmutableArray.ToImmutableArray``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary`
- `Overload:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet`
- ``M:System.Collections.Immutable.ImmutableList.ToImmutableList``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary`
- `Overload:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet`
- `Overload:System.Data.DataTableExtensions.CopyToDataTable`
- `Overload:System.Linq.Enumerable.Count`
- `Overload:System.Linq.ParallelEnumerable.AsParallel`
- `Overload:System.Linq.Queryable.AsQueryable`

-->
