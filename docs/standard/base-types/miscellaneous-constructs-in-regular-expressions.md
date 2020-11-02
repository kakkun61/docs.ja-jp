---
title: 正規表現でのその他の構成体
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- constructs, miscellaneous
- .NET regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
ms.openlocfilehash: f7800dee67513f885339fad67c7a999cc06cca36
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889271"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a><span data-ttu-id="a354e-102">正規表現でのその他の構成体</span><span class="sxs-lookup"><span data-stu-id="a354e-102">Miscellaneous Constructs in Regular Expressions</span></span>
<span data-ttu-id="a354e-103">.NET の正規表現には、次の 3 つのその他の言語コンストラクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a354e-103">Regular expressions in .NET include three miscellaneous language constructs.</span></span> <span data-ttu-id="a354e-104">1 つは、正規表現パターンの途中で特定の一致オプションを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a354e-104">One lets you enable or disable particular matching options in the middle of a regular expression pattern.</span></span> <span data-ttu-id="a354e-105">残りの 2 つは、正規表現にコメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a354e-105">The remaining two let you include comments in a regular expression.</span></span>  
  
## <a name="inline-options"></a><span data-ttu-id="a354e-106">インライン オプション</span><span class="sxs-lookup"><span data-stu-id="a354e-106">Inline Options</span></span>  
 <span data-ttu-id="a354e-107">この構文を使用して、正規表現の一部の特定のパターン一致オプションを設定または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a354e-107">You can set or disable specific pattern matching options for part of a regular expression by using the syntax</span></span>  
  
