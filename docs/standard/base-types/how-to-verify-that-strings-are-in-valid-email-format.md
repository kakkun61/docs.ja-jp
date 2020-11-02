---
title: 文字列が有効な電子メール形式であるかどうかを検証する方法
description: 正規表現を使用して、.NET で文字列が有効な電子メール形式であるかどうかを確認する方法の例について確認します。
ms.date: 06/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET], examples [Visual Basic]
- email [.NET], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 07b8e31e4a0203b87492eb01ab686a1c56f5565d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889076"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="f5113-103">文字列が有効な電子メール形式であるかどうかを検証する方法</span><span class="sxs-lookup"><span data-stu-id="f5113-103">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="f5113-104">正規表現を使用して文字列の形式が有効な電子メール形式であるかどうかを検証する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f5113-104">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

<span data-ttu-id="f5113-105">この正規表現は、電子メールとして実際に使用できるものに比べると単純です。</span><span class="sxs-lookup"><span data-stu-id="f5113-105">This regular expression is comparatively simple to what can actually be used as an email.</span></span> <span data-ttu-id="f5113-106">正規表現を使用して電子メールを検証することは、電子メールの構造が正しいことを確認するのに役立ちますが、実際に電子メールが存在することを確認する代わりにはなりません。</span><span class="sxs-lookup"><span data-stu-id="f5113-106">Using a regular expression to validate an email is useful to make sure the structure of an email is correct, but it isn't a substitution for verifying the email actually exists.</span></span>

<span data-ttu-id="f5113-107">✔️ 小さい正規表現を使用して、電子メールの有効な構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="f5113-107">✔️ DO use a small regular expression to check for the valid structure of an email.</span></span>

<span data-ttu-id="f5113-108">✔️ アプリのユーザーが指定したアドレスにテスト メールを送信します。</span><span class="sxs-lookup"><span data-stu-id="f5113-108">✔️ DO send a test email to the address provided by a user of your app.</span></span>

<span data-ttu-id="f5113-109">❌ 電子メールを検証する唯一の方法として、正規表現を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f5113-109">❌ DON'T use a regular expression as the only way you validate an email.</span></span>

<span data-ttu-id="f5113-110">電子メールの構造が正しいことを検証するために " _完全な_ " 正規表現を作成しようとすると、正規表現が非常に複雑になり、デバッグや改善が非常に困難になります。</span><span class="sxs-lookup"><span data-stu-id="f5113-110">If you try to create the _perfect_ regular expression to validate that the structure of an email is correct, the expression becomes so complex that it's incredibly difficult to debug or improve.</span></span> <span data-ttu-id="f5113-111">正規表現では、電子メールが正しく構成されていても、それが存在することを検証できません。</span><span class="sxs-lookup"><span data-stu-id="f5113-111">Regular expressions can't validate an email exists, even if it's structured correctly.</span></span> <span data-ttu-id="f5113-112">電子メールを検証する最善の方法は、そのアドレスにテスト メールを送信することです。</span><span class="sxs-lookup"><span data-stu-id="f5113-112">The best way to validate an email is to send a test email to the address.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="f5113-113">例</span><span class="sxs-lookup"><span data-stu-id="f5113-113">Example</span></span>

<span data-ttu-id="f5113-114">次の例では、`IsValidEmail` メソッドを定義します。このメソッドは、文字列に有効なメール アドレスが含まれている場合には `true` を返し、含まれていない場合には `false` を返します。それ以外のアクションは行われません。</span><span class="sxs-lookup"><span data-stu-id="f5113-114">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it doesn't, but takes no other action.</span></span>

<span data-ttu-id="f5113-115">電子メール アドレスが有効であることを確認するため、 `IsValidEmail` メソッドは <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> メソッドを呼び出し、 `(@)(.+)$` の正規表現パターンを指定して、電子メール アドレスからドメイン名を切り離します。</span><span class="sxs-lookup"><span data-stu-id="f5113-115">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="f5113-116">3 番目のパラメーターは、一致したテキストを操作また置換するメソッドを表す <xref:System.Text.RegularExpressions.MatchEvaluator> デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="f5113-116">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="f5113-117">正規表現パターンは次のように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="f5113-117">The regular expression pattern is interpreted as follows.</span></span>

| <span data-ttu-id="f5113-118">パターン</span><span class="sxs-lookup"><span data-stu-id="f5113-118">Pattern</span></span> | <span data-ttu-id="f5113-119">説明</span><span class="sxs-lookup"><span data-stu-id="f5113-119">Description</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | <span data-ttu-id="f5113-120">@ 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="f5113-120">Match the @ character.</span></span> <span data-ttu-id="f5113-121">この部分が最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="f5113-121">This part is the first capturing group.</span></span>                           |
| `(.+)`  | <span data-ttu-id="f5113-122">任意の文字の 1 回以上の出現に一致します。</span><span class="sxs-lookup"><span data-stu-id="f5113-122">Match one or more occurrences of any character.</span></span> <span data-ttu-id="f5113-123">この部分が 2 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="f5113-123">This part is the second capturing group.</span></span> |
| `$`     | <span data-ttu-id="f5113-124">入力文字列の末尾で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="f5113-124">End the match at the end of the string.</span></span>                                             |

