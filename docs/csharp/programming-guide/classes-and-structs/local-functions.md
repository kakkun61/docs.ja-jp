---
title: ローカル関数 - C# プログラミング ガイド
description: C# のローカル関数は、別のメンバーの入れ子になっているプライベート メソッドであり、その親メンバーから呼び出すことができます。
ms.date: 10/16/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 75accda2e40443073274ece4d8964c13a0945dad
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332901"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="bc183-103">ローカル関数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="bc183-103">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="bc183-104">C# 7.0 以降、C# では *ローカル関数* がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bc183-104">Starting with C# 7.0, C# supports *local functions* .</span></span> <span data-ttu-id="bc183-105">ローカル関数は、別のメンバーの入れ子になっているタイプのプライベート メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bc183-105">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="bc183-106">親メンバーからのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bc183-106">They can only be called from their containing member.</span></span> <span data-ttu-id="bc183-107">ローカル関数は次の要素で宣言し、呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bc183-107">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="bc183-108">メソッド (特に反復子メソッドと非同期メソッド)</span><span class="sxs-lookup"><span data-stu-id="bc183-108">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="bc183-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="bc183-109">Constructors</span></span>
- <span data-ttu-id="bc183-110">プロパティ アクセサー</span><span class="sxs-lookup"><span data-stu-id="bc183-110">Property accessors</span></span>
- <span data-ttu-id="bc183-111">イベント アクセサー</span><span class="sxs-lookup"><span data-stu-id="bc183-111">Event accessors</span></span>
- <span data-ttu-id="bc183-112">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="bc183-112">Anonymous methods</span></span>
- <span data-ttu-id="bc183-113">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="bc183-113">Lambda expressions</span></span>
- <span data-ttu-id="bc183-114">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="bc183-114">Finalizers</span></span>
- <span data-ttu-id="bc183-115">その他のローカル関数</span><span class="sxs-lookup"><span data-stu-id="bc183-115">Other local functions</span></span>

