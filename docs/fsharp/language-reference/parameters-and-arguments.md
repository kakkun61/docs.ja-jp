---
title: パラメーターと引数
description: 'パラメーターを定義し、関数、メソッド、およびプロパティに引数を渡すための F # 言語サポートについて説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 3c391ca37a1cf3bd150316943e5b06efa532b317
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740290"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="97122-103">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="97122-103">Parameters and Arguments</span></span>

<span data-ttu-id="97122-104">このトピックでは、パラメーターを定義し、関数、メソッド、およびプロパティに引数を渡すための言語サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="97122-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="97122-105">これには、参照渡しの方法に関する情報と、可変個の引数を受け取ることができるメソッドを定義して使用する方法についての情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="97122-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="97122-106">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="97122-106">Parameters and Arguments</span></span>

<span data-ttu-id="97122-107">Term *パラメーター* を使用して、指定される値の名前を記述します。</span><span class="sxs-lookup"><span data-stu-id="97122-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="97122-108">Term *引数* は、各パラメーターに指定された値に使用されます。</span><span class="sxs-lookup"><span data-stu-id="97122-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="97122-109">パラメーターは、組またはカリー化形式、またはその2つの組み合わせで指定できます。</span><span class="sxs-lookup"><span data-stu-id="97122-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="97122-110">引数は、明示的なパラメーター名を使用して渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="97122-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="97122-111">メソッドのパラメーターは、省略可能として指定し、既定値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="97122-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="97122-112">パラメーターパターン</span><span class="sxs-lookup"><span data-stu-id="97122-112">Parameter Patterns</span></span>

<span data-ttu-id="97122-113">関数およびメソッドに渡すパラメーターは、通常、スペースで区切られたパターンです。</span><span class="sxs-lookup"><span data-stu-id="97122-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="97122-114">つまり、原則として、関数またはメンバーのパラメーターリストでは、「 [Match 式](match-expressions.md) 」で説明されているパターンのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="97122-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="97122-115">メソッドは、通常、引数を渡す組形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="97122-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="97122-116">これにより、他の .NET 言語の観点から、.NET メソッドで引数が渡される方法と組の形式が一致するため、より明確な結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="97122-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="97122-117">カリー化形式は、バインディングを使用して作成された関数で最もよく使用され `let` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="97122-118">次の擬似コードは、組とカリー化引数の例を示しています。</span><span class="sxs-lookup"><span data-stu-id="97122-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="97122-119">一部の引数が組に含まれていて、一部がでない場合は、結合されたフォームを使用できます。</span><span class="sxs-lookup"><span data-stu-id="97122-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="97122-120">パラメーターリストで他のパターンを使用することもできますが、パラメーターパターンがすべての可能な入力と一致しない場合は、実行時に不完全な一致が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97122-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="97122-121">例外 `MatchFailureException` は、引数の値がパラメーターリストで指定されたパターンと一致しない場合に生成されます。</span><span class="sxs-lookup"><span data-stu-id="97122-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="97122-122">パラメーターパターンで不完全な一致が許可されている場合、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="97122-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="97122-123">少なくとも1つの他のパターンはパラメーターリストに便利で、ワイルドカードパターンです。</span><span class="sxs-lookup"><span data-stu-id="97122-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="97122-124">指定された引数を無視するだけの場合は、パラメーターリストでワイルドカードパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="97122-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="97122-125">次のコードは、引数リストでワイルドカードパターンを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="97122-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="97122-126">ワイルドカードパターンは、次のコードのように、通常は文字列配列として指定されているコマンドライン引数を必要としない場合に、プログラムへのメインエントリポイントなど、渡された引数が不要な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="97122-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="97122-127">引数で使用されるその他のパターンとしては、 `as` パターン、および判別共用体とアクティブパターンに関連付けられた識別子パターンがあります。</span><span class="sxs-lookup"><span data-stu-id="97122-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="97122-128">次のように、単一ケース判別共用体パターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="97122-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="97122-129">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="97122-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="97122-130">アクティブパターンは、次の例のように、引数を目的の形式に変換するときなどに、パラメーターとして役立ちます。</span><span class="sxs-lookup"><span data-stu-id="97122-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="97122-131">`as`次のコード行に示すように、パターンを使用して、一致した値をローカル値として格納することができます。</span><span class="sxs-lookup"><span data-stu-id="97122-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="97122-132">場合によって使用されるもう1つのパターンは、関数の本体として、暗黙的な引数に対してパターン一致を直ちに実行するラムダ式を指定することによって、最後の引数を無名のままにする関数です。</span><span class="sxs-lookup"><span data-stu-id="97122-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="97122-133">例として、次のコード行があります。</span><span class="sxs-lookup"><span data-stu-id="97122-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="97122-134">このコードは、ジェネリックリストを受け取り、リストが空の場合はを返し、それ以外の場合はを返す関数を定義し `true` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="97122-135">このような手法を使用すると、コードが読みにくくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97122-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="97122-136">場合によっては、不完全な一致を含むパターンが役に立つことがあります。たとえば、プログラムのリストに3つの要素しかないことがわかっている場合は、パラメーターリストで次のようなパターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="97122-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="97122-137">一致しないパターンを使用すると、簡単なプロトタイプ作成やその他の一時的な使用に適しています。</span><span class="sxs-lookup"><span data-stu-id="97122-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="97122-138">コンパイラは、このようなコードに対して警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="97122-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="97122-139">このようなパターンでは、可能なすべての入力の一般的なケースに対応できないため、コンポーネント Api には適していません。</span><span class="sxs-lookup"><span data-stu-id="97122-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="97122-140">名前付き引数</span><span class="sxs-lookup"><span data-stu-id="97122-140">Named Arguments</span></span>

