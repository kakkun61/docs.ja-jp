---
title: 一般的な名前付け規則
description: 単語の選択に関連する一般的な名前付け規則、略語と頭字語の使用に関するガイドライン、および言語固有の名前を回避するためのガイダンスを使用します。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: 60832e823ed2f51fdd13c467dbbef4378de27885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706711"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="39e47-103">一般的な名前付け規則</span><span class="sxs-lookup"><span data-stu-id="39e47-103">General Naming Conventions</span></span>

<span data-ttu-id="39e47-104">ここでは、単語の選択に関連する一般的な名前付け規則、略語と頭字語の使用に関するガイドライン、および言語固有の名前の使用を回避するための推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="39e47-104">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>

## <a name="word-choice"></a><span data-ttu-id="39e47-105">単語の選択</span><span class="sxs-lookup"><span data-stu-id="39e47-105">Word Choice</span></span>

 <span data-ttu-id="39e47-106">✔️は、簡単に判読できる識別子名を選択します。</span><span class="sxs-lookup"><span data-stu-id="39e47-106">✔️ DO choose easily readable identifier names.</span></span>

 <span data-ttu-id="39e47-107">たとえば、という名前のプロパティは、 `HorizontalAlignment` よりも英語で読みやすく `AlignmentHorizontal` なります。</span><span class="sxs-lookup"><span data-stu-id="39e47-107">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>

 <span data-ttu-id="39e47-108">✔️簡潔にするために読みやすさを優先します。</span><span class="sxs-lookup"><span data-stu-id="39e47-108">✔️ DO favor readability over brevity.</span></span>

 <span data-ttu-id="39e47-109">プロパティ名 `CanScrollHorizontally` は、 `ScrollableX` (X 軸へのあいまいな参照) よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="39e47-109">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>

 <span data-ttu-id="39e47-110">❌ アンダースコア、ハイフン、またはその他の英数字以外の文字は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39e47-110">❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.</span></span>

 <span data-ttu-id="39e47-111">❌ ハンガリー表記法は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39e47-111">❌ DO NOT use Hungarian notation.</span></span>

 <span data-ttu-id="39e47-112">❌ 広く使用されているプログラミング言語のキーワードと競合する識別子を使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="39e47-112">❌ AVOID using identifiers that conflict with keywords of widely used programming languages.</span></span>

 <span data-ttu-id="39e47-113">共通言語仕様 (CLS) の規則4に従って、すべての準拠言語は、その言語のキーワードを識別子として使用する名前付き項目へのアクセスを許可する機構を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e47-113">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="39e47-114">たとえば、C# では、この場合、エスケープメカニズムとして @ sign が使用されます。</span><span class="sxs-lookup"><span data-stu-id="39e47-114">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="39e47-115">ただし、エスケープシーケンスではなく1つのメソッドを使用する方がはるかに困難であるため、一般的なキーワードを避けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39e47-115">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>

## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="39e47-116">省略形と頭字語の使用</span><span class="sxs-lookup"><span data-stu-id="39e47-116">Using Abbreviations and Acronyms</span></span>

 <span data-ttu-id="39e47-117">❌ 識別子名の一部として省略形または短縮形を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39e47-117">❌ DO NOT use abbreviations or contractions as part of identifier names.</span></span>

 <span data-ttu-id="39e47-118">たとえば、で `GetWindow` はなくを使用 `GetWin` します。</span><span class="sxs-lookup"><span data-stu-id="39e47-118">For example, use `GetWindow` rather than `GetWin`.</span></span>

 <span data-ttu-id="39e47-119">❌ 広く受け入れられていない頭字語は使用せず、必要な場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="39e47-119">❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>

