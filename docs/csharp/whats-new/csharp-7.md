---
title: C# 7.0 の新機能 - C# ガイド
description: C# 言語のバージョン 7.0 での新機能の概要を説明します。
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: c238439b0f435e579d932b3b1eb13e9b0061fa5f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678222"
---
# <a name="whats-new-in-c-70-through-c-73"></a><span data-ttu-id="ef7b8-103">C# 7.0 - C# 7.3 の新機能</span><span class="sxs-lookup"><span data-stu-id="ef7b8-103">What's new in C# 7.0 through C# 7.3</span></span>

<span data-ttu-id="ef7b8-104">C# 7.0 - C# 7.3 では、多くの機能が追加され、C# での開発エクスぺリエンスが段階的に改善されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-104">C# 7.0 through C# 7.3 brought a number of features and incremental improvements to your development experience with C#.</span></span> <span data-ttu-id="ef7b8-105">この記事では、新しい言語機能とコンパイラ オプションの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-105">This article provides an overview of the new language features and compiler options.</span></span> <span data-ttu-id="ef7b8-106">.NET Framework ベースのアプリケーションでサポートされている最新バージョンである C# 7.3 の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-106">The descriptions describe the behavior for C# 7.3, which is the most recent version supported for .NET Framework-based applications.</span></span>

<span data-ttu-id="ef7b8-107">C# 7.1 で[言語バージョンの選択](../language-reference/configure-language-version.md)の構成要素が追加され、これにより、プロジェクト ファイルでコンパイラ言語バージョンが指定できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-107">The [language version selection](../language-reference/configure-language-version.md) configuration element was added with C# 7.1, which enables you to specify the compiler language version in your project file.</span></span>

<span data-ttu-id="ef7b8-108">C# 7.0 - 7.3 で C# 言語に追加された機能とテーマは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-108">C# 7.0-7.3 adds these features and themes to the C# language:</span></span>