`(?imnsx-imnsx)`  
  
 <span data-ttu-id="a354e-108">疑問符の後に有効にするオプション、マイナス記号の後に無効にするオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a354e-108">You list the options you want to enable after the question mark, and the options you want to disable after the minus sign.</span></span> <span data-ttu-id="a354e-109">各オプションの説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a354e-109">The following table describes each option.</span></span> <span data-ttu-id="a354e-110">各オプションの詳細については、「[正規表現のオプション](regular-expression-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a354e-110">For more information about each option, see [Regular Expression Options](regular-expression-options.md).</span></span>  
  
|<span data-ttu-id="a354e-111">オプション</span><span class="sxs-lookup"><span data-stu-id="a354e-111">Option</span></span>|<span data-ttu-id="a354e-112">説明</span><span class="sxs-lookup"><span data-stu-id="a354e-112">Description</span></span>|  
|------------|-----------------|  
|`i`|<span data-ttu-id="a354e-113">大文字と小文字を区別しない一致。</span><span class="sxs-lookup"><span data-stu-id="a354e-113">Case-insensitive matching.</span></span>|  
|`m`|<span data-ttu-id="a354e-114">複数行モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a354e-114">Multiline mode.</span></span>|  
|`n`|<span data-ttu-id="a354e-115">明示的なキャプチャのみ</span><span class="sxs-lookup"><span data-stu-id="a354e-115">Explicit captures only.</span></span> <span data-ttu-id="a354e-116">(かっこはキャプチャ グループとして機能しません)。</span><span class="sxs-lookup"><span data-stu-id="a354e-116">(Parentheses do not act as capturing groups.)</span></span>|  
|`s`|<span data-ttu-id="a354e-117">単一行モード。</span><span class="sxs-lookup"><span data-stu-id="a354e-117">Single-line mode.</span></span>|  
|`x`|<span data-ttu-id="a354e-118">エスケープされていない空白を無視し、x モード コメントを許可します。</span><span class="sxs-lookup"><span data-stu-id="a354e-118">Ignore unescaped white space, and allow x-mode comments.</span></span>|  
  
 <span data-ttu-id="a354e-119">`(?imnsx-imnsx)` コンストラクトによって定義された正規表現オプションの変更は、囲んでいるグループの末尾まで有効です。</span><span class="sxs-lookup"><span data-stu-id="a354e-119">Any change in regular expression options defined by the `(?imnsx-imnsx)` construct remains in effect until the end of the enclosing group.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a354e-120">`(?imnsx-imnsx:`*subexpression*`)` グループ化コンストラクトは、部分式と同じ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="a354e-120">The `(?imnsx-imnsx:`*subexpression*`)` grouping construct provides identical functionality for a subexpression.</span></span> <span data-ttu-id="a354e-121">詳細については、「 [グループ化構成体](grouping-constructs-in-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a354e-121">For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="a354e-122">次の例では `i`、`n`、`x` オプションを使用して、大文字と小文字の区別をせず、明示的なキャプチャを有効にして、正規表現の途中の正規表現パターン内の空白を無視します。</span><span class="sxs-lookup"><span data-stu-id="a354e-122">The following example uses the `i`, `n`, and `x` options to enable case insensitivity and explicit captures, and to ignore white space in the regular expression pattern in the middle of a regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 <span data-ttu-id="a354e-123">この例では、2 つの正規表現を定義しています。</span><span class="sxs-lookup"><span data-stu-id="a354e-123">The example defines two regular expressions.</span></span> <span data-ttu-id="a354e-124">最初の `\b(D\w+)\s(d\w+)\b` は、大文字の "D" と小文字の "d" で始まる 2 つの連続した単語に一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-124">The first, `\b(D\w+)\s(d\w+)\b`, matches two consecutive words that begin with an uppercase "D" and a lowercase "d".</span></span> <span data-ttu-id="a354e-125">2 つ目の正規表現 `\b(D\w+)(?ixn) \s (d\w+) \b` は、次の表に示すように、インライン オプションを使用して、このパターンを変更します。</span><span class="sxs-lookup"><span data-stu-id="a354e-125">The second regular expression, `\b(D\w+)(?ixn) \s (d\w+) \b`, uses inline options to modify this pattern, as described in the following table.</span></span> <span data-ttu-id="a354e-126">結果の比較で、`(?ixn)` コンストラクトの効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="a354e-126">A comparison of the results confirms the effect of the `(?ixn)` construct.</span></span>  
  
|<span data-ttu-id="a354e-127">パターン</span><span class="sxs-lookup"><span data-stu-id="a354e-127">Pattern</span></span>|<span data-ttu-id="a354e-128">説明</span><span class="sxs-lookup"><span data-stu-id="a354e-128">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a354e-129">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="a354e-129">Start at a word boundary.</span></span>|  
|`(D\w+)`|<span data-ttu-id="a354e-130">大文字 "D" の後に 1 つ以上の単語の文字が続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-130">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="a354e-131">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="a354e-131">This is the first capture group.</span></span>|  
|`(?ixn)`|<span data-ttu-id="a354e-132">この時点から、大文字と小文字を区別しない比較を行い、明示的なキャプチャのみを行って、正規表現パターン内の空白を無視します。</span><span class="sxs-lookup"><span data-stu-id="a354e-132">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`\s`|<span data-ttu-id="a354e-133">空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-133">Match a white-space character.</span></span>|  
|`(d\w+)`|<span data-ttu-id="a354e-134">大文字または小文字 "d" の後に 1 つ以上の単語の文字が続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-134">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="a354e-135">`n` (明示的なキャプチャ) オプションが有効になっているため、このグループはキャプチャされません。</span><span class="sxs-lookup"><span data-stu-id="a354e-135">This group is not captured because the `n` (explicit capture) option was enabled..</span></span>|  
|`\b`|<span data-ttu-id="a354e-136">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-136">Match a word boundary.</span></span>|  
  
## <a name="inline-comment"></a><span data-ttu-id="a354e-137">インライン コメント</span><span class="sxs-lookup"><span data-stu-id="a354e-137">Inline Comment</span></span>  
 <span data-ttu-id="a354e-138">`(?#` *comment*`)` コンストラクトを使用して、正規表現にインライン コメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a354e-138">The `(?#` *comment*`)` construct lets you include an inline comment in a regular expression.</span></span> <span data-ttu-id="a354e-139"><xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> メソッドによって返される文字列にコメントが含まれますが、正規表現エンジンは、パターン マッチングでコメントのどの部分も使用しません。</span><span class="sxs-lookup"><span data-stu-id="a354e-139">The regular expression engine does not use any part of the comment in pattern matching, although the comment is included in the string that is returned by the <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a354e-140">コメントは、最初の閉じかっこで終了します。</span><span class="sxs-lookup"><span data-stu-id="a354e-140">The comment ends at the first closing parenthesis.</span></span>  
  
 <span data-ttu-id="a354e-141">次の例では、前のセクションの例の最初の正規表現パターンを繰り返しています。</span><span class="sxs-lookup"><span data-stu-id="a354e-141">The following example repeats the first regular expression pattern from the example in the previous section.</span></span> <span data-ttu-id="a354e-142">比較で大文字小文字を区別するかどうかを示す 2 つのインライン コメントを正規表現に追加しています。</span><span class="sxs-lookup"><span data-stu-id="a354e-142">It adds two inline comments to the regular expression to indicate whether the comparison is case-sensitive.</span></span> <span data-ttu-id="a354e-143">正規表現パターン `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b` は、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="a354e-143">The regular expression pattern, `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, is defined as follows.</span></span>  
  
|<span data-ttu-id="a354e-144">パターン</span><span class="sxs-lookup"><span data-stu-id="a354e-144">Pattern</span></span>|<span data-ttu-id="a354e-145">説明</span><span class="sxs-lookup"><span data-stu-id="a354e-145">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a354e-146">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="a354e-146">Start at a word boundary.</span></span>|  
|`(?# case-sensitive comparison)`|<span data-ttu-id="a354e-147">コメント。</span><span class="sxs-lookup"><span data-stu-id="a354e-147">A comment.</span></span> <span data-ttu-id="a354e-148">これは、パターンマッチング動作に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="a354e-148">It does not affect pattern-matching behavior.</span></span>|  
|`(D\w+)`|<span data-ttu-id="a354e-149">大文字 "D" の後に 1 つ以上の単語の文字が続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-149">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="a354e-150">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="a354e-150">This is the first capturing group.</span></span>|  
|`\s`|<span data-ttu-id="a354e-151">空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-151">Match a white-space character.</span></span>|  
|`(?ixn)`|<span data-ttu-id="a354e-152">この時点から、大文字と小文字を区別しない比較を行い、明示的なキャプチャのみを行って、正規表現パターン内の空白を無視します。</span><span class="sxs-lookup"><span data-stu-id="a354e-152">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`(?#case-insensitive comparison)`|<span data-ttu-id="a354e-153">コメント。</span><span class="sxs-lookup"><span data-stu-id="a354e-153">A comment.</span></span> <span data-ttu-id="a354e-154">これは、パターンマッチング動作に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="a354e-154">It does not affect pattern-matching behavior.</span></span>|  
|`(d\w+)`|<span data-ttu-id="a354e-155">大文字または小文字 "d" の後に 1 つ以上の単語の文字が続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-155">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="a354e-156">これが 2 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="a354e-156">This is the second capture group.</span></span>|  
|`\b`|<span data-ttu-id="a354e-157">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-157">Match a word boundary.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a><span data-ttu-id="a354e-158">行末のコメント</span><span class="sxs-lookup"><span data-stu-id="a354e-158">End-of-Line Comment</span></span>  
 <span data-ttu-id="a354e-159">シャープ記号 (`#`) は、正規表現パターンの末尾のエスケープ解除された # 文字から始まり、行の末尾まで続く x モード コメントをマークします。</span><span class="sxs-lookup"><span data-stu-id="a354e-159">A number sign (`#`)marks an x-mode comment, which starts at the unescaped # character at the end of the regular expression pattern and continues until the end of the line.</span></span> <span data-ttu-id="a354e-160">このコンストラクトを使用するには、<xref:System.Text.RegularExpressions.Regex> オブジェクトをインスタンス化したり、静的 <xref:System.Text.RegularExpressions.Regex> メソッドを呼び出したりする際に、`x` オプションを有効にする (インライン オプションによって) か、または `option` パラメーターに <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> 値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a354e-160">To use this construct, you must either enable the `x` option (through inline options) or supply the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> value to the `option` parameter when instantiating the <xref:System.Text.RegularExpressions.Regex> object or calling a static <xref:System.Text.RegularExpressions.Regex> method.</span></span>  
  
 <span data-ttu-id="a354e-161">次の例は、行末のコメント コンストラクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="a354e-161">The following example illustrates the end-of-line comment construct.</span></span> <span data-ttu-id="a354e-162">これは、1 つ以上の書式指定項目を含む複合書式文字列かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="a354e-162">It determines whether a string is a composite format string that includes at least one format item.</span></span> <span data-ttu-id="a354e-163">次の表に、正規表現パターン内のコンストラクトを説明しています。</span><span class="sxs-lookup"><span data-stu-id="a354e-163">The following table describes the constructs in the regular expression pattern:</span></span>  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|<span data-ttu-id="a354e-164">パターン</span><span class="sxs-lookup"><span data-stu-id="a354e-164">Pattern</span></span>|<span data-ttu-id="a354e-165">説明</span><span class="sxs-lookup"><span data-stu-id="a354e-165">Description</span></span>|  
|-------------|-----------------|  
|`\{`|<span data-ttu-id="a354e-166">左中かっこと一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-166">Match an opening brace.</span></span>|  
|`\d+`|<span data-ttu-id="a354e-167">1 個以上の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-167">Match one or more decimal digits.</span></span>|  
|`(,-*\d+)*`|<span data-ttu-id="a354e-168">0 個または 1 つのコンマの後にオプションのマイナス記号が続き、その後に 1 つ以上の 10 進数が続くパターンと一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-168">Match zero or one occurrence of a comma, followed by an optional minus sign, followed by one or more decimal digits.</span></span>|  
|`(\:\w{1,4}?)*`|<span data-ttu-id="a354e-169">0 個または 1 つのコロンの後に 1 ～ 4 個の、ただし可能な限り少ない空白文字が続くパターンと一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-169">Match zero or one occurrence of a colon, followed by one to four, but as few as possible, white-space characters.</span></span>|  
|`\}`|<span data-ttu-id="a354e-170">右中かっこと一致します。</span><span class="sxs-lookup"><span data-stu-id="a354e-170">Match a closing brace.</span></span>|  
|`(?x)`|<span data-ttu-id="a354e-171">行末のコメントが認識されるように、パターンの空白を無視するオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a354e-171">Enable the ignore pattern white-space option so that the end-of-line comment will be recognized.</span></span>|  
|`# Looks for a composite format item.`|<span data-ttu-id="a354e-172">行末のコメント。</span><span class="sxs-lookup"><span data-stu-id="a354e-172">An end-of-line comment.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 <span data-ttu-id="a354e-173">正規表現で `(?x)` コンストラクトを指定する代わりに、<xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> メソッドを呼び出し、それに <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> 列挙値を渡して、コメントを認識させることもできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a354e-173">Note that, instead of providing the `(?x)` construct in the regular expression, the comment could also have been recognized by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method and passing it the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> enumeration value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a354e-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="a354e-174">See also</span></span>

- [<span data-ttu-id="a354e-175">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="a354e-175">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
