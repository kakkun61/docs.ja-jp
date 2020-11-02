---
title: 量指定子 (正規表現)
description: 一致する入力中に存在する必要がある文字、グループ、または文字クラスの出現数を指定する、正規表現の量指定子について説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
ms.openlocfilehash: 361286b992180e1d7fdf18d88022780cc3aa53fc
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889427"
---
# <a name="quantifiers-in-regular-expressions"></a><span data-ttu-id="ff071-103">量指定子 (正規表現)</span><span class="sxs-lookup"><span data-stu-id="ff071-103">Quantifiers in Regular Expressions</span></span>
<span data-ttu-id="ff071-104">量指定子は、一致と見なされるために入力中に存在する必要がある文字、グループ、または文字クラスの出現数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff071-104">Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.</span></span>  <span data-ttu-id="ff071-105">次の表に、.NET でサポートされている量指定子の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff071-105">The following table lists the quantifiers supported by .NET.</span></span>  
  
|<span data-ttu-id="ff071-106">最長一致の量指定子</span><span class="sxs-lookup"><span data-stu-id="ff071-106">Greedy quantifier</span></span>|<span data-ttu-id="ff071-107">最短一致の量指定子</span><span class="sxs-lookup"><span data-stu-id="ff071-107">Lazy quantifier</span></span>|<span data-ttu-id="ff071-108">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-108">Description</span></span>|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|<span data-ttu-id="ff071-109">0 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-109">Match zero or more times.</span></span>|  
|`+`|`+?`|<span data-ttu-id="ff071-110">1 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-110">Match one or more times.</span></span>|  
|`?`|`??`|<span data-ttu-id="ff071-111">0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-111">Match zero or one time.</span></span>|  
|<span data-ttu-id="ff071-112">`{` *n* `}`</span><span class="sxs-lookup"><span data-stu-id="ff071-112">`{` *n* `}`</span></span>|<span data-ttu-id="ff071-113">`{` *n* `}?`</span><span class="sxs-lookup"><span data-stu-id="ff071-113">`{` *n* `}?`</span></span>|<span data-ttu-id="ff071-114">*n* 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-114">Match exactly *n* times.</span></span>|  
|<span data-ttu-id="ff071-115">`{` *n* `,}`</span><span class="sxs-lookup"><span data-stu-id="ff071-115">`{` *n* `,}`</span></span>|<span data-ttu-id="ff071-116">`{` *n* `,}?`</span><span class="sxs-lookup"><span data-stu-id="ff071-116">`{` *n* `,}?`</span></span>|<span data-ttu-id="ff071-117">*n* 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-117">Match at least *n* times.</span></span>|  
|<span data-ttu-id="ff071-118">`{` *n* `,` *m* `}`</span><span class="sxs-lookup"><span data-stu-id="ff071-118">`{` *n* `,` *m* `}`</span></span>|<span data-ttu-id="ff071-119">`{` *n* `,` *m* `}?`</span><span class="sxs-lookup"><span data-stu-id="ff071-119">`{` *n* `,` *m* `}?`</span></span>|<span data-ttu-id="ff071-120">*n* 回から *m* 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-120">Match from *n* to *m* times.</span></span>|  
  
 <span data-ttu-id="ff071-121">量 `n` および `m` は整数の定数です。</span><span class="sxs-lookup"><span data-stu-id="ff071-121">The quantities `n` and `m` are integer constants.</span></span> <span data-ttu-id="ff071-122">通常、量指定子は最長一致です。最長一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ多くなるように照合が行われます。</span><span class="sxs-lookup"><span data-stu-id="ff071-122">Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible.</span></span> <span data-ttu-id="ff071-123">量指定子に `?` 文字を付けると最短一致になります。最短一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ少なくなるように照合が行われます。</span><span class="sxs-lookup"><span data-stu-id="ff071-123">Appending the `?` character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible.</span></span> <span data-ttu-id="ff071-124">最長一致と最短一致の量指定子の違いの詳細については、このトピックの「[最長一致と最短一致の量指定子](#Greedy)」のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ff071-124">For a complete description of the difference between greedy and lazy quantifiers, see the section [Greedy and Lazy Quantifiers](#Greedy) later in this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ff071-125">量指定子を入れ子にすると (たとえば、正規表現パターン `(a*)*` など)、入力文字列の文字数に応じて指数関数的に、正規表現エンジンで実行する必要がある比較の回数が増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff071-125">Nesting quantifiers (for example, as the regular expression pattern `(a*)*` does) can increase the number of comparisons that the regular expression engine must perform, as an exponential function of the number of characters in the input string.</span></span> <span data-ttu-id="ff071-126">この動作と回避方法の詳細については、[バックトラッキング](backtracking-in-regular-expressions.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff071-126">For more information about this behavior and its workarounds, see [Backtracking](backtracking-in-regular-expressions.md).</span></span>  
  
## <a name="regular-expression-quantifiers"></a><span data-ttu-id="ff071-127">正規表現の量指定子</span><span class="sxs-lookup"><span data-stu-id="ff071-127">Regular Expression Quantifiers</span></span>  
 <span data-ttu-id="ff071-128">以降のセクションでは、.NET の正規表現でサポートされている量指定子について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff071-128">The following sections list the quantifiers supported by .NET regular expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff071-129">正規表現エンジンでは、正規表現パターンで \*、+、?、{、および } の各文字を検出すると、[文字クラス](character-classes-in-regular-expressions.md)に含まれているもの以外は量指定子または量指定子コンストラクトの一部として解釈します。</span><span class="sxs-lookup"><span data-stu-id="ff071-129">If the \*, +, ?, {, and } characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a [character class](character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="ff071-130">文字クラスの外側でこれらをリテラル文字として解釈するには、文字の前に円記号を付けてエスケープする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff071-130">To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash.</span></span> <span data-ttu-id="ff071-131">たとえば、正規表現パターン内の `\*` という文字列は、リテラルのアスタリスク ("\*") 文字と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="ff071-131">For example, the string `\*` in a regular expression pattern is interpreted as a literal asterisk ("\*") character.</span></span>  
  
### <a name="match-zero-or-more-times-"></a><span data-ttu-id="ff071-132">0 回以上の繰り返しに一致: \*</span><span class="sxs-lookup"><span data-stu-id="ff071-132">Match Zero or More Times: \*</span></span>  
 <span data-ttu-id="ff071-133">`*` 量指定子は、直前の要素の 0 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-133">The `*` quantifier matches the preceding element zero or more times.</span></span> <span data-ttu-id="ff071-134">これは `{0,}` 量指定子と同じです。</span><span class="sxs-lookup"><span data-stu-id="ff071-134">It is equivalent to the `{0,}` quantifier.</span></span> <span data-ttu-id="ff071-135">`*` は最長一致の量指定子であり、最短一致でこれに対応するのは `*?` です。</span><span class="sxs-lookup"><span data-stu-id="ff071-135">`*` is a greedy quantifier whose lazy equivalent is `*?`.</span></span>  
  
 <span data-ttu-id="ff071-136">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-136">The following example illustrates this regular expression.</span></span> <span data-ttu-id="ff071-137">入力文字列の 9 個の数字グループにおいて、5 個がパターンに一致し、4 個 (`95`、`929`、`9219`、および `9919`) が一致しません。</span><span class="sxs-lookup"><span data-stu-id="ff071-137">Of the nine digit groups in the input string, five match the pattern and four (`95`, `929`, `9219`, and `9919`) do not.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 <span data-ttu-id="ff071-138">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-138">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-139">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-139">Pattern</span></span>|<span data-ttu-id="ff071-140">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-140">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-141">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-141">Start at a word boundary.</span></span>|  
|`91*`|<span data-ttu-id="ff071-142">"9" の後に文字 "1" が 0 個以上続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-142">Match a "9" followed by zero or more "1" characters.</span></span>|  
|`9*`|<span data-ttu-id="ff071-143">0 個以上の文字 "9" に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-143">Match zero or more "9" characters.</span></span>|  
|`\b`|<span data-ttu-id="ff071-144">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="ff071-144">End at a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-"></a><span data-ttu-id="ff071-145">1 回以上の繰り返しに一致: +</span><span class="sxs-lookup"><span data-stu-id="ff071-145">Match One or More Times: +</span></span>  
 <span data-ttu-id="ff071-146">`+` 量指定子は、直前の要素の 1 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-146">The `+` quantifier matches the preceding element one or more times.</span></span> <span data-ttu-id="ff071-147">これは `{1,}` と同じです。</span><span class="sxs-lookup"><span data-stu-id="ff071-147">It is equivalent to `{1,}`.</span></span> <span data-ttu-id="ff071-148">`+` は最長一致の量指定子であり、最短一致でこれに対応するのは `+?` です。</span><span class="sxs-lookup"><span data-stu-id="ff071-148">`+` is a greedy quantifier whose lazy equivalent is `+?`.</span></span>  
  
 <span data-ttu-id="ff071-149">たとえば、正規表現 `\ban+\w*?\b` は、文字 `a` で始まり、文字 `n` が 1 回以上繰り返されるすべての単語に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff071-149">For example, the regular expression `\ban+\w*?\b` tries to match entire words that begin with the letter `a` followed by one or more instances of the letter `n`.</span></span> <span data-ttu-id="ff071-150">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-150">The following example illustrates this regular expression.</span></span> <span data-ttu-id="ff071-151">この正規表現は、単語 `an`、`annual`、`announcement`、および `antique` に一致し、`autumn` と `all` では不一致となります。</span><span class="sxs-lookup"><span data-stu-id="ff071-151">The regular expression matches the words `an`, `annual`, `announcement`, and `antique`, and correctly fails to match `autumn` and `all`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 <span data-ttu-id="ff071-152">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-152">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-153">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-153">Pattern</span></span>|<span data-ttu-id="ff071-154">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-154">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-155">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-155">Start at a word boundary.</span></span>|  
|`an+`|<span data-ttu-id="ff071-156">"a" の後に文字 "n" が 1 個以上続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-156">Match an "a" followed by one or more "n" characters.</span></span>|  
|`\w*?`|<span data-ttu-id="ff071-157">単語に含まれる文字の 0 回以上の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-157">Match a word character zero or more times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="ff071-158">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="ff071-158">End at a word boundary.</span></span>|  
  
### <a name="match-zero-or-one-time-"></a><span data-ttu-id="ff071-159">0 回または 1 回の繰り返しに一致: ?</span><span class="sxs-lookup"><span data-stu-id="ff071-159">Match Zero or One Time: ?</span></span>  
 <span data-ttu-id="ff071-160">`?` 量指定子は、直前の要素の 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-160">The `?` quantifier matches the preceding element zero or one time.</span></span> <span data-ttu-id="ff071-161">これは `{0,1}` と同じです。</span><span class="sxs-lookup"><span data-stu-id="ff071-161">It is equivalent to `{0,1}`.</span></span> <span data-ttu-id="ff071-162">`?` は最長一致の量指定子であり、最短一致でこれに対応するのは `??` です。</span><span class="sxs-lookup"><span data-stu-id="ff071-162">`?` is a greedy quantifier whose lazy equivalent is `??`.</span></span>  
  
 <span data-ttu-id="ff071-163">たとえば、正規表現 `\ban?\b` は、文字 `a` で始まり、文字 `n` が 0 回または 1 回繰り返されるすべての単語に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff071-163">For example, the regular expression `\ban?\b` tries to match entire words that begin with the letter `a` followed by zero or one instances of the letter `n`.</span></span> <span data-ttu-id="ff071-164">つまり、単語 `a` と `an` に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff071-164">In other words, it tries to match the words `a` and `an`.</span></span> <span data-ttu-id="ff071-165">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-165">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 <span data-ttu-id="ff071-166">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-166">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-167">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-167">Pattern</span></span>|<span data-ttu-id="ff071-168">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-168">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-169">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-169">Start at a word boundary.</span></span>|  
|`an?`|<span data-ttu-id="ff071-170">"a" の後に文字 "n" が 0 個または 1 個続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-170">Match an "a" followed by zero or one "n" character.</span></span>|  
|`\b`|<span data-ttu-id="ff071-171">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="ff071-171">End at a word boundary.</span></span>|  
  
### <a name="match-exactly-n-times-n"></a><span data-ttu-id="ff071-172">n 回の繰り返しに一致: {n}</span><span class="sxs-lookup"><span data-stu-id="ff071-172">Match Exactly n Times: {n}</span></span>  
 <span data-ttu-id="ff071-173">`{`*n*`}` 量指定子は、直前の要素の *n* 回の繰り返しに一致します。ここで、 *n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="ff071-173">The `{`*n*`}` quantifier matches the preceding element exactly *n* times, where *n* is any integer.</span></span> <span data-ttu-id="ff071-174">`{`*n*`}` は最長一致の量指定子であり、最短一致でこれに対応するのは `{`*n*`}?` です。</span><span class="sxs-lookup"><span data-stu-id="ff071-174">`{`*n*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="ff071-175">たとえば、正規表現 `\b\d+\,\d{3}\b` は、ワード境界、1 個以上の 10 進数、3 個の 10 進数、ワード境界の順に続く文字に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff071-175">For example, the regular expression `\b\d+\,\d{3}\b` tries to match a word boundary followed by one or more decimal digits followed by three decimal digits followed by a word boundary.</span></span> <span data-ttu-id="ff071-176">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-176">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 <span data-ttu-id="ff071-177">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-177">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-178">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-178">Pattern</span></span>|<span data-ttu-id="ff071-179">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-179">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-180">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-180">Start at a word boundary.</span></span>|  
|`\d+`|<span data-ttu-id="ff071-181">1 個以上の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-181">Match one or more decimal digits.</span></span>|  
|`\,`|<span data-ttu-id="ff071-182">コンマ文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-182">Match a comma character.</span></span>|  
|`\d{3}`|<span data-ttu-id="ff071-183">3 個の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-183">Match three decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="ff071-184">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="ff071-184">End at a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-n"></a><span data-ttu-id="ff071-185">n 回以上の繰り返しに一致: {n,}</span><span class="sxs-lookup"><span data-stu-id="ff071-185">Match at Least n Times: {n,}</span></span>  
 <span data-ttu-id="ff071-186">`{`*n*`,}` 量指定子は、直前の要素の *n* 回以上の繰り返しに一致します。ここで、 *n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="ff071-186">The `{`*n*`,}` quantifier matches the preceding element at least *n* times, where *n* is any integer.</span></span> <span data-ttu-id="ff071-187">`{`*n*`,}` は最長一致の量指定子であり、最短一致でこれに対応するのは `{`*n*`,}?` です。</span><span class="sxs-lookup"><span data-stu-id="ff071-187">`{`*n*`,}` is a greedy quantifier whose lazy equivalent is `{`*n*`,}?`.</span></span>  
  
 <span data-ttu-id="ff071-188">たとえば、正規表現 `\b\d{2,}\b\D+` は、ワード境界、2 個以上の 10 進数、ワード境界、数字以外の文字の順に続く文字に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff071-188">For example, the regular expression `\b\d{2,}\b\D+` tries to match a word boundary followed by at least two digits followed by a word boundary and a non-digit character.</span></span> <span data-ttu-id="ff071-189">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-189">The following example illustrates this regular expression.</span></span> <span data-ttu-id="ff071-190">この正規表現は `"7 days"` という語句には一致しません。これは、10 進数が 1 個しか含まれていないためです。しかし、`"10 weeks and 300 years"` という語句には正常に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-190">The regular expression fails to match the phrase `"7 days"` because it contains just one decimal digit, but it successfully matches the phrases `"10 weeks and 300 years"`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 <span data-ttu-id="ff071-191">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-191">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-192">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-192">Pattern</span></span>|<span data-ttu-id="ff071-193">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-193">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-194">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-194">Start at a word boundary.</span></span>|  
|`\d{2,}`|<span data-ttu-id="ff071-195">2 個以上の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-195">Match at least two decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="ff071-196">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-196">Match a word boundary.</span></span>|  
|`\D+`|<span data-ttu-id="ff071-197">1 個以上の 10 進数以外の数字と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-197">Match at least one non-decimal digit.</span></span>|  
  
### <a name="match-between-n-and-m-times-nm"></a><span data-ttu-id="ff071-198">n 回から m 回までの繰り返しに一致: {n,m}</span><span class="sxs-lookup"><span data-stu-id="ff071-198">Match Between n and m Times: {n,m}</span></span>  
 <span data-ttu-id="ff071-199">`{`*n*`,`*m*`}` 量指定子は、直前の要素の *n* 回以上、 *m* 回以下の繰り返しに一致します。ここで、 *n* と *m* は整数です。</span><span class="sxs-lookup"><span data-stu-id="ff071-199">The `{`*n*`,`*m*`}` quantifier matches the preceding element at least *n* times, but no more than *m* times, where *n* and *m* are integers.</span></span> <span data-ttu-id="ff071-200">`{`*n*`,`*m*`}` は最長一致の量指定子であり、最短一致でこれに対応するのは `{`*n*`,`*m*`}?` です。</span><span class="sxs-lookup"><span data-stu-id="ff071-200">`{`*n*`,`*m*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`,`*m*`}?`.</span></span>  
  
 <span data-ttu-id="ff071-201">次の例では、正規表現 `(00\s){2,4}` は、2 個の 0 と 1 個のスペースが、2 回以上 4 回以下だけ現れる文字列に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff071-201">In the following example, the regular expression `(00\s){2,4}` tries to match between two and four occurrences of two zero digits followed by a space.</span></span> <span data-ttu-id="ff071-202">入力文字列の最後の部分には、このパターンが最大の 4 回ではなく 5 回含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff071-202">Note that the final portion of the input string includes this pattern five times rather than the maximum of four.</span></span> <span data-ttu-id="ff071-203">この部分文字列の最初の部分 (スペースと 5 つ目の 0 のペアまで) だけが正規表現パターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-203">However, only the initial portion of this substring (up to the space and the fifth pair of zeros) matches the regular expression pattern.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a><span data-ttu-id="ff071-204">0 回以上の繰り返しに一致 (最短一致): \*?</span><span class="sxs-lookup"><span data-stu-id="ff071-204">Match Zero or More Times (Lazy Match): \*?</span></span>  
 <span data-ttu-id="ff071-205">`*?` 量指定子は、直前の要素の 0 回以上の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-205">The `*?` quantifier matches the preceding element zero or more times, but as few times as possible.</span></span> <span data-ttu-id="ff071-206">これは、最長一致の量指定子 `*` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="ff071-206">It is the lazy counterpart of the greedy quantifier `*`.</span></span>  
  
 <span data-ttu-id="ff071-207">次の例では、正規表現 `\b\w*?oo\w*?\b` は、文字列 `oo` を含むすべての単語に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-207">In the following example, the regular expression `\b\w*?oo\w*?\b` matches all words that contain the string `oo`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 <span data-ttu-id="ff071-208">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-208">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-209">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-209">Pattern</span></span>|<span data-ttu-id="ff071-210">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-210">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-211">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-211">Start at a word boundary.</span></span>|  
|`\w*?`|<span data-ttu-id="ff071-212">単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-212">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`oo`|<span data-ttu-id="ff071-213">文字列 "oo" と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-213">Match the string "oo".</span></span>|  
|`\w*?`|<span data-ttu-id="ff071-214">単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-214">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`\b`|<span data-ttu-id="ff071-215">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="ff071-215">End on a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-lazy-match-"></a><span data-ttu-id="ff071-216">1 回以上の繰り返しに一致 (最短一致): +?</span><span class="sxs-lookup"><span data-stu-id="ff071-216">Match One or More Times (Lazy Match): +?</span></span>  
 <span data-ttu-id="ff071-217">`+?` 量指定子は、直前の要素の 1 回以上の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-217">The `+?` quantifier matches the preceding element one or more times, but as few times as possible.</span></span> <span data-ttu-id="ff071-218">これは、最長一致の量指定子 `+` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="ff071-218">It is the lazy counterpart of the greedy quantifier `+`.</span></span>  
  
 <span data-ttu-id="ff071-219">たとえば、正規表現 `\b\w+?\b` は、ワード境界で区切られた 1 つ以上の文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-219">For example, the regular expression `\b\w+?\b` matches one or more characters separated by word boundaries.</span></span> <span data-ttu-id="ff071-220">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-220">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a><span data-ttu-id="ff071-221">0 回または 1 回の繰り返しに一致 (最短一致): ??</span><span class="sxs-lookup"><span data-stu-id="ff071-221">Match Zero or One Time (Lazy Match): ??</span></span>  
 <span data-ttu-id="ff071-222">`??` 量指定子は、直前の要素の 0 回または 1 回の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-222">The `??` quantifier matches the preceding element zero or one time, but as few times as possible.</span></span> <span data-ttu-id="ff071-223">これは、最長一致の量指定子 `?` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="ff071-223">It is the lazy counterpart of the greedy quantifier `?`.</span></span>  
  
 <span data-ttu-id="ff071-224">たとえば、正規表現 `^\s*(System.)??Console.Write(Line)??\(??` は、文字列 "Console.Write" または "Console.WriteLine" に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff071-224">For example, the regular expression `^\s*(System.)??Console.Write(Line)??\(??` attempts to match the strings "Console.Write" or "Console.WriteLine".</span></span> <span data-ttu-id="ff071-225">文字列には、"Console" の前に</span><span class="sxs-lookup"><span data-stu-id="ff071-225">The string can also include "System."</span></span> <span data-ttu-id="ff071-226">"System." が含まれていてもよく、最後に左かっこがあってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="ff071-226">before "Console", and it can be followed by an opening parenthesis.</span></span> <span data-ttu-id="ff071-227">文字列は行の先頭にある必要がありますが、文字列の前に空白があってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="ff071-227">The string must be at the beginning of a line, although it can be preceded by white space.</span></span> <span data-ttu-id="ff071-228">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-228">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 <span data-ttu-id="ff071-229">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-229">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-230">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-230">Pattern</span></span>|<span data-ttu-id="ff071-231">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-231">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="ff071-232">入力ストリームの先頭と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-232">Match the start of the input stream.</span></span>|  
|`\s*`|<span data-ttu-id="ff071-233">0 個以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-233">Match zero or more white-space characters.</span></span>|  
|`(System.)??`|<span data-ttu-id="ff071-234">文字列 "System." の 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-234">Match zero or one occurrence of the string "System.".</span></span>|  
|`Console.Write`|<span data-ttu-id="ff071-235">文字列 "Console.Write" と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-235">Match the string "Console.Write".</span></span>|  
|`(Line)??`|<span data-ttu-id="ff071-236">文字列 "Line" の 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-236">Match zero or one occurrence of the string "Line".</span></span>|  
|`\(??`|<span data-ttu-id="ff071-237">左かっこの 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-237">Match zero or one occurrence of the opening parenthesis.</span></span>|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a><span data-ttu-id="ff071-238">n 回の繰り返しに一致 (最短一致): {n}?</span><span class="sxs-lookup"><span data-stu-id="ff071-238">Match Exactly n Times (Lazy Match): {n}?</span></span>  
 <span data-ttu-id="ff071-239">`{`*n*`}?` 量指定子は、直前の要素の `n` 回の繰り返しに一致します。ここで、 *n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="ff071-239">The `{`*n*`}?` quantifier matches the preceding element exactly `n` times, where *n* is any integer.</span></span> <span data-ttu-id="ff071-240">これは、最長一致の量指定子 `{`*n*`}` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="ff071-240">It is the lazy counterpart of the greedy quantifier `{`*n*`}`.</span></span>  
  
 <span data-ttu-id="ff071-241">次の例では、正規表現 `\b(\w{3,}?\.){2}?\w{3,}?\b` を使用して Web サイトのアドレスを識別します。</span><span class="sxs-lookup"><span data-stu-id="ff071-241">In the following example, the regular expression `\b(\w{3,}?\.){2}?\w{3,}?\b` is used to identify a Web site address.</span></span> <span data-ttu-id="ff071-242">"www.microsoft.com" と "msdn.microsoft.com" には一致しますが、"mywebsite" や "mycompany.com" には一致しない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff071-242">Note that it matches "www.microsoft.com" and "msdn.microsoft.com", but does not match "mywebsite" or "mycompany.com".</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 <span data-ttu-id="ff071-243">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-243">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-244">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-244">Pattern</span></span>|<span data-ttu-id="ff071-245">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-245">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-246">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-246">Start at a word boundary.</span></span>|  
|`(\w{3,}?\.)`|<span data-ttu-id="ff071-247">単語に含まれる 3 個以上の文字のうち、最も少ない文字の後に、ドット (ピリオド) 文字が続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-247">Match at least 3 word characters, but as few characters as possible, followed by a dot or period character.</span></span> <span data-ttu-id="ff071-248">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="ff071-248">This is the first capturing group.</span></span>|  
|`(\w{3,}?\.){2}?`|<span data-ttu-id="ff071-249">最初のグループのパターンの 2 回の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-249">Match the pattern in the first group two times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="ff071-250">ワード境界で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="ff071-250">End the match on a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a><span data-ttu-id="ff071-251">n 回以上の繰り返しに一致 (最短一致): {n,}?</span><span class="sxs-lookup"><span data-stu-id="ff071-251">Match at Least n Times (Lazy Match): {n,}?</span></span>  
 <span data-ttu-id="ff071-252">`{`*n*`,}?` 量指定子は、直前の要素の `n` 回以上の繰り返しのうち、最も少ない繰り返しに一致します。ここで、 *n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="ff071-252">The `{`*n*`,}?` quantifier matches the preceding element at least `n` times, where *n* is any integer, but as few times as possible.</span></span> <span data-ttu-id="ff071-253">これは、最長一致の量指定子 `{`*n*`,}` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="ff071-253">It is the lazy counterpart of the greedy quantifier `{`*n*`,}`.</span></span>  
  
 <span data-ttu-id="ff071-254">`{`*n*`}?` 量指定子の例については、前のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff071-254">See the example for the `{`*n*`}?` quantifier in the previous section for an illustration.</span></span> <span data-ttu-id="ff071-255">この例の正規表現は、3 文字以上の後にピリオドが続く文字列に一致させるために `{`*n*`,}` 量指定子を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ff071-255">The regular expression in that example uses the `{`*n*`,}` quantifier to match a string that has at least three characters followed by a period.</span></span>  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a><span data-ttu-id="ff071-256">n 回から m 回までの繰り返しに一致 (最短一致): {n,m}?</span><span class="sxs-lookup"><span data-stu-id="ff071-256">Match Between n and m Times (Lazy Match): {n,m}?</span></span>  
 <span data-ttu-id="ff071-257">`{`*n*`,`*m*`}?` 量指定子は、直前の要素の `n` 回から `m` 回までの繰り返しのうち、最も少ない繰り返しに一致します。ここで、 *n* と *m* は整数です。</span><span class="sxs-lookup"><span data-stu-id="ff071-257">The `{`*n*`,`*m*`}?` quantifier matches the preceding element between `n` and `m` times, where *n* and *m* are integers, but as few times as possible.</span></span> <span data-ttu-id="ff071-258">これは、最長一致の量指定子 `{`*n*`,`*m*`}` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="ff071-258">It is the lazy counterpart of the greedy quantifier `{`*n*`,`*m*`}`.</span></span>  
  
 <span data-ttu-id="ff071-259">次の例では、正規表現 `\b[A-Z](\w*?\s*?){1,10}[.!?]` は、1 個以上 10 個以下の単語が含まれる文に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-259">In the following example, the regular expression `\b[A-Z](\w*?\s*?){1,10}[.!?]` matches sentences that contain between one and ten words.</span></span> <span data-ttu-id="ff071-260">18 個の単語が含まれている 1 つの文を除き、入力文字列中のすべての文に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-260">It matches all the sentences in the input string except for one sentence that contains 18 words.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 <span data-ttu-id="ff071-261">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-261">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-262">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-262">Pattern</span></span>|<span data-ttu-id="ff071-263">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-263">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ff071-264">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="ff071-264">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="ff071-265">A から Z の大文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-265">Match an uppercase character from A to Z.</span></span>|  
|`(\w*?\s*?)`|<span data-ttu-id="ff071-266">0 個以上の単語文字の後に 1 個以上の空白文字続くパターンのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-266">Match zero or more word characters, followed by one or more white-space characters, but as few times as possible.</span></span> <span data-ttu-id="ff071-267">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="ff071-267">This is the first capture group.</span></span>|  
|`{1,10}`|<span data-ttu-id="ff071-268">前のパターンの 1 回以上 10 回以下に一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-268">Match the previous pattern between 1 and 10 times.</span></span>|  
|`[.!?]`|<span data-ttu-id="ff071-269">区切り文字 "."、"!"、"?" のいずれか 1 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-269">Match any one of the punctuation characters ".", "!", or "?".</span></span>|  
  
<a name="Greedy"></a>
## <a name="greedy-and-lazy-quantifiers"></a><span data-ttu-id="ff071-270">最長一致と最短一致の量指定子</span><span class="sxs-lookup"><span data-stu-id="ff071-270">Greedy and Lazy Quantifiers</span></span>  
 <span data-ttu-id="ff071-271">いくつかの量指定子には次の 2 つのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="ff071-271">A number of the quantifiers have two versions:</span></span>  
  
- <span data-ttu-id="ff071-272">最長一致バージョン。</span><span class="sxs-lookup"><span data-stu-id="ff071-272">A greedy version.</span></span>  
  
     <span data-ttu-id="ff071-273">最長一致の量指定子は、要素をできるだけ多く一致させようとします。</span><span class="sxs-lookup"><span data-stu-id="ff071-273">A greedy quantifier tries to match an element as many times as possible.</span></span>  
  
- <span data-ttu-id="ff071-274">最短一致バージョン。</span><span class="sxs-lookup"><span data-stu-id="ff071-274">A non-greedy (or lazy) version.</span></span>  
  
     <span data-ttu-id="ff071-275">最短一致の量指定子は、要素をできるだけ少なく一致させようとします。</span><span class="sxs-lookup"><span data-stu-id="ff071-275">A non-greedy quantifier tries to match an element as few times as possible.</span></span> <span data-ttu-id="ff071-276">最長一致の量指定子に `?` を追加するだけで最短一致の量指定子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ff071-276">You can turn a greedy quantifier into a lazy quantifier by simply adding a `?`.</span></span>  
  
 <span data-ttu-id="ff071-277">クレジット カード番号などの数値の列から最後の 4 桁の数字を取り出す、単純な正規表現について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ff071-277">Consider a simple regular expression that is intended to extract the last four digits from a string of numbers such as a credit card number.</span></span> <span data-ttu-id="ff071-278">最長一致の `*` 量指定子を使用するバージョンの正規表現は、`\b.*([0-9]{4})\b` です。</span><span class="sxs-lookup"><span data-stu-id="ff071-278">The version of the regular expression that uses the `*` greedy quantifier is `\b.*([0-9]{4})\b`.</span></span> <span data-ttu-id="ff071-279">しかし、2 個の数値が含まれている文字列の場合、この正規表現は、次の例に示すように 2 番目の数値の最後の 4 桁の数字だけに一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-279">However, if a string contains two numbers, this regular expression matches the last four digits of the second number only, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 <span data-ttu-id="ff071-280">この正規表現は最初の数値の一致に失敗します。`*` 量指定子では、直前の要素をできるだけ多く繰り返して文字列全体に一致させようとして、文字列の最後まで一致と見なされるためです。</span><span class="sxs-lookup"><span data-stu-id="ff071-280">The regular expression fails to match the first number because the `*` quantifier tries to match the previous element as many times as possible in the entire string, and so it finds its match at the end of the string.</span></span>  
  
 <span data-ttu-id="ff071-281">これは期待した動作ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff071-281">This is not the desired behavior.</span></span> <span data-ttu-id="ff071-282">代わりに `*?` 最短一致の量指定子を使用すると、次の例のように両方の数値から数字を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="ff071-282">Instead, you can use the `*?`lazy quantifier to extract digits from both numbers, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 <span data-ttu-id="ff071-283">多くの場合、最長一致と最短一致の量指定子を使用した正規表現は、同じ一致結果を返します。</span><span class="sxs-lookup"><span data-stu-id="ff071-283">In most cases, regular expressions with greedy and lazy quantifiers return the same matches.</span></span> <span data-ttu-id="ff071-284">異なる結果を返すことが最も多いのは、任意の文字に一致するワイルドカード (`.`) のメタ文字を使用した場合です。</span><span class="sxs-lookup"><span data-stu-id="ff071-284">They most commonly return different results when they are used with the wildcard (`.`) metacharacter, which matches any character.</span></span>  
  
## <a name="quantifiers-and-empty-matches"></a><span data-ttu-id="ff071-285">量指定子と空一致</span><span class="sxs-lookup"><span data-stu-id="ff071-285">Quantifiers and Empty Matches</span></span>  
 <span data-ttu-id="ff071-286">量指定子 `*`、`+`、および `{`*n*`,`*m*`}` と、これらに対応する最短一致の量指定子は、最小回数のキャプチャが見つかった場合、空一致の後には繰り返されません。</span><span class="sxs-lookup"><span data-stu-id="ff071-286">The quantifiers `*`, `+`, and `{`*n*`,`*m*`}` and their lazy counterparts never repeat after an empty match when the minimum number of captures has been found.</span></span> <span data-ttu-id="ff071-287">この規則により、可能なグループ キャプチャの最大回数が無限またはほぼ無限のときに、量指定子が空の部分式一致の無限ループに入ることを回避できます。</span><span class="sxs-lookup"><span data-stu-id="ff071-287">This rule prevents quantifiers from entering infinite loops on empty subexpression matches when the maximum number of possible group captures is infinite or near infinite.</span></span>  
  
 <span data-ttu-id="ff071-288">たとえば、次のコードは、0 個または 1 個の文字 "a" と 0 回以上一致する正規表現パターン `(a?)*` を指定して <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> メソッドを呼び出した結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="ff071-288">For example, the following code shows the result of a call to the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> method with the regular expression pattern `(a?)*`, which matches zero or one "a" character zero or more times.</span></span> <span data-ttu-id="ff071-289">単一のキャプチャ グループによって各 "a" と <xref:System.String.Empty?displayProperty=nameWithType> がキャプチャされますが、2 番目の空一致はないことに注意してください。これは、最初の空一致により量指定子が繰り返しを停止するためです。</span><span class="sxs-lookup"><span data-stu-id="ff071-289">Note that the single capturing group captures each "a" as well as <xref:System.String.Empty?displayProperty=nameWithType>, but that there is no second empty match, because the first empty match causes the quantifier to stop repeating.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 <span data-ttu-id="ff071-290">最小回数と最大回数のキャプチャを定義するキャプチャ グループと固定回数のキャプチャを定義するキャプチャ グループとの間の実際の違いを確認するために、正規表現パターンの `(a\1|(?(1)\1)){0,2}` と `(a\1|(?(1)\1)){2}` について検討します。</span><span class="sxs-lookup"><span data-stu-id="ff071-290">To see the practical difference between a capturing group that defines a minimum and a maximum number of captures and one that defines a fixed number of captures, consider the regular expression patterns `(a\1|(?(1)\1)){0,2}` and `(a\1|(?(1)\1)){2}`.</span></span> <span data-ttu-id="ff071-291">どちらの正規表現も、次の表に示すように定義される単一のキャプチャ グループで構成されています。</span><span class="sxs-lookup"><span data-stu-id="ff071-291">Both regular expressions consist of a single capturing group, which is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="ff071-292">パターン</span><span class="sxs-lookup"><span data-stu-id="ff071-292">Pattern</span></span>|<span data-ttu-id="ff071-293">説明</span><span class="sxs-lookup"><span data-stu-id="ff071-293">Description</span></span>|  
|-------------|-----------------|  
|`(a\1`|<span data-ttu-id="ff071-294">"a" と最初のキャプチャ グループの値に一致します …</span><span class="sxs-lookup"><span data-stu-id="ff071-294">Either match "a" along with the value of the first captured group …</span></span>|  
|<code>&#124;(?(1)</code>|<span data-ttu-id="ff071-295">…</span><span class="sxs-lookup"><span data-stu-id="ff071-295">…</span></span> <span data-ttu-id="ff071-296">または、最初のキャプチャ グループが定義されているかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="ff071-296">or test whether the first captured group has been defined.</span></span> <span data-ttu-id="ff071-297">(`(?(1)` コンストラクトではキャプチャ グループは定義されないことに注意してください。)</span><span class="sxs-lookup"><span data-stu-id="ff071-297">(Note that the `(?(1)` construct does not define a capturing group.)</span></span>|  
|`\1))`|<span data-ttu-id="ff071-298">最初のキャプチャ グループが存在する場合、その値と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-298">If the first captured group exists, match its value.</span></span> <span data-ttu-id="ff071-299">グループが存在しない場合、そのグループは <xref:System.String.Empty?displayProperty=nameWithType> と一致します。</span><span class="sxs-lookup"><span data-stu-id="ff071-299">If the group does not exist, the group will match <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|  
  
 <span data-ttu-id="ff071-300">最初の正規表現では 0 ～ 2 回、このパターンとの照合が行われます。2 番目の正規表現では、厳密に 2 回です。</span><span class="sxs-lookup"><span data-stu-id="ff071-300">The first regular expression tries to match this pattern between zero and two times; the second, exactly two times.</span></span> <span data-ttu-id="ff071-301">最初のパターンは <xref:System.String.Empty?displayProperty=nameWithType> の最初のキャプチャでキャプチャの最小回数に達するため、`a\1` との照合は繰り返されません。`{0,2}` 量指定子では、最後の繰り返しでの空一致だけが許可されます。</span><span class="sxs-lookup"><span data-stu-id="ff071-301">Because the first pattern reaches its minimum number of captures with its first capture of <xref:System.String.Empty?displayProperty=nameWithType>, it never repeats to try to match `a\1`; the `{0,2}` quantifier allows only empty matches in the last iteration.</span></span> <span data-ttu-id="ff071-302">一方、2 番目の正規表現では、2 回目の `a\1` が評価されるため、"a" に一致します。繰り返しの最小回数は 2 で、空一致の後でエンジンが繰り返さなければならない回数になります。</span><span class="sxs-lookup"><span data-stu-id="ff071-302">In contrast, the second regular expression does match "a" because it evaluates `a\1` a second time; the minimum number of iterations, 2, forces the engine to repeat after an empty match.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ff071-303">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff071-303">See also</span></span>

- [<span data-ttu-id="ff071-304">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="ff071-304">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
- [<span data-ttu-id="ff071-305">バックトラッキング</span><span class="sxs-lookup"><span data-stu-id="ff071-305">Backtracking</span></span>](backtracking-in-regular-expressions.md)
