---
title: 文字列を部分文字列に分離する
description: String.Split、正規表現、String.Substring など、文字列の一部を抽出するさまざまな手法について説明します。
ms.date: 10/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: b753476b7d8e5808fdcacc6f28bd1de5f8b232bb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829650"
---
# <a name="extract-substrings-from-a-string"></a><span data-ttu-id="e08a2-103">文字列から部分文字列を抽出する</span><span class="sxs-lookup"><span data-stu-id="e08a2-103">Extract substrings from a string</span></span>

<span data-ttu-id="e08a2-104">この記事では、文字列の一部を抽出するためのさまざまな手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-104">This article covers some different techniques for extracting parts of a string.</span></span>

- <span data-ttu-id="e08a2-105">目的の部分文字列が既知の区切り文字 (1 つまたは複数) で区切られている場合は、[Split メソッド](#stringsplit-method)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-105">Use the [Split method](#stringsplit-method) when the substrings you want are separated by a known delimiting character (or characters).</span></span>
- <span data-ttu-id="e08a2-106">文字列が固定パターンに準拠している場合は、[正規表現](#regular-expressions)が便利です。</span><span class="sxs-lookup"><span data-stu-id="e08a2-106">[Regular expressions](#regular-expressions) are useful when the string conforms to a fixed pattern.</span></span>
- <span data-ttu-id="e08a2-107">文字列内の "*すべての*" 部分文字列を抽出したくないときは、[IndexOf メソッドと Substring メソッド](#stringindexof-and-stringsubstring-methods)を組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-107">Use the [IndexOf and Substring methods](#stringindexof-and-stringsubstring-methods) in conjunction when you don't want to extract *all* of the substrings in a string.</span></span>

## <a name="stringsplit-method"></a><span data-ttu-id="e08a2-108">String.Split メソッド</span><span class="sxs-lookup"><span data-stu-id="e08a2-108">String.Split method</span></span>

<span data-ttu-id="e08a2-109"><xref:System.String.Split%2A?displayProperty=nameWithType> には、指定した 1 つ以上の区切り文字に基づいて文字列を部分文字列のグループに分割するのに役立つ、いくつかのオーバーロードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e08a2-109"><xref:System.String.Split%2A?displayProperty=nameWithType> provides a handful of overloads to help you break up a string into a group of substrings based on one or more delimiting characters that you specify.</span></span> <span data-ttu-id="e08a2-110">最終結果の部分文字列の合計数を制限したり、部分文字列から空白文字を取り除いたり、空の部分文字列を除外したりできます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-110">You can choose to limit the total number of substrings in the final result, trim white-space characters from substrings, or exclude empty substrings.</span></span>

<span data-ttu-id="e08a2-111">次の例では、`String.Split()` の 3 つの異なるオーバーロードを示します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-111">The following examples show three different overloads of `String.Split()`.</span></span> <span data-ttu-id="e08a2-112">最初の例では、区切り文字を渡さずに <xref:System.String.Split(System.Char[])> のオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-112">The first example calls the <xref:System.String.Split(System.Char[])> overload without passing any separator characters.</span></span> <span data-ttu-id="e08a2-113">区切り文字を指定しないと、`String.Split()` により、文字列を分割するための既定の区切り記号 (空白文字) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-113">When you don't specify any delimiting characters, `String.Split()` uses default delimiters, which are white-space characters, to split up the string.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

<span data-ttu-id="e08a2-114">ご覧のように、部分文字列の 2 つにピリオド文字 (`.`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e08a2-114">As you can see, the period characters (`.`) are included in two of the substrings.</span></span> <span data-ttu-id="e08a2-115">ピリオド文字を除外する場合は、ピリオド文字を追加の区切り文字として追加できます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-115">If you want to exclude the period characters, you can add the period character as an additional delimiting character.</span></span> <span data-ttu-id="e08a2-116">その方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-116">The next example shows how to do this.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

<span data-ttu-id="e08a2-117">部分文字列からピリオドは削除されましたが、今度は 2 つの余分な空の部分文字列が含まれるようになっています。</span><span class="sxs-lookup"><span data-stu-id="e08a2-117">The periods are gone from the substrings, but now two extra empty substrings have been included.</span></span> <span data-ttu-id="e08a2-118">これらの空の部分文字列は、単語とそれに続くピリオドの間の部分文字列を表します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-118">These empty substring represent the substring between the word and the period that follows it.</span></span> <span data-ttu-id="e08a2-119">結果の配列から空の部分文字列を省略するには、<xref:System.String.Split(System.Char[],System.StringSplitOptions)> のオーバーロードを呼び出し、`options` パラメーターとして <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> を指定します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-119">To omit empty substrings from the resulting array, you can call the <xref:System.String.Split(System.Char[],System.StringSplitOptions)> overload and specify <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> for the `options` parameter.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a><span data-ttu-id="e08a2-120">正規表現</span><span class="sxs-lookup"><span data-stu-id="e08a2-120">Regular expressions</span></span>

<span data-ttu-id="e08a2-121">文字列が固定パターンに準拠している場合は、正規表現を使用してその要素を抽出して処理できます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-121">If your string conforms to a fixed pattern, you can use a regular expression to extract and handle its elements.</span></span> <span data-ttu-id="e08a2-122">たとえば、文字列の形式が "*数字* *オペランド* *数字*" の場合、[正規表現](regular-expressions.md)を使用して、文字列の要素を抽出して処理できます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-122">For example, if strings take the form "*number* *operand* *number*", you can use a [regular expression](regular-expressions.md) to extract and handle the string's elements.</span></span> <span data-ttu-id="e08a2-123">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-123">Here's an example:</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

<span data-ttu-id="e08a2-124">`(\d+)\s+([-+*/])\s+(\d+)` という正規表現パターンは、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-124">The regular expression pattern `(\d+)\s+([-+*/])\s+(\d+)` is defined like this:</span></span>

|<span data-ttu-id="e08a2-125">Pattern</span><span class="sxs-lookup"><span data-stu-id="e08a2-125">Pattern</span></span>|<span data-ttu-id="e08a2-126">説明</span><span class="sxs-lookup"><span data-stu-id="e08a2-126">Description</span></span>|
|-------------|-----------------|
|`(\d+)`|<span data-ttu-id="e08a2-127">1 個以上の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-127">Match one or more decimal digits.</span></span> <span data-ttu-id="e08a2-128">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="e08a2-128">This is the first capturing group.</span></span>|
|`\s+`|<span data-ttu-id="e08a2-129">1 つ以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-129">Match one or more white-space characters.</span></span>|
|`([-+*/])`|<span data-ttu-id="e08a2-130">算術演算子の記号 (+、-、\*、/) と一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-130">Match an arithmetic operator sign (+, -, \*, or /).</span></span> <span data-ttu-id="e08a2-131">これが 2 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="e08a2-131">This is the second capturing group.</span></span>|
|`\s+`|<span data-ttu-id="e08a2-132">1 つ以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-132">Match one or more white-space characters.</span></span>|
|`(\d+)`|<span data-ttu-id="e08a2-133">1 個以上の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-133">Match one or more decimal digits.</span></span> <span data-ttu-id="e08a2-134">これが 3 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="e08a2-134">This is the third capturing group.</span></span>|

<span data-ttu-id="e08a2-135">また、正規表現を使用して、固定の文字セットではなく、パターンに基づいて文字列から部分文字列を抽出することもできます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-135">You can also use a regular expression to extract substrings from a string based on a pattern rather than a fixed set of characters.</span></span> <span data-ttu-id="e08a2-136">これは、次のいずれかの条件が発生するときの一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="e08a2-136">This is a common scenario when either of these conditions occurs:</span></span>

- <span data-ttu-id="e08a2-137">1 つ以上の区切り文字が、<xref:System.String> インスタンスの区切り記号として "*常に*" 使用されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="e08a2-137">One or more of the delimiter characters does not *always* serve as a delimiter in the <xref:System.String> instance.</span></span>

- <span data-ttu-id="e08a2-138">区切り文字のシーケンスと数が、可変または不明です。</span><span class="sxs-lookup"><span data-stu-id="e08a2-138">The sequence and number of delimiter characters is variable or unknown.</span></span>

<span data-ttu-id="e08a2-139">たとえば、<xref:System.String.Split%2A> メソッドを使用して、次の文字列を分割することはできません。これは、`\n` (改行) 文字の数が可変であり、常に区切り記号として機能しないためです。</span><span class="sxs-lookup"><span data-stu-id="e08a2-139">For example, the <xref:System.String.Split%2A> method cannot be used to split the following string, because the number of `\n` (newline) characters is variable, and they don't always serve as delimiters.</span></span>

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

<span data-ttu-id="e08a2-140">次の例に示すように、正規表現を使用すると、この文字列を簡単に分割できます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-140">A regular expression can split this string easily, as the following example shows.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

<span data-ttu-id="e08a2-141">`\[([^\[\]]+)\]` という正規表現パターンは、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-141">The regular expression pattern `\[([^\[\]]+)\]` is defined like this:</span></span>

|<span data-ttu-id="e08a2-142">Pattern</span><span class="sxs-lookup"><span data-stu-id="e08a2-142">Pattern</span></span>|<span data-ttu-id="e08a2-143">説明</span><span class="sxs-lookup"><span data-stu-id="e08a2-143">Description</span></span>|
|-------------|-----------------|
|`\[`|<span data-ttu-id="e08a2-144">左角かっこと一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-144">Match an opening bracket.</span></span>|
|`([^\[\]]+)`|<span data-ttu-id="e08a2-145">左または右の角かっこではない任意の文字と 1 回以上一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-145">Match any character that is not an opening or a closing bracket one or more times.</span></span> <span data-ttu-id="e08a2-146">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="e08a2-146">This is the first capturing group.</span></span>|
|`\]`|<span data-ttu-id="e08a2-147">右角かっこと一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-147">Match a closing bracket.</span></span>|

<span data-ttu-id="e08a2-148"><xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> メソッドは <xref:System.String.Split%2A?displayProperty=nameWithType> とほぼ同じですが、固定文字セットではなく正規表現パターンに基づいて文字列を分割する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="e08a2-148">The <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method is almost identical to <xref:System.String.Split%2A?displayProperty=nameWithType>, except that it splits a string based on a regular expression pattern instead of a fixed character set.</span></span> <span data-ttu-id="e08a2-149">たとえば、次の例では、<xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> メソッドを使用して、ハイフンと他の文字のさまざまな組み合わせで区切られた部分文字列が含まれる文字列を分割します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-149">For example, the following example uses the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to split a string that contains substrings delimited by various combinations of hyphens and other characters.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

<span data-ttu-id="e08a2-150">`\s-\s?[+*]?\s?-\s` という正規表現パターンは、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-150">The regular expression pattern `\s-\s?[+*]?\s?-\s` is defined like this:</span></span>

|<span data-ttu-id="e08a2-151">Pattern</span><span class="sxs-lookup"><span data-stu-id="e08a2-151">Pattern</span></span>|<span data-ttu-id="e08a2-152">説明</span><span class="sxs-lookup"><span data-stu-id="e08a2-152">Description</span></span>|
|-------------|-----------------|
|`\s-`|<span data-ttu-id="e08a2-153">空白文字の後にハイフンが続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-153">Match a white-space character followed by a hyphen.</span></span>|
|`\s?`|<span data-ttu-id="e08a2-154">0 個または 1 個の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-154">Match zero or one white-space character.</span></span>|
|`[+*]?`|<span data-ttu-id="e08a2-155">\+ または \* のいずれかの文字の 0 回または 1 回の出現に一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-155">Match zero or one occurrence of either the + or \* character.</span></span>|
|`\s?`|<span data-ttu-id="e08a2-156">0 個または 1 個の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-156">Match zero or one white-space character.</span></span>|
|`-\s`|<span data-ttu-id="e08a2-157">ハイフンの後に空白文字が続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-157">Match a hyphen followed by a white-space character.</span></span>|

## <a name="stringindexof-and-stringsubstring-methods"></a><span data-ttu-id="e08a2-158">String.IndexOf メソッドと String.Substring メソッド</span><span class="sxs-lookup"><span data-stu-id="e08a2-158">String.IndexOf and String.Substring methods</span></span>

<span data-ttu-id="e08a2-159">文字列内のすべての部分文字列に関心があるわけではない場合は、一致が始まる位置のインデックスを返す文字列比較メソッドのいずれかを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e08a2-159">If you aren't interested in all of the substrings in a string, you might prefer to work with one of the string comparison methods that returns the index at which the match begins.</span></span> <span data-ttu-id="e08a2-160">その後、<xref:System.String.Substring%2A> メソッドを呼び出して、必要な部分文字列を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="e08a2-160">You can then call the <xref:System.String.Substring%2A> method to extract the substring that you want.</span></span> <span data-ttu-id="e08a2-161">次のような文字列比較メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="e08a2-161">The string comparison methods include:</span></span>

- <span data-ttu-id="e08a2-162"><xref:System.String.IndexOf%2A>。文字列インスタンス内で文字または文字列が最初に出現する位置の 0 から始まるインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-162"><xref:System.String.IndexOf%2A>, which returns the zero-based index of the first occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="e08a2-163"><xref:System.String.IndexOfAny%2A>。文字配列内で任意の文字が最初に出現する位置の、現在の文字列インスタンス内での 0 から始まるインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-163"><xref:System.String.IndexOfAny%2A>, which returns the zero-based index in the current string instance of the first occurrence of any character in a character array.</span></span>

- <span data-ttu-id="e08a2-164"><xref:System.String.LastIndexOf%2A>。文字列インスタンス内で文字または文字列が最後に出現する位置の 0 から始まるインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-164"><xref:System.String.LastIndexOf%2A>, which returns the zero-based index of the last occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="e08a2-165"><xref:System.String.LastIndexOfAny%2A>。文字配列内で任意の文字が最後に出現する位置の、現在の文字列インスタンス内での 0 から始まるインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-165"><xref:System.String.LastIndexOfAny%2A>, which returns a zero-based index in the current string instance of the last occurrence of any character in a character array.</span></span>

<span data-ttu-id="e08a2-166">次の例では、<xref:System.String.IndexOf%2A> メソッドを使用して、文字列内のピリオドを検索します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-166">The following example uses the <xref:System.String.IndexOf%2A> method to find the periods in a string.</span></span> <span data-ttu-id="e08a2-167">次に、<xref:System.String.Substring%2A> メソッドを使用して完全な文を返します。</span><span class="sxs-lookup"><span data-stu-id="e08a2-167">It then uses the <xref:System.String.Substring%2A> method to return full sentences.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a><span data-ttu-id="e08a2-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="e08a2-168">See also</span></span>

- [<span data-ttu-id="e08a2-169">.NET の基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="e08a2-169">Basic string operations in .NET</span></span>](basic-string-operations.md)
- [<span data-ttu-id="e08a2-170">.NET 正規表現</span><span class="sxs-lookup"><span data-stu-id="e08a2-170">.NET regular expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="e08a2-171">C# で String.Split を使用して文字列を解析する方法</span><span class="sxs-lookup"><span data-stu-id="e08a2-171">How to parse strings using String.Split in C#</span></span>](../../csharp/how-to/parse-strings-using-split.md)
