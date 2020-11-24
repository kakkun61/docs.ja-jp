---
title: .NET 正規表現での前方参照コンストラクト
description: 正規表現の中で前方参照構成体を使用して、繰り返されるテキスト要素を識別する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
ms.openlocfilehash: 79702f266e7233c96fef6b6aa32a7e756589f49c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825261"
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="6ef2f-103">正規表現での前方参照コンストラクト</span><span class="sxs-lookup"><span data-stu-id="6ef2f-103">Backreference Constructs in Regular Expressions</span></span>

<span data-ttu-id="6ef2f-104">前方参照は、文字列内の繰り返しの文字または部分文字列を識別するために便利な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-104">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="6ef2f-105">たとえば、入力文字列に複数回出現する任意の部分文字列が含まれている場合は、キャプチャ グループを使用して最初の一致を検出し、前方参照を使用して部分文字列の後続の出現箇所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-105">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>

> [!NOTE]
> <span data-ttu-id="6ef2f-106">別の構文を使用して、置換文字列内の名前付きおよび番号付きのキャプチャ グループを参照します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-106">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="6ef2f-107">詳細については、「 [置換](substitutions-in-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-107">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>

<span data-ttu-id="6ef2f-108">.NET では、番号付きおよび名前付きのキャプチャ グループを参照する個別の言語要素が定義されています。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-108">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="6ef2f-109">キャプチャ グループの詳細については、「[グループ化コンストラクト](grouping-constructs-in-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-109">For more information about capturing groups, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).</span></span>

## <a name="numbered-backreferences"></a><span data-ttu-id="6ef2f-110">番号付き前方参照</span><span class="sxs-lookup"><span data-stu-id="6ef2f-110">Numbered Backreferences</span></span>

<span data-ttu-id="6ef2f-111">番号付き前方参照は、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-111">A numbered backreference uses the following syntax:</span></span>

