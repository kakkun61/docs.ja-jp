---
title: 列挙型デザイン
description: 列挙型の設計。特別な種類の値型です。 単純な列挙型には、小さな、閉じられた一連の選択肢があります。 フラグ列挙型は、列挙値のビットごとの演算をサポートします。
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: a2e19197b114daa2a0956a6fc87231a6a81de916
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821360"
---
# <a name="enum-design"></a><span data-ttu-id="ddea9-105">列挙型デザイン</span><span class="sxs-lookup"><span data-stu-id="ddea9-105">Enum Design</span></span>

<span data-ttu-id="ddea9-106">列挙型は、特別な種類の値型です。</span><span class="sxs-lookup"><span data-stu-id="ddea9-106">Enums are a special kind of value type.</span></span> <span data-ttu-id="ddea9-107">列挙型には、単純な列挙型とフラグ列挙型の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-107">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="ddea9-108">単純な列挙型は、選択の小さな閉じられたセットを表します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-108">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="ddea9-109">単純な列挙型の一般的な例としては、一連の色があります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-109">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="ddea9-110">フラグ列挙型は、列挙値のビットごとの演算をサポートするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="ddea9-110">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="ddea9-111">Flags 列挙型の一般的な例として、オプションの一覧があります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-111">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="ddea9-112">厳密に型指定されたパラメーター、プロパティ、および値のセットを表す戻り値には、列挙型を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-112">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="ddea9-113">✔️は、静的な定数ではなく列挙型を使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="ddea9-113">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="ddea9-114">❌ オープンセットには列挙型を使用しないでください (オペレーティングシステムのバージョン、友人の名前など)。</span><span class="sxs-lookup"><span data-stu-id="ddea9-114">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="ddea9-115">❌ 将来使用するための予約済み列挙値を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-115">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="ddea9-116">後の段階で、既存の列挙に値をいつでも追加できます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-116">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="ddea9-117">列挙型に値を追加する方法の詳細については、「 [列挙型への値の追加](#add_value) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-117">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="ddea9-118">予約済みの値は、実際の値のセットを汚染するだけで、ユーザーエラーにつながる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-118">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="ddea9-119">❌ 1つの値のみを使用して enum を公開しないようにします。</span><span class="sxs-lookup"><span data-stu-id="ddea9-119">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="ddea9-120">C Api の将来の拡張性を確保するための一般的な方法は、メソッドシグネチャに予約済みのパラメーターを追加することです。</span><span class="sxs-lookup"><span data-stu-id="ddea9-120">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="ddea9-121">このような予約済みのパラメーターは、単一の既定値を持つ列挙型として表すことができます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-121">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="ddea9-122">これは、マネージ Api では実行できません。</span><span class="sxs-lookup"><span data-stu-id="ddea9-122">This should not be done in managed APIs.</span></span> <span data-ttu-id="ddea9-123">メソッドのオーバーロードでは、将来のリリースでパラメーターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-123">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="ddea9-124">❌ 列挙型には、sentinel 値を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-124">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="ddea9-125">Framework 開発者にとっては便利な場合もありますが、sentinel 値はフレームワークのユーザーにとって混乱を招くことがあります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-125">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="ddea9-126">列挙型によって表されるセットの値の1つではなく、列挙型の状態を追跡するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-126">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="ddea9-127">単純な列挙型で値0を指定する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-127">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="ddea9-128">"None" のような値を呼び出すことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-128">Consider calling the value something like "None."</span></span> <span data-ttu-id="ddea9-129">このような値がこの特定の列挙型に適していない場合は、列挙型の最も一般的な既定値に0の基になる値を代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-129">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="ddea9-130"><xref:System.Int32>次のいずれかに該当しない場合は、列挙型の基になる型として (ほとんどのプログラミング言語で既定) を使用することを✔️してください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-130">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="ddea9-131">列挙型はフラグの列挙型であり、32を超えるフラグがあるか、または今後さらに多くなることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-131">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="ddea9-132"><xref:System.Int32>異なるサイズの列挙型が必要なアンマネージコードとの相互運用性を容易にするために、基になる型はとは異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-132">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="ddea9-133">基になる型が小さいと、スペースが大幅に節約されます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-133">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="ddea9-134">列挙型が主に制御フローの引数として使用されることが予想される場合、サイズの違いはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="ddea9-134">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="ddea9-135">次の場合、サイズを節約することが重要になります。</span><span class="sxs-lookup"><span data-stu-id="ddea9-135">The size savings might be significant if:</span></span>

  - <span data-ttu-id="ddea9-136">非常に頻繁にインスタンス化される構造体またはクラスのフィールドとして列挙型を使用することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="ddea9-136">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="ddea9-137">ユーザーは、大規模な配列または列挙型インスタンスのコレクションを作成することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="ddea9-137">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="ddea9-138">列挙型の多数のインスタンスをシリアル化することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="ddea9-138">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="ddea9-139">メモリ内での使用については、マネージオブジェクトが常に固定されていることに注意してください。したがって、インスタンス `DWORD` 全体のサイズは常にに切り上げられるため、より小さな列挙型をパックするために、インスタンス内に複数の列挙型またはその他の小さな構造体を効果的に使用する必要があり `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-139">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="ddea9-140">✔️は、複数形の名詞または名詞句を持つ列挙型と、単数形または名詞句を持つ単純な列挙型を使用します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-140">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="ddea9-141">❌ を直接拡張しないで <xref:System.Enum?displayProperty=nameWithType> ください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-141">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="ddea9-142"><xref:System.Enum?displayProperty=nameWithType> は、ユーザー定義の列挙を作成するために CLR によって使用される特殊な型です。</span><span class="sxs-lookup"><span data-stu-id="ddea9-142"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="ddea9-143">ほとんどのプログラミング言語には、この機能にアクセスできるプログラミング要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ddea9-143">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="ddea9-144">たとえば、C# では、 `enum` キーワードを使用して列挙型を定義します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-144">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="ddea9-145">フラグ列挙型のデザイン</span><span class="sxs-lookup"><span data-stu-id="ddea9-145">Designing Flag Enums</span></span>

<span data-ttu-id="ddea9-146">✔️には、 <xref:System.FlagsAttribute?displayProperty=nameWithType> 列挙型にフラグを適用します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-146">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="ddea9-147">単純な列挙型にはこの属性を適用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-147">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="ddea9-148">フラグの列挙値には2の累乗を使用して、ビットごとの OR 演算を使用して自由に組み合わせることができるように✔️ます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-148">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="ddea9-149">一般的に使用されるフラグの組み合わせに対して特別な列挙値を指定することを✔️検討します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-149">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="ddea9-150">ビットごとの演算は高度な概念であり、単純なタスクには必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ddea9-150">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="ddea9-151"><xref:System.IO.FileAccess.ReadWrite> このような特殊な値の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-151"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="ddea9-152">❌ 値の特定の組み合わせが無効な場合は、フラグの列挙型を作成しないようにします。</span><span class="sxs-lookup"><span data-stu-id="ddea9-152">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="ddea9-153">❌ 次のガイドラインで規定されているように、値が "すべてのフラグがクリアされています" を表し、適切な名前が付けられている場合を除き、フラグの列挙値0を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ddea9-153">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="ddea9-154">✔️には、フラグの列挙型の0の値を指定 `None` します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-154">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="ddea9-155">フラグの列挙型の場合、値は常に "すべてのフラグがクリアされている" ことを意味します。</span><span class="sxs-lookup"><span data-stu-id="ddea9-155">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="ddea9-156">列挙型への値の追加</span><span class="sxs-lookup"><span data-stu-id="ddea9-156">Adding Value to Enums</span></span>

<span data-ttu-id="ddea9-157">列挙型に値を追加する必要があることを既に確認しています。</span><span class="sxs-lookup"><span data-stu-id="ddea9-157">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="ddea9-158">新しく追加された値が既存の API から返された場合、アプリケーションの互換性の問題が発生する可能性があります。これは、正しく記述されていないアプリケーションが新しい値を正しく処理できない可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="ddea9-158">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="ddea9-159">互換性のリスクが小さいとしても、列挙値に値を追加することを検討✔️。</span><span class="sxs-lookup"><span data-stu-id="ddea9-159">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="ddea9-160">列挙型への追加によって発生するアプリケーションの非互換性に関する実際のデータがある場合は、新しい値と古い値を返す新しい API を追加し、古い API を廃止することを検討してください。これにより、古い値だけが返されます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-160">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="ddea9-161">これにより、既存のアプリケーションに互換性があることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ddea9-161">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="ddea9-162">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="ddea9-162">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="ddea9-163">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="ddea9-163">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ddea9-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddea9-164">See also</span></span>

- [<span data-ttu-id="ddea9-165">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ddea9-165">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="ddea9-166">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ddea9-166">Framework Design Guidelines</span></span>](index.md)
