---
title: .NET で文字列を比較する
description: .NET で文字列を比較する方法について確認します。 Compare、CompareOrdinal、CompareTo、StartsWith、EndsWith、Equals、IndexOf、LastIndexOf の各メソッドについて説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: 658f8b2cf7d7b2431654df1caebdac8118b3674b
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889492"
---
# <a name="comparing-strings-in-net"></a><span data-ttu-id="abc7d-104">.NET で文字列を比較する</span><span class="sxs-lookup"><span data-stu-id="abc7d-104">Comparing Strings in .NET</span></span>
<span data-ttu-id="abc7d-105">.NET は、文字列の値を比較するためのメソッドをいくつか提供します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="abc7d-106">これらの値の比較メソッドとその説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-106">The following table lists and describes the value-comparison methods.</span></span>  
  
|<span data-ttu-id="abc7d-107">メソッド名</span><span class="sxs-lookup"><span data-stu-id="abc7d-107">Method name</span></span>|<span data-ttu-id="abc7d-108">使用</span><span class="sxs-lookup"><span data-stu-id="abc7d-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-109">2 つの文字列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-109">Compares the values of two strings.</span></span> <span data-ttu-id="abc7d-110">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-110">Returns an integer value.</span></span>|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-111">ローカル カルチャに関係なく、2 つの文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-111">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="abc7d-112">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-112">Returns an integer value.</span></span>|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-113">現在の文字列オブジェクトを別の文字列と比較します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-113">Compares the current string object to another string.</span></span> <span data-ttu-id="abc7d-114">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-114">Returns an integer value.</span></span>|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-115">文字列が、渡された文字列で始まるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-115">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="abc7d-116">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-116">Returns a Boolean value.</span></span>|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-117">文字列が、渡された文字列で終わるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-117">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="abc7d-118">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-118">Returns a Boolean value.</span></span>|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-119">2 つの文字列が等しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-119">Determines whether two strings are the same.</span></span> <span data-ttu-id="abc7d-120">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-120">Returns a Boolean value.</span></span>|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-121">検索対象文字列の先頭から開始して、特定の文字または文字列が見つかったインデックス位置を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-121">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="abc7d-122">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-122">Returns an integer value.</span></span>|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="abc7d-123">検索対象文字列の末尾から開始して、特定の文字または文字列が見つかったインデックス位置を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-123">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="abc7d-124">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-124">Returns an integer value.</span></span>|  
  
## <a name="compare"></a><span data-ttu-id="abc7d-125">比較</span><span class="sxs-lookup"><span data-stu-id="abc7d-125">Compare</span></span>  
 <span data-ttu-id="abc7d-126">静的な <xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドは、2 つの文字列を詳細に比較する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-126">The static <xref:System.String.Compare%2A?displayProperty=nameWithType> method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="abc7d-127">このメソッドはカルチャに対応しています。</span><span class="sxs-lookup"><span data-stu-id="abc7d-127">This method is culturally aware.</span></span> <span data-ttu-id="abc7d-128">この機能は、2 つの文字列、または 2 つの文字列の部分文字列を比較するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-128">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="abc7d-129">また、大文字と小文字の区別やカルチャの違いを考慮または無視するためのオーバーロードも用意されています。</span><span class="sxs-lookup"><span data-stu-id="abc7d-129">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="abc7d-130">このメソッドによって返される可能性のある 3 つの整数値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-130">The following table shows the three integer values that this method might return.</span></span>  
  
