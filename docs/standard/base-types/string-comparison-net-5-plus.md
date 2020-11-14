---
title: .NET 5 以降で文字列を比較するときの動作の変更
description: Windows の .NET 5 以降のバージョンでの文字列比較の動作の変更について説明します。
ms.date: 11/04/2020
ms.openlocfilehash: 49be2169bb165b8fe0205800415542bea7bf9787
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403490"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a><span data-ttu-id="3d576-103">.NET 5 以降で文字列を比較するときの動作の変更</span><span class="sxs-lookup"><span data-stu-id="3d576-103">Behavior changes when comparing strings on .NET 5+</span></span>

<span data-ttu-id="3d576-104">.NET 5.0 で導入されたランタイム動作の変更により、グローバリゼーション API では、サポートされているすべてのプラットフォームで [ICU が既定で使用される](../../core/compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows)ようになりました。</span><span class="sxs-lookup"><span data-stu-id="3d576-104">.NET 5.0 introduces a runtime behavioral change where globalization APIs [now use ICU by default](../../core/compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows) across all supported platforms.</span></span> <span data-ttu-id="3d576-105">これは、Windows で実行されるときはオペレーティング システムの各国語サポート (NLS) 機能を利用する以前のバージョンの .NET Core と .NET Framework とは異なります。</span><span class="sxs-lookup"><span data-stu-id="3d576-105">This is a departure from earlier versions of .NET Core and from .NET Framework, which utilize the operating system's national language support (NLS) functionality when running on Windows.</span></span> <span data-ttu-id="3d576-106">動作の変更を元に戻すことができる互換性スイッチなど、これらの変更の詳細については、「[.NET グローバリゼーションと ICU](../globalization-localization/globalization-icu.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-106">For more information on these changes, including compatibility switches that can revert the behavior change, see [.NET globalization and ICU](../globalization-localization/globalization-icu.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3d576-107">変更理由</span><span class="sxs-lookup"><span data-stu-id="3d576-107">Reason for change</span></span>