<span data-ttu-id="f5113-125">ドメイン名は @ 文字と合わせて `DomainMapper` メソッドに渡されます。このメソッドは <xref:System.Globalization.IdnMapping> クラスを使用して、US-ASCII 文字の範囲に含まれない Unicode 文字を Punycode に変換します。</span><span class="sxs-lookup"><span data-stu-id="f5113-125">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="f5113-126">また、このメソッドは、 `invalid` メソッドがドメイン名に無効な文字を検出すると、 `True` フラグを <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="f5113-126">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="f5113-127">このメソッドは、Punycode ドメイン名の前に @ 記号を付けて、これを `IsValidEmail` メソッドに返します。</span><span class="sxs-lookup"><span data-stu-id="f5113-127">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

> [!TIP]
> <span data-ttu-id="f5113-128">単純な `(@)(.+)$` 正規表現パターンを使用してドメインを正規化し、それが成功または失敗したことを示す値を返すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f5113-128">It's recommended that you use use the simple `(@)(.+)$` regular expression pattern to normalize the domain and then return a value indicating that it passed or failed.</span></span> <span data-ttu-id="f5113-129">ただし、この記事の例では、正規表現を使用して電子メールを検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5113-129">However, the example in this article describes how to further use a regular expression to validate the email.</span></span> <span data-ttu-id="f5113-130">電子メールの検証方法に関係なく、必ずそのアドレスにテスト メールを送信して、それが存在することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5113-130">Regardless of how you validate an email, you should always send a test email to the address to make sure it exists.</span></span>

<span data-ttu-id="f5113-131">次に、 `IsValidEmail` メソッドは <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> メソッドを呼び出して、電子メール アドレスが正規表現パターンに準拠するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f5113-131">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="f5113-132">`IsValidEmail` メソッドは、電子メールの形式がメール アドレスに対して有効かどうかを判断するだけで、電子メールが存在するかどうかの検証は行われません。</span><span class="sxs-lookup"><span data-stu-id="f5113-132">The `IsValidEmail` method merely determines whether the email format is valid for an email address, it doesn't validate that the email exists.</span></span> <span data-ttu-id="f5113-133">また、`IsValidEmail` メソッドでは、トップレベル ドメイン名が [IANA ルート ゾーン データベース](https://www.iana.org/domains/root/db)に掲載されている有効なドメイン名であることの確認は行われません (これには検索操作が必要です)。</span><span class="sxs-lookup"><span data-stu-id="f5113-133">Also, the `IsValidEmail` method doesn't verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span>

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

<span data-ttu-id="f5113-134">この例の正規表現パターン `^[^@\s]+@[^@\s]+\.[^@\s]+$` の意味を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5113-134">In this example, the regular expression pattern `^[^@\s]+@[^@\s]+\.[^@\s]+$` is interpreted as shown in the following table.</span></span> <span data-ttu-id="f5113-135">正規表現のコンパイルには、<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> フラグが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f5113-135">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

| <span data-ttu-id="f5113-136">Pattern</span><span class="sxs-lookup"><span data-stu-id="f5113-136">Pattern</span></span>   | <span data-ttu-id="f5113-137">説明</span><span class="sxs-lookup"><span data-stu-id="f5113-137">Description</span></span>                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | <span data-ttu-id="f5113-138">文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="f5113-138">Begin the match at the start of the string.</span></span>                                              |
| `[^@\s]+` | <span data-ttu-id="f5113-139">@ 文字または空白以外の任意の文字の 1 回以上の出現を照合します。</span><span class="sxs-lookup"><span data-stu-id="f5113-139">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `@`       | <span data-ttu-id="f5113-140">@ 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="f5113-140">Match the @ character.</span></span>                                                                   |
| `[^@\s]+` | <span data-ttu-id="f5113-141">@ 文字または空白以外の任意の文字の 1 回以上の出現を照合します。</span><span class="sxs-lookup"><span data-stu-id="f5113-141">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `\.`      | <span data-ttu-id="f5113-142">1 つのピリオド文字を照合します。</span><span class="sxs-lookup"><span data-stu-id="f5113-142">Match a single period character.</span></span>                                                         |
| `[^@\s]+` | <span data-ttu-id="f5113-143">@ 文字または空白以外の任意の文字の 1 回以上の出現を照合します。</span><span class="sxs-lookup"><span data-stu-id="f5113-143">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `$`       | <span data-ttu-id="f5113-144">入力文字列の末尾で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="f5113-144">End the match at the end of the string.</span></span>                                                  |

> [!IMPORTANT]
> <span data-ttu-id="f5113-145">この正規表現は、有効なメール アドレスのすべての側面をカバーすることを意図したものではありません。</span><span class="sxs-lookup"><span data-stu-id="f5113-145">This regular expression is not intended to cover every aspect of a valid email address.</span></span> <span data-ttu-id="f5113-146">必要に応じて拡張するための例として提供されています。</span><span class="sxs-lookup"><span data-stu-id="f5113-146">It's provided as an example for you to extend as needed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5113-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5113-147">See also</span></span>

- [<span data-ttu-id="f5113-148">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="f5113-148">.NET Regular Expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="f5113-149">メール アドレスの検証はどこまで行う必要があるか</span><span class="sxs-lookup"><span data-stu-id="f5113-149">How far should one take e-mail address validation?</span></span>](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
