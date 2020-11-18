---
title: 大文字の使用規則
description: 識別子、複合語、および一般的な用語の大文字小文字の表記規則を適用します。 .NET での大文字と小文字の区別のしくみについて説明します。
ms.date: 10/22/2008
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 8df136fb57ad61ddfd87f4dec1f6490c63c3d977
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821529"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="aaa8c-104">大文字の使用規則</span><span class="sxs-lookup"><span data-stu-id="aaa8c-104">Capitalization Conventions</span></span>
<span data-ttu-id="aaa8c-105">この章のガイドラインでは、一貫して適用されている場合に、型、メンバー、およびパラメーターの識別子を読みやすくするための簡単な方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-105">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="aaa8c-106">識別子の大文字小文字の規則</span><span class="sxs-lookup"><span data-stu-id="aaa8c-106">Capitalization Rules for Identifiers</span></span>
 <span data-ttu-id="aaa8c-107">識別子内の単語を区別するには、識別子内の各単語の最初の文字を大文字にします。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-107">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="aaa8c-108">語句を区別するためにアンダースコアを使用したり、識別子内の任意の場所で単語を区別したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-108">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="aaa8c-109">識別子の使用方法によっては、次の2つの適切な方法で識別子を大文字にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-109">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="aaa8c-110">パスワードの大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="aaa8c-110">PascalCasing</span></span>

- <span data-ttu-id="aaa8c-111">キャメル</span><span class="sxs-lookup"><span data-stu-id="aaa8c-111">camelCasing</span></span>

 <span data-ttu-id="aaa8c-112">次の例に示すように、パラメーター名を除くすべての識別子に使用される、文字表記規則は、各単語の最初の文字 (長さが2文字を超える頭字語を含む) を大文字にします。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-112">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="aaa8c-113">次の識別子に示されているように、2文字の頭字語では、両方の文字が大文字になります。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-113">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="aaa8c-114">次の例に示すように、キャメル規則は、パラメーター名に対してのみ使用され、最初の単語を除く各単語の最初の文字を大文字にします。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-114">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="aaa8c-115">この例に示すように、camel 形式の識別子を開始する2文字の頭字語は両方とも小文字です。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-115">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="aaa8c-116">複数の単語で構成されるすべてのパブリックメンバー、型、名前空間の名前に対しては、文字の大文字と小文字の区別を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-116">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="aaa8c-117">パラメーター名にはキャメルを使用します。✔️</span><span class="sxs-lookup"><span data-stu-id="aaa8c-117">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="aaa8c-118">次の表では、さまざまな種類の識別子の大文字と小文字の規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-118">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="aaa8c-119">識別子</span><span class="sxs-lookup"><span data-stu-id="aaa8c-119">Identifier</span></span>|<span data-ttu-id="aaa8c-120">大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="aaa8c-120">Casing</span></span>|<span data-ttu-id="aaa8c-121">例</span><span class="sxs-lookup"><span data-stu-id="aaa8c-121">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="aaa8c-122">名前空間</span><span class="sxs-lookup"><span data-stu-id="aaa8c-122">Namespace</span></span>|<span data-ttu-id="aaa8c-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-123">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="aaa8c-124">Type</span><span class="sxs-lookup"><span data-stu-id="aaa8c-124">Type</span></span>|<span data-ttu-id="aaa8c-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-125">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="aaa8c-126">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aaa8c-126">Interface</span></span>|<span data-ttu-id="aaa8c-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-127">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="aaa8c-128">Method</span><span class="sxs-lookup"><span data-stu-id="aaa8c-128">Method</span></span>|<span data-ttu-id="aaa8c-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-129">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="aaa8c-130">プロパティ</span><span class="sxs-lookup"><span data-stu-id="aaa8c-130">Property</span></span>|<span data-ttu-id="aaa8c-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-131">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="aaa8c-132">イベント</span><span class="sxs-lookup"><span data-stu-id="aaa8c-132">Event</span></span>|<span data-ttu-id="aaa8c-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-133">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="aaa8c-134">フィールド</span><span class="sxs-lookup"><span data-stu-id="aaa8c-134">Field</span></span>|<span data-ttu-id="aaa8c-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-135">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="aaa8c-136">列挙値</span><span class="sxs-lookup"><span data-stu-id="aaa8c-136">Enum value</span></span>|<span data-ttu-id="aaa8c-137">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-137">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="aaa8c-138">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aaa8c-138">Parameter</span></span>|<span data-ttu-id="aaa8c-139">Camel</span><span class="sxs-lookup"><span data-stu-id="aaa8c-139">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="aaa8c-140">複合語と一般的な用語を大文字にする</span><span class="sxs-lookup"><span data-stu-id="aaa8c-140">Capitalizing Compound Words and Common Terms</span></span>
 <span data-ttu-id="aaa8c-141">ほとんどの複合用語は、大文字と小文字を区別するために1つの単語として扱われます。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-141">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="aaa8c-142">❌ いわゆる終了形式の複合単語内の各単語を大文字にしないでください。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-142">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="aaa8c-143">これらは、エンドポイントなどの1つの単語として記述された複合ワードです。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-143">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="aaa8c-144">大文字と小文字のガイドラインのために、閉じた複合ワードを1つの単語として扱います。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-144">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="aaa8c-145">現在のディクショナリを使用して、複合単語が閉じた形式で記述されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-145">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="aaa8c-146">Pascal</span><span class="sxs-lookup"><span data-stu-id="aaa8c-146">Pascal</span></span>|<span data-ttu-id="aaa8c-147">Camel</span><span class="sxs-lookup"><span data-stu-id="aaa8c-147">Camel</span></span>|<span data-ttu-id="aaa8c-148">Not</span><span class="sxs-lookup"><span data-stu-id="aaa8c-148">Not</span></span>|