<span data-ttu-id="3d576-108">この変更は、サポートされているすべてのオペレーティング システムで .NET のグローバリゼーション動作を統一するために導入されました。</span><span class="sxs-lookup"><span data-stu-id="3d576-108">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="3d576-109">また、それにより、OS の組み込みライブラリに依存するのではなく、アプリケーションで独自のグローバリゼーション ライブラリをバンドルする機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-109">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the OS's built-in libraries.</span></span> <span data-ttu-id="3d576-110">詳細については、[破壊的変更の通知](../../core/compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-110">For more information, see [the breaking change notification](../../core/compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="3d576-111">動作の違い</span><span class="sxs-lookup"><span data-stu-id="3d576-111">Behavioral differences</span></span>

<span data-ttu-id="3d576-112"><xref:System.StringComparison> 引数を受け取るオーバーロードを呼び出さずに `string.IndexOf(string)` のような関数を使用する場合は、" *序数* " 検索を実行するつもりであっても、意図せずカルチャ固有の動作に依存します。</span><span class="sxs-lookup"><span data-stu-id="3d576-112">If you use functions like `string.IndexOf(string)` without calling the overload that takes a <xref:System.StringComparison> argument, you might intend to perform an *ordinal* search, but instead you inadvertently take a dependency on culture-specific behavior.</span></span> <span data-ttu-id="3d576-113">NLS と ICU では言語比較子で実装されているロジックが異なるため、`string.IndexOf(string)` のようなメソッドの結果で、予期しない値が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3d576-113">Since NLS and ICU implement different logic in their linguistic comparers, the results of methods like `string.IndexOf(string)` can return unexpected values.</span></span>

<span data-ttu-id="3d576-114">これは、常にグローバリゼーション機能がアクティブになっている必要がない場所であっても発生します。</span><span class="sxs-lookup"><span data-stu-id="3d576-114">This can manifest itself even in places where you aren't always expecting globalization facilities to be active.</span></span> <span data-ttu-id="3d576-115">たとえば、次のコードからは、現在のランタイムにより異なる結果が生成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-115">For example, the following code can produce a different answer depending on the current runtime.</span></span>

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a><span data-ttu-id="3d576-116">予期しない動作を防ぐ</span><span class="sxs-lookup"><span data-stu-id="3d576-116">Guard against unexpected behavior</span></span>

<span data-ttu-id="3d576-117">このセクションでは、.NET 5.0 における予期しない動作の変更に対処するための 2 つのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3d576-117">This section provides two options for dealing with unexpected behavior changes in .NET 5.0.</span></span>

### <a name="enable-code-analyzers"></a><span data-ttu-id="3d576-118">コード アナライザーを有効にする</span><span class="sxs-lookup"><span data-stu-id="3d576-118">Enable code analyzers</span></span>

<span data-ttu-id="3d576-119">[コード アナライザー](../../fundamentals/code-analysis/overview.md)を使用すると、バグがある可能性のある呼び出しサイトを検出できます。</span><span class="sxs-lookup"><span data-stu-id="3d576-119">[Code analyzers](../../fundamentals/code-analysis/overview.md) can detect possibly buggy call sites.</span></span> <span data-ttu-id="3d576-120">予期しない動作を防ぐため、 [__Microsoft.CodeAnalysis.FxCopAnalyzers__ NuGet パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)をプロジェクトに インストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d576-120">To help guard against any surprising behaviors, we recommend installing [the __Microsoft.CodeAnalysis.FxCopAnalyzers__ NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) into your project.</span></span> <span data-ttu-id="3d576-121">このパッケージに含まれるコード分析規則 [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) と [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) は、序数比較子が意図されていたと思われる箇所で誤って言語比較子が使用されている可能性のあるコードにフラグを設定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3d576-121">This package includes the code analysis rules [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), which help flag code that might inadvertently be using a linguistic comparer when an ordinal comparer was likely intended.</span></span>

<span data-ttu-id="3d576-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3d576-122">For example:</span></span>

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1307.
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

<span data-ttu-id="3d576-123">同様に、並べ替えられた文字列のコレクションをインスタンス化したり、既存の文字列ベースのコレクションを並べ替えたりする場合は、明示的な比較子を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d576-123">Similarly, when instantiating a sorted collection of strings or sorting an existing string-based collection, specify an explicit comparer.</span></span>

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

<span data-ttu-id="3d576-124">独自のコード ベースでこれらの規則を抑制することが適切な場合など、これらのコード アナライザー規則の詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-124">For more information about these code analyzer rules, including when it might be appropriate to suppress these rules in your own code base, see the following articles:</span></span>

* [<span data-ttu-id="3d576-125">CA1307:意味を明確にするための StringComparison の指定</span><span class="sxs-lookup"><span data-stu-id="3d576-125">CA1307: Specify StringComparison for clarity</span></span>](../../fundamentals/code-analysis/quality-rules/ca1307.md)
* [<span data-ttu-id="3d576-126">CA1309:順序を示す StringComparison を使用します</span><span class="sxs-lookup"><span data-stu-id="3d576-126">CA1309: Use ordinal StringComparison</span></span>](../../fundamentals/code-analysis/quality-rules/ca1309.md)

### <a name="revert-back-to-nls-behaviors"></a><span data-ttu-id="3d576-127">NLS の動作に戻す</span><span class="sxs-lookup"><span data-stu-id="3d576-127">Revert back to NLS behaviors</span></span>

<span data-ttu-id="3d576-128">Windows で実行されるときに、.NET 5 アプリケーションを古い NLS の動作に戻すには、「[.NET グローバリゼーションと ICU](../globalization-localization/globalization-icu.md)」の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="3d576-128">To revert .NET 5 applications back to older NLS behaviors when running on Windows, follow the steps in [.NET Globalization and ICU](../globalization-localization/globalization-icu.md).</span></span> <span data-ttu-id="3d576-129">このアプリケーション全体の互換性スイッチは、アプリケーション レベルで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-129">This application-wide compatibility switch must be set at the application level.</span></span> <span data-ttu-id="3d576-130">個々のライブラリについてこの動作をオプトインまたはオプトアウトすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3d576-130">Individual libraries cannot opt-in or opt-out of this behavior.</span></span>

> [!TIP]
> <span data-ttu-id="3d576-131">コードの安全性を向上させ、既存の潜在的なバグを検出するため、[CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) と [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) のコード分析規則を有効にすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d576-131">We strongly recommend you enable the [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) code analysis rules to help improve code hygiene and discover any existing latent bugs.</span></span> <span data-ttu-id="3d576-132">詳細については、「[コード アナライザーを有効にする](#enable-code-analyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-132">For more information, see [Enable code analyzers](#enable-code-analyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3d576-133">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="3d576-133">Affected APIs</span></span>

<span data-ttu-id="3d576-134">ほとんどの .NET アプリケーションでは、.NET 5.0 の変更によって予期しない動作が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="3d576-134">Most .NET applications won't encounter any unexpected behaviors due to the changes in .NET 5.0.</span></span> <span data-ttu-id="3d576-135">ただし、影響を受ける API の数と、これらの API が広範な .NET エコシステムの基礎になっているため、.NET 5.0 によって望ましくない動作が発生したり、アプリケーションに既に存在する潜在的なバグが明らかになったりする可能性があることに、注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-135">However, due to the number of affected APIs and how foundational these APIs are to the wider .NET ecosystem, you should be aware of the potential for .NET 5.0 to introduce unwanted behaviors or to expose latent bugs that already exist in your application.</span></span>

<span data-ttu-id="3d576-136">影響を受ける API は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3d576-136">The affected APIs include:</span></span>

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <span data-ttu-id="3d576-137"><xref:System.Globalization.TextInfo?displayProperty=fullName> (ほとんどのメンバー)</span><span class="sxs-lookup"><span data-stu-id="3d576-137"><xref:System.Globalization.TextInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="3d576-138"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (ほとんどのメンバー)</span><span class="sxs-lookup"><span data-stu-id="3d576-138"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="3d576-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (文字列の配列を並べ替えるとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting arrays of strings)</span></span>
- <span data-ttu-id="3d576-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (リストの要素が文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="3d576-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (キーが文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="3d576-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (キーが文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="3d576-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (セットに文字列が含まれるとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

> [!NOTE]
> <span data-ttu-id="3d576-144">これは、影響を受けるすべての API を網羅した一覧ではありません。</span><span class="sxs-lookup"><span data-stu-id="3d576-144">This is not an exhaustive list of affected APIs.</span></span>

<span data-ttu-id="3d576-145">既定では、上記のすべての API において、スレッドの [現在のカルチャ](xref:System.Threading.Thread.CurrentCulture)を使用する " *言語* " 文字列の検索と比較が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-145">All of the above APIs use *linguistic* string searching and comparison using the thread's [current culture](xref:System.Threading.Thread.CurrentCulture), by default.</span></span> <span data-ttu-id="3d576-146">" *言語* " と " *序数* " での検索と比較の違いについては、「[序数と言語での検索と比較](#ordinal-vs-linguistic-search-and-comparison)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-146">The differences between *linguistic* and *ordinal* search and comparison are called out in the [Ordinal vs. linguistic search and comparison](#ordinal-vs-linguistic-search-and-comparison).</span></span>

<span data-ttu-id="3d576-147">ICU で実装されている言語文字列比較は NLS と異なるため、以前のバージョンの .NET Core または .NET Framework から .NET 5.0 にアップグレードした Windows ベースのアプリケーションで、影響を受ける API のいずれかが呼び出されている場合、API が異なる動作を示し始めることに気付く場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-147">Because ICU implements linguistic string comparisons differently from NLS, Windows-based applications that upgrade to .NET 5.0 from an earlier version of .NET Core or .NET Framework and that call one of the affected APIs may notice that the APIs begin exhibiting different behaviors.</span></span>

### <a name="exceptions"></a><span data-ttu-id="3d576-148">例外</span><span class="sxs-lookup"><span data-stu-id="3d576-148">Exceptions</span></span>

* <span data-ttu-id="3d576-149">明示的な `StringComparison` または `CultureInfo` パラメーターを受け取る API の場合、そのパラメーターによって API の既定の動作がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="3d576-149">If an API accepts an explicit `StringComparison` or `CultureInfo` parameter, that parameter overrides the API's default behavior.</span></span>
* <span data-ttu-id="3d576-150">最初のパラメーターが `char` 型である `System.String` のメンバーの場合 (例: <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>)、呼び出し元によって `CurrentCulture[IgnoreCase]` または `InvariantCulture[IgnoreCase]` を指定する明示的な `StringComparison` 引数が渡されない限り、序数検索が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-150">`System.String` members where the first parameter is of type `char` (for example, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>) use ordinal searching, unless the caller passes an explicit `StringComparison` argument that specifies `CurrentCulture[IgnoreCase]` or `InvariantCulture[IgnoreCase]`.</span></span>

<span data-ttu-id="3d576-151">各 <xref:System.String> API の既定の動作の詳細な分析については、「[既定の検索と比較の種類](#default-search-and-comparison-types)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-151">For a more detailed analysis of the default behavior of each <xref:System.String> API, see the [Default search and comparison types](#default-search-and-comparison-types) section.</span></span>

## <a name="ordinal-vs-linguistic-search-and-comparison"></a><span data-ttu-id="3d576-152">序数と言語での検索と比較</span><span class="sxs-lookup"><span data-stu-id="3d576-152">Ordinal vs. linguistic search and comparison</span></span>

<span data-ttu-id="3d576-153">" *序数* " (" *非言語* " とも呼ばれます) による検索と比較の場合は、文字列が個別の `char` 要素に分解された後、文字単位の検索または比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-153">*Ordinal* (also known as *non-linguistic* ) search and comparison decomposes a string into its individual `char` elements and performs a char-by-char search or comparison.</span></span> <span data-ttu-id="3d576-154">たとえば、文字列 `"dog"` と `"dog"` は、2 つの文字列が完全に同じ文字のシーケンスで構成されているため、`Ordinal` 比較子で " *等しい* " と比較されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-154">For example, the strings `"dog"` and `"dog"` compare as *equal* under an `Ordinal` comparer, since the two strings consist of the exact same sequence of chars.</span></span> <span data-ttu-id="3d576-155">一方、`"dog"` と `"Dog"` は、それらが完全に同じ文字のシーケンスで構成されていないため、`Ordinal` 比較子で " *等しくない* " と比較されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-155">However, `"dog"` and `"Dog"` compare as *not equal* under an `Ordinal` comparer, because they don't consist of the exact same sequence of chars.</span></span> <span data-ttu-id="3d576-156">つまり、大文字 `'D'` のコード ポイント `U+0044` は、小文字 `'d'` のコード ポイント `U+0064` より前にあるので、`"dog"` は `"Dog"` より前に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="3d576-156">That is, uppercase `'D'`'s code point `U+0044` occurs before lowercase `'d'`'s code point `U+0064`, resulting in `"dog"` sorting before `"Dog"`.</span></span>

<span data-ttu-id="3d576-157">`OrdinalIgnoreCase` 比較子はやはり文字単位で動作しますが、操作の実行中に大文字と小文字の違いがなくなります。</span><span class="sxs-lookup"><span data-stu-id="3d576-157">An `OrdinalIgnoreCase` comparer still operates on a char-by-char basis, but it eliminates case differences while performing the operation.</span></span> <span data-ttu-id="3d576-158">`OrdinalIgnoreCase` 比較子の下では、文字のペア `'d'` と `'D'` は、文字のペア `'á'` と `'Á'` の場合と同様に、" *等しい* " として比較されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-158">Under an `OrdinalIgnoreCase` comparer, the char pairs `'d'` and `'D'` compare as *equal* , as do the char pairs `'á'` and `'Á'`.</span></span> <span data-ttu-id="3d576-159">しかし、アクセントが付いていない文字 `'a'` とアクセントが付いている文字 `'á'` の場合は、" *等しくない* " と比較されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-159">But the unaccented char `'a'` compares as *not equal* to the accented char `'á'`.</span></span>

<span data-ttu-id="3d576-160">これについてのいくつかの例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="3d576-160">Some examples of this are provided in the following table:</span></span>

| <span data-ttu-id="3d576-161">String 1</span><span class="sxs-lookup"><span data-stu-id="3d576-161">String 1</span></span> | <span data-ttu-id="3d576-162">文字列 2</span><span class="sxs-lookup"><span data-stu-id="3d576-162">String 2</span></span> | <span data-ttu-id="3d576-163">`Ordinal` 比較</span><span class="sxs-lookup"><span data-stu-id="3d576-163">`Ordinal` comparison</span></span> | <span data-ttu-id="3d576-164">`OrdinalIgnoreCase` 比較</span><span class="sxs-lookup"><span data-stu-id="3d576-164">`OrdinalIgnoreCase` comparison</span></span> |
|---|---|---|---|
| `"dog"` | `"dog"` | <span data-ttu-id="3d576-165">equal</span><span class="sxs-lookup"><span data-stu-id="3d576-165">equal</span></span> | <span data-ttu-id="3d576-166">equal</span><span class="sxs-lookup"><span data-stu-id="3d576-166">equal</span></span> |
| `"dog"` | `"Dog"` | <span data-ttu-id="3d576-167">等しくない</span><span class="sxs-lookup"><span data-stu-id="3d576-167">not equal</span></span> | <span data-ttu-id="3d576-168">equal</span><span class="sxs-lookup"><span data-stu-id="3d576-168">equal</span></span> |
| `"resume"` | `"Resume"` | <span data-ttu-id="3d576-169">等しくない</span><span class="sxs-lookup"><span data-stu-id="3d576-169">not equal</span></span> | <span data-ttu-id="3d576-170">equal</span><span class="sxs-lookup"><span data-stu-id="3d576-170">equal</span></span> |
| `"resume"` | `"résumé"` | <span data-ttu-id="3d576-171">等しくない</span><span class="sxs-lookup"><span data-stu-id="3d576-171">not equal</span></span> | <span data-ttu-id="3d576-172">等しくない</span><span class="sxs-lookup"><span data-stu-id="3d576-172">not equal</span></span> |

<span data-ttu-id="3d576-173">Unicode の場合も、文字列に複数の異なるメモリ内表現を使用することが認められています。</span><span class="sxs-lookup"><span data-stu-id="3d576-173">Unicode also allows strings to have several different in-memory representations.</span></span> <span data-ttu-id="3d576-174">たとえば、e アキュート (é) は、次の 2 つの方法で表すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d576-174">For example, an e-acute (é) can be represented in two possible ways:</span></span>

* <span data-ttu-id="3d576-175">1 つのリテラル `'é'` 文字 (`'\u00E9'` とも記述されます)。</span><span class="sxs-lookup"><span data-stu-id="3d576-175">A single literal `'é'` character (also written as `'\u00E9'`).</span></span>
* <span data-ttu-id="3d576-176">リテラルのアクセントなし `'e'` 文字の後に、結合アクセント修飾子文字 `'\u0301'` を付けたもの。</span><span class="sxs-lookup"><span data-stu-id="3d576-176">A literal unaccented `'e'` character, followed by a combining accent modifier character `'\u0301'`.</span></span>

<span data-ttu-id="3d576-177">これは、構成要素が異なる場合でも、次の " _4 つ_ " の文字列はすべて表示されるときは `"résumé"` になることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3d576-177">This means that the following _four_ strings all result in `"résumé"` when displayed, even though their constituent pieces are different.</span></span> <span data-ttu-id="3d576-178">これらの文字列には、リテラル `'é'` 文字またはリテラル非アクセント `'e'` 文字と結合アクセント修飾子 `'\u0301'` の組み合わせが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-178">The strings use a combination of literal `'é'` characters or literal unaccented `'e'` characters plus the combining accent modifier `'\u0301'`.</span></span>

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

<span data-ttu-id="3d576-179">序数比較子では、これらのどの文字列も相互に等しくないと比較されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-179">Under an ordinal comparer, none of these strings compare as equal to each other.</span></span> <span data-ttu-id="3d576-180">これは、画面にレンダリングされるときはすべて同じように見えても、含まれる基の文字シーケンスが異なるためです。</span><span class="sxs-lookup"><span data-stu-id="3d576-180">This is because they all contain different underlying char sequences, even though when they're rendered to the screen, they all look the same.</span></span>

<span data-ttu-id="3d576-181">`string.IndexOf(..., StringComparison.Ordinal)` 操作を実行すると、ランタイムにより完全に一致する部分文字列が検索されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-181">When performing a `string.IndexOf(..., StringComparison.Ordinal)` operation, the runtime looks for an exact substring match.</span></span> <span data-ttu-id="3d576-182">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3d576-182">The results are as follows.</span></span>

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

<span data-ttu-id="3d576-183">序数検索と序数比較のルーチンは、現在のスレッドのカルチャ設定の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="3d576-183">Ordinal search and comparison routines are never affected by the current thread's culture setting.</span></span>

<span data-ttu-id="3d576-184">" *言語* " の検索および比較ルーチンの場合、文字列が " *照合順序要素* " に分解されてから、これらの要素に対して検索や比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-184">*Linguistic* search and comparison routines decompose a string into *collation elements* and perform searches or comparisons on these elements.</span></span> <span data-ttu-id="3d576-185">文字列の文字とそれを構成する照合順序要素の間に、1:1 のマッピングが存在するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="3d576-185">There's not necessarily a 1:1 mapping between a string's characters and its constituent collation elements.</span></span> <span data-ttu-id="3d576-186">たとえば、長さが 2 の文字列でも、単一の照合順序要素で構成されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-186">For example, a string of length 2 may consist of only a single collation element.</span></span> <span data-ttu-id="3d576-187">2 つの文字列を言語対応の方法で比較すると、文字列のリテラル文字が異なる場合でも、比較子により、2 つの文字列の照合順序要素のセマンティックな意味が同じかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-187">When two strings are compared in a linguistic-aware fashion, the comparer checks whether the two strings' collation elements have the same semantic meaning, even if the string's literal characters are different.</span></span>

<span data-ttu-id="3d576-188">再び、文字列 `"résumé"` とその 4 つの異なる表現を検討します。</span><span class="sxs-lookup"><span data-stu-id="3d576-188">Consider again the string `"résumé"` and its four different representations.</span></span> <span data-ttu-id="3d576-189">次の表は、各表現を照合順序要素に分割したものです。</span><span class="sxs-lookup"><span data-stu-id="3d576-189">The following table shows each representation broken down into its collation elements.</span></span>

| <span data-ttu-id="3d576-190">文字列型</span><span class="sxs-lookup"><span data-stu-id="3d576-190">String</span></span> | <span data-ttu-id="3d576-191">照合順序要素</span><span class="sxs-lookup"><span data-stu-id="3d576-191">As collation elements</span></span> |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

<span data-ttu-id="3d576-192">照合順序要素は、読み手が 1 つの文字または文字の塊として認識するものと緩く対応しています。</span><span class="sxs-lookup"><span data-stu-id="3d576-192">A collation element corresponds loosely to what readers would think of as a single character or cluster of characters.</span></span> <span data-ttu-id="3d576-193">概念的には[書記素クラスター](character-encoding-introduction.md#grapheme-clusters)に似ていますが、より大きな包括的なものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3d576-193">It's conceptually similar to a [grapheme cluster](character-encoding-introduction.md#grapheme-clusters) but encompasses a somewhat larger umbrella.</span></span>

<span data-ttu-id="3d576-194">言語比較子では、完全一致は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3d576-194">Under a linguistic comparer, exact matches aren't necessary.</span></span> <span data-ttu-id="3d576-195">照合順序要素が、そのセマンティックの意味に基づいて代わりに比較されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-195">Collation elements are instead compared based on their semantic meaning.</span></span> <span data-ttu-id="3d576-196">たとえば、言語比較子の場合、部分文字列 `"\u00E9"` と `"e\u0301"` は、どちらもセマンティック的には "小文字の e とアキュート アクセント修飾子" を意味するので、等しいものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="3d576-196">For example, a linguistic comparer tsreat the substrings `"\u00E9"` and `"e\u0301"` as equal since they both semantically mean "a lowercase e with an acute accent modifier."</span></span> <span data-ttu-id="3d576-197">これにより、次のコード サンプルに示すように、`IndexOf` メソッドを使用すると、セマンティック的に等しい部分文字列 `"\u00E9"` が含まれる大きな文字列内で部分文字列 `"e\u0301"` を照合できます。</span><span class="sxs-lookup"><span data-stu-id="3d576-197">This allows the `IndexOf` method to match the substring `"e\u0301"` within a larger string that contains the semantically equivalent substring `"\u00E9"`, as shown in the following code sample.</span></span>

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

<span data-ttu-id="3d576-198">このため、言語比較を使用した場合、長さが異なる 2 つの文字列が等しいと見なされることがあります。</span><span class="sxs-lookup"><span data-stu-id="3d576-198">As a consequence of this, two strings of different lengths may compare as equal if a linguistic comparison is used.</span></span> <span data-ttu-id="3d576-199">呼び出し元は、このようなシナリオで文字列の長さを扱う特殊なケースのロジックを使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-199">Callers should take care not to special-case logic that deals with string length in such scenarios.</span></span>

<span data-ttu-id="3d576-200">" *カルチャ対応* " の検索および比較ルーチンは、言語検索および比較ルーチンの特殊な形式です。</span><span class="sxs-lookup"><span data-stu-id="3d576-200">*Culture-aware* search and comparison routines are a special form of linguistic search and comparison routines.</span></span> <span data-ttu-id="3d576-201">カルチャ対応の比較子の場合、照合順序要素の概念が拡張され、指定されたカルチャに固有の情報が含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="3d576-201">Under a culture-aware comparer, the concept of a collation element is extended to include information specific to the specified culture.</span></span>

<span data-ttu-id="3d576-202">たとえば、[ハンガリー語アルファベット](https://en.wikipedia.org/wiki/Hungarian_alphabet)では、2 つの文字 \<dz\> が連続して出現する場合、それらは \<d\> または \<z\> とは異なるそれ自体で一意の文字と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3d576-202">For example, [in the Hungarian alphabet](https://en.wikipedia.org/wiki/Hungarian_alphabet), when the two characters \<dz\> appear back-to-back, they are considered their own unique letter distinct from either \<d\> or \<z\>.</span></span> <span data-ttu-id="3d576-203">つまり、文字列に \<dz\> が含まれると、ハンガリー語のカルチャ対応の比較子により、それは単一の照合順序要素として扱われます。</span><span class="sxs-lookup"><span data-stu-id="3d576-203">This means that when \<dz\> is seen in a string, a Hungarian culture-aware comparer treats it as a single collation element.</span></span>

| <span data-ttu-id="3d576-204">文字列型</span><span class="sxs-lookup"><span data-stu-id="3d576-204">String</span></span> | <span data-ttu-id="3d576-205">照合順序要素</span><span class="sxs-lookup"><span data-stu-id="3d576-205">As collation elements</span></span> | <span data-ttu-id="3d576-206">Remarks</span><span class="sxs-lookup"><span data-stu-id="3d576-206">Remarks</span></span> |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | <span data-ttu-id="3d576-207">(標準の言語比較子を使用)</span><span class="sxs-lookup"><span data-stu-id="3d576-207">(using a standard linguistic comparer)</span></span> |
| `"endz"` | `"e" + "n" + "dz"` | <span data-ttu-id="3d576-208">(ハンガリー語のカルチャ対応比較子を使用)</span><span class="sxs-lookup"><span data-stu-id="3d576-208">(using a Hungarian culture-aware comparer)</span></span> |

<span data-ttu-id="3d576-209">ハンガリー語のカルチャ対応比較子を使用する場合、<\dz\> と <\z\> はセマンティックの意味が異なる照合順序要素と見なされるため、文字列 `"endz"` は部分文字列 `"z"` で終わって " *いない* " ことを意味します。</span><span class="sxs-lookup"><span data-stu-id="3d576-209">When using a Hungarian culture-aware comparer, this means that the string `"endz"` *does not* end with the substring `"z"`, as <\dz\> and <\z\> are considered collation elements with different semantic meaning.</span></span>

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - <span data-ttu-id="3d576-210">動作: 言語対応およびカルチャ対応の比較子は、ときどき動作の調整が行われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-210">Behavior: Linguistic and culture-aware comparers can undergo behavioral adjustments from time to time.</span></span> <span data-ttu-id="3d576-211">ICU と古い Windows NLS 機能はどちらも、世界的な言語の変化を考慮して更新されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-211">Both ICU and the older Windows NLS facility are updated to account for how world languages change.</span></span> <span data-ttu-id="3d576-212">詳細については、ブログ記事「[ロケール (カルチャ) データの変動](/archive/blogs/shawnste/locale-culture-data-churn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-212">For more information, see the blog post [Locale (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn).</span></span> <span data-ttu-id="3d576-213">" *序数* " 比較子の動作は、完全にビットごとの検索と比較が実行されるため、変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="3d576-213">The *Ordinal* comparer's behavior will never change since it performs exact bitwise searching and comparison.</span></span> <span data-ttu-id="3d576-214">ただし、 *OrdinalIgnoreCase* 比較子の動作は、Unicode の拡大によって含まれる文字セットが増え、既存の大文字小文字データの不備が修正されると、変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-214">However, the *OrdinalIgnoreCase* comparer's behavior may change as Unicode grows to encompass more character sets and corrects omissions in existing casing data.</span></span>
> - <span data-ttu-id="3d576-215">使用方法: 比較子 `StringComparison.InvariantCulture` と `StringComparison.InvariantCultureIgnoreCase` は、カルチャ対応ではない言語比較子です。</span><span class="sxs-lookup"><span data-stu-id="3d576-215">Usage: The comparers `StringComparison.InvariantCulture` and `StringComparison.InvariantCultureIgnoreCase` are linguistic comparers that are not culture-aware.</span></span> <span data-ttu-id="3d576-216">つまり、これらの比較子では、é のようなアクセント付き文字には複数の可能な基になる表現があり、そのようなすべての表現を等しいと見なす必要がある、といった概念が理解されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-216">That is, these comparers understand concepts such as the accented character é having multiple possible underlying representations, and that all such representations should be treated equal.</span></span> <span data-ttu-id="3d576-217">しかし、非カルチャ対応の言語比較子には、上記のような \<d\> や \<z\> とは異なる \<dz\> の特殊な処理は含まれません。</span><span class="sxs-lookup"><span data-stu-id="3d576-217">But non-culture-aware linguistic comparers won't contain special handling for \<dz\> as distinct from \<d\> or \<z\>, as shown above.</span></span> <span data-ttu-id="3d576-218">また、ドイツ語の Eszett (ß) のような特殊なケースの文字もありません。</span><span class="sxs-lookup"><span data-stu-id="3d576-218">They also won't special-case characters like the German Eszett (ß).</span></span>

<span data-ttu-id="3d576-219">.NET には、" *インバリアント グローバリゼーション モード* " も用意されています。</span><span class="sxs-lookup"><span data-stu-id="3d576-219">.NET also offers the *invariant globalization mode*.</span></span> <span data-ttu-id="3d576-220">このオプトイン モードを使用すると、言語検索および比較ルーチンを処理するコード パスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="3d576-220">This opt-in mode disables code paths that deal with linguistic search and comparison routines.</span></span> <span data-ttu-id="3d576-221">このモードでは、呼び出し元が提供する `CultureInfo` または `StringComparison` の引数に関係なく、すべての操作で *Ordinal* または *OrdinalIgnoreCase* の動作が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-221">In this mode, all operations use *Ordinal* or *OrdinalIgnoreCase* behaviors, regardless of what `CultureInfo` or `StringComparison` argument the caller provides.</span></span> <span data-ttu-id="3d576-222">詳細については、「[グローバリゼーションのランタイム構成オプション](../../core/run-time-config/globalization.md)」および「[.NET Core のグローバリゼーション インバリアント モード](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-222">For more information, see [Run-time configuration options for globalization](../../core/run-time-config/globalization.md) and [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

<span data-ttu-id="3d576-223">詳細については、「[.NET での文字列の比較に関するベスト プラクティス](best-practices-strings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d576-223">For more information, see [Best practices for comparing strings in .NET](best-practices-strings.md).</span></span>

## <a name="security-implications"></a><span data-ttu-id="3d576-224">セキュリティへの影響</span><span class="sxs-lookup"><span data-stu-id="3d576-224">Security implications</span></span>

<span data-ttu-id="3d576-225">影響を受ける API をアプリでフィルター処理に使用している場合、CA1307 と CA1309 のコード分析規則を有効にすることをお勧めします。これにより、序数検索の代わりに言語検索が意図せずに使用される可能性がある場所を特定することができます。</span><span class="sxs-lookup"><span data-stu-id="3d576-225">If your app uses an affected API for filtering, we recommend enabling the CA1307 and CA1309 code analysis rules to help locate places where a linguistic search may have inadvertently been used instead of an ordinal search.</span></span> <span data-ttu-id="3d576-226">次のようなコード パターンは、セキュリティ攻撃の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-226">Code patterns like the following may be susceptible to security exploits.</span></span>

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

<span data-ttu-id="3d576-227">`string.IndexOf(string)` メソッドでは既定で言語検索が使用されるため、文字列にリテラルの `'<'` または `'&'` 文字が含まれる可能性があり、`string.IndexOf(string)` ルーチンで検索部分文字列が見つからなかったことを示す `-1` が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-227">Because the `string.IndexOf(string)` method uses a linguistic search by default, it's possible for a string to contain a literal `'<'` or `'&'` character and for the `string.IndexOf(string)` routine to return `-1`, indicating that the search substring was not found.</span></span> <span data-ttu-id="3d576-228">コード分析規則 CA1307 と CA1309 フラグを使用すると、このような呼び出しサイトが識別され、潜在的な問題があることが開発者に通知されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-228">Code analysis rules CA1307 and CA1309 flag such call sites and alert the developer that there's a potential problem.</span></span>

## <a name="default-search-and-comparison-types"></a><span data-ttu-id="3d576-229">既定の検索と比較の種類</span><span class="sxs-lookup"><span data-stu-id="3d576-229">Default search and comparison types</span></span>

<span data-ttu-id="3d576-230">次の表では、さまざまな文字列 API と文字列に似た API での既定の検索と比較の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="3d576-230">The following table lists the default search and comparison types for various string and string-like APIs.</span></span> <span data-ttu-id="3d576-231">呼び出し元によって明示的な `CultureInfo` または `StringComparison` パラメーターが提供された場合は、そのパラメーターが既定値より優先されます。</span><span class="sxs-lookup"><span data-stu-id="3d576-231">If the caller provides an explicit `CultureInfo` or `StringComparison` parameter, that parameter will be honored over any default.</span></span>

| <span data-ttu-id="3d576-232">API</span><span class="sxs-lookup"><span data-stu-id="3d576-232">API</span></span> | <span data-ttu-id="3d576-233">既定の動作</span><span class="sxs-lookup"><span data-stu-id="3d576-233">Default behavior</span></span> | <span data-ttu-id="3d576-234">Remarks</span><span class="sxs-lookup"><span data-stu-id="3d576-234">Remarks</span></span> |
|---|---|---|
| `string.Compare` | <span data-ttu-id="3d576-235">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-235">CurrentCulture</span></span> | |
| `string.CompareTo` | <span data-ttu-id="3d576-236">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-236">CurrentCulture</span></span> | |
| `string.Contains` | <span data-ttu-id="3d576-237">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-237">Ordinal</span></span> | |
| `string.EndsWith` | <span data-ttu-id="3d576-238">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-238">Ordinal</span></span> | <span data-ttu-id="3d576-239">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-239">(when the first parameter is a `char`)</span></span> |
| `string.EndsWith` | <span data-ttu-id="3d576-240">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-240">CurrentCulture</span></span> | <span data-ttu-id="3d576-241">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-241">(when the first parameter is a `string`)</span></span> |
| `string.Equals` | <span data-ttu-id="3d576-242">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-242">Ordinal</span></span> | |
| `string.GetHashCode` | <span data-ttu-id="3d576-243">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-243">Ordinal</span></span> | |
| `string.IndexOf` | <span data-ttu-id="3d576-244">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-244">Ordinal</span></span> | <span data-ttu-id="3d576-245">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-245">(when the first parameter is a `char`)</span></span> |
| `string.IndexOf` | <span data-ttu-id="3d576-246">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-246">CurrentCulture</span></span> | <span data-ttu-id="3d576-247">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-247">(when the first parameter is a `string`)</span></span> |
| `string.IndexOfAny` | <span data-ttu-id="3d576-248">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-248">Ordinal</span></span> | |
| `string.LastIndexOf` | <span data-ttu-id="3d576-249">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-249">Ordinal</span></span> | <span data-ttu-id="3d576-250">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-250">(when the first parameter is a `char`)</span></span> |
| `string.LastIndexOf` | <span data-ttu-id="3d576-251">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-251">CurrentCulture</span></span> | <span data-ttu-id="3d576-252">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-252">(when the first parameter is a `string`)</span></span> |
| `string.LastIndexOfAny` | <span data-ttu-id="3d576-253">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-253">Ordinal</span></span> | |
| `string.Replace` | <span data-ttu-id="3d576-254">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-254">Ordinal</span></span> | |
| `string.Split` | <span data-ttu-id="3d576-255">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-255">Ordinal</span></span> | |
| `string.StartsWith` | <span data-ttu-id="3d576-256">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-256">Ordinal</span></span> | <span data-ttu-id="3d576-257">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-257">(when the first parameter is a `char`)</span></span> |
| `string.StartsWith` | <span data-ttu-id="3d576-258">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-258">CurrentCulture</span></span> | <span data-ttu-id="3d576-259">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-259">(when the first parameter is a `string`)</span></span> |
| `string.ToLower` | <span data-ttu-id="3d576-260">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-260">CurrentCulture</span></span> | |
| `string.ToLowerInvariant` | <span data-ttu-id="3d576-261">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-261">InvariantCulture</span></span> | |
| `string.ToUpper` | <span data-ttu-id="3d576-262">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-262">CurrentCulture</span></span> | |
| `string.ToUpperInvariant` | <span data-ttu-id="3d576-263">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-263">InvariantCulture</span></span> | |
| `string.Trim` | <span data-ttu-id="3d576-264">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-264">Ordinal</span></span> | |
| `string.TrimEnd` | <span data-ttu-id="3d576-265">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-265">Ordinal</span></span> | |
| `string.TrimStart` | <span data-ttu-id="3d576-266">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-266">Ordinal</span></span> | |
| `string == string` | <span data-ttu-id="3d576-267">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-267">Ordinal</span></span> | |
| `string != string` | <span data-ttu-id="3d576-268">Ordinal</span><span class="sxs-lookup"><span data-stu-id="3d576-268">Ordinal</span></span> | |

<span data-ttu-id="3d576-269">`string` API とは異なり、すべての `MemoryExtensions` API で " *序数* " による検索と比較が既定で実行されますが、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-269">Unlike `string` APIs, all `MemoryExtensions` APIs perform *Ordinal* searches and comparisons by default, with the following exceptions.</span></span>

| <span data-ttu-id="3d576-270">API</span><span class="sxs-lookup"><span data-stu-id="3d576-270">API</span></span> | <span data-ttu-id="3d576-271">既定の動作</span><span class="sxs-lookup"><span data-stu-id="3d576-271">Default behavior</span></span> | <span data-ttu-id="3d576-272">Remarks</span><span class="sxs-lookup"><span data-stu-id="3d576-272">Remarks</span></span> |
|---|---|---|
| `MemoryExtensions.ToLower` | <span data-ttu-id="3d576-273">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-273">CurrentCulture</span></span> | <span data-ttu-id="3d576-274">(`CultureInfo` 引数で null が渡されたとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-274">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToLowerInvariant` | <span data-ttu-id="3d576-275">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-275">InvariantCulture</span></span> | |
| `MemoryExtensions.ToUpper` | <span data-ttu-id="3d576-276">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-276">CurrentCulture</span></span> | <span data-ttu-id="3d576-277">(`CultureInfo` 引数で null が渡されたとき)</span><span class="sxs-lookup"><span data-stu-id="3d576-277">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToUpperInvariant` | <span data-ttu-id="3d576-278">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3d576-278">InvariantCulture</span></span> | |

<span data-ttu-id="3d576-279">結果として、コードを `string` の使用から `ReadOnlySpan<char>` の使用に変換すると、動作が誤って変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-279">A consequence is that when converting code from consuming `string` to consuming `ReadOnlySpan<char>`, behavioral changes may be introduced inadvertently.</span></span> <span data-ttu-id="3d576-280">たとえば次のような場合です。</span><span class="sxs-lookup"><span data-stu-id="3d576-280">An example of this follows.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

<span data-ttu-id="3d576-281">これに対処するには、明示的な `StringComparison` パラメーターをこれらの API に渡すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d576-281">The recommended way to address this is to pass an explicit `StringComparison` parameter to these APIs.</span></span> <span data-ttu-id="3d576-282">コード分析規則 CA1307 と CA1309 がこれに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d576-282">The code analysis rules CA1307 and CA1309 can assist with this.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a><span data-ttu-id="3d576-283">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d576-283">See also</span></span>

- [<span data-ttu-id="3d576-284">グローバリゼーションに関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="3d576-284">Globalization breaking changes</span></span>](../../core/compatibility/globalization.md)
- [<span data-ttu-id="3d576-285">.NET での文字列の比較に関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="3d576-285">Best practices for comparing strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="3d576-286">C# で文字列を比較する方法</span><span class="sxs-lookup"><span data-stu-id="3d576-286">How to compare strings in C#</span></span>](../../csharp/how-to/compare-strings.md)
- [<span data-ttu-id="3d576-287">.NET グローバリゼーションと ICU</span><span class="sxs-lookup"><span data-stu-id="3d576-287">.NET globalization and ICU</span></span>](../globalization-localization/globalization-icu.md)
- [<span data-ttu-id="3d576-288">序数対応とカルチャ対応の文字列操作</span><span class="sxs-lookup"><span data-stu-id="3d576-288">Ordinal vs. culture-sensitive string operations</span></span>](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [<span data-ttu-id="3d576-289">.NET ソース コード分析の概要</span><span class="sxs-lookup"><span data-stu-id="3d576-289">Overview of .NET source code analysis</span></span>](../../fundamentals/code-analysis/overview.md)