<span data-ttu-id="97122-141">メソッドの引数は、コンマで区切られた引数リスト内の位置によって指定できます。また、名前を指定してメソッドに明示的に渡すこともできます。その後、等号と渡される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="97122-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="97122-142">名前を指定して指定した場合は、宣言で使用されているものとは異なる順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="97122-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="97122-143">名前付き引数を使用すると、メソッドパラメーターの並べ替えなど、API の特定の種類の変更にコードを読みやすくし、適応性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="97122-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="97122-144">名前付き引数は、バインドされていない `let` 関数、関数値、またはラムダ式ではなく、メソッドに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="97122-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="97122-145">名前付き引数の使用方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="97122-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="97122-146">クラスコンストラクターの呼び出しでは、名前付き引数と同様の構文を使用して、クラスのプロパティの値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="97122-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="97122-147">次の例は、この構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="97122-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="97122-148">詳細については、「 [コンストラクター (F #)](members/constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97122-148">For more information, see [Constructors (F#)](members/constructors.md).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="97122-149">省略可能のパラメーター</span><span class="sxs-lookup"><span data-stu-id="97122-149">Optional Parameters</span></span>

<span data-ttu-id="97122-150">パラメーター名の前に疑問符を使用して、メソッドの省略可能なパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="97122-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="97122-151">省略可能なパラメーターは F # のオプションの型として解釈されるので、およびで式を使用して、オプションの型のクエリを実行する通常の方法でクエリを実行でき `match` `Some` `None` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="97122-152">省略可能なパラメーターは、バインディングを使用して作成された関数ではなく、メンバーに対してのみ許可され `let` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="97122-153">またはなどのパラメーター名を使用して、既存の省略可能な値をメソッドに渡すことができ `?arg=None` `?arg=Some(3)` `?arg=arg` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="97122-154">これは、オプションの引数を別のメソッドに渡すメソッドを構築する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="97122-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="97122-155">また、 `defaultArg` 省略可能な引数の既定値を設定する関数を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="97122-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="97122-156">関数は、省略可能なパラメーターを最初の引数として `defaultArg` 受け取り、既定値を2番目の引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="97122-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="97122-157">省略可能なパラメーターの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="97122-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="97122-158">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="97122-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="97122-159">C# と Visual Basic の相互運用を目的として、F # の属性を使用して、 `[<Optional; DefaultParameterValue<(...)>]` 呼び出し元が引数を省略可能として認識できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="97122-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="97122-160">これは、のように、C# では引数を省略可能として定義することと同じです `MyMethod(int i = 3)` 。</span><span class="sxs-lookup"><span data-stu-id="97122-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn $"{message}"
```

<span data-ttu-id="97122-161">また、新しいオブジェクトを既定のパラメーター値として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="97122-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="97122-162">たとえば、メンバーは `Foo` 省略可能なを入力として持つことができ `CancellationToken` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn $"{ct}"
```

<span data-ttu-id="97122-163">の引数として指定された値は、 `DefaultParameterValue` パラメーターの型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97122-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="97122-164">たとえば、次は許可されていません。</span><span class="sxs-lookup"><span data-stu-id="97122-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="97122-165">この場合、コンパイラは警告を生成し、両方の属性を完全に無視します。</span><span class="sxs-lookup"><span data-stu-id="97122-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="97122-166">既定値には型指定の注釈を付ける必要があることに注意し `null` てください。そうでない場合、コンパイラは正しくない型を推論します。 `[<Optional; DefaultParameterValue(null:obj)>] o:obj`</span><span class="sxs-lookup"><span data-stu-id="97122-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="97122-167">参照渡し</span><span class="sxs-lookup"><span data-stu-id="97122-167">Passing by Reference</span></span>

<span data-ttu-id="97122-168">参照による F # 値の引き渡しには、マネージポインター型である [byref](byrefs.md)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="97122-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="97122-169">使用する種類に関するガイダンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="97122-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="97122-170">`inref<'T>`ポインターのみを読み取る必要がある場合は、を使用します。</span><span class="sxs-lookup"><span data-stu-id="97122-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="97122-171">`outref<'T>`ポインターへの書き込みのみが必要な場合は、を使用します。</span><span class="sxs-lookup"><span data-stu-id="97122-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="97122-172">`byref<'T>`ポインターの読み取りと書き込みの両方を行う必要がある場合は、を使用します。</span><span class="sxs-lookup"><span data-stu-id="97122-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn $"It's %d{x}"

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn $"It's %d{x}"
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="97122-173">パラメーターはポインターであり、値は変更可能であるため、値に対する変更は、関数の実行後も保持されます。</span><span class="sxs-lookup"><span data-stu-id="97122-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="97122-174">戻り値としてタプルを使用して、 `out` .net ライブラリメソッドに任意のパラメーターを格納できます。</span><span class="sxs-lookup"><span data-stu-id="97122-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="97122-175">または、パラメーターを `out` パラメーターとして扱うこともでき `byref` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="97122-176">両方の方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="97122-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="97122-177">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="97122-177">Parameter Arrays</span></span>

<span data-ttu-id="97122-178">場合によっては、異種型の任意の数のパラメーターを受け取る関数を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97122-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="97122-179">すべてのオーバーロードされたメソッドを作成して、使用可能なすべての型を考慮することは実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="97122-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="97122-180">.NET 実装では、パラメーター配列機能を使用して、このようなメソッドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="97122-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="97122-181">シグネチャでパラメーター配列を受け取るメソッドには、任意の数のパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="97122-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="97122-182">パラメーターは配列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="97122-182">The parameters are put into an array.</span></span> <span data-ttu-id="97122-183">配列要素の型によって、関数に渡すことができるパラメーターの型が決まります。</span><span class="sxs-lookup"><span data-stu-id="97122-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="97122-184">要素の型としてを使用してパラメーター配列を定義すると `System.Object` 、クライアントコードは任意の型の値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="97122-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="97122-185">F # では、パラメーター配列はメソッドでのみ定義できます。</span><span class="sxs-lookup"><span data-stu-id="97122-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="97122-186">これらは、モジュールで定義されているスタンドアロン関数または関数では使用できません。</span><span class="sxs-lookup"><span data-stu-id="97122-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="97122-187">パラメーター配列は、属性を使用して定義し `ParamArray` ます。</span><span class="sxs-lookup"><span data-stu-id="97122-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="97122-188">属性は、 `ParamArray` 最後のパラメーターにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="97122-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="97122-189">次のコードは、パラメーター配列を受け取る .NET メソッドと、パラメーター配列を受け取るメソッドを持つ F # の型の定義の両方を呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="97122-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="97122-190">プロジェクト内で実行すると、前のコードの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="97122-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="97122-191">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="97122-191">See also</span></span>

- [<span data-ttu-id="97122-192">メンバー</span><span class="sxs-lookup"><span data-stu-id="97122-192">Members</span></span>](./members/index.md)