<span data-ttu-id="6ef2f-112">`\` *number*</span><span class="sxs-lookup"><span data-stu-id="6ef2f-112">`\` *number*</span></span>

<span data-ttu-id="6ef2f-113">ここで、*number* は、正規表現でのキャプチャ グループの位置を表す序数です。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-113">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="6ef2f-114">たとえば、`\4` は 4 番目のキャプチャ グループの内容と一致します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-114">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="6ef2f-115">*number* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンが <xref:System.ArgumentException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-115">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="6ef2f-116">たとえば、正規表現 `\b(\w+)\s\1` は有効です (`(\w+)` が式の中の最初で唯一のキャプチャ グループであるため)。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-116">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="6ef2f-117">これに対して、`\b(\w+)\s\2` は無効であり、引数の例外がスローされます (`\2` という番号のキャプチャ グループは存在しないため)。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-117">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span> <span data-ttu-id="6ef2f-118">さらに、*number* が特定の序数位置のキャプチャ グループを示していても、そのキャプチャ グループにその序数位置とは異なる数値名が割り当てられている場合、正規表現パーサーで <xref:System.ArgumentException> もスローされます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-118">In addition, if *number* identifies a capturing group in a particular ordinal position, but that capturing group has been assigned a numeric name different than its ordinal position, the regular expression parser also throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="6ef2f-119">同じ表記法を使用した、8 進数のエスケープ コード (`\16` など) と `\`*number* 前方参照との間には、あいまいさがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-119">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="6ef2f-120">このあいまいさは、次のように解決されます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-120">This ambiguity is resolved as follows:</span></span>

- <span data-ttu-id="6ef2f-121">`\1` から `\9` までの式は、8 進数コードとしてではなく、常に前方参照として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-121">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>

- <span data-ttu-id="6ef2f-122">複数桁の式の最初の桁が 8 または 9 (`\80`や `\91`) の場合、式はリテラルとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-122">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>

- <span data-ttu-id="6ef2f-123">`\10` 以降の式は、その番号に対応する前方参照がある場合、前方参照として解釈されます。それ以外の場合は、8 進数のコードとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-123">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>

- <span data-ttu-id="6ef2f-124">正規表現に未定義のグループ番号への前方参照が含まれる場合、解析エラーが発生し、正規表現エンジンが <xref:System.ArgumentException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-124">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="6ef2f-125">あいまいさが問題になる場合は、`\k<`*name*`>` という表記を使用できます。この表記はあいまいではなく、8 進数の文字コードと混同することはありません。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-125">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="6ef2f-126">同様に、`\xdd` などの 16 進数コードはあいまいではなく、前方参照と混同することはありません。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-126">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>

<span data-ttu-id="6ef2f-127">次の例では、文字列内の単語に使用される重複した文字を検索します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-127">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="6ef2f-128">例で定義している正規表現 `(\w)\1` は、次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-128">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>

|<span data-ttu-id="6ef2f-129">要素</span><span class="sxs-lookup"><span data-stu-id="6ef2f-129">Element</span></span>|<span data-ttu-id="6ef2f-130">[説明]</span><span class="sxs-lookup"><span data-stu-id="6ef2f-130">Description</span></span>|
|-------------|-----------------|
|`(\w)`|<span data-ttu-id="6ef2f-131">単語文字を検出し、最初のキャプチャ グループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-131">Match a word character and assign it to the first capturing group.</span></span>|
|`\1`|<span data-ttu-id="6ef2f-132">最初のキャプチャ グループの値と同じ次の文字を検出します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-132">Match the next character that is the same as the value of the first capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a><span data-ttu-id="6ef2f-133">名前付き前方参照</span><span class="sxs-lookup"><span data-stu-id="6ef2f-133">Named Backreferences</span></span>

<span data-ttu-id="6ef2f-134">名前付き前方参照は、次の構文を使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-134">A named backreference is defined by using the following syntax:</span></span>

<span data-ttu-id="6ef2f-135">`\k<` *name* `>`</span><span class="sxs-lookup"><span data-stu-id="6ef2f-135">`\k<` *name* `>`</span></span>

<span data-ttu-id="6ef2f-136">または</span><span class="sxs-lookup"><span data-stu-id="6ef2f-136">or:</span></span>

<span data-ttu-id="6ef2f-137">`\k'` *name* `'`</span><span class="sxs-lookup"><span data-stu-id="6ef2f-137">`\k'` *name* `'`</span></span>

<span data-ttu-id="6ef2f-138">ここで、*name* は正規表現パターンで定義されたキャプチャ グループの名前です。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-138">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="6ef2f-139">*name* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンが <xref:System.ArgumentException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-139">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="6ef2f-140">次の例では、文字列内の単語に使用される重複した文字を検索します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-140">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="6ef2f-141">例で定義している正規表現 `(?<char>\w)\k<char>` は、次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-141">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>

|<span data-ttu-id="6ef2f-142">要素</span><span class="sxs-lookup"><span data-stu-id="6ef2f-142">Element</span></span>|<span data-ttu-id="6ef2f-143">[説明]</span><span class="sxs-lookup"><span data-stu-id="6ef2f-143">Description</span></span>|
|-------------|-----------------|
|`(?<char>\w)`|<span data-ttu-id="6ef2f-144">単語文字を検出し、`char` という名前のキャプチャ グループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-144">Match a word character and assign it to a capturing group named `char`.</span></span>|
|`\k<char>`|<span data-ttu-id="6ef2f-145">`char` キャプチャ グループの値と同じ次の文字を検出します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-145">Match the next character that is the same as the value of the `char` capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a><span data-ttu-id="6ef2f-146">名前付き数値前方参照</span><span class="sxs-lookup"><span data-stu-id="6ef2f-146">Named numeric backreferences</span></span>

<span data-ttu-id="6ef2f-147">`\k` を使用する名前付き前方参照の場合、*name* は数字の文字列表現にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-147">In a named backreference with `\k`, *name* can also be the string representation of a number.</span></span> <span data-ttu-id="6ef2f-148">たとえば、次の例では正規表現 `(?<2>\w)\k<2>` を使用して、文字列内の単語の重複した文字を検索します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-148">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span> <span data-ttu-id="6ef2f-149">この例では、明示的に "2" という名前が付けられたキャプチャ グループを定義し、これに応じて、前方参照には "2" という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-149">In this case, the example defines a capturing group that is explicitly named "2", and the backreference is correspondingly named "2".</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

<span data-ttu-id="6ef2f-150">*name* が数字の文字列表現で、その名前を持つキャプチャ グループが存在しない場合、`\k<`*name*`>` は前方参照 `\`*number* と同じになります。ここで、*number* はキャプチャの序数位置です。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-150">If *name* is the string representation of a number, and no capturing group has that name, `\k<`*name*`>` is the same as the backreference `\`*number*, where *number* is the ordinal position of the capture.</span></span> <span data-ttu-id="6ef2f-151">次の例には、`char` という名前の単一のキャプチャ グループがあります。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-151">In the following example, there is a single capturing group named `char`.</span></span> <span data-ttu-id="6ef2f-152">前方参照構成体ではこれを `\k<1>` と呼びます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-152">The backreference construct refers to it as `\k<1>`.</span></span> <span data-ttu-id="6ef2f-153">例からの出力に示されているように、`char` は最初のキャプチャ グループであるため、<xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> の呼び出しは正常に行われています。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-153">As the output from the example shows, the call to the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> succeeds because `char` is the first capturing group.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

<span data-ttu-id="6ef2f-154">ただし、*name* が数字の文字列表現であり、その位置のキャプチャ グループに数値名が明示的に割り当てられている場合、正規表現パーサーではその序数位置でキャプチャ グループを識別することはできません。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-154">However, if *name* is the string representation of a number and the capturing group in that position has been explicitly assigned a numeric name, the regular expression parser cannot identify the capturing group by its ordinal position.</span></span> <span data-ttu-id="6ef2f-155">代わりに、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-155">Instead, it throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="6ef2f-156">次の例の唯一のキャプチャ グループには "2" という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-156">The only capturing group in the following example is named "2".</span></span> <span data-ttu-id="6ef2f-157">`\k` コンストラクトが "1" という名前の前方参照を定義するために使用されているため、正規表現パーサーは最初のキャプチャ グループを識別できず、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-157">Because the `\k` construct is used to define a backreference named "1", the regular expression parser is unable to identify the first capturing group and throws an exception.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a><span data-ttu-id="6ef2f-158">前方参照と一致する内容</span><span class="sxs-lookup"><span data-stu-id="6ef2f-158">What Backreferences Match</span></span>

<span data-ttu-id="6ef2f-159">前方参照は、グループの最新の定義 (左から右に検出する場合は、すぐ左にある定義) を参照します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-159">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="6ef2f-160">1 つのグループで複数のキャプチャが発生した場合、前方参照は最新のキャプチャを参照します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-160">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>

<span data-ttu-id="6ef2f-161">次の例には、正規表現パターン `(?<1>a)(?<1>\1b)*` が含まれています。このパターンは \1 の名前付きグループを再定義します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-161">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="6ef2f-162">正規表現の各パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-162">The following table describes each pattern in the regular expression.</span></span>

|<span data-ttu-id="6ef2f-163">パターン</span><span class="sxs-lookup"><span data-stu-id="6ef2f-163">Pattern</span></span>|<span data-ttu-id="6ef2f-164">[説明]</span><span class="sxs-lookup"><span data-stu-id="6ef2f-164">Description</span></span>|
|-------------|-----------------|
|`(?<1>a)`|<span data-ttu-id="6ef2f-165">文字 "a" を検出し、結果を `1` という名前のキャプチャ グループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-165">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|
|`(?<1>\1b)*`|<span data-ttu-id="6ef2f-166">`1` という名前のグループの 0 個以上の出現箇所を "b" と共に検出し、結果を `1` という名前のキャプチャ グループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-166">Match zero or more occurrences of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

<span data-ttu-id="6ef2f-167">正規表現を入力文字列 ("aababb") と比較する際、正規表現エンジンは次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-167">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>

1. <span data-ttu-id="6ef2f-168">文字列の先頭から開始し、式 `(?<1>a)` で "a" を検出します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-168">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="6ef2f-169">グループ `1` の値が "a" になります。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-169">The value of the `1` group is now "a".</span></span>

2. <span data-ttu-id="6ef2f-170">次の文字に進み、式 `\1b` で文字列 "ab" を検出します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-170">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="6ef2f-171">次に、その結果 "ab" を `\1` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-171">It then assigns the result, "ab" to `\1`.</span></span>

3. <span data-ttu-id="6ef2f-172">これにより 4 番目の文字に進みます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-172">It advances to the fourth character.</span></span> <span data-ttu-id="6ef2f-173">式 `(?<1>\1b)*` を 0 回以上照合し、式 `\1b` で文字列 "abb" を検出します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-173">The expression `(?<1>\1b)*` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="6ef2f-174">その結果 "abb" を `\1` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-174">It assigns the result, "abb", back to `\1`.</span></span>

<span data-ttu-id="6ef2f-175">この例では、`*` はループ量指定子であり、正規表現エンジンが定義したパターンを照合できなくなるまで、繰り返し評価されます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-175">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="6ef2f-176">ループ量指定子によってグループの定義はクリアされません。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-176">Looping quantifiers do not clear group definitions.</span></span>

<span data-ttu-id="6ef2f-177">グループで部分文字列がキャプチャされなかった場合、そのグループへの前方参照は未定義になり、一致することはありません。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-177">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="6ef2f-178">次のように定義されている正規表現パターン `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` を例として示します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-178">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>

|<span data-ttu-id="6ef2f-179">パターン</span><span class="sxs-lookup"><span data-stu-id="6ef2f-179">Pattern</span></span>|<span data-ttu-id="6ef2f-180">[説明]</span><span class="sxs-lookup"><span data-stu-id="6ef2f-180">Description</span></span>|
|-------------|-----------------|
|`\b`|<span data-ttu-id="6ef2f-181">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-181">Begin the match on a word boundary.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="6ef2f-182">2 つの大文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-182">Match two uppercase letters.</span></span> <span data-ttu-id="6ef2f-183">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-183">This is the first capturing group.</span></span>|
|`(\d{2})?`|<span data-ttu-id="6ef2f-184">2 桁の 10 進数の 0 回または 1 回の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-184">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="6ef2f-185">これが 2 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-185">This is the second capturing group.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="6ef2f-186">2 つの大文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-186">Match two uppercase letters.</span></span> <span data-ttu-id="6ef2f-187">これが 3 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-187">This is the third capturing group.</span></span>|
|`\b`|<span data-ttu-id="6ef2f-188">ワード境界で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-188">End the match on a word boundary.</span></span>|

<span data-ttu-id="6ef2f-189">2 番目のキャプチャ グループによって定義されている 2 桁の 10 進数が存在しない場合でも、入力文字列はこの正規表現を照合できます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-189">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="6ef2f-190">次の例では、一致が見つかった場合でも、成功した 2 つのキャプチャ グループの間に空のキャプチャ グループが検出されます。</span><span class="sxs-lookup"><span data-stu-id="6ef2f-190">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="6ef2f-191">参照</span><span class="sxs-lookup"><span data-stu-id="6ef2f-191">See also</span></span>

- [<span data-ttu-id="6ef2f-192">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="6ef2f-192">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
