---
title: 破棄 - C# ガイド
description: C# の破棄のサポートについて説明します。破棄は、未割り当てで破棄可能な変数です。また、破棄の使用例についても説明します。
ms.technology: csharp-fundamentals
ms.date: 09/22/2020
ms.openlocfilehash: baa7c559095460cf747cb5c8f7ad581270893bd7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "95698807"
---
# <a name="discards---c-guide"></a><span data-ttu-id="b438e-103">破棄 - C# ガイド</span><span class="sxs-lookup"><span data-stu-id="b438e-103">Discards - C# Guide</span></span>

<span data-ttu-id="b438e-104">C# 7.0 以降では、C# で破棄がサポートされます。これらは、アプリケーション コードで意図的に使用しないプレースホルダー変数です。</span><span class="sxs-lookup"><span data-stu-id="b438e-104">Starting with C# 7.0, C# supports discards, which are placeholder variables that are intentionally unused in application code.</span></span> <span data-ttu-id="b438e-105">破棄は、未割り当ての変数と同等です。つまり、値がありません。</span><span class="sxs-lookup"><span data-stu-id="b438e-105">Discards are equivalent to unassigned variables; they do not have a value.</span></span> <span data-ttu-id="b438e-106">破棄変数は 1 つのみであり、破棄変数には記憶域も割り当てられないため、破棄を使用するとメモリの割り当てを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="b438e-106">Because there is only a single discard variable, and that variable may not even be allocated storage, discards can reduce memory allocations.</span></span> <span data-ttu-id="b438e-107">また、コードの意図がわかりやすくなるため、読みやすさと保守性が向上します。</span><span class="sxs-lookup"><span data-stu-id="b438e-107">Because they make the intent of your code clear, they enhance its readability and maintainability.</span></span>