<span data-ttu-id="bc183-116">ただし、ローカル関数は、式形式のメンバーの内部では宣言できません。</span><span class="sxs-lookup"><span data-stu-id="bc183-116">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="bc183-117">場合によっては、ラムダ式を使用して、ローカル関数でもサポートされている機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-117">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="bc183-118">比較については、「[ローカル関数とラムダ式の比較](#local-functions-vs-lambda-expressions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc183-118">For a comparison, see [Local functions vs. lambda expressions](#local-functions-vs-lambda-expressions).</span></span>

<span data-ttu-id="bc183-119">ローカル関数を使用すると、コードの意図が明確になります。</span><span class="sxs-lookup"><span data-stu-id="bc183-119">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="bc183-120">コードを見た人は、メソッドが親メソッドによってのみ呼び出し可能であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="bc183-120">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="bc183-121">また、チーム プロジェクトの場合は、別の開発者がクラスや構造体の別の場所から誤ってメソッドを直接呼び出すことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="bc183-121">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="bc183-122">ローカル関数の構文</span><span class="sxs-lookup"><span data-stu-id="bc183-122">Local function syntax</span></span>

<span data-ttu-id="bc183-123">ローカル関数は、親メンバーの内側に、入れ子になったメソッドとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-123">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="bc183-124">その定義の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bc183-124">Its definition has the following syntax:</span></span>

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="bc183-125">ローカル関数と共に次の修飾子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-125">You can use the following modifiers with a local function:</span></span>

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- <span data-ttu-id="bc183-126">[`static`](../../language-reference/keywords/static.md) (C# 8.0 以降)。</span><span class="sxs-lookup"><span data-stu-id="bc183-126">[`static`](../../language-reference/keywords/static.md) (in C# 8.0 and later).</span></span> <span data-ttu-id="bc183-127">静的なローカル関数では、ローカル変数やインスタンスの状態をキャプチャすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bc183-127">A static local function can't capture local variables or instance state.</span></span>
- <span data-ttu-id="bc183-128">[`extern`](../../language-reference/keywords/extern.md) (C# 9.0 以降)。</span><span class="sxs-lookup"><span data-stu-id="bc183-128">[`extern`](../../language-reference/keywords/extern.md) (in C# 9.0 and later).</span></span> <span data-ttu-id="bc183-129">外部ローカル関数は `static` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc183-129">An external local function must be `static`.</span></span>

<span data-ttu-id="bc183-130">メソッドのパラメーターを含め、親メンバー内で定義されているすべてのローカル変数は、非静的ローカル関数からアクセス可能です。</span><span class="sxs-lookup"><span data-stu-id="bc183-130">All local variables that are defined in the containing member, including its method parameters, are accessible in a non-static local function.</span></span>

<span data-ttu-id="bc183-131">メソッド定義とは異なり、ローカル関数の定義にメンバー アクセス修飾子を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="bc183-131">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="bc183-132">すべてのローカル関数はプライベートであるため、`private` キーワードなどのアクセス修飾子が含まれていると、コンパイラ エラー CS0106 "修飾子 'private' がこの項目に対して有効ではありません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-132">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

<span data-ttu-id="bc183-133">次の例は、`GetText` というメソッドに対してプライベートな `AppendPathSeparator` というローカル関数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="bc183-133">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

<span data-ttu-id="bc183-134">C# 9.0 以降、次の例に示すように、ローカル関数およびそのパラメーターと型パラメーターに属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-134">Beginning with C# 9.0, you can apply attributes to a local function, its parameters and type parameters, as the following example shows:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

<span data-ttu-id="bc183-135">上の例では、[特殊な属性](../../language-reference/attributes/nullable-analysis.md)を使用して、Null 許容コンテキストでの静的分析に関してコンパイラをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bc183-135">The preceding example uses a [special attribute](../../language-reference/attributes/nullable-analysis.md) to assist the compiler in static analysis in a nullable context.</span></span>

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="bc183-136">ローカル関数と例外</span><span class="sxs-lookup"><span data-stu-id="bc183-136">Local functions and exceptions</span></span>

<span data-ttu-id="bc183-137">ローカル関数の便利な機能の 1 つは、例外を直ちに検出できることです。</span><span class="sxs-lookup"><span data-stu-id="bc183-137">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="bc183-138">メソッド反復子の場合、例外は返されたシーケンスを列挙する時点でしか検出されず、反復子を取得した時点では検出されません。</span><span class="sxs-lookup"><span data-stu-id="bc183-138">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="bc183-139">非同期メソッドの場合、非同期メソッドでスローされた例外は、タスクの戻りを待機中に検出されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-139">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="bc183-140">次の例は、指定した範囲にある奇数を列挙する `OddSequence` メソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="bc183-140">The following example defines an `OddSequence` method that enumerates odd numbers in a specified range.</span></span> <span data-ttu-id="bc183-141">100 より大きい数値を `OddSequence` 列挙子メソッドに渡しているため、メソッドは <xref:System.ArgumentOutOfRangeException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="bc183-141">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="bc183-142">この例の出力が示すように、例外は列挙子を取得したときではなく、数値を反復処理した時点でのみ検出されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-142">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

<span data-ttu-id="bc183-143">反復子ロジックをローカル関数に追加した場合、次の例に示すように、列挙子を取得すると引数の検証例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc183-143">If you put iterator logic into a local function, argument validation exceptions are thrown when you retrieve the enumerator, as the following example shows:</span></span>

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

<span data-ttu-id="bc183-144">ローカル関数は、非同期操作と同様の方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-144">You can use local functions in a similar way with asynchronous operations.</span></span> <span data-ttu-id="bc183-145">非同期メソッドでスローされる例外は、対応するタスクが待機しているときに検出されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-145">Exceptions thrown in an async method surface when the corresponding task is awaited.</span></span> <span data-ttu-id="bc183-146">ローカル関数を使用すると、コードを迅速に失敗させ (Fail Fast)、例外のスローと検出の両方を同時に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc183-146">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="bc183-147">次の例は、`GetMultipleAsync` という非同期メソッドを使用して、指定した秒数だけ一時停止した後、その秒数のランダムな倍数である値を返します。</span><span class="sxs-lookup"><span data-stu-id="bc183-147">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="bc183-148">遅延の最大値は 5 秒です。値が 5 より大きい場合は <xref:System.ArgumentOutOfRangeException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="bc183-148">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="bc183-149">次の例に示すように、`GetMultipleAsync` メソッドに渡された値が 6 の場合にスローされる例外は、タスクが待機中の場合のみ検出されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-149">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is observed only when the task is awaited.</span></span>

:::code language="csharp" source="snippets/local-functions/AsyncWithoutLocal.cs" :::

<span data-ttu-id="bc183-150">メソッド反復子と同様に、前の例をリファクターして、非同期操作のコードをローカル関数に配置できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-150">Like with the method iterator, you can refactor the preceding example and put the code of asynchronous operation in a local function.</span></span> <span data-ttu-id="bc183-151">次の例の出力に示されているように、<xref:System.ArgumentOutOfRangeException> は `GetMultiple` メソッドが呼び出されるとすぐにスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc183-151">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is thrown as soon as the `GetMultiple` method is called.</span></span>

:::code language="csharp" source="snippets/local-functions/AsyncWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a><span data-ttu-id="bc183-152">ローカル関数とラムダ式の比較</span><span class="sxs-lookup"><span data-stu-id="bc183-152">Local functions vs. lambda expressions</span></span>

<span data-ttu-id="bc183-153">一見したところ、ローカル関数と[ラムダ式](../../language-reference/operators/lambda-expressions.md)は、非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="bc183-153">At first glance, local functions and [lambda expressions](../../language-reference/operators/lambda-expressions.md) are very similar.</span></span> <span data-ttu-id="bc183-154">多くの場合、ラムダ式とローカル関数の使用のどちらを選択するかは、スタイルと個人的な好みの問題です。</span><span class="sxs-lookup"><span data-stu-id="bc183-154">In many cases, the choice between using lambda expressions and local functions is a matter of style and personal preference.</span></span> <span data-ttu-id="bc183-155">ただし、どちらか一方を使用できる場合、認識しておくべき実質的な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="bc183-155">However, there are real differences in where you can use one or the other that you should be aware of.</span></span>

<span data-ttu-id="bc183-156">階乗アルゴリズムのローカル関数とラムダ式の実装の違いについて見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="bc183-156">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="bc183-157">ローカル関数を使用するバージョンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc183-157">Here's the version using a local function:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

<span data-ttu-id="bc183-158">このバージョンでは、ラムダ式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-158">This version uses lambda expressions:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

### <a name="naming"></a><span data-ttu-id="bc183-159">名前を付ける</span><span class="sxs-lookup"><span data-stu-id="bc183-159">Naming</span></span>

<span data-ttu-id="bc183-160">ローカル関数には、メソッドと同様に明示的に名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="bc183-160">Local functions are explicitly named like methods.</span></span> <span data-ttu-id="bc183-161">ラムダ式は匿名メソッドであり、`delegate` 型の変数 (通常は `Action` 型または `Func` 型) に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc183-161">Lambda expressions are anonymous methods and need to be assigned to variables of a `delegate` type, typically either `Action` or `Func` types.</span></span> <span data-ttu-id="bc183-162">ローカル関数を宣言する場合、プロセスは通常のメソッドを記述するのと似ています。戻り値の型と関数シグネチャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bc183-162">When you declare a local function, the process is like writing a normal method; you declare a return type and a function signature.</span></span>

### <a name="function-signatures-and-lambda-expression-types"></a><span data-ttu-id="bc183-163">関数シグネチャとラムダ式の型</span><span class="sxs-lookup"><span data-stu-id="bc183-163">Function signatures and lambda expression types</span></span>

<span data-ttu-id="bc183-164">ラムダ式は、引数と戻り値の型を決定するために割り当てられている `Action`/`Func` 変数の型に依存します。</span><span class="sxs-lookup"><span data-stu-id="bc183-164">Lambda expressions rely on the type of the `Action`/`Func` variable that they're assigned to determine the argument and return types.</span></span> <span data-ttu-id="bc183-165">ローカル関数では、構文は通常のメソッドの記述とよく似ているため、引数の型と戻り値の型は既に関数宣言の一部になっています。</span><span class="sxs-lookup"><span data-stu-id="bc183-165">In local functions, since the syntax is much like writing a normal method, argument types and return type are already part of the function declaration.</span></span>

### <a name="definite-assignment"></a><span data-ttu-id="bc183-166">確実な代入</span><span class="sxs-lookup"><span data-stu-id="bc183-166">Definite assignment</span></span>

<span data-ttu-id="bc183-167">ラムダ式は、実行時に宣言されて割り当てられるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="bc183-167">Lambda expressions are objects that are declared and assigned at runtime.</span></span> <span data-ttu-id="bc183-168">ラムダ式を使用するには、その式を確実に代入する必要があります。代入先の `Action`/`Func` 変数と、代入するラムダ式を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc183-168">In order for a lambda expression to be used, it needs to be definitely assigned: the `Action`/`Func` variable that it will be assigned to must be declared and the lambda expression assigned to it.</span></span> <span data-ttu-id="bc183-169">`LambdaFactorial` では、ラムダ式 `nthFactorial` を定義する前に、宣言と初期化を行う必要があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="bc183-169">Notice that `LambdaFactorial` must declare and initialize the lambda expression `nthFactorial` before defining it.</span></span> <span data-ttu-id="bc183-170">その手順を踏まないと、`nthFactorial` の割り当て前に参照することによるコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bc183-170">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>

<span data-ttu-id="bc183-171">ローカル関数は、コンパイル時に定義されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-171">Local functions are defined at compile time.</span></span> <span data-ttu-id="bc183-172">これらは変数に割り当てられないため、 **スコープ内の** どのコードの場所からでも参照できます。最初の `LocalFunctionFactorial` の例では、`return` ステートメントの上または下でローカル関数を宣言して、コンパイラ エラーが発生しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="bc183-172">As they're not assigned to variables, they can be referenced from any code location **where it is in scope** ; in our first example `LocalFunctionFactorial`, we could declare our local function either above or below the `return` statement and not trigger any compiler errors.</span></span>

<span data-ttu-id="bc183-173">これらの違いは、再帰的なアルゴリズムの作成はローカル関数を使用する方が簡単であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bc183-173">These differences mean that recursive algorithms are easier to create using local functions.</span></span> <span data-ttu-id="bc183-174">自身を呼び出すローカル関数を宣言して定義することができます。</span><span class="sxs-lookup"><span data-stu-id="bc183-174">You can declare and define a local function that calls itself.</span></span> <span data-ttu-id="bc183-175">ラムダ式は宣言して、既定値を割り当てないと、同じラムダ式を参照する本体に再割り当てできません。</span><span class="sxs-lookup"><span data-stu-id="bc183-175">Lambda expressions must be declared, and assigned a default value before they can be re-assigned to a body that references the same lambda expression.</span></span>

### <a name="implementation-as-a-delegate"></a><span data-ttu-id="bc183-176">デリゲートとしての実装</span><span class="sxs-lookup"><span data-stu-id="bc183-176">Implementation as a delegate</span></span>

<span data-ttu-id="bc183-177">ラムダ式は、宣言時にデリゲートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-177">Lambda expressions are converted to delegates when they're declared.</span></span> <span data-ttu-id="bc183-178">ローカル関数は、従来のメソッド " *または* " デリゲートと同様に記述できるので、より柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="bc183-178">Local functions are more flexible in that they can be written like a traditional method *or* as a delegate.</span></span> <span data-ttu-id="bc183-179">ローカル関数は、デリゲートとして " ***使用される*** " 場合にのみ、デリゲートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-179">Local functions are only converted to delegates when ***used*** as a delegate.</span></span>

<span data-ttu-id="bc183-180">ローカル関数を宣言し、メソッドのように呼び出して参照のみを行う場合は、デリゲートに変換されません。</span><span class="sxs-lookup"><span data-stu-id="bc183-180">If you declare a local function and only reference it by calling it like a method, it will not be converted to a delegate.</span></span>

### <a name="variable-capture"></a><span data-ttu-id="bc183-181">変数のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="bc183-181">Variable capture</span></span>

<span data-ttu-id="bc183-182">[確実な代入](../../../../_csharplang/spec/variables.md#definite-assignment)のルールは、ローカル関数またはラムダ式でキャプチャされる変数にも影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="bc183-182">The rules of [definite assignment](../../../../_csharplang/spec/variables.md#definite-assignment) also affect any variables that are captured by the local function or lambda expression.</span></span> <span data-ttu-id="bc183-183">コンパイラによって静的分析を実行できます。これにより、ローカル関数で外側のスコープ内のキャプチャされた変数を確実に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="bc183-183">The compiler can perform static analysis that enables local functions to definitely assign captured variables in the enclosing scope.</span></span> <span data-ttu-id="bc183-184">次の例について考えます。</span><span class="sxs-lookup"><span data-stu-id="bc183-184">Consider this example:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="bc183-185">コンパイラは、呼び出し時に `LocalFunction` が `y` を確実に割り当てるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-185">The compiler can determine that `LocalFunction` definitely assigns `y` when called.</span></span> <span data-ttu-id="bc183-186">`return` ステートメントの前に `LocalFunction` が呼び出されるため、`y` は `return` ステートメントで確実に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bc183-186">Because `LocalFunction` is called before the `return` statement, `y` is definitely assigned at the `return` statement.</span></span>

<span data-ttu-id="bc183-187">ローカル関数によって外側のスコープ内の変数をキャプチャする場合、ローカル関数はデリゲート型として実装されることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="bc183-187">Note that when a local function captures variables in the enclosing scope, the local function is implemented as a delegate type.</span></span>

### <a name="heap-allocations"></a><span data-ttu-id="bc183-188">ヒープの割り当て</span><span class="sxs-lookup"><span data-stu-id="bc183-188">Heap allocations</span></span>

<span data-ttu-id="bc183-189">ローカル関数では、その使用に応じて、ラムダ式では常に必要なヒープの割り当てを回避できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-189">Depending on their use, local functions can avoid heap allocations that are always necessary for lambda expressions.</span></span> <span data-ttu-id="bc183-190">ローカル関数がデリゲートに変換されておらず、ローカル関数でキャプチャされたいずれの変数も、デリゲートに変換された他のラムダやローカル関数でキャプチャされていない場合は、コンパイラによってヒープの割り当てを回避できます。</span><span class="sxs-lookup"><span data-stu-id="bc183-190">If a local function is never converted to a delegate, and none of the variables captured by the local function are captured by other lambdas or local functions that are converted to delegates, the compiler can avoid heap allocations.</span></span>

<span data-ttu-id="bc183-191">次の非同期の例について考えます。</span><span class="sxs-lookup"><span data-stu-id="bc183-191">Consider this async example:</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

<span data-ttu-id="bc183-192">このラムダ式のクロージャに含まれるのは、`address`、`index`、および `name` 変数です。</span><span class="sxs-lookup"><span data-stu-id="bc183-192">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="bc183-193">ローカル関数の場合、クロージャを実装するオブジェクトが `struct` になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc183-193">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="bc183-194">その構造体型はローカル関数に参照によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="bc183-194">That struct type would be passed by reference to the local function.</span></span> <span data-ttu-id="bc183-195">この実装の違いにより、割り当てが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="bc183-195">This difference in implementation would save on an allocation.</span></span>

<span data-ttu-id="bc183-196">ラムダ式に必要なインスタンス化では、余分なメモリの割り当てが必要となり、タイム クリティカルなコード パスに影響を与えるパフォーマンス因子となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bc183-196">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time-critical code paths.</span></span> <span data-ttu-id="bc183-197">ローカル関数では、このオーバーヘッドは発生しません。</span><span class="sxs-lookup"><span data-stu-id="bc183-197">Local functions do not incur this overhead.</span></span> <span data-ttu-id="bc183-198">上記の例では、ローカル関数のバージョンは、ラムダ式のバージョンよりも割り当てが 2 つ少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="bc183-198">In the example above, the local functions version has two fewer allocations than the lambda expression version.</span></span>

<span data-ttu-id="bc183-199">ローカル関数がデリゲートに変換されず、それによってキャプチャされた変数が、デリゲートに変換された他のラムダまたはローカル関数によってキャプチャされないことがわかっている場合は、ローカル関数を `static` ローカル関数として宣言することで、ヒープに割り当てられないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="bc183-199">If you know that your local function won't be converted to a delegate and none of the variables captured by it are captured by other lambdas or local functions that are converted to delegates, you can guarantee that your local function avoids being allocated on the heap by declaring it as a `static` local function.</span></span> <span data-ttu-id="bc183-200">この機能は C# 8.0 以降で使用可能であることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="bc183-200">Note that this feature is available in C# 8.0 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="bc183-201">このメソッドのローカル関数と同等のものも、同じクロージャのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc183-201">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="bc183-202">ローカル関数のクロージャが `class` として実装される場合でも、実装の詳細が `struct` である場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="bc183-202">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="bc183-203">ローカル関数は `struct` を使用する場合がありますが、ラムダは常に `class` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc183-203">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

### <a name="usage-of-the-yield-keyword"></a><span data-ttu-id="bc183-204">`yield` キーワードの使用法</span><span class="sxs-lookup"><span data-stu-id="bc183-204">Usage of the `yield` keyword</span></span>

<span data-ttu-id="bc183-205">この例では説明しませんが、最後の 1 つの利点は値のシーケンスを生成するために `yield return` 構文を使用して、ローカル関数を反復子として実装できることです。</span><span class="sxs-lookup"><span data-stu-id="bc183-205">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span>

:::code language="csharp" source="snippets/local-functions/Program.cs" id="YieldReturn" :::

<span data-ttu-id="bc183-206">`yield return` ステートメントは、ラムダ式では許可されていません。[コンパイラ エラー CS1621](../../misc/cs1621.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc183-206">The `yield return` statement is not allowed in lambda expressions, see [compiler error CS1621](../../misc/cs1621.md).</span></span>

<span data-ttu-id="bc183-207">ローカル関数はラムダ式より冗長に思えるかもしれませんが、実際にはさまざまな目的に役立ち、用途もさまざまです。</span><span class="sxs-lookup"><span data-stu-id="bc183-207">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span> <span data-ttu-id="bc183-208">ローカル関数は、別のメソッドのコンテキストからのみ呼び出される関数を記述する場合に、より効率が高くなります。</span><span class="sxs-lookup"><span data-stu-id="bc183-208">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc183-209">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc183-209">See also</span></span>

- [<span data-ttu-id="bc183-210">メソッド</span><span class="sxs-lookup"><span data-stu-id="bc183-210">Methods</span></span>](methods.md)