|------------|-----------|---------|
|`BitFlag`|`bitFlag`|`Bitflag`|
|`Callback`|`callback`|`CallBack`|
|`Canceled`|`canceled`|`Cancelled`|
|`DoNot`|`doNot`|`Don't`|
|`Email`|`email`|`EMail`|
|`Endpoint`|`endpoint`|`EndPoint`|
|`FileName`|`fileName`|`Filename`|
|`Gridline`|`gridline`|`GridLine`|
|`Hashtable`|`hashtable`|`HashTable`|
|`Id`|`id`|`ID`|
|`Indexes`|`indexes`|`Indices`|
|`LogOff`|`logOff`|`LogOut`|
|`LogOn`|`logOn`|`LogIn`|
|`Metadata`|`metadata`|`MetaData, metaData`|
|`Multipanel`|`multipanel`|`MultiPanel`|
|`Multiview`|`multiview`|`MultiView`|
|`Namespace`|`namespace`|`NameSpace`|
|`Ok`|`ok`|`OK`|
|`Pi`|`pi`|`PI`|
|`Placeholder`|`placeholder`|`PlaceHolder`|
|`SignIn`|`signIn`|`SignOn`|
|`SignOut`|`signOut`|`SignOff`|
|`UserName`|`userName`|`Username`|
|`WhiteSpace`|`whiteSpace`|`Whitespace`|
|`Writable`|`writable`|`Writeable`|

## <a name="case-sensitivity"></a><span data-ttu-id="aaa8c-149">大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="aaa8c-149">Case Sensitivity</span></span>
 <span data-ttu-id="aaa8c-150">CLR で実行できる言語は、大文字と小文字の区別をサポートするためには必要ありません。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-150">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="aaa8c-151">お使いの言語でサポートされている場合でも、フレームワークにアクセスする可能性のある他の言語はありません。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-151">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="aaa8c-152">したがって、外部からアクセスできるすべての Api では、同じコンテキスト内の2つの名前を区別するために大文字と小文字だけを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-152">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="aaa8c-153">❌ すべてのプログラミング言語で大文字と小文字が区別されると想定しないでください。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-153">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="aaa8c-154">しかし、そうではありません。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-154">They are not.</span></span> <span data-ttu-id="aaa8c-155">名前は大文字と小文字のみで異なることはできません。</span><span class="sxs-lookup"><span data-stu-id="aaa8c-155">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="aaa8c-156">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="aaa8c-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="aaa8c-157">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="aaa8c-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="aaa8c-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="aaa8c-158">See also</span></span>

- [<span data-ttu-id="aaa8c-159">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="aaa8c-159">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="aaa8c-160">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="aaa8c-160">Naming Guidelines</span></span>](naming-guidelines.md)