|<span data-ttu-id="abc7d-131">戻り値</span><span class="sxs-lookup"><span data-stu-id="abc7d-131">Return value</span></span>|<span data-ttu-id="abc7d-132">条件</span><span class="sxs-lookup"><span data-stu-id="abc7d-132">Condition</span></span>|  
|------------------|---------------|  
|<span data-ttu-id="abc7d-133">負の整数</span><span class="sxs-lookup"><span data-stu-id="abc7d-133">A negative integer</span></span>|<span data-ttu-id="abc7d-134">最初の文字列は、並べ替え順序が 2 番目の文字列の前に置かれます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-134">The first string precedes the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="abc7d-135">\- または -</span><span class="sxs-lookup"><span data-stu-id="abc7d-135">-or-</span></span><br /><br /> <span data-ttu-id="abc7d-136">最初の文字列は `null`です。</span><span class="sxs-lookup"><span data-stu-id="abc7d-136">The first string is `null`.</span></span>|  
|<span data-ttu-id="abc7d-137">0</span><span class="sxs-lookup"><span data-stu-id="abc7d-137">0</span></span>|<span data-ttu-id="abc7d-138">最初の文字列と 2 番目の文字列は等価です。</span><span class="sxs-lookup"><span data-stu-id="abc7d-138">The first string and the second string are equal.</span></span><br /><br /> <span data-ttu-id="abc7d-139">\- または -</span><span class="sxs-lookup"><span data-stu-id="abc7d-139">-or-</span></span><br /><br /> <span data-ttu-id="abc7d-140">両方の文字列が `null`です。</span><span class="sxs-lookup"><span data-stu-id="abc7d-140">Both strings are `null`.</span></span>|  
|<span data-ttu-id="abc7d-141">正の整数</span><span class="sxs-lookup"><span data-stu-id="abc7d-141">A positive integer</span></span><br /><br /> <span data-ttu-id="abc7d-142">\- または -</span><span class="sxs-lookup"><span data-stu-id="abc7d-142">-or-</span></span><br /><br /> <span data-ttu-id="abc7d-143">1</span><span class="sxs-lookup"><span data-stu-id="abc7d-143">1</span></span>|<span data-ttu-id="abc7d-144">最初の文字列は、並べ替え順序が 2 番目の文字列の後に続きます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-144">The first string follows the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="abc7d-145">\- または -</span><span class="sxs-lookup"><span data-stu-id="abc7d-145">-or-</span></span><br /><br /> <span data-ttu-id="abc7d-146">第 2 文字列は `null`です。</span><span class="sxs-lookup"><span data-stu-id="abc7d-146">The second string is `null`.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="abc7d-147"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="abc7d-147">The <xref:System.String.Compare%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="abc7d-148">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、 <xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-148">You should not use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="abc7d-149">2 つの文字列が等価かどうかを判断するには、 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-149">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="abc7d-150"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドを使用して、2 つの文字列の相対値を確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-150">The following example uses the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to determine the relative values of two strings.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 <span data-ttu-id="abc7d-151">この例は、コンソールに `-1` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-151">This example displays `-1` to the console.</span></span>  
  
 <span data-ttu-id="abc7d-152">既定では、上の例はカルチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="abc7d-152">The preceding example is culture-sensitive by default.</span></span> <span data-ttu-id="abc7d-153">カルチャに依存しない文字列操作を実行するには、 <xref:System.String.Compare%2A?displayProperty=nameWithType> culture *パラメーターを指定することによって使用するカルチャを指定することを可能にする* メソッドのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-153">To perform a culture-insensitive string comparison, use an overload of the <xref:System.String.Compare%2A?displayProperty=nameWithType> method that allows you to specify the culture to use by supplying a *culture* parameter.</span></span> <span data-ttu-id="abc7d-154"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドを使用してカルチャに依存しない比較を実行する例については、「 [カルチャを認識しない文字列比較の実行](../globalization-localization/performing-culture-insensitive-string-comparisons.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-154">For an example that demonstrates how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to perform a culture-insensitive comparison, see [Performing Culture-Insensitive String Comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>  
  
## <a name="compareordinal"></a><span data-ttu-id="abc7d-155">CompareOrdinal</span><span class="sxs-lookup"><span data-stu-id="abc7d-155">CompareOrdinal</span></span>  
 <span data-ttu-id="abc7d-156"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> メソッドは、ローカル カルチャを考慮せずに 2 つの文字列オブジェクトを比較します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-156">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="abc7d-157">このメソッドの戻り値は、上の表で示した **Compare** メソッドによって返される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="abc7d-157">The return values of this method are identical to the values returned by the **Compare** method in the previous table.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="abc7d-158"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="abc7d-158">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="abc7d-159">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-159">You should not use the <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="abc7d-160">2 つの文字列が等価かどうかを判断するには、 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-160">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="abc7d-161">**CompareOrdinal** メソッドを使用して、2 つの文字列の値を比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-161">The following example uses the **CompareOrdinal** method to compare the values of two strings.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 <span data-ttu-id="abc7d-162">この例は、コンソールに `-32` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-162">This example displays `-32` to the console.</span></span>  
  
## <a name="compareto"></a><span data-ttu-id="abc7d-163">CompareTo</span><span class="sxs-lookup"><span data-stu-id="abc7d-163">CompareTo</span></span>  
 <span data-ttu-id="abc7d-164"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドは、現在の文字列オブジェクトがカプセル化している文字列を別の文字列またはオブジェクトと比較します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-164">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="abc7d-165">このメソッドの戻り値は、上の表で示した <xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドによって返される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="abc7d-165">The return values of this method are identical to the values returned by the <xref:System.String.Compare%2A?displayProperty=nameWithType> method in the previous table.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="abc7d-166"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="abc7d-166">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="abc7d-167">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-167">You should not use the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="abc7d-168">2 つの文字列が等価かどうかを判断するには、 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-168">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="abc7d-169"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドを使用して、 `string1` オブジェクトを `string2` オブジェクトと比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-169">The following example uses the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to compare the `string1` object to the `string2` object.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 <span data-ttu-id="abc7d-170">この例は、コンソールに `-1` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-170">This example displays `-1` to the console.</span></span>  
  
 <span data-ttu-id="abc7d-171"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドのすべてのオーバーロードは、既定で、カルチャに依存して大文字小文字を区別する比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-171">All overloads of the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method perform culture-sensitive and case-sensitive comparisons by default.</span></span> <span data-ttu-id="abc7d-172">このメソッドのオーバーロードで、カルチャに依存しない比較を実行できるものはありません。</span><span class="sxs-lookup"><span data-stu-id="abc7d-172">No overloads of this method are provided that allow you to perform a culture-insensitive comparison.</span></span> <span data-ttu-id="abc7d-173">コードを理解しやすくするために、 **String.Compare** メソッドを使用することをお勧めします。その際、カルチャに依存する操作には <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> を指定し、カルチャに依存しない操作には <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を指定します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-173">For code clarity, we recommend that you use the **String.Compare** method instead, specifying <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> for culture-sensitive operations or <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> for culture-insensitive operations.</span></span> <span data-ttu-id="abc7d-174">**String.Compare** メソッドを使用してカルチャに依存する比較とカルチャに依存しない比較の両方を実行する例については、「 [カルチャを認識しない文字列比較の実行](../globalization-localization/performing-culture-insensitive-string-comparisons.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abc7d-174">For examples that demonstrate how to use the **String.Compare** method to perform both culture-sensitive and culture-insensitive comparisons, see [Performing Culture-Insensitive String Comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>  
  
## <a name="equals"></a><span data-ttu-id="abc7d-175">次の値に等しい</span><span class="sxs-lookup"><span data-stu-id="abc7d-175">Equals</span></span>  
 <span data-ttu-id="abc7d-176">**String.Equals** メソッドを使用すると、2 つの文字列が等しいかどうかを簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-176">The **String.Equals** method can easily determine if two strings are the same.</span></span> <span data-ttu-id="abc7d-177">このメソッドは大文字と小文字を区別し、 **True** または **False** の Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-177">This case-sensitive method returns a **true** or **false** Boolean value.</span></span> <span data-ttu-id="abc7d-178">このメソッドは、次の例に示すように、既存のクラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-178">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="abc7d-179">**Equals** メソッドを使用して、文字列オブジェクトに "Hello World" という語句が含まれているかどうかを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-179">The following example uses the **Equals** method to determine whether a string object contains the phrase "Hello World".</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 <span data-ttu-id="abc7d-180">この例は、コンソールに `True` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-180">This example displays `True` to the console.</span></span>  
  
 <span data-ttu-id="abc7d-181">このメソッドは、静的メソッドとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-181">This method can also be used as a static method.</span></span> <span data-ttu-id="abc7d-182">静的メソッドを使用して、2 つの文字列オブジェクトを比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-182">The following example compares two string objects using a static method.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 <span data-ttu-id="abc7d-183">この例は、コンソールに `True` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-183">This example displays `True` to the console.</span></span>  
  
## <a name="startswith-and-endswith"></a><span data-ttu-id="abc7d-184">StartsWith と EndsWith</span><span class="sxs-lookup"><span data-stu-id="abc7d-184">StartsWith and EndsWith</span></span>  
 <span data-ttu-id="abc7d-185">**String.StartsWith** メソッドを使用すると、文字列オブジェクトが、別の文字列を構成している文字と同じ文字で始まっているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-185">You can use the **String.StartsWith** method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="abc7d-186">このメソッドは大文字と小文字を区別し、現在の文字列オブジェクトが、渡された文字列で始まる場合は **true** 、それ以外の場合は **false** を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-186">This case-sensitive method returns **true** if the current string object begins with the passed string and **false** if it does not.</span></span> <span data-ttu-id="abc7d-187">このメソッドを使用して、文字列オブジェクトが "Hello" で始まるかどうかを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-187">The following example uses this method to determine if a string object begins with "Hello".</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 <span data-ttu-id="abc7d-188">この例は、コンソールに `True` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-188">This example displays `True` to the console.</span></span>  
  
 <span data-ttu-id="abc7d-189">**String.EndsWith** メソッドは、渡された文字列を現在の文字列オブジェクトの末尾にある文字列と比較します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-189">The **String.EndsWith** method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="abc7d-190">このメソッドも Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-190">It also returns a Boolean value.</span></span> <span data-ttu-id="abc7d-191">**EndsWith** メソッドを使用して、文字列の末尾を確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-191">The following example checks the end of a string using the **EndsWith** method.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 <span data-ttu-id="abc7d-192">この例は、コンソールに `False` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-192">This example displays `False` to the console.</span></span>  
  
## <a name="indexof-and-lastindexof"></a><span data-ttu-id="abc7d-193">IndexOf と LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="abc7d-193">IndexOf and LastIndexOf</span></span>  
 <span data-ttu-id="abc7d-194">**String.IndexOf** メソッドを使用すると、特定の文字が文字列内で最初に出現する位置を確認できます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-194">You can use the **String.IndexOf** method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="abc7d-195">このメソッドは大文字と小文字を区別し、文字列の先頭からカウントを開始し、0 から始まるインデックスを使用して、渡された文字が出現する位置を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-195">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="abc7d-196">指定した文字が見つからない場合は、値 –1 を返します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-196">If the character cannot be found, a value of –1 is returned.</span></span>  
  
 <span data-ttu-id="abc7d-197">**IndexOf** メソッドを使用して、'`l`' という文字が文字列内で最初に出現する位置を検索する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-197">The following example uses the **IndexOf** method to search for the first occurrence of the '`l`' character in a string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 <span data-ttu-id="abc7d-198">この例は、コンソールに `2` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-198">This example displays `2` to the console.</span></span>  
  
 <span data-ttu-id="abc7d-199">**String.LastIndexOf** メソッドは **String.IndexOf** メソッドに似ていますが、指定した文字列が文字列内で最後に出現する位置を返すという点が異なります。</span><span class="sxs-lookup"><span data-stu-id="abc7d-199">The **String.LastIndexOf** method is similar to the **String.IndexOf** method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="abc7d-200">このメソッドは大文字と小文字を区別し、0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-200">It is case-sensitive and uses a zero-based index.</span></span>  
  
 <span data-ttu-id="abc7d-201">**LastIndexOf** メソッドを使用して、'`l`' という文字が文字列内で最後に出現する位置を検索する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-201">The following example uses the **LastIndexOf** method to search for the last occurrence of the '`l`' character in a string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 <span data-ttu-id="abc7d-202">この例は、コンソールに `9` と出力します。</span><span class="sxs-lookup"><span data-stu-id="abc7d-202">This example displays `9` to the console.</span></span>  
  
 <span data-ttu-id="abc7d-203">いずれのメソッドも、 **String.Remove** メソッドと組み合わせて使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="abc7d-203">Both methods are useful when used in conjunction with the **String.Remove** method.</span></span> <span data-ttu-id="abc7d-204">**IndexOf** メソッドまたは **LastIndexOf** メソッドのいずれかを使用して文字の位置を取得し、その位置を **Remove** メソッドに渡すことによって、その文字またはその文字で始まる単語を削除できます。</span><span class="sxs-lookup"><span data-stu-id="abc7d-204">You can use either the **IndexOf** or **LastIndexOf** methods to retrieve the position of a character, and then supply that position to the **Remove** method in order to remove a character or a word that begins with that character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc7d-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="abc7d-205">See also</span></span>

- [<span data-ttu-id="abc7d-206">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="abc7d-206">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="abc7d-207">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="abc7d-207">Performing Culture-Insensitive String Operations</span></span>](../globalization-localization/performing-culture-insensitive-string-operations.md)
- [<span data-ttu-id="abc7d-208">並べ替え重みテーブル (Windows 上の .NET 用)</span><span class="sxs-lookup"><span data-stu-id="abc7d-208">Sorting Weight Tables (for .NET on Windows)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="abc7d-209">デフォルト Unicode 照合基本テーブル (Linux と macOS 上の .NET Core 用)</span><span class="sxs-lookup"><span data-stu-id="abc7d-209">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