## <a name="avoiding-language-specific-names"></a><span data-ttu-id="39e47-120">Language-Specific 名の回避</span><span class="sxs-lookup"><span data-stu-id="39e47-120">Avoiding Language-Specific Names</span></span>

 <span data-ttu-id="39e47-121">型名の言語固有のキーワードではなく、意味的に興味深い名前を使用する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="39e47-121">✔️ DO use semantically interesting names rather than language-specific keywords for type names.</span></span>

 <span data-ttu-id="39e47-122">たとえば、 `GetLength` はよりもわかりやすい名前です `GetInt` 。</span><span class="sxs-lookup"><span data-stu-id="39e47-122">For example, `GetLength` is a better name than `GetInt`.</span></span>

 <span data-ttu-id="39e47-123">通常は、言語固有の名前ではなく、汎用的な CLR 型名を使用します。これは、識別子が型以外のセマンティックの意味を持たない場合に、まれに発生します。✔️</span><span class="sxs-lookup"><span data-stu-id="39e47-123">✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>

 <span data-ttu-id="39e47-124">たとえば、に変換するメソッドは、では <xref:System.Int64> なくという名前にする必要があり `ToInt64` `ToLong` <xref:System.Int64> ます (は C# 固有のエイリアスの CLR 名であるため `long` )。</span><span class="sxs-lookup"><span data-stu-id="39e47-124">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="39e47-125">次の表は、CLR 型名を使用したいくつかの基本データ型 (C#、Visual Basic、および C++ の対応する型名) を示しています。</span><span class="sxs-lookup"><span data-stu-id="39e47-125">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>

|<span data-ttu-id="39e47-126">C#</span><span class="sxs-lookup"><span data-stu-id="39e47-126">C#</span></span>|<span data-ttu-id="39e47-127">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39e47-127">Visual Basic</span></span>|<span data-ttu-id="39e47-128">C++</span><span class="sxs-lookup"><span data-stu-id="39e47-128">C++</span></span>|<span data-ttu-id="39e47-129">CLR</span><span class="sxs-lookup"><span data-stu-id="39e47-129">CLR</span></span>|
|---------|------------------|-----------|---------|
|<span data-ttu-id="39e47-130">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="39e47-130">**sbyte**</span></span>|<span data-ttu-id="39e47-131">**SByte**</span><span class="sxs-lookup"><span data-stu-id="39e47-131">**SByte**</span></span>|<span data-ttu-id="39e47-132">**char**</span><span class="sxs-lookup"><span data-stu-id="39e47-132">**char**</span></span>|<span data-ttu-id="39e47-133">**SByte**</span><span class="sxs-lookup"><span data-stu-id="39e47-133">**SByte**</span></span>|
|<span data-ttu-id="39e47-134">**byte**</span><span class="sxs-lookup"><span data-stu-id="39e47-134">**byte**</span></span>|<span data-ttu-id="39e47-135">**Byte**</span><span class="sxs-lookup"><span data-stu-id="39e47-135">**Byte**</span></span>|<span data-ttu-id="39e47-136">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="39e47-136">**unsigned char**</span></span>|<span data-ttu-id="39e47-137">**Byte**</span><span class="sxs-lookup"><span data-stu-id="39e47-137">**Byte**</span></span>|
|<span data-ttu-id="39e47-138">**short**</span><span class="sxs-lookup"><span data-stu-id="39e47-138">**short**</span></span>|<span data-ttu-id="39e47-139">**Short**</span><span class="sxs-lookup"><span data-stu-id="39e47-139">**Short**</span></span>|<span data-ttu-id="39e47-140">**short**</span><span class="sxs-lookup"><span data-stu-id="39e47-140">**short**</span></span>|<span data-ttu-id="39e47-141">**Int16**</span><span class="sxs-lookup"><span data-stu-id="39e47-141">**Int16**</span></span>|
|<span data-ttu-id="39e47-142">**ushort**</span><span class="sxs-lookup"><span data-stu-id="39e47-142">**ushort**</span></span>|<span data-ttu-id="39e47-143">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="39e47-143">**UInt16**</span></span>|<span data-ttu-id="39e47-144">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="39e47-144">**unsigned short**</span></span>|<span data-ttu-id="39e47-145">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="39e47-145">**UInt16**</span></span>|
|<span data-ttu-id="39e47-146">**int**</span><span class="sxs-lookup"><span data-stu-id="39e47-146">**int**</span></span>|<span data-ttu-id="39e47-147">**Integer**</span><span class="sxs-lookup"><span data-stu-id="39e47-147">**Integer**</span></span>|<span data-ttu-id="39e47-148">**int**</span><span class="sxs-lookup"><span data-stu-id="39e47-148">**int**</span></span>|<span data-ttu-id="39e47-149">**Int32**</span><span class="sxs-lookup"><span data-stu-id="39e47-149">**Int32**</span></span>|
|<span data-ttu-id="39e47-150">**uint**</span><span class="sxs-lookup"><span data-stu-id="39e47-150">**uint**</span></span>|<span data-ttu-id="39e47-151">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="39e47-151">**UInt32**</span></span>|<span data-ttu-id="39e47-152">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="39e47-152">**unsigned int**</span></span>|<span data-ttu-id="39e47-153">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="39e47-153">**UInt32**</span></span>|
|<span data-ttu-id="39e47-154">**long**</span><span class="sxs-lookup"><span data-stu-id="39e47-154">**long**</span></span>|<span data-ttu-id="39e47-155">**Long**</span><span class="sxs-lookup"><span data-stu-id="39e47-155">**Long**</span></span>|<span data-ttu-id="39e47-156">**__int64**</span><span class="sxs-lookup"><span data-stu-id="39e47-156">**__int64**</span></span>|<span data-ttu-id="39e47-157">**Int64**</span><span class="sxs-lookup"><span data-stu-id="39e47-157">**Int64**</span></span>|
|<span data-ttu-id="39e47-158">**ulong**</span><span class="sxs-lookup"><span data-stu-id="39e47-158">**ulong**</span></span>|<span data-ttu-id="39e47-159">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="39e47-159">**UInt64**</span></span>|<span data-ttu-id="39e47-160">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="39e47-160">**unsigned __int64**</span></span>|<span data-ttu-id="39e47-161">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="39e47-161">**UInt64**</span></span>|
|<span data-ttu-id="39e47-162">**float**</span><span class="sxs-lookup"><span data-stu-id="39e47-162">**float**</span></span>|<span data-ttu-id="39e47-163">**Single**</span><span class="sxs-lookup"><span data-stu-id="39e47-163">**Single**</span></span>|<span data-ttu-id="39e47-164">**float**</span><span class="sxs-lookup"><span data-stu-id="39e47-164">**float**</span></span>|<span data-ttu-id="39e47-165">**Single**</span><span class="sxs-lookup"><span data-stu-id="39e47-165">**Single**</span></span>|
|<span data-ttu-id="39e47-166">**double**</span><span class="sxs-lookup"><span data-stu-id="39e47-166">**double**</span></span>|<span data-ttu-id="39e47-167">**Double**</span><span class="sxs-lookup"><span data-stu-id="39e47-167">**Double**</span></span>|<span data-ttu-id="39e47-168">**double**</span><span class="sxs-lookup"><span data-stu-id="39e47-168">**double**</span></span>|<span data-ttu-id="39e47-169">**Double**</span><span class="sxs-lookup"><span data-stu-id="39e47-169">**Double**</span></span>|
|<span data-ttu-id="39e47-170">**bool**</span><span class="sxs-lookup"><span data-stu-id="39e47-170">**bool**</span></span>|<span data-ttu-id="39e47-171">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="39e47-171">**Boolean**</span></span>|<span data-ttu-id="39e47-172">**bool**</span><span class="sxs-lookup"><span data-stu-id="39e47-172">**bool**</span></span>|<span data-ttu-id="39e47-173">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="39e47-173">**Boolean**</span></span>|
|<span data-ttu-id="39e47-174">**char**</span><span class="sxs-lookup"><span data-stu-id="39e47-174">**char**</span></span>|<span data-ttu-id="39e47-175">**Char**</span><span class="sxs-lookup"><span data-stu-id="39e47-175">**Char**</span></span>|<span data-ttu-id="39e47-176">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="39e47-176">**wchar_t**</span></span>|<span data-ttu-id="39e47-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="39e47-177">**Char**</span></span>|
|<span data-ttu-id="39e47-178">**string**</span><span class="sxs-lookup"><span data-stu-id="39e47-178">**string**</span></span>|<span data-ttu-id="39e47-179">**String**</span><span class="sxs-lookup"><span data-stu-id="39e47-179">**String**</span></span>|<span data-ttu-id="39e47-180">**String**</span><span class="sxs-lookup"><span data-stu-id="39e47-180">**String**</span></span>|<span data-ttu-id="39e47-181">**String**</span><span class="sxs-lookup"><span data-stu-id="39e47-181">**String**</span></span>|
|<span data-ttu-id="39e47-182">**object**</span><span class="sxs-lookup"><span data-stu-id="39e47-182">**object**</span></span>|<span data-ttu-id="39e47-183">**Object**</span><span class="sxs-lookup"><span data-stu-id="39e47-183">**Object**</span></span>|<span data-ttu-id="39e47-184">**Object**</span><span class="sxs-lookup"><span data-stu-id="39e47-184">**Object**</span></span>|<span data-ttu-id="39e47-185">**Object**</span><span class="sxs-lookup"><span data-stu-id="39e47-185">**Object**</span></span>|

 <span data-ttu-id="39e47-186">一般的な名前 (やなど) は、型名を繰り返すのではなく、通常の名前を使用します。たとえば、識別子に意味が `value` `item` なく、パラメーターの型が重要でない場合には、型名を繰り返すのではなく、✔️ます。</span><span class="sxs-lookup"><span data-stu-id="39e47-186">✔️ DO  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>

## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="39e47-187">既存の Api の新しいバージョンの命名</span><span class="sxs-lookup"><span data-stu-id="39e47-187">Naming New Versions of Existing APIs</span></span>

 <span data-ttu-id="39e47-188">既存の API の新しいバージョンを作成するときに、古い API に似た名前を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="39e47-188">✔️ DO use a name similar to the old API when creating new versions of an existing API.</span></span>

 <span data-ttu-id="39e47-189">これは、Api 間の関係を強調表示するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="39e47-189">This helps to highlight the relationship between the APIs.</span></span>

 <span data-ttu-id="39e47-190">✔️は、既存の API の新しいバージョンを示すために、プレフィックスではなくサフィックスを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39e47-190">✔️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>

 <span data-ttu-id="39e47-191">これにより、ドキュメントを参照したり、IntelliSense を使用したりするときに検出がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39e47-191">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="39e47-192">以前のバージョンの API は、ほとんどのブラウザーや IntelliSense がアルファベット順に識別子を表示するため、新しい Api の近くに編成されます。</span><span class="sxs-lookup"><span data-stu-id="39e47-192">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>

 <span data-ttu-id="39e47-193">サフィックスまたはプレフィックスを追加するのではなく、新しいがわかりやすい識別子を使用する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="39e47-193">✔️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>

 <span data-ttu-id="39e47-194">✔️は、既存の API の新しいバージョンを示すために数字のサフィックスを使用します。特に、API の既存の名前が意味のある唯一の名前 (業界標準の場合) であり、意味のあるサフィックス (または名前の変更) を追加することは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="39e47-194">✔️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>

 <span data-ttu-id="39e47-195">❌ 同じ API の以前のバージョンと区別するために、識別子に "Ex" (または同様の) サフィックスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39e47-195">❌ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>

 <span data-ttu-id="39e47-196">✔️は、32ビット整数ではなく64ビット整数 (long 整数) で動作する Api のバージョンを導入するときに、"64" サフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="39e47-196">✔️ DO use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="39e47-197">既存の32ビット API が存在する場合にのみ、このアプローチを行う必要があります。これは、64ビットバージョンのみの新しい Api では使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39e47-197">You only need to take this approach when the existing 32-bit API exists; don't do it for brand new APIs with only a 64-bit version.</span></span>

 <span data-ttu-id="39e47-198">*部分 &copy; 2005、2009 Microsoft Corporation。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="39e47-198">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="39e47-199">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="39e47-199">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="39e47-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="39e47-200">See also</span></span>

- [<span data-ttu-id="39e47-201">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="39e47-201">Framework design guidelines</span></span>](index.md)
- [<span data-ttu-id="39e47-202">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="39e47-202">Naming guidelines</span></span>](naming-guidelines.md)
- [<span data-ttu-id="39e47-203">EditorConfig での .NET の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="39e47-203">.NET naming conventions for EditorConfig</span></span>](/visualstudio/ide/editorconfig-naming-conventions)