<span data-ttu-id="b438e-108">変数を破棄と指定するには、変数名にアンダースコア (`_`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b438e-108">You indicate that a variable is a discard by assigning it the underscore (`_`) as its name.</span></span> <span data-ttu-id="b438e-109">たとえば、次のメソッド呼び出しは 3 つのタプルを返します。この 1 つ目と 2 つ目の値が破棄されます。*area* は以前に宣言した変数であり、*GetCityInformation* から返された、対応する 3 つ目のコンポーネントに設定されます。</span><span class="sxs-lookup"><span data-stu-id="b438e-109">For example, the following method call returns a 3-tuple in which the first and second values are discards and *area* is a previously declared variable to be set to the corresponding third component returned by *GetCityInformation*:</span></span>

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

<span data-ttu-id="b438e-110">C# 7.0 以降では、破棄は次のコンテキストの割り当てでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b438e-110">In C# 7.0 and later, discards are supported in assignments in the following contexts:</span></span>

- <span data-ttu-id="b438e-111">タプルとオブジェクトの[分解](deconstruct.md)。</span><span class="sxs-lookup"><span data-stu-id="b438e-111">Tuple and object [deconstruction](deconstruct.md).</span></span>
- <span data-ttu-id="b438e-112">[is](language-reference/keywords/is.md) と [switch](language-reference/keywords/switch.md) によるパターン マッチング。</span><span class="sxs-lookup"><span data-stu-id="b438e-112">Pattern matching with [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md).</span></span>
- <span data-ttu-id="b438e-113">`out` パラメーターを使用したメソッドの呼び出し。</span><span class="sxs-lookup"><span data-stu-id="b438e-113">Calls to methods with `out` parameters.</span></span>
- <span data-ttu-id="b438e-114">`_` がスコープ内にない場合のスタンドアロンの `_`。</span><span class="sxs-lookup"><span data-stu-id="b438e-114">A standalone `_` when no `_` is in scope.</span></span>

<span data-ttu-id="b438e-115">C# 9.0 以降では、破棄を使用して、ラムダ式の未使用の入力パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b438e-115">Beginning with C# 9.0, you can use discards to specify unused input parameters of a lambda expression.</span></span> <span data-ttu-id="b438e-116">詳細については、[ラムダ式](language-reference/operators/lambda-expressions.md)に関する記事の「[ラムダ式の入力パラメーター](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b438e-116">For more information, see the [Input parameters of a lambda expression](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) section of the [Lambda expressions](language-reference/operators/lambda-expressions.md) article.</span></span>

<span data-ttu-id="b438e-117">`_` が有効な破棄の場合、その値を取得しようとすると、または代入演算で使用しようとすると、"名前 '\_' は、現在のコンテキストに存在していません" というコンパイラ エラー CS0301 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b438e-117">When `_` is a valid discard, attempting to retrieve its value or use it in an assignment operation generates compiler error CS0301, "The name '\_' does not exist in the current context".</span></span> <span data-ttu-id="b438e-118">これは、`_` に値が割り当てられておらず、記憶域の場所も割り当てることができないためです。</span><span class="sxs-lookup"><span data-stu-id="b438e-118">This is because `_` is not assigned a value, and may not even be assigned a storage location.</span></span> <span data-ttu-id="b438e-119">実際の変数であれば、前の例のように、複数の値を破棄できません。</span><span class="sxs-lookup"><span data-stu-id="b438e-119">If it were an actual variable, you could not discard more than one value, as the previous example did.</span></span>

## <a name="tuple-and-object-deconstruction"></a><span data-ttu-id="b438e-120">タプルとオブジェクトの分解</span><span class="sxs-lookup"><span data-stu-id="b438e-120">Tuple and object deconstruction</span></span>

<span data-ttu-id="b438e-121">分解は、複数のタプルがあり、アプリケーション コードで一部のタプル要素を使用し、その他の要素を無視する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="b438e-121">Discards are particularly useful in working with tuples when your application code uses some tuple elements but ignores others.</span></span> <span data-ttu-id="b438e-122">たとえば、次の `QueryCityDataForYears` メソッドは、市区町村名、その地域、年、市区町村のその年の人口、2 つ目の年、市区町村のその 2 つ目の年の人口という 6 つのタプルを返します。</span><span class="sxs-lookup"><span data-stu-id="b438e-122">For example, the following `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="b438e-123">この例は、2 つの年の間に変化した人口数を示しています。</span><span class="sxs-lookup"><span data-stu-id="b438e-123">The example shows the change in population between those two years.</span></span> <span data-ttu-id="b438e-124">タプルから使用できるデータのうち、市区町村の地域は使用しません。また、指定時に市区町村名と 2 つの日付はわかっています。</span><span class="sxs-lookup"><span data-stu-id="b438e-124">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="b438e-125">そのため、タプルに格納されている 2 つの人口値のみが必要であり、残りの値は破棄対象として処理できます。</span><span class="sxs-lookup"><span data-stu-id="b438e-125">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="b438e-126">破棄を使用したタプルの分解の詳細については、「[タプルとその他の型の分解](deconstruct.md#deconstructing-tuple-elements-with-discards)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b438e-126">For more information on deconstructing tuples with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-tuple-elements-with-discards).</span></span>

<span data-ttu-id="b438e-127">また、クラス、構造体、またはインターフェイスの `Deconstruct` メソッドを使用すると、オブジェクトから特定セットのデータを取得し、分解することもできます。</span><span class="sxs-lookup"><span data-stu-id="b438e-127">The `Deconstruct` method of a class, structure, or interface also allows you to retrieve and deconstruct a specific set of data from an object.</span></span> <span data-ttu-id="b438e-128">分解された値の一部のみが必要な場合は、破棄を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b438e-128">You can use discards when you are interested in working with only a subset of the deconstructed values.</span></span> <span data-ttu-id="b438e-129">`Person` オブジェクトを 4 つの文字列 (名、姓、市区町村、州) に分解し、姓と州を破棄する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b438e-129">The following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state), but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

<span data-ttu-id="b438e-130">破棄を使用したユーザー定義型の分解の詳細については、「[タプルとその他の型の分解](deconstruct.md#deconstructing-a-user-defined-type-with-discards)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b438e-130">For more information on deconstructing user-defined types with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span></span>

## <a name="pattern-matching-with-switch-and-is"></a><span data-ttu-id="b438e-131">`switch` と `is` を使用したパターン マッチング</span><span class="sxs-lookup"><span data-stu-id="b438e-131">Pattern matching with `switch` and `is`</span></span>

<span data-ttu-id="b438e-132">*破棄パターン* は、[is](language-reference/keywords/is.md) キーワードと [switch](language-reference/keywords/switch.md) キーワードを使用したパターン マッチングで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b438e-132">The *discard pattern* can be used in pattern matching with the [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md) keywords.</span></span> <span data-ttu-id="b438e-133">各式は常に破棄パターンと一致します。</span><span class="sxs-lookup"><span data-stu-id="b438e-133">Every expression always matches the discard pattern.</span></span>

<span data-ttu-id="b438e-134">[is](language-reference/keywords/is.md) ステートメントを使用して、オブジェクトが <xref:System.IFormatProvider> 実装を提供しているかどうかを判断し、オブジェクトが `null` かどうかをテストする `ProvidesFormatInfo` メソッドの定義例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b438e-134">The following example defines a `ProvidesFormatInfo` method that uses [is](language-reference/keywords/is.md) statements to determine whether an object provides an <xref:System.IFormatProvider> implementation and tests whether the object is `null`.</span></span> <span data-ttu-id="b438e-135">また、破棄パターンを使用して、その他の任意の型の null 以外のオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="b438e-135">It also uses the discard pattern to handle non-null objects of any other type.</span></span>

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a><span data-ttu-id="b438e-136">out パラメーターを使用したメソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="b438e-136">Calls to methods with out parameters</span></span>

<span data-ttu-id="b438e-137">`Deconstruct` メソッドを呼び出してユーザー定義型 (クラス、構造体、またはインターフェイスのインスタンス) を分解する場合、個々の `out` 引数の値を破棄できます。</span><span class="sxs-lookup"><span data-stu-id="b438e-137">When calling the `Deconstruct` method to deconstruct a user-defined type (an instance of a class, structure, or interface), you can discard the values of individual `out` arguments.</span></span> <span data-ttu-id="b438e-138">また、out パラメーターを指定して任意のメソッドを呼び出すときに、`out` 引数の値を破棄することもできます。</span><span class="sxs-lookup"><span data-stu-id="b438e-138">But you can also discard the value of `out` arguments when calling any method with an out parameter.</span></span>

<span data-ttu-id="b438e-139">次の例では、[DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) メソッドを呼び出して、現在のカルチャで日付の文字列表現が有効かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="b438e-139">The following example calls the [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) method to determine whether the string representation of a date is valid in the current culture.</span></span> <span data-ttu-id="b438e-140">この例では、日付文字列の検証のみが目的で、解析して日付を抽出する処理は行わないため、メソッドの `out` 引数は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="b438e-140">Because the example is concerned only with validating the date string and not with parsing it to extract the date, the `out` argument to the method is a discard.</span></span>

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a><span data-ttu-id="b438e-141">スタンドアロンの破棄</span><span class="sxs-lookup"><span data-stu-id="b438e-141">A standalone discard</span></span>

<span data-ttu-id="b438e-142">スタンドアロンの破棄を使用して、無視対象として任意の変数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b438e-142">You can use a standalone discard to indicate any variable that you choose to ignore.</span></span> <span data-ttu-id="b438e-143">次の例では、スタンドアロンの破棄を使用して、非同期操作で返される <xref:System.Threading.Tasks.Task> オブジェクトを無視します。</span><span class="sxs-lookup"><span data-stu-id="b438e-143">The following example uses a standalone discard to ignore the <xref:System.Threading.Tasks.Task> object returned by an asynchronous operation.</span></span> <span data-ttu-id="b438e-144">この結果、この処理が完了するときにスローされる例外が抑制される効果があります。</span><span class="sxs-lookup"><span data-stu-id="b438e-144">This has the effect of suppressing the exception that the operation throws as it is about to complete.</span></span>

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

<span data-ttu-id="b438e-145">`_` は有効な識別子でもある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b438e-145">Note that `_` is also a valid identifier.</span></span> <span data-ttu-id="b438e-146">サポートされるコンテキスト以外で `_` を使用すると、破棄対象ではなく、有効な変数として扱われます。</span><span class="sxs-lookup"><span data-stu-id="b438e-146">When used outside of a supported context, `_` is treated not as a discard but as a valid variable.</span></span> <span data-ttu-id="b438e-147">`_` という識別子が既にスコープ内にある場合、スタンドアロンの破棄として `_` を使用すると、次のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="b438e-147">If an identifier named `_` is already in scope, the use of `_` as a standalone discard can result in:</span></span>

- <span data-ttu-id="b438e-148">意図した破棄の値を割り当てることで、スコープ内の `_` 変数の値が誤って変更される。</span><span class="sxs-lookup"><span data-stu-id="b438e-148">Accidental modification of the value of the in-scope `_` variable by assigning it the value of the intended discard.</span></span> <span data-ttu-id="b438e-149">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b438e-149">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- <span data-ttu-id="b438e-150">タイプ セーフに違反するコンパイラ エラーが発生する。</span><span class="sxs-lookup"><span data-stu-id="b438e-150">A compiler error for violating type safety.</span></span> <span data-ttu-id="b438e-151">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b438e-151">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- <span data-ttu-id="b438e-152">コンパイラ エラー CS0136 "ローカルまたはパラメーター '\_' は、その名前が外側のローカルのスコープでローカルやパラメーターの定義に使用されているため、このスコープでは宣言できません" が発生する。</span><span class="sxs-lookup"><span data-stu-id="b438e-152">Compiler error CS0136, "A local or parameter named '\_' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter."</span></span> <span data-ttu-id="b438e-153">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b438e-153">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a><span data-ttu-id="b438e-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="b438e-154">See also</span></span>

- [<span data-ttu-id="b438e-155">タプルとその他の型の分解</span><span class="sxs-lookup"><span data-stu-id="b438e-155">Deconstructing tuples and other types</span></span>](deconstruct.md)
- [<span data-ttu-id="b438e-156">`is` キーワード</span><span class="sxs-lookup"><span data-stu-id="b438e-156">`is` keyword</span></span>](language-reference/keywords/is.md)
- [<span data-ttu-id="b438e-157">`switch` キーワード</span><span class="sxs-lookup"><span data-stu-id="b438e-157">`switch` keyword</span></span>](language-reference/keywords/switch.md)
