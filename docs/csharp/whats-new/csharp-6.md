---
title: C# 6 の新機能 - C# ガイド
description: C# バージョン 6 の新機能について説明します
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224240"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="5f863-103">C# 6 の新機能</span><span class="sxs-lookup"><span data-stu-id="5f863-103">What's New in C# 6</span></span>

<span data-ttu-id="5f863-104">C# の 6.0 リリースには、開発者の生産性を向上させる多くの機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f863-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="5f863-105">これらの機能がもたらす全体的な効果として、より読みやすく簡潔なコードを記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5f863-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="5f863-106">一般的なベスト プラクティスを多数反映することで、構文に使用される形式的な記述が減っています。</span><span class="sxs-lookup"><span data-stu-id="5f863-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="5f863-107">形式的な記述が減ったことで、設計の意図が理解しやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="5f863-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="5f863-108">これらの機能を十分に学習すると、生産性が向上し、より読みやすいコードを記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5f863-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="5f863-109">言語のコンストラクトよりも機能により集中することができます。</span><span class="sxs-lookup"><span data-stu-id="5f863-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="5f863-110">この記事の残りの部分では、これらの各機能の概要と、各機能をより詳しく学習するためのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="5f863-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="5f863-111">チュートリアル セクションの [C# 6 の対話型探索](../tutorials/exploration/csharp-6.yml)で、機能を探究することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f863-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="5f863-112">読み取り専用の自動プロパティ</span><span class="sxs-lookup"><span data-stu-id="5f863-112">Read-only auto-properties</span></span>