- [<span data-ttu-id="ef7b8-109">タプルと破棄</span><span class="sxs-lookup"><span data-stu-id="ef7b8-109">Tuples and discards</span></span>](#tuples-and-discards)
  - <span data-ttu-id="ef7b8-110">複数のパブリック フィールドを含む、軽量で名前のない型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-110">You can create lightweight, unnamed types that contain multiple public fields.</span></span> <span data-ttu-id="ef7b8-111">コンパイラおよび IDE ツールでは、このような型のセマンティクスが認識されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-111">Compilers and IDE tools understand the semantics of these types.</span></span>
  - <span data-ttu-id="ef7b8-112">破棄は、割り当てられた値を考慮しない場合に割り当てで使用された、一時的な書き込み専用の値です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-112">Discards are temporary, write-only variables used in assignments when you don't care about the value assigned.</span></span> <span data-ttu-id="ef7b8-113">タプルおよびユーザー定義の型を分解する場合や、メソッドを `out` パラメーターを使用して呼び出す場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-113">They're most useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.</span></span>
- [<span data-ttu-id="ef7b8-114">パターン一致</span><span class="sxs-lookup"><span data-stu-id="ef7b8-114">Pattern Matching</span></span>](#pattern-matching)
  - <span data-ttu-id="ef7b8-115">これらの型のメンバーの任意の型と値に基づいて、分岐ロジックを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-115">You can create branching logic based on arbitrary types and values of the members of those types.</span></span>
- [<span data-ttu-id="ef7b8-116">`async` `Main`メソッド</span><span class="sxs-lookup"><span data-stu-id="ef7b8-116">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="ef7b8-117">アプリケーションのエントリ ポイントに `async` 修飾子を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-117">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="ef7b8-118">ローカル関数</span><span class="sxs-lookup"><span data-stu-id="ef7b8-118">Local Functions</span></span>](#local-functions)
  - <span data-ttu-id="ef7b8-119">関数を他の関数の中に入れ子にして、関数のスコープと可視性を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-119">You can nest functions inside other functions to limit their scope and visibility.</span></span>
- [<span data-ttu-id="ef7b8-120">式形式のメンバーの追加</span><span class="sxs-lookup"><span data-stu-id="ef7b8-120">More expression-bodied members</span></span>](#more-expression-bodied-members)
  - <span data-ttu-id="ef7b8-121">式を使用して作成できるメンバーが増加しました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-121">The list of members that can be authored using expressions has grown.</span></span>
- [<span data-ttu-id="ef7b8-122">`throw` 式</span><span class="sxs-lookup"><span data-stu-id="ef7b8-122">`throw` Expressions</span></span>](#throw-expressions)
  - <span data-ttu-id="ef7b8-123">`throw` がステートメントだったためにこれまで許可されなかったコード コンストラクトで例外をスローできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-123">You can throw exceptions in code constructs that previously weren't allowed because `throw` was a statement.</span></span>
- [<span data-ttu-id="ef7b8-124">`default` リテラル式</span><span class="sxs-lookup"><span data-stu-id="ef7b8-124">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="ef7b8-125">ターゲットの種類を推論できるとき、既定の値式で既定のリテラル式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-125">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="ef7b8-126">数値リテラルの構文の改善</span><span class="sxs-lookup"><span data-stu-id="ef7b8-126">Numeric literal syntax improvements</span></span>](#numeric-literal-syntax-improvements)
  - <span data-ttu-id="ef7b8-127">新しいトークンにより、数値定数の読みやすさが向上します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-127">New tokens improve readability for numeric constants.</span></span>
- [<span data-ttu-id="ef7b8-128">`out` 変数</span><span class="sxs-lookup"><span data-stu-id="ef7b8-128">`out` variables</span></span>](#out-variables)
  - <span data-ttu-id="ef7b8-129">`out` の値は、それが使用されるメソッドの引数としてインラインで宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-129">You can declare `out` values inline as arguments to the method where they're used.</span></span>
- [<span data-ttu-id="ef7b8-130">末尾以外の名前付き引数</span><span class="sxs-lookup"><span data-stu-id="ef7b8-130">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="ef7b8-131">名前付き引数の後ろに位置引数を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-131">Named arguments can be followed by positional arguments.</span></span>
- [<span data-ttu-id="ef7b8-132">`private protected` アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="ef7b8-132">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="ef7b8-133">`private protected` アクセス修飾子によって、同じアセンブリ内の派生クラスのアクセスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-133">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
- [<span data-ttu-id="ef7b8-134">オーバーロード解決の改善</span><span class="sxs-lookup"><span data-stu-id="ef7b8-134">Improved overload resolution</span></span>](#improved-overload-candidates)
  - <span data-ttu-id="ef7b8-135">オーバーロードの解決のあいまいさを解決するための新しい規則。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-135">New rules to resolve overload resolution ambiguity.</span></span>
- [<span data-ttu-id="ef7b8-136">安全で効率的なコードを記述するための手法</span><span class="sxs-lookup"><span data-stu-id="ef7b8-136">Techniques for writing safe efficient code</span></span>](#enabling-more-efficient-safe-code)
  - <span data-ttu-id="ef7b8-137">参照セマンティクスを使用したさまざまな値の型の使用を有効にする、構文の機能強化の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-137">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>

<span data-ttu-id="ef7b8-138">最後に、コンパイラに新しいオプションが追加されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-138">Finally, the compiler has new options:</span></span>

- <span data-ttu-id="ef7b8-139">`-refout` と `-refonly`: [参照アセンブリの生成](#reference-assembly-generation)を制御します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-139">`-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>
- <span data-ttu-id="ef7b8-140">`-publicsign`: オープン ソース ソフトウェア (OSS) のアセンブリの署名を可能にします。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-140">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="ef7b8-141">`-pathmap`: ソース ディレクトリのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-141">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="ef7b8-142">この記事の残りでは、各機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-142">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="ef7b8-143">各機能について、背後にある論拠と構文について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-143">For each feature, you'll learn the reasoning behind it and the syntax.</span></span> <span data-ttu-id="ef7b8-144">`dotnet try` グローバル ツールを使って、これらの機能をご自身の環境で調べることができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-144">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="ef7b8-145">[dotnet try](https://github.com/dotnet/try/blob/master/README.md#setup) グローバル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-145">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="ef7b8-146">[dotnet/try-samples](https://github.com/dotnet/try-samples) リポジトリを複製します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-146">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="ef7b8-147">現在のディレクトリを、*try-samples* リポジトリの *csharp7* サブディレクトリに設定します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-147">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="ef7b8-148">`dotnet try` を実行します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-148">Run `dotnet try`.</span></span>

## <a name="tuples-and-discards"></a><span data-ttu-id="ef7b8-149">タプルと破棄</span><span class="sxs-lookup"><span data-stu-id="ef7b8-149">Tuples and discards</span></span>

<span data-ttu-id="ef7b8-150">C# には、設計の意図を説明するために使用される、クラスと構造体の豊富な構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-150">C# provides a rich syntax for classes and structs that is used to explain your design intent.</span></span> <span data-ttu-id="ef7b8-151">ところが、場合によっては、その豊富な構文を使用するために、余分な作業が必要になることがあります。この場合、メリットはごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-151">But sometimes that rich syntax requires extra work with minimal benefit.</span></span> <span data-ttu-id="ef7b8-152">複数のデータ要素を含む単純な構造を必要とするメソッドを記述することはよくあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-152">You may often write methods that need a simple structure containing more than one data element.</span></span> <span data-ttu-id="ef7b8-153">このようなシナリオをサポートするために、C# には "*タプル*" が追加されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-153">To support these scenarios *tuples* were added to C#.</span></span> <span data-ttu-id="ef7b8-154">タプルとは、データ メンバーを表す複数のフィールドを含む軽量なデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-154">Tuples are lightweight data structures that contain multiple fields to represent the data members.</span></span> <span data-ttu-id="ef7b8-155">フィールドは検証されず、独自のメソッドを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-155">The fields aren't validated, and you can't define your own methods.</span></span> <span data-ttu-id="ef7b8-156">C# のタプル型は、`==` と `!=` をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-156">C# tuple types support `==` and `!=`.</span></span> <span data-ttu-id="ef7b8-157">詳しくは、</span><span class="sxs-lookup"><span data-stu-id="ef7b8-157">For more information.</span></span>

> [!NOTE]
> <span data-ttu-id="ef7b8-158">タプルは C# 7.0 より前で使用できましたが、効率的でなく、言語サポートがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-158">Tuples were available before C# 7.0, but they were inefficient and had no language support.</span></span> <span data-ttu-id="ef7b8-159">これは、タプル要素が `Item1` や `Item2` などとしてのみ参照できることを意味しました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-159">This meant that tuple elements could only be referenced as `Item1`, `Item2` and so on.</span></span> <span data-ttu-id="ef7b8-160">C# 7.0 では、タプルの言語サポートが導入されたことで、新しい、より効率的なタプル型を使用するフィールドのセマンティック名が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-160">C# 7.0 introduces language support for tuples, which enables semantic names for the fields of a tuple using new, more efficient tuple types.</span></span>

<span data-ttu-id="ef7b8-161">各メンバーに値を割り当て、任意でタプルの各メンバーにセマンティック名を付けることでタプルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-161">You can create a tuple by assigning a value to each member, and optionally providing semantic names to each of the members of the tuple:</span></span>

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

<span data-ttu-id="ef7b8-162">`namedLetters` タプルには、`Alpha` と `Beta` と呼ばれるフィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-162">The `namedLetters` tuple contains fields referred to as `Alpha` and `Beta`.</span></span> <span data-ttu-id="ef7b8-163">これらの名前は、コンパイル時にのみ存在し、実行時にリフレクションを使用してタプルを検査するときなどには保持されません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-163">Those names exist only at compile time and aren't preserved, for example when inspecting the tuple using reflection at run time.</span></span>

<span data-ttu-id="ef7b8-164">タプルの割り当てでは、代入の右辺でフィールドの名前を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-164">In a tuple assignment, you can also specify the names of the fields on the right-hand side of the assignment:</span></span>

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

<span data-ttu-id="ef7b8-165">状況によっては、メソッドから返されたタプルのメンバーをばらすことが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-165">There may be times when you want to unpackage the members of a tuple that were returned from a method.</span></span>  <span data-ttu-id="ef7b8-166">そのためには、タプル内のそれぞれの値に対して別個の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-166">You can do that by declaring separate variables for each of the values in the tuple.</span></span> <span data-ttu-id="ef7b8-167">このばらす行為は、タプルの *分解* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-167">This unpackaging is called *deconstructing* the tuple:</span></span>

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

<span data-ttu-id="ef7b8-168">.NET でも任意の型に同様の分解を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-168">You can also provide a similar deconstruction for any type in .NET.</span></span> <span data-ttu-id="ef7b8-169">クラスのメンバーとして `Deconstruct` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-169">You write a `Deconstruct` method as a member of the class.</span></span> <span data-ttu-id="ef7b8-170">その `Deconstruct` メソッドは、抽出する各プロパティ用に一連の `out` 引数を提供します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-170">That `Deconstruct` method provides a set of `out` arguments for each of the properties you want to extract.</span></span> <span data-ttu-id="ef7b8-171">次の `Point` クラスを考えてみましょう。このクラスは、`X` 座標と `Y` 座標を抽出するデコンストラクター メソッドを指定しています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-171">Consider this `Point` class that provides a deconstructor method that extracts the `X` and `Y` coordinates:</span></span>

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

<span data-ttu-id="ef7b8-172">`Point` をタプルに割り当てて、個々のフィールドを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-172">You can extract the individual fields by assigning a `Point` to a tuple:</span></span>

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

<span data-ttu-id="ef7b8-173">タプルを何度初期化しても、代入の右項に使用される変数は、タプル要素に使用するものと同じ名前になります。タプル要素の名前は、タプルの初期化に使用される変数から推測できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-173">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements: The names of tuple elements can be inferred from the variables used to initialize the tuple:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="ef7b8-174">この機能の詳細については、[タプルの型](../language-reference/builtin-types/value-tuples.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-174">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

<span data-ttu-id="ef7b8-175">`out` パラメーターを使用してタプルを分解したりメソッドを呼び出したりする場合に、使用する予定がなく、考慮にも入れない値の変数の定義を強制されることが多くあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-175">Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use.</span></span> <span data-ttu-id="ef7b8-176">C# ではこのシナリオを処理するために *破棄* のサポートを追加しています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-176">C# adds support for *discards* to handle this scenario.</span></span> <span data-ttu-id="ef7b8-177">破棄は名前が `_` (アンダースコア (_) 文字) の書き込み専用の変数で、破棄するすべての値をこの 1 つの変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-177">A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable.</span></span> <span data-ttu-id="ef7b8-178">破棄は未割り当ての変数に似ています。代入ステートメントとは異なり、破棄はコードで使用できません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-178">A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.</span></span>

<span data-ttu-id="ef7b8-179">次のシナリオでは破棄はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-179">Discards are supported in the following scenarios:</span></span>

- <span data-ttu-id="ef7b8-180">タプルまたはユーザー定義の型を分解する場合。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-180">When deconstructing tuples or user-defined types.</span></span>
- <span data-ttu-id="ef7b8-181">[out](../language-reference/keywords/out-parameter-modifier.md) パラメーターを使用してメソッドを呼び出す場合。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-181">When calling methods with [out](../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>
- <span data-ttu-id="ef7b8-182">[is](../language-reference/keywords/is.md) および [switch](../language-reference/keywords/switch.md) ステートメントによるパターン マッチング操作。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-182">In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.</span></span>
- <span data-ttu-id="ef7b8-183">割り当ての値を破棄として明示的に識別する必要がある場合の、スタンドアロン識別子。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-183">As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.</span></span>

<span data-ttu-id="ef7b8-184">次の例では、ある都市の 2 つの異なる年度のデータを含む 6 つのタプルを戻す `QueryCityDataForYears` メソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-184">The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains data for a city for two different years.</span></span> <span data-ttu-id="ef7b8-185">この例のメソッド呼び出しでは、メソッドによって戻された 2 つの人口の値のみが考慮されているため、タプルの残りの値はタプルの分解時に破棄として扱われます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-185">The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.</span></span>

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="ef7b8-186">詳細については、[破棄](../discards.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-186">For more information, see [Discards](../discards.md).</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="ef7b8-187">パターン マッチング</span><span class="sxs-lookup"><span data-stu-id="ef7b8-187">Pattern matching</span></span>

<span data-ttu-id="ef7b8-188">"*パターン マッチング*" は、コード内の制御フローを新しい方法で表現できるようにする一連の機能です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-188">*Pattern matching* is a set of features that enable new ways to express control flow in your code.</span></span> <span data-ttu-id="ef7b8-189">変数の型、値、またはプロパティの値をテストできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-189">You can test variables for their type, values or the values of their properties.</span></span> <span data-ttu-id="ef7b8-190">これらの手法により、より読みやすいコード フローが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-190">These techniques create more readable code flow.</span></span>

<span data-ttu-id="ef7b8-191">パターン マッチングでは、`is` 式と `switch` 式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-191">Pattern matching supports `is` expressions and `switch` expressions.</span></span> <span data-ttu-id="ef7b8-192">どちらの式でも、オブジェクトとそのプロパティを検査して、そのオブジェクトが必要なパターンを満たしているかどうかを判定できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-192">Each enables inspecting an object and its properties to determine if that object satisfies the sought pattern.</span></span> <span data-ttu-id="ef7b8-193">パターンに追加の規則を指定するには、`when` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-193">You use the `when` keyword to specify additional rules to the pattern.</span></span>

<span data-ttu-id="ef7b8-194">`is` パターン式を使用すると、使い慣れた [`is` 演算子](../language-reference/keywords/is.md#pattern-matching-with-is)を拡張し、その型を超えてオブジェクトを照会したり、1 つの命令で結果を割り当てたりできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-194">The `is` pattern expression extends the familiar [`is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) to query an object about its type and assign the result in one instruction.</span></span> <span data-ttu-id="ef7b8-195">次のコードでは、変数が `int` であるかどうかが確認されます。int の場合、現在の合計に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-195">The following code checks if a variable is an `int`, and if so, adds it to the current sum:</span></span>

```csharp
if (input is int count)
    sum += count;
```

<span data-ttu-id="ef7b8-196">先の小さな例では、`is` 式の拡張が示されています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-196">The preceding small example demonstrates the enhancements to the `is` expression.</span></span> <span data-ttu-id="ef7b8-197">値の型や参照型に対してテストしたり、正しい型の新しい変数に成功した結果を割り当てたりできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-197">You can test against value types as well as reference types, and you can assign the successful result to a new variable of the correct type.</span></span>

<span data-ttu-id="ef7b8-198">switch 一致式には、既に C# 言語に含まれている `switch` ステートメントに基づいた、使い慣れた構文があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-198">The switch match expression has a familiar syntax, based on the `switch` statement already part of the C# language.</span></span> <span data-ttu-id="ef7b8-199">更新された switch 式には新しいコンストラクトがいくつか含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-199">The updated switch statement has several new constructs:</span></span>

- <span data-ttu-id="ef7b8-200">`switch` 式を制御する型は、整数型、`Enum` 型、`string`、あるいはそれらの型のいずれかに対応する null 許容型に制限されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-200">The governing type of a `switch` expression is no longer restricted to integral types, `Enum` types, `string`, or a nullable type corresponding to one of those types.</span></span> <span data-ttu-id="ef7b8-201">任意の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-201">Any type may be used.</span></span>
- <span data-ttu-id="ef7b8-202">各 `case` ラベルで `switch` 式の型をテストできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-202">You can test the type of the `switch` expression in each `case` label.</span></span> <span data-ttu-id="ef7b8-203">`is` 式と同様に、その型に新しい変数を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-203">As with the `is` expression, you may assign a new variable to that type.</span></span>
- <span data-ttu-id="ef7b8-204">`when` 句を追加し、その変数で条件をさらにテストできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-204">You may add a `when` clause to further test conditions on that variable.</span></span>
- <span data-ttu-id="ef7b8-205">`case` ラベルの順序が重要になります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-205">The order of `case` labels is now important.</span></span> <span data-ttu-id="ef7b8-206">一致する最初の分岐が実行されます。他の分岐はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-206">The first branch to match is executed; others are skipped.</span></span>

<span data-ttu-id="ef7b8-207">次のコードでこれらの新しい機能を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-207">The following code demonstrates these new features:</span></span>

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- <span data-ttu-id="ef7b8-208">`case 0:` はおなじみの定数パターンです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-208">`case 0:` is the familiar constant pattern.</span></span>
- <span data-ttu-id="ef7b8-209">`case IEnumerable<int> childSequence:` は型パターンです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-209">`case IEnumerable<int> childSequence:` is a type pattern.</span></span>
- <span data-ttu-id="ef7b8-210">`case int n when n > 0:` は `when` 条件が追加された型パターンです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-210">`case int n when n > 0:` is a type pattern with an additional `when` condition.</span></span>
- <span data-ttu-id="ef7b8-211">`case null:` は null パターンです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-211">`case null:` is the null pattern.</span></span>
- <span data-ttu-id="ef7b8-212">`default:` はおなじみの既定ケースです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-212">`default:` is the familiar default case.</span></span>

<span data-ttu-id="ef7b8-213">C#7.1 以降では、`is` 型パターンと `switch` 型パターンのパターン式は、ジェネリック型パラメーターの型を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-213">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="ef7b8-214">これは `struct` 型か `class` 型のいずれかである可能性がある型を確認し、ボックス化を回避するときに最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-214">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

<span data-ttu-id="ef7b8-215">パターン マッチングの詳細については、[C# のパターン マッチング](../pattern-matching.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-215">You can learn more about pattern matching in [Pattern Matching in C#](../pattern-matching.md).</span></span>

## <a name="async-main"></a><span data-ttu-id="ef7b8-216">async main</span><span class="sxs-lookup"><span data-stu-id="ef7b8-216">Async main</span></span>

<span data-ttu-id="ef7b8-217">*async main* メソッドにより、`Main` メソッドで `await` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-217">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="ef7b8-218">以前は次のように記述する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-218">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="ef7b8-219">それが次のように記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-219">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="ef7b8-220">プログラムによって終了コードが返されない場合、<xref:System.Threading.Tasks.Task> を返す `Main` メソッドを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-220">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="ef7b8-221">プログラミング ガイドの [async main](../programming-guide/main-and-command-args/index.md) の記事に詳細があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-221">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="local-functions"></a><span data-ttu-id="ef7b8-222">ローカル関数</span><span class="sxs-lookup"><span data-stu-id="ef7b8-222">Local functions</span></span>

<span data-ttu-id="ef7b8-223">クラスの多くの設計には、1 つの場所からのみ呼び出されるメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-223">Many designs for classes include methods that are called from only one location.</span></span> <span data-ttu-id="ef7b8-224">このような追加のプライベート メソッドを使用することで、各メソッドのサイズを小さくし、その焦点を絞ることができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-224">These additional private methods keep each method small and focused.</span></span> <span data-ttu-id="ef7b8-225">*ローカル関数* を使用すると、別のメソッドのコンテキスト内でメソッドを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-225">*Local functions* enable you to declare methods inside the context of another method.</span></span> <span data-ttu-id="ef7b8-226">ローカル関数のおかげで、クラスを読み取る際に、ローカル メソッドはそれ自体が宣言されているコンテキストからしか呼び出されないことが、簡単にわかります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-226">Local functions make it easier for readers of the class to see that the local method is only called from the context in which it is declared.</span></span>

<span data-ttu-id="ef7b8-227">ローカル関数には、パブリック反復子メソッドとパブリック非同期メソッドという 2 つの一般的なユース ケースがあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-227">There are two common use cases for local functions: public iterator methods and public async methods.</span></span> <span data-ttu-id="ef7b8-228">どちらの種類のメソッドも、プログラマーが期待するよりも遅くエラーを報告するコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-228">Both types of methods generate code that reports errors later than programmers might expect.</span></span> <span data-ttu-id="ef7b8-229">反復子メソッドの場合、例外が検出されるのは、返されたシーケンスを列挙するコードを呼び出した場合のみです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-229">In iterator methods, any exceptions are observed only when calling code that enumerates the returned sequence.</span></span> <span data-ttu-id="ef7b8-230">非同期メソッドの場合、例外が検出されるのは、返された `Task` が待機状態になったときのみです。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-230">In async methods, any exceptions are only observed when the returned `Task` is awaited.</span></span> <span data-ttu-id="ef7b8-231">次の例では、ローカル関数を使用し、反復子の実装からパラメーター検証を分ける動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-231">The following example demonstrates separating parameter validation from the iterator implementation using a local function:</span></span>

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

<span data-ttu-id="ef7b8-232">同じ手法を `async` メソッドで使用すると、引数の検証で発生する例外が非同期操作の開始前にスローされることを保証できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-232">The same technique can be employed with `async` methods to ensure that exceptions arising from argument validation are thrown before the asynchronous work begins:</span></span>

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

<span data-ttu-id="ef7b8-233">次の構文がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-233">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="ef7b8-234">属性 `SomeThingAboutFieldAttribute` は、`SomeProperty` のコンパイラによって生成されるバッキング フィールドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-234">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="ef7b8-235">詳しくは、C# プログラミング ガイドの「[属性](../programming-guide/concepts/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-235">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

> [!NOTE]
> <span data-ttu-id="ef7b8-236">ローカル関数によってサポートされる設計の中には、"*ラムダ式*" を使用して実現できるものもあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-236">Some of the designs that are supported by local functions can also be accomplished using *lambda expressions*.</span></span> <span data-ttu-id="ef7b8-237">詳細については、[ローカル関数とラムダ式](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-237">For more information, see [Local functions vs. lambda expressions](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span></span>

## <a name="more-expression-bodied-members"></a><span data-ttu-id="ef7b8-238">式形式のメンバーの追加</span><span class="sxs-lookup"><span data-stu-id="ef7b8-238">More expression-bodied members</span></span>

<span data-ttu-id="ef7b8-239">C# 6 では、メンバー関数の式形式のメンバーと読み取り専用プロパティが導入されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-239">C# 6 introduced expression-bodied members for member functions and read-only properties.</span></span> <span data-ttu-id="ef7b8-240">C# 7.0 では、式として実装できる許可されたメンバーが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-240">C# 7.0 expands the allowed members that can be implemented as expressions.</span></span> <span data-ttu-id="ef7b8-241">C# 7.0 では、"*コンストラクター*"、"*ファイナライザー*"、`get` アクセサー、および `set` アクセサーを "*プロパティ*" と "*インデクサー*" に実装できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-241">In C# 7.0, you can implement *constructors*, *finalizers*, and `get` and `set` accessors on *properties* and *indexers*.</span></span> <span data-ttu-id="ef7b8-242">それぞれの例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-242">The following code shows examples of each:</span></span>

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> <span data-ttu-id="ef7b8-243">この例ではファイナライザーは必要ありませんが、その構文を紹介するために示しています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-243">This example does not need a finalizer, but it is shown to demonstrate the syntax.</span></span> <span data-ttu-id="ef7b8-244">アンマネージ リソースを解放する必要がない限り、クラスにファイナライザーを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-244">You should not implement a finalizer in your class unless it is necessary to  release unmanaged resources.</span></span> <span data-ttu-id="ef7b8-245">また、アンマネージ リソースを直接管理する代わりに、<xref:System.Runtime.InteropServices.SafeHandle> クラスの使用を検討する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-245">You should also consider using the <xref:System.Runtime.InteropServices.SafeHandle> class instead of managing unmanaged resources directly.</span></span>

<span data-ttu-id="ef7b8-246">式形式のメンバー用のこれらの新しい場所は、C# 言語の重要なマイルストーンです。これらの機能は、オープン ソースの [Roslyn](https://github.com/dotnet/Roslyn) プロジェクトに関わるコミュニティ メンバーによって実装されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-246">These new locations for expression-bodied members represent an important milestone for the C# language: These features were implemented by community members working on the open-source [Roslyn](https://github.com/dotnet/Roslyn) project.</span></span>

<span data-ttu-id="ef7b8-247">メソッドを式のようなメンバーに変更することは、[バイナリ互換性がある変更](version-update-considerations.md#binary-compatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-247">Changing a method to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="throw-expressions"></a><span data-ttu-id="ef7b8-248">throw 式</span><span class="sxs-lookup"><span data-stu-id="ef7b8-248">Throw expressions</span></span>

<span data-ttu-id="ef7b8-249">C# では、`throw` は常にステートメントでした。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-249">In C#, `throw` has always been a statement.</span></span> <span data-ttu-id="ef7b8-250">`throw` は式ではなくステートメントであるため、使用できない C# コンストラクトがありました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-250">Because `throw` is a statement, not an expression, there were C# constructs where you couldn't use it.</span></span> <span data-ttu-id="ef7b8-251">これには、条件式、null 結合式、および一部のラムダ式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-251">These included conditional expressions, null coalescing expressions, and some lambda expressions.</span></span> <span data-ttu-id="ef7b8-252">式形式のメンバーが追加されたことにより、さらに多くの場所で `throw` 式が役に立つようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-252">The addition of expression-bodied members adds more locations where `throw` expressions would be useful.</span></span> <span data-ttu-id="ef7b8-253">C# 7.0 では、このようなコンストラクトを記述できるように、[*throw 式*](../language-reference/keywords/throw.md#the-throw-expression)が導入されています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-253">So that you can write any of these constructs, C# 7.0 introduces [*throw expressions*](../language-reference/keywords/throw.md#the-throw-expression).</span></span>

<span data-ttu-id="ef7b8-254">この導入により、式ベースのコードをたくさん記述することが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-254">This addition makes it easier to write more expression-based code.</span></span> <span data-ttu-id="ef7b8-255">エラー チェックのためにステートメントを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-255">You don't need additional statements for error checking.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="ef7b8-256">既定のリテラル式</span><span class="sxs-lookup"><span data-stu-id="ef7b8-256">Default literal expressions</span></span>

<span data-ttu-id="ef7b8-257">既定のリテラル式は既定の値式の拡張版です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-257">Default literal expressions are an enhancement to default value expressions.</span></span> <span data-ttu-id="ef7b8-258">これらの式によって変数が初期化され、既定値になります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-258">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="ef7b8-259">以前は次のように記述していました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-259">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="ef7b8-260">それが今では、初期化の右項で種類を省略できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-260">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="ef7b8-261">詳しくは、「[default 演算子](../language-reference/operators/default.md)」記事の「[default リテラル](../language-reference/operators/default.md#default-literal)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-261">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="numeric-literal-syntax-improvements"></a><span data-ttu-id="ef7b8-262">数値リテラルの構文の改善</span><span class="sxs-lookup"><span data-stu-id="ef7b8-262">Numeric literal syntax improvements</span></span>

<span data-ttu-id="ef7b8-263">数値定数を読み間違えると、コードを初めて読むときにコードを理解するのが難しくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-263">Misreading numeric constants can make it harder to understand code when reading it for the first time.</span></span> <span data-ttu-id="ef7b8-264">ビット マスクやその他の記号を用いた値では誤解を招きやすくなります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-264">Bit masks or other symbolic values are prone to misunderstanding.</span></span> <span data-ttu-id="ef7b8-265">C# 7.0 では、使用目的に応じて最も読みやすい形式で数値を記述しできるように、*バイナリ リテラル* と *桁区切り文字* という 2 つの新機能が導入されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-265">C# 7.0 includes two new features to write numbers in the most readable fashion for the intended use: *binary literals*, and *digit separators*.</span></span>

<span data-ttu-id="ef7b8-266">ビット マスクを作成しているときや、数値をバイナリで表現するとコードが最も読みやすくなる場合は、数字をバイナリで記述します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-266">For those times when you're creating bit masks, or whenever a binary representation of a number makes the most readable code, write that number in binary:</span></span>

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

<span data-ttu-id="ef7b8-267">定数の先頭にある `0b` は、数値が 2 進数として記述されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-267">The `0b` at the beginning of the constant indicates that the number is written as a binary number.</span></span> <span data-ttu-id="ef7b8-268">2 進数は長くなる可能性があるため、前の例の 2 進定数に示されているように、`_` を桁区切り文字として導入すると、ビット パターンが見やすくなることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-268">Binary numbers can get long, so it's often easier to see the bit patterns by introducing the `_` as a digit separator, as shown in the binary constant in the preceding example.</span></span> <span data-ttu-id="ef7b8-269">桁区切り記号は定数のどこにでも置くことができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-269">The digit separator can appear anywhere in the constant.</span></span> <span data-ttu-id="ef7b8-270">10 進数の場合は、3 桁の区切り記号として使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-270">For base 10 numbers, it is common to use it as a thousands separator.</span></span> <span data-ttu-id="ef7b8-271">16 進と 2 進の数値リテラルの先頭に `_` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-271">Hex and binary numeric literals may begin with an `_`:</span></span>

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

<span data-ttu-id="ef7b8-272">桁区切り記号は、`decimal` 型、`float` 型、`double` 型でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-272">The digit separator can be used with `decimal`, `float`, and `double` types as well:</span></span>

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

<span data-ttu-id="ef7b8-273">これらをまとめると、数値定数をさらに見やすい状態で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-273">Taken together, you can declare numeric constants with much more readability.</span></span>

## <a name="out-variables"></a><span data-ttu-id="ef7b8-274">`out` 変数</span><span class="sxs-lookup"><span data-stu-id="ef7b8-274">`out` variables</span></span>

<span data-ttu-id="ef7b8-275">`out` パラメーターをサポートする既存の構文は、C# 7 で改良されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-275">The existing syntax that supports `out` parameters has been improved in C# 7.</span></span> <span data-ttu-id="ef7b8-276">現在は、別の宣言ステートメントを記述するのではなく、メソッド呼び出しの引数リストで `out` 変数を宣言できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-276">You can now declare `out` variables in the argument list of a method call, rather than writing a separate declaration statement:</span></span>

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

<span data-ttu-id="ef7b8-277">前の例に示されているように、わかりやすくするために `out` 変数の型を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-277">You may want to specify the type of the `out` variable for clarity, as shown in the preceding example.</span></span> <span data-ttu-id="ef7b8-278">ただし、この言語では、次のように暗黙的に型指定されたローカル変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-278">However, the language does support using an implicitly typed local variable:</span></span>

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- <span data-ttu-id="ef7b8-279">コードが読みやすくなる。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-279">The code is easier to read.</span></span>
  - <span data-ttu-id="ef7b8-280">out 変数は、前のコード行ではなく、使用する場所で宣言します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-280">You declare the out variable where you use it, not on a preceding line of code.</span></span>
- <span data-ttu-id="ef7b8-281">初期値を割り当てる必要がない。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-281">No need to assign an initial value.</span></span>
  - <span data-ttu-id="ef7b8-282">`out` 変数は、メソッド呼び出し内の使用場所で宣言することにより、割り当てる前に誤って使用することがなくなります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-282">By declaring the `out` variable where it's used in a method call, you can't accidentally use it before it is assigned.</span></span>

<span data-ttu-id="ef7b8-283">`out` 変数の宣言を許可するために C# 7.0 に追加された構文が、フィールド初期化子、プロパティ初期化子、コンストラクター初期化子、およびクエリ句を含めるように拡張されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-283">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="ef7b8-284">これにより、次の例に示すようなコードを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-284">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="ef7b8-285">末尾以外の名前付き引数</span><span class="sxs-lookup"><span data-stu-id="ef7b8-285">Non-trailing named arguments</span></span>

<span data-ttu-id="ef7b8-286">メソッド呼び出しで、位置引数の前に名前付き引数を使用できるようになりました。ただし、そのような名前付き引数が正しい位置にある場合です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-286">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="ef7b8-287">詳細については、「[名前付き引数と省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-287">For more information, see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="private-protected-access-modifier"></a><span data-ttu-id="ef7b8-288">*private protected* アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="ef7b8-288">*private protected* access modifier</span></span>

<span data-ttu-id="ef7b8-289">新しい複合アクセス修飾子: `private protected` は、同じアセンブリで宣言されているクラスまたは派生クラスを含むことでメンバーにアクセスできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-289">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="ef7b8-290">`protected internal` は同じアセンブリの派生クラスまたはクラスによるアクセスを許可していますが、`private protected` は同じアセンブリで宣言された派生型へのアクセスを制限しています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-290">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="ef7b8-291">詳細については、言語リファレンスの[アクセス修飾子](../language-reference/keywords/access-modifiers.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-291">For more information, see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="improved-overload-candidates"></a><span data-ttu-id="ef7b8-292">オーバーロード候補の改善</span><span class="sxs-lookup"><span data-stu-id="ef7b8-292">Improved overload candidates</span></span>

<span data-ttu-id="ef7b8-293">すべてのリリースにおいて、あいまいなメソッド呼び出しに対する "明らかな" 選択肢が存在する状況に対応するようにオーバーロードの解決ルールが更新されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-293">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="ef7b8-294">このリリースでは、コンパイラが明らかな選択肢を選択できるようにする 3 つの新しいルールが追加されています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-294">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="ef7b8-295">インスタンス メンバーと静的メンバーの両方がメソッド グループに含まれている場合は、インスタンス レシーバーまたはコンテキストを指定せずにメソッドが呼び出されると、コンパイラがインスタンス メンバーを破棄します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-295">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="ef7b8-296">インスタンス レシーバーを使用してメソッドが呼び出された場合、コンパイラは静的メンバーを破棄します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-296">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="ef7b8-297">レシーバーがない場合、コンパイラは静的メンバーだけを静的コンテキストに含めます。それ以外の場合は、静的メンバーとインスタンス メンバーの両方を含めます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-297">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="ef7b8-298">レシーバーがあいまいなインスタンスまたは型である場合、コンパイラは両方のメンバーを含めます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-298">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="ef7b8-299">暗黙的な `this` インスタンス レシーバーを使用できない静的コンテキストには、`this` が定義されないメンバー (静的メンバーなど) の本体および `this` を使用できない場所 (フィールド初期化子やコンストラクター初期化子など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-299">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="ef7b8-300">型引数が制約を満たしていない複数のジェネリック メソッドがメソッド グループに含まれている場合、そのグループのメンバーは候補セットから削除されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-300">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="ef7b8-301">メソッド グループの変換では、戻り値の型がデリゲートの戻り値の型と一致しない候補メソッドが候補セットから削除されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-301">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="ef7b8-302">適切なメソッドがわかっている場合には、あいまいなメソッドのオーバーロードに対するコンパイラ エラーが少なくなることを認識できるため、この変更点にのみ注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-302">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="ef7b8-303">セーフ コードをより効率的にする</span><span class="sxs-lookup"><span data-stu-id="ef7b8-303">Enabling more efficient safe code</span></span>

<span data-ttu-id="ef7b8-304">アンセーフ コードと同様のパフォーマンスを確保した C# コードを安全に記述できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-304">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="ef7b8-305">セーフ コードは、バッファー オーバーラン、ストレイ ポインター、その他のメモリ アクセス エラーなどのエラーを回避します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-305">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="ef7b8-306">ここで説明する新機能は、検証可能なセーフ コードの機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-306">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="ef7b8-307">安全なコンストラクトを使用してより多くのコードを記述するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-307">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="ef7b8-308">以下に示す機能によって、コードの記述が容易になります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-308">These features make that easier.</span></span>

<span data-ttu-id="ef7b8-309">次の新機能は、セーフ コードのパフォーマンス向上のテーマをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-309">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="ef7b8-310">ピン留めを使用せずに fixed フィールドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-310">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="ef7b8-311">`ref` ローカル変数を再割り当てできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-311">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="ef7b8-312">`stackalloc` 配列で初期化子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-312">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="ef7b8-313">パターンをサポートする型と共に `fixed` ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-313">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="ef7b8-314">追加のジェネリック制約を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-314">You can use additional generic constraints.</span></span>
- <span data-ttu-id="ef7b8-315">パラメーターの `in` 修飾子。引数が参照によって渡されるが、呼び出されたメソッドでは変更されないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-315">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="ef7b8-316">引数に `in` 修飾子を加えることは、[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-316">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="ef7b8-317">メソッド戻りの `ref readonly` 修飾子。メソッドが参照によってその値を戻しますが、そのオブジェクトに対する書き込みを許可しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-317">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="ef7b8-318">戻り値が値に割り当てられている場合、`ref readonly` 修飾子を追加することは、[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-318">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="ef7b8-319">既存の `ref` return ステートメントに `readonly` 修飾子を追加することは、[互換性がない変更](version-update-considerations.md#incompatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-319">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="ef7b8-320">呼び出し元は、`readonly` 修飾子を含むように `ref` ローカル変数の宣言を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-320">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="ef7b8-321">`readonly struct` 宣言。変更不可の構造体で、そのメンバー メソッドの `in` パラメーターとして渡す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-321">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="ef7b8-322">既存の構造体の宣言に `readonly` 修飾子を追加することは、[バイナリ互換性がある変更](version-update-considerations.md#binary-compatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-322">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="ef7b8-323">`ref struct` 宣言。構造体型がマネージド メモリに直接アクセスし、常にスタック割り当てが必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-323">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="ef7b8-324">既存の `struct` の宣言に `ref` 修飾子を追加することは、[互換性がない変更](version-update-considerations.md#incompatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-324">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="ef7b8-325">`ref struct` をクラスのメンバーにすることはできません。また、ヒープ上に割り当てられている可能性がある他の場所で使用することもできません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-325">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="ef7b8-326">これらすべての変更点の詳細については、[安全で効率的なコードを記述する方法](../write-safe-efficient-code.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-326">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

### <a name="ref-locals-and-returns"></a><span data-ttu-id="ef7b8-327">ref ローカル変数と戻り値</span><span class="sxs-lookup"><span data-stu-id="ef7b8-327">Ref locals and returns</span></span>

<span data-ttu-id="ef7b8-328">この機能により、他の場所に定義されている変数への参照を使用したり返したりするアルゴリズムが実現します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-328">This feature enables algorithms that use and return references to variables defined elsewhere.</span></span> <span data-ttu-id="ef7b8-329">1 つの例として、大規模なマトリックスを使用していて、特定の特性を持つ 1 つの場所を探します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-329">One example is working with large matrices, and finding a single location with certain characteristics.</span></span> <span data-ttu-id="ef7b8-330">次のメソッドでは、マトリックスのそのストレージに **参照** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-330">The following method returns a **reference** to that storage in the matrix:</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="ef7b8-331">戻り値を `ref` として宣言し、次のコードのように、マトリックスでその値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-331">You can declare the return value as a `ref` and modify that value in the matrix, as shown in the following code:</span></span>

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

<span data-ttu-id="ef7b8-332">C# 言語には、`ref` ローカル変数と戻り値の誤用を防ぐ規則がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-332">The C# language has several rules that protect you from misusing the `ref` locals and returns:</span></span>

- <span data-ttu-id="ef7b8-333">メソッド シグネチャと、メソッド内のすべての `return` ステートメントに `ref` キーワードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-333">You must add the `ref` keyword to the method signature and to all `return` statements in a method.</span></span>
  - <span data-ttu-id="ef7b8-334">それにより、メソッド全体でメソッドは参照渡しで返すことになります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-334">That makes it clear the method returns by reference throughout the method.</span></span>
- <span data-ttu-id="ef7b8-335">`ref return` は値の変数か `ref` 変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-335">A `ref return` may be assigned to a value variable, or a `ref` variable.</span></span>
  - <span data-ttu-id="ef7b8-336">呼び出し元により、戻り値がコピーされるかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-336">The caller controls whether the return value is copied or not.</span></span> <span data-ttu-id="ef7b8-337">戻り値を割り当てるとき、`ref` 修飾子を省略すると、呼び出し元はストレージの参照ではなく、値のコピーを求めることになります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-337">Omitting the `ref` modifier when assigning the return value indicates that the caller wants a copy of the value, not a reference to the storage.</span></span>
- <span data-ttu-id="ef7b8-338">標準的なメソッドの戻り値を `ref` ローカル変数に割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-338">You can't assign a standard method return value to a `ref` local variable.</span></span>
  - <span data-ttu-id="ef7b8-339">したがって、`ref int i = sequence.Count();` のようなステートメントは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-339">That disallows statements like `ref int i = sequence.Count();`</span></span>
- <span data-ttu-id="ef7b8-340">有効期間がメソッドの実行期間を超えない変数に `ref` を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-340">You can't return a `ref` to a variable whose lifetime doesn't extend beyond the execution of the method.</span></span>
  - <span data-ttu-id="ef7b8-341">つまり、ローカル変数または類似のスコープの変数への参照を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-341">That means you can't return a reference to a local variable or a variable with a similar scope.</span></span>
- <span data-ttu-id="ef7b8-342">`ref` ローカル変数と戻り値は、非同期メソッドと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-342">`ref` locals and returns can't be used with async methods.</span></span>
  - <span data-ttu-id="ef7b8-343">コンパイラは、非同期メソッドが戻るときに、参照先の変数が、最終的な値に設定されているかどうかを認識できません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-343">The compiler can't know if the referenced variable has been set to its final value when the async method returns.</span></span>

<span data-ttu-id="ef7b8-344">ref ローカル変数および ref 戻り値の追加により、値のコピーを回避したり、逆参照操作を複数回実行したりすることで、より効率的なアルゴリズムを実現できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-344">The addition of ref locals and ref returns enables algorithms that are more efficient by avoiding copying values, or performing dereferencing operations multiple times.</span></span>

<span data-ttu-id="ef7b8-345">戻り値に `ref` を追加することは、[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-345">Adding `ref` to the return value is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span> <span data-ttu-id="ef7b8-346">既存のコードはコンパイルされますが、参照戻り値は割り当て時にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-346">Existing code compiles, but the ref return value is copied when assigned.</span></span> <span data-ttu-id="ef7b8-347">呼び出し元は、戻り値を参照として格納するために、戻り値の記憶域を `ref` ローカル変数に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-347">Callers must update the storage for the return value to a `ref` local variable to store the return as a reference.</span></span>

<span data-ttu-id="ef7b8-348">初期化後に別のインスタンスを参照するために、`ref` ローカル変数を再割り当てできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-348">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="ef7b8-349">次のコードがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-349">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="ef7b8-350">詳しくは、[`ref` 戻り値と `ref` ローカル変数](../programming-guide/classes-and-structs/ref-returns.md)に関する記事と [`foreach`](../language-reference/keywords/foreach-in.md) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-350">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

<span data-ttu-id="ef7b8-351">詳しくは、[ref](../language-reference/keywords/ref.md) キーワードに関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-351">For more information, see the [ref keyword](../language-reference/keywords/ref.md) article.</span></span>

### <a name="conditional-ref-expressions"></a><span data-ttu-id="ef7b8-352">条件付きの `ref` 式</span><span class="sxs-lookup"><span data-stu-id="ef7b8-352">Conditional `ref` expressions</span></span>

<span data-ttu-id="ef7b8-353">最後に、条件式で値の結果ではなく参照結果を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-353">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="ef7b8-354">たとえば、次のように記述して、2 つの配列のいずれかに含まれる最初の要素の参照を取得できます</span><span class="sxs-lookup"><span data-stu-id="ef7b8-354">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="ef7b8-355">変数 `r` は、`arr` または `otherArr` の最初の値の参照です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-355">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="ef7b8-356">詳細については、言語リファレンスの[条件演算子 (?:)](../language-reference/operators/conditional-operator.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-356">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>

### <a name="in-parameter-modifier"></a><span data-ttu-id="ef7b8-357">`in` パラメーター修飾子</span><span class="sxs-lookup"><span data-stu-id="ef7b8-357">`in` parameter modifier</span></span>

<span data-ttu-id="ef7b8-358">`in` キーワードは、ref と out の既存のキーワードを補完し、引数を参照で渡します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-358">The `in` keyword complements the existing ref and out keywords to pass arguments by reference.</span></span> <span data-ttu-id="ef7b8-359">`in` キーワードでは、引数を参照で渡すことが指定されますが、呼び出されたメソッドでは値は変更されません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-359">The `in` keyword specifies passing the argument by reference, but the called method doesn't modify the value.</span></span>

<span data-ttu-id="ef7b8-360">次のコードに示すように、値または読み取り専用参照によって渡されるオーバーロードを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-360">You may declare overloads that pass by value or by readonly reference, as shown in the following code:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="ef7b8-361">値によるオーバーロード (前述の例の 1 番目) の方が、読み取り専用参照による方法よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-361">The by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="ef7b8-362">readonly 参照引数を使用してバージョンを呼び出すには、メソッドの呼び出し時に `in` 修飾子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-362">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

<span data-ttu-id="ef7b8-363">詳しくは、[`in` パラメーター修飾子](../language-reference/keywords/in-parameter-modifier.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-363">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="ef7b8-364">`fixed` ステートメントをサポートする型の増加</span><span class="sxs-lookup"><span data-stu-id="ef7b8-364">More types support the `fixed` statement</span></span>

<span data-ttu-id="ef7b8-365">`fixed` ステートメントは、限られた一連の型をサポートしていました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-365">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="ef7b8-366">C# 7.3 以降では、`ref T` または `ref readonly T` を返す `GetPinnableReference()` メソッドを格納する型として `fixed` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-366">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="ef7b8-367">この機能の追加により、`fixed` を <xref:System.Span%601?displayProperty=nameWithType> および関連する型と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-367">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="ef7b8-368">詳しくは、言語リファレンスの [`fixed` ステートメント](../language-reference/keywords/fixed-statement.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-368">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="ef7b8-369">ピン留めが不要な `fixed` フィールドのインデックス付け</span><span class="sxs-lookup"><span data-stu-id="ef7b8-369">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="ef7b8-370">たとえば、次の構造体があるとします。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-370">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="ef7b8-371">以前のバージョンの C# では、`myFixedField` の一部であるいずれかの整数にアクセスするために変数のピン留めが必要でした。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-371">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="ef7b8-372">今では、次のコードは、変数 `p` を別の `fixed` ステートメントの内部にピン留めせずに、コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-372">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="ef7b8-373">変数 `p` は `myFixedField` の 1 個の要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-373">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="ef7b8-374">個別の `int*` 変数を宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-374">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="ef7b8-375">`unsafe` コンテキストは引き続き必要です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-375">You still need an `unsafe` context.</span></span> <span data-ttu-id="ef7b8-376">以前のバージョンの C# では、2 番目の固定ポインターを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-376">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="ef7b8-377">詳細については、[`fixed` ステートメント](../language-reference/keywords/fixed-statement.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-377">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="ef7b8-378">`stackalloc` 配列による初期化子のサポート</span><span class="sxs-lookup"><span data-stu-id="ef7b8-378">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="ef7b8-379">配列を初期化する際に、配列内の要素の値を指定することが可能でした。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-379">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="ef7b8-380">現在では、`stackalloc` で宣言された配列に同じ構文を適用できます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-380">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="ef7b8-381">詳細については、「[`stackalloc` 演算子](../language-reference/operators/stackalloc.md)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-381">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="ef7b8-382">ジェネリック制約の拡張</span><span class="sxs-lookup"><span data-stu-id="ef7b8-382">Enhanced generic constraints</span></span>

<span data-ttu-id="ef7b8-383">型パラメーターの基底クラスの制約として、<xref:System.Enum?displayProperty=nameWithType> 型または <xref:System.Delegate?displayProperty=nameWithType> 型を指定できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-383">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="ef7b8-384">また、新しい `unmanaged` 制約を使用して、型パラメーターが null 非許容で[アンマネージ型](../language-reference/builtin-types/unmanaged-types.md)である必要があることを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-384">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="ef7b8-385">詳しくは、[`where` ジェネリック制約](../language-reference/keywords/where-generic-type-constraint.md)および[型パラメーターの制約](../programming-guide/generics/constraints-on-type-parameters.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-385">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="ef7b8-386">これらの制約を既存の型に追加することは、[互換性のない変更](version-update-considerations.md#incompatible-changes)です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-386">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="ef7b8-387">クローズ ジェネリック型は、これらの新しい制約を満たさなくなります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-387">Closed generic types may no longer meet these new constraints.</span></span>

### <a name="generalized-async-return-types"></a><span data-ttu-id="ef7b8-388">一般化された async の戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ef7b8-388">Generalized async return types</span></span>

<span data-ttu-id="ef7b8-389">非同期メソッドから `Task` オブジェクトを返すと、特定のパスでパフォーマンスのボトルネックが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-389">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="ef7b8-390">`Task` は参照型です。したがって、これを使うことは、オブジェクトを割り当てることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-390">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="ef7b8-391">`async` 修飾子で宣言されたメソッドがキャッシュされた結果を返すか、同期的に完了する場合、追加の割り当ては、コードのパフォーマンスが重要なセクションにおいて大きな時間コストにつながります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-391">In cases where a method declared with the `async` modifier returns a cached result, or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="ef7b8-392">厳密なループ処理でこのような割り当てが発生した場合、コストがかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-392">It can become costly if those allocations occur in tight loops.</span></span>

<span data-ttu-id="ef7b8-393">新しい言語機能では、非同期メソッドの戻り値の型が `Task`、`Task<T>`、`void` に限定されません。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-393">The new language feature means that async method return types aren't limited to `Task`, `Task<T>`, and `void`.</span></span> <span data-ttu-id="ef7b8-394">返される型は引き続き非同期パターンを満たす必要があります。つまり、`GetAwaiter` メソッドはアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-394">The returned type must still satisfy the async pattern, meaning a `GetAwaiter` method must be accessible.</span></span> <span data-ttu-id="ef7b8-395">1 つの具体的な例として、この新しい言語機能を使用するために .NET に `ValueTask` 型が追加されました。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-395">As one concrete example, the `ValueTask` type has been added to .NET to make use of this new language feature:</span></span>

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <span data-ttu-id="ef7b8-396"><xref:System.Threading.Tasks.ValueTask%601> 型を使用するには、NuGet パッケージ [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-396">You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.</span></span>

<span data-ttu-id="ef7b8-397">この機能強化は、ライブラリの作成時、パフォーマンス クリティカルなコードに `Task` を割り当てることを回避する目的で非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-397">This enhancement is most useful for library authors to avoid allocating a `Task` in performance critical code.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="ef7b8-398">新しいコンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="ef7b8-398">New compiler options</span></span>

<span data-ttu-id="ef7b8-399">新しいコンパイラ オプションでは、C# プログラムの新しいビルドと DevOps のシナリオがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-399">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="reference-assembly-generation"></a><span data-ttu-id="ef7b8-400">参照アセンブリ生成</span><span class="sxs-lookup"><span data-stu-id="ef7b8-400">Reference assembly generation</span></span>

<span data-ttu-id="ef7b8-401">"*参照専用アセンブリ*" を生成する新しい 2 つのコンパイラ オプション [-refout](../language-reference/compiler-options/refout-compiler-option.md) と [-refonly](../language-reference/compiler-options/refonly-compiler-option.md) があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-401">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="ef7b8-402">リンク先の記事には、オプションと参照アセンブリに関する詳細があります。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-402">The linked articles explain these options and reference assemblies in more detail.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="ef7b8-403">公開署名またはオープン ソース署名</span><span class="sxs-lookup"><span data-stu-id="ef7b8-403">Public or Open Source signing</span></span>

<span data-ttu-id="ef7b8-404">`-publicsign` コンパイラ オプションは、公開キーを使用してアセンブリに署名するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-404">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="ef7b8-405">アセンブリは署名済みとしてマークされますが、署名は公開キーから取得されます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-405">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="ef7b8-406">このオプションでは、公開キーを使用するオープン ソース プロジェクトから署名済みのアセンブリをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-406">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="ef7b8-407">詳しくは、[-publicsign コンパイラ オプション](../language-reference/compiler-options/publicsign-compiler-option.md)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-407">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="ef7b8-408">pathmap</span><span class="sxs-lookup"><span data-stu-id="ef7b8-408">pathmap</span></span>

<span data-ttu-id="ef7b8-409">`-pathmap` コンパイラ オプションは、ビルド環境からのソース パスをマップ済みのソース パスに置き換えるようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-409">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="ef7b8-410">`-pathmap` オプションは、コンパイラが記述した PDB ファイルまたは <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> のソース パスを制御します。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-410">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="ef7b8-411">詳しくは、[-pathmap コンパイラ オプション](../language-reference/compiler-options/pathmap-compiler-option.md)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef7b8-411">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