<span data-ttu-id="5f863-113">*読み取り専用の自動プロパティ* を使用すると、より簡潔な構文で不変型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="5f863-114">自動プロパティは、get アクセサーのみを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="5f863-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="5f863-115">`FirstName` プロパティと `LastName` プロパティは、同じクラスのコンストラクターの本体内でのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-115">The `FirstName` and `LastName` properties can be set only in the body of the constructor of the same class:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="5f863-116">別のメソッドで `LastName` を設定しようとすると、コンパイル エラー `CS0200` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="5f863-117">この機能を使用すれば、不変型を作成したり、より簡潔で便利な自動プロパティ構文を使用するための、本格的な言語サポートを実現できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="5f863-118">この構文を追加してもアクセス可能なメソッドが削除されない場合は、[バイナリ互換性がある変更](version-update-considerations.md#binary-compatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="5f863-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="5f863-119">自動プロパティ初期化子</span><span class="sxs-lookup"><span data-stu-id="5f863-119">Auto-property initializers</span></span>

<span data-ttu-id="5f863-120">*自動プロパティ初期化子* を使用すると、プロパティ宣言の一部として自動プロパティの初期値を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="5f863-121">`Grades` メンバーは宣言された場所で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="5f863-122">これにより、初期化を厳密に 1 回だけ実行しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="5f863-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="5f863-123">初期化がプロパティ宣言の一部になることで、ストレージ割り当てが `Student` オブジェクトのパブリック インターフェイスと同じであることを示しやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="5f863-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="5f863-124">式形式の関数メンバー</span><span class="sxs-lookup"><span data-stu-id="5f863-124">Expression-bodied function members</span></span>

<span data-ttu-id="5f863-125">記述する多くのメンバーは、単一の式の可能性がある 1 つのステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5f863-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="5f863-126">代わりに式形式のメンバーを記述します。</span><span class="sxs-lookup"><span data-stu-id="5f863-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="5f863-127">この方法は、メソッドと読み取り専用プロパティに有効です。</span><span class="sxs-lookup"><span data-stu-id="5f863-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="5f863-128">たとえば、`ToString()` のオーバーライドはその好例です。</span><span class="sxs-lookup"><span data-stu-id="5f863-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="5f863-129">読み取り専用プロパティには、次の構文を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f863-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="5f863-130">既存のメンバーを式のようなメンバーに変更することは、[バイナリ互換性がある変更](version-update-considerations.md#binary-compatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="5f863-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="5f863-131">using static</span><span class="sxs-lookup"><span data-stu-id="5f863-131">using static</span></span>

<span data-ttu-id="5f863-132">*using static* 拡張機能を使用すると、1 つのクラスの静的メソッドをインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="5f863-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="5f863-133">具体的には、使用するクラスを次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="5f863-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="5f863-134"><xref:System.Math> にはいずれのインスタンス メソッドも含まれていません。</span><span class="sxs-lookup"><span data-stu-id="5f863-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="5f863-135">また `using static` は、静的メソッドとインスタンス メソッドの両方を持つクラスの静的クラスをインポートするためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="5f863-136">特に便利な例の 1 つが <xref:System.String> です。</span><span class="sxs-lookup"><span data-stu-id="5f863-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="5f863-137">static using ステートメントでは、完全修飾クラス名 (`System.String`) 使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f863-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="5f863-138">代わりに `string` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5f863-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="5f863-139">`static using` ステートメントからインポートすると、拡張メソッドは、拡張メソッドの呼び出し構文を使用して呼び出された場合にのみ、スコープ内に含められます。</span><span class="sxs-lookup"><span data-stu-id="5f863-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="5f863-140">静的メソッドとして呼び出された場合には含められません。</span><span class="sxs-lookup"><span data-stu-id="5f863-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="5f863-141">これは、LINQ クエリで多く見受けられることになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="5f863-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="5f863-142">LINQ パターンは、<xref:System.Linq.Enumerable> または <xref:System.Linq.Queryable> をインポートすることによってインポートできます。</span><span class="sxs-lookup"><span data-stu-id="5f863-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="5f863-143">拡張メソッドは通常、拡張メソッドの呼び出し式を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5f863-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="5f863-144">まれなケースですが、静的メソッドの呼び出し構文を使用して拡張メソッドを呼び出す場合は、クラス名を追加することであいまいさを解決します。</span><span class="sxs-lookup"><span data-stu-id="5f863-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="5f863-145">`static using` ディレクティブは、入れ子にされた型もインポートします。</span><span class="sxs-lookup"><span data-stu-id="5f863-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="5f863-146">これにより、入れ子にされた型を修飾なしで参照できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="5f863-147">Null 条件演算子</span><span class="sxs-lookup"><span data-stu-id="5f863-147">Null-conditional operators</span></span>

<span data-ttu-id="5f863-148">*null 条件演算子* を使用すれば、これらの null チェックをより簡単で円滑なものにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5f863-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="5f863-149">メンバー アクセス `.` を `?.` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5f863-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="5f863-150">上記の例では、person オブジェクトが `null` の場合に、変数 `first` に `null` が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5f863-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="5f863-151">それ以外の場合には、`FirstName` プロパティの値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5f863-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="5f863-152">特に重要なのは、`?.` を使用した場合、変数 `person` が `null` の場合、このコード行では `NullReferenceException` が生成されないということです。</span><span class="sxs-lookup"><span data-stu-id="5f863-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="5f863-153">代わりに、処理がショートサーキットされ、`null` が返されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="5f863-154">null 条件演算子は配列アクセスまたはインデクサー アクセスにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="5f863-155">インデックス式の `[]` を `?[]` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5f863-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="5f863-156">次の式では、`person` の値に関係なく、`string` が返されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="5f863-157">このコンストラクトは、いずれかのプロパティが `null` の場合に既定値を割り当てる目的で、 *null 結合* 演算子と共によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="5f863-158">式がショート サーキットされると、返された `null` 値が式全体に一致するように入力されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="5f863-159">`?.` を使用してメソッドを条件付きで呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="5f863-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="5f863-160">null 条件演算子を使用したメンバー関数の最も一般的な用途は、`null` の可能性があるデリゲート (またはイベント ハンドラー) を安全に呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="5f863-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="5f863-161">`?.` 演算子を使用してデリゲートの `Invoke` メソッドを呼び出して、メンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="5f863-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="5f863-162">例については、[デリゲート パターン](../delegates-patterns.md#handling-null-delegates)に関する記事でご覧になれます。</span><span class="sxs-lookup"><span data-stu-id="5f863-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="5f863-163">`?.` 演算子のルールでは、、演算子の左側が 1 回だけ評価されることが保証されています。</span><span class="sxs-lookup"><span data-stu-id="5f863-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="5f863-164">これによって、イベント ハンドラーを使用した次の例のように、多くの表現方法が可能になります。</span><span class="sxs-lookup"><span data-stu-id="5f863-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="5f863-165">左辺が 1 回だけ評価されることを保証し、また `?.` の左辺で、メソッドの呼び出しなどの任意の式を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5f863-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="5f863-166">文字列補間</span><span class="sxs-lookup"><span data-stu-id="5f863-166">String interpolation</span></span>

<span data-ttu-id="5f863-167">C# 6 では、新しい[文字列補間](../language-reference/tokens/interpolated.md)機能を使用し、文字列に式を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5f863-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="5f863-168">文字列の前に `$` を付けて、序数の代わりに `{` と `}` の間に式を使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="5f863-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="5f863-169">この例では、置換される式にプロパティを使用しています。</span><span class="sxs-lookup"><span data-stu-id="5f863-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="5f863-170">任意の式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-170">You can use any expression.</span></span> <span data-ttu-id="5f863-171">たとえば、補間の一部として生徒の評価点の平均を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f863-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="5f863-172">上記のコード行では、`Grades.Average()` の値が、小数点以下 2 桁の浮動小数点数として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="5f863-173">しかし場合によっては、生成された文字列を特定のカルチャで書式設定する必要が生じる場合もあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="5f863-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="5f863-174">文字列補間によって生成されたオブジェクトは暗黙的に <xref:System.FormattableString?displayProperty=nameWithType> に変換できることを利用します。</span><span class="sxs-lookup"><span data-stu-id="5f863-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f863-175"><xref:System.FormattableString> インスタンスには、複合書式文字列と、それらを文字列に変換する前の式評価の結果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5f863-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="5f863-176"><xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> メソッドを使用し、文字列の書式設定時にカルチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f863-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="5f863-177">次の例は、ドイツ (de-DE) のカルチャを使用して文字列を生成します</span><span class="sxs-lookup"><span data-stu-id="5f863-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="5f863-178">(既定では、ドイツのカルチャでは小数点区切り文字に ',' 文字が使用され、桁区切り記号に '.' 文字が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="5f863-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="5f863-179">文字列補間を開始するには、[C# における文字列補間](../tutorials/exploration/interpolated-strings.yml)の対話型チュートリアル、[文字列補間](../language-reference/tokens/interpolated.md)に関する記事、および「[C# における文字列補間](../tutorials/string-interpolation.md)」のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f863-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="5f863-180">例外フィルター</span><span class="sxs-lookup"><span data-stu-id="5f863-180">Exception filters</span></span>

<span data-ttu-id="5f863-181">*例外フィルター* は、特定の catch 句がいつ適用されるのかを決定する句です。</span><span class="sxs-lookup"><span data-stu-id="5f863-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="5f863-182">例外フィルターに使用されている式が `true` と評価された場合、catch 句は例外に対して通常の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="5f863-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="5f863-183">式が `false` と評価された場合、`catch` 句はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="5f863-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="5f863-184">用途としては、例外に関する情報を調べて、`catch` 句で例外を処理できるかどうかを確認するという使い方があります。</span><span class="sxs-lookup"><span data-stu-id="5f863-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="5f863-185">`nameof` 式</span><span class="sxs-lookup"><span data-stu-id="5f863-185">The `nameof` expression</span></span>

<span data-ttu-id="5f863-186">[nameof](../language-reference/operators/nameof.md) 式では、シンボルの名前が評価されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="5f863-187">この式は、変数、プロパティ、またはメンバー フィールドの名前が必要なときに便利です。</span><span class="sxs-lookup"><span data-stu-id="5f863-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="5f863-188">`nameof` の用途として特に一般的なものの 1 つは、例外の原因となったシンボルの名前を取得することです。</span><span class="sxs-lookup"><span data-stu-id="5f863-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="5f863-189">また、`INotifyPropertyChanged` インターフェイスを実装する XAML ベースのアプリケーションでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="5f863-190">Catch ブロックと Finally ブロックでの Await</span><span class="sxs-lookup"><span data-stu-id="5f863-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="5f863-191">C# 5 では、`await` 式を配置できる位置について、いくつかの制限がありました。</span><span class="sxs-lookup"><span data-stu-id="5f863-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="5f863-192">C# 6 では、`await` を `catch` 式や `finally` 式で使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5f863-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="5f863-193">次に示すのは、ロギングのシナリオで特によく使用されるコードです。</span><span class="sxs-lookup"><span data-stu-id="5f863-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="5f863-194">`catch` 句と `finally` 句の内部に `await` のサポートを追加するための実装詳細では、その動作と、同期コードの動作との整合性が保証されています。</span><span class="sxs-lookup"><span data-stu-id="5f863-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="5f863-195">`catch` または `finally` 句で実行されたコードがエラーをスローした場合、プログラムは次の包含ブロック内から適切な `catch` 句を検索します。</span><span class="sxs-lookup"><span data-stu-id="5f863-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="5f863-196">現行の例外があった場合、その例外は失われます。</span><span class="sxs-lookup"><span data-stu-id="5f863-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="5f863-197">`catch` 句や `finally` 句で待機中の式についても、これと同じことが起こります。つまり、適切な `catch` が検索され、現行の例外がある場合は、その例外が失われます。</span><span class="sxs-lookup"><span data-stu-id="5f863-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="5f863-198">この動作を理由に、`catch` 句と `finally` 句は慎重に記述することが推奨されています (新しい例外が導入されないようにしてください)。</span><span class="sxs-lookup"><span data-stu-id="5f863-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="5f863-199">インデクサーを使用して関連コレクションを初期化する</span><span class="sxs-lookup"><span data-stu-id="5f863-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="5f863-200">*インデックス初期化子* は、インデックスの使用によってコレクション初期化子の一貫性を高める 2 つの機能のうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="5f863-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="5f863-201">C# の以前のリリースでは、キーと値のペアを中かっこで囲むことで <xref:System.Collections.Generic.Dictionary%602> を含めたシーケンス スタイルのコレクションで *コレクション初期化子* を使用できました。</span><span class="sxs-lookup"><span data-stu-id="5f863-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="5f863-202">それらを <xref:System.Collections.Generic.Dictionary%602> コレクションおよびアクセス可能な `Add` メソッドが複数の引数を受け取るその他の型と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="5f863-203">新しい構文は、インデックスを使用したコレクションへの割り当てをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5f863-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="5f863-204">この機能が加わったことにより、いくつかのバージョンでシーケンス コンテナーに使用されていたものと同様の構文を使用して、連想コンテナーを初期化できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5f863-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="5f863-205">コレクション初期化子内の拡張 `Add` メソッド</span><span class="sxs-lookup"><span data-stu-id="5f863-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="5f863-206">コレクション初期化を使いやすくするもう 1 つの機能として、 *メソッドの* 拡張メソッド`Add`を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5f863-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="5f863-207">この機能は、Visual Basic との同等性を確保するために追加されました。</span><span class="sxs-lookup"><span data-stu-id="5f863-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="5f863-208">この機能は、新しい項目を意味的に追加するために、カスタム コレクション クラスで別の名前のメソッドを使用している場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="5f863-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="5f863-209">オーバーロード解決の改善</span><span class="sxs-lookup"><span data-stu-id="5f863-209">Improved overload resolution</span></span>

<span data-ttu-id="5f863-210">最後に説明するのは、言われなければ気付かないかもしれない機能です。</span><span class="sxs-lookup"><span data-stu-id="5f863-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="5f863-211">以前のバージョンの C# コンパイラでは、ラムダ式を使用した一部のメソッド呼び出しがあいまいと判断されるコンストラクトがありました。</span><span class="sxs-lookup"><span data-stu-id="5f863-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="5f863-212">たとえば、次のメソッドがあったとします。</span><span class="sxs-lookup"><span data-stu-id="5f863-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="5f863-213">以前のバージョンの C# では、メソッド グループ構文を使用してこのメソッドを呼び出すと、エラーが発生していました。</span><span class="sxs-lookup"><span data-stu-id="5f863-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="5f863-214">以前のコンパイラでは、`Task.Run(Action)` と `Task.Run(Func<Task>())` を正しく区別することができませんでした。</span><span class="sxs-lookup"><span data-stu-id="5f863-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="5f863-215">以前のバージョンでは、引数としてラムダ式を使用する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="5f863-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="5f863-216">C# 6 の コンパイラは、`Task.Run(Func<Task>())` のほうが適切であるということを正しく判断できます。</span><span class="sxs-lookup"><span data-stu-id="5f863-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="5f863-217">決定論的コンパイラの出力</span><span class="sxs-lookup"><span data-stu-id="5f863-217">Deterministic compiler output</span></span>

<span data-ttu-id="5f863-218">`-deterministic` オプションが、同じソース ファイルの連続するコンパイルで、バイト単位で同じ出力アセンブリを生成するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="5f863-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="5f863-219">既定では、すべてのコンパイルでは、コンパイルごとに一意な出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5f863-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="5f863-220">コンパイラは、タイムスタンプを追加し、ランダムな数から生成された GUID を追加します。</span><span class="sxs-lookup"><span data-stu-id="5f863-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="5f863-221">ビルド間の一貫性を確保するために、バイト単位で出力を比較する場合は、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f863-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="5f863-222">詳細については、[-deterministic コンパイラ オプション](../language-reference/compiler-options/deterministic-compiler-option.md)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f863-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
