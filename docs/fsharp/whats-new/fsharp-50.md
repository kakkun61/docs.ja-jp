---
title: 'F # 5.0 の新機能-F # ガイド'
description: 'F # 5.0 で利用可能な新機能の概要を説明します。'
ms.date: 11/06/2020
ms.openlocfilehash: 0b25d48a97792e780515226170151f3bbf2f2301
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982467"
---
# <a name="whats-new-in-f-50"></a><span data-ttu-id="ad3b8-103">F# 5.0 の新機能</span><span class="sxs-lookup"><span data-stu-id="ad3b8-103">What's new in F# 5.0</span></span>

<span data-ttu-id="ad3b8-104">F # 5.0 では、F # 言語と F# インタラクティブにいくつかの機能強化が加えられています。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-104">F# 5.0 adds several improvements to the F# language and F# Interactive.</span></span> <span data-ttu-id="ad3b8-105">**.Net 5** でリリースされます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-105">It is released with **.NET 5**.</span></span>

<span data-ttu-id="ad3b8-106">最新の .NET SDK は [.NET のダウンロード ページ](https://dotnet.microsoft.com/download)でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-106">You can download the latest .NET SDK from the [.NET downloads page](https://dotnet.microsoft.com/download).</span></span>

## <a name="get-started"></a><span data-ttu-id="ad3b8-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="ad3b8-107">Get started</span></span>

<span data-ttu-id="ad3b8-108">F # 5.0 は、すべての .NET Core ディストリビューションと Visual Studio ツールで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-108">F# 5.0 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="ad3b8-109">詳細については、「 [F # の使用を開始](../get-started/index.md) する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-109">For more information, see [Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="package-references-in-f-scripts"></a><span data-ttu-id="ad3b8-110">F # スクリプトでのパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="ad3b8-110">Package references in F# scripts</span></span>

<span data-ttu-id="ad3b8-111">F # 5 では、構文を使用して F # スクリプトにパッケージ参照がサポートさ `#r "nuget:..."` れます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-111">F# 5 brings support for package references in F# scripts with `#r "nuget:..."` syntax.</span></span> <span data-ttu-id="ad3b8-112">たとえば、次のパッケージ参照を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-112">For example, consider the following package reference:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

<span data-ttu-id="ad3b8-113">次のように、パッケージの名前の後に明示的なバージョンを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-113">You can also supply an explicit version after the name of the package like this:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

<span data-ttu-id="ad3b8-114">パッケージ参照は、ML.NET などのネイティブ依存関係を含むパッケージをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-114">Package references support packages with native dependencies, such as ML.NET.</span></span>

<span data-ttu-id="ad3b8-115">パッケージ参照は、依存するを参照するための特別な要件を持つパッケージもサポート `.dll` します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-115">Package references also support packages with special requirements about referencing dependent `.dll`s.</span></span> <span data-ttu-id="ad3b8-116">たとえば、ユーザーが F# インタラクティブで参照される前に、その依存が先に参照されていることをユーザーが手動で確認するように要求するために使用される [Fparsec](https://www.nuget.org/packages/FParsec/) パッケージなど `FParsecCS.dll` `FParsec.dll` です。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-116">For example, the [FParsec](https://www.nuget.org/packages/FParsec/) package used to require that users manually ensure that its dependent `FParsecCS.dll` was referenced first before `FParsec.dll` was referenced in F# Interactive.</span></span> <span data-ttu-id="ad3b8-117">これは不要になったため、次のようにしてパッケージを参照できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-117">This is no longer needed, and you can reference the package as follows:</span></span>

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

<span data-ttu-id="ad3b8-118">この機能は [、F # ツーリング RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-118">This feature implements [F# Tooling RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md).</span></span> <span data-ttu-id="ad3b8-119">パッケージ参照の詳細については、 [F# インタラクティブ](../tutorials/fsharp-interactive/index.md) チュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-119">For more information on package references, see the [F# Interactive](../tutorials/fsharp-interactive/index.md) tutorial.</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="ad3b8-120">文字列補間</span><span class="sxs-lookup"><span data-stu-id="ad3b8-120">String interpolation</span></span>

<span data-ttu-id="ad3b8-121">F # の挿入文字列は、C# または JavaScript の挿入文字列に似ています。つまり、文字列リテラル内の "穴" にコードを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-121">F# interpolated strings are fairly similar to C# or JavaScript interpolated strings, in that they let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="ad3b8-122">基本的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-122">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="ad3b8-123">ただし、F # の補間文字列では、関数と同様に、型指定された補間を使用して、 `sprintf` 補間されたコンテキスト内の式が特定の型に準拠するようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-123">However, F# interpolated strings also allow for typed interpolations, just like the `sprintf` function, to enforce that an expression inside of an interpolated context conforms to a particular type.</span></span> <span data-ttu-id="ad3b8-124">同じ書式指定子を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-124">It uses the same format specifiers.</span></span>

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="ad3b8-125">前の型指定された補間の例では、で補間が型である必要がありますが、では補間がである必要があり `%s` `string` `%d` `integer` ます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-125">In the preceding typed interpolation example, the `%s` requires the interpolation to be of type `string`, whereas the `%d` requires the interpolation to be an `integer`.</span></span>

<span data-ttu-id="ad3b8-126">また、任意の F # 式 (または式) を補間コンテキストの側に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-126">Additionally, any arbitrary F# expression (or expressions) can be placed in side of an interpolation context.</span></span> <span data-ttu-id="ad3b8-127">次のように、より複雑な式を記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-127">It is even possible to write a more complicated expression, like so:</span></span>

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

<span data-ttu-id="ad3b8-128">ただし、これはあまり実践されていません。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-128">Although we don't recommend doing this too much in practice.</span></span>

<span data-ttu-id="ad3b8-129">この機能は [、F # RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-129">This feature implements [F# RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).</span></span>

## <a name="support-for-nameof"></a><span data-ttu-id="ad3b8-130">のためのサポート</span><span class="sxs-lookup"><span data-stu-id="ad3b8-130">Support for nameof</span></span>

<span data-ttu-id="ad3b8-131">F # 5 では演算子がサポートされてい `nameof` ます。この演算子は、で使用されているシンボルを解決し、f # ソースでその名前を生成します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-131">F# 5 supports the `nameof` operator, which resolves the symbol it's being used for and produces its name in F# source.</span></span> <span data-ttu-id="ad3b8-132">これは、ログ記録などのさまざまなシナリオで役立ち、ソースコードの変更に対するログ記録を保護します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-132">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="ad3b8-133">最後の行は例外をスローし、"month" はエラーメッセージに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-133">The last line will throw an exception and "month" will be shown in the error message.</span></span>

<span data-ttu-id="ad3b8-134">ほぼすべての F # コンストラクトの名前を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-134">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

<span data-ttu-id="ad3b8-135">最後の3つの追加は、演算子のしくみに対する変更です。 `nameof<'type-parameter>` ジェネリック型パラメーターのフォームの追加と、 `nameof` パターン一致式のパターンとしての使用が可能です。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-135">Three final additions are changes to how operators work: the addition of the `nameof<'type-parameter>` form for generic type parameters, and the ability to use `nameof` as a pattern in a pattern match expression.</span></span>

<span data-ttu-id="ad3b8-136">演算子の名前を取得すると、そのソース文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-136">Taking a name of an operator gives its source string.</span></span> <span data-ttu-id="ad3b8-137">コンパイル済みのフォームが必要な場合は、演算子のコンパイルされた名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-137">If you need the compiled form, use the compiled name of an operator:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

<span data-ttu-id="ad3b8-138">型パラメーターの名前を取得するには、次のように若干異なる構文が必要です。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-138">Taking the name of a type parameter requires a slightly different syntax:</span></span>

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

<span data-ttu-id="ad3b8-139">これは、 `typeof<'T>` 演算子および演算子に似てい `typedefof<'T>` ます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-139">This is similar to the `typeof<'T>` and `typedefof<'T>` operators.</span></span>

<span data-ttu-id="ad3b8-140">F # 5 では、 `nameof` 式で使用できるパターンのサポートも追加されてい `match` ます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-140">F# 5 also adds support for a `nameof` pattern that can be used in `match` expressions:</span></span>

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

<span data-ttu-id="ad3b8-141">上記のコードでは、match 式の文字列リテラルではなく、' 文字列 ' を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-141">The preceding code uses 'nameof' instead of the string literal in the match expression.</span></span>

<span data-ttu-id="ad3b8-142">この機能は [、F # RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-142">This feature implements [F# RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="ad3b8-143">オープン型の宣言</span><span class="sxs-lookup"><span data-stu-id="ad3b8-143">Open type declarations</span></span>

<span data-ttu-id="ad3b8-144">F # 5 では、オープン型の宣言のサポートも追加されています。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-144">F# 5 also adds support for open type declarations.</span></span> <span data-ttu-id="ad3b8-145">オープン型の宣言は、C# で静的クラスを開くのと似ています。ただし、F # のセマンティクスに適合するように、構文や動作が少し異なります。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-145">An open type declaration is like opening a static class in C#, except with some different syntax and some slightly different behavior to fit F# semantics.</span></span>

<span data-ttu-id="ad3b8-146">オープン型の宣言では、 `open` 任意の型を使用して、静的な内容をその中に公開できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-146">With open type declarations, you can `open` any type to expose static contents inside of it.</span></span> <span data-ttu-id="ad3b8-147">さらに、 `open` F # で定義された共用体とレコードを使用して、その内容を公開できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-147">Additionally, you can `open` F#-defined unions and records to expose their contents.</span></span> <span data-ttu-id="ad3b8-148">たとえば、モジュールで共用体が定義されていて、そのケースにアクセスするが、モジュール全体を開かないようにする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-148">For example, this can be useful if you have a union defined in a module and want to access its cases, but don't want to open the entire module.</span></span>

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

<span data-ttu-id="ad3b8-149">C# とは異なり、 `open type` 同じ名前を持つメンバーを公開する2つの型がある場合、最後の型のメンバーは、 `open` 他の名前をシャドウします。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-149">Unlike C#, when you `open type` on two types that expose a member with the same name, the member from the last type being `open`ed shadows the other name.</span></span> <span data-ttu-id="ad3b8-150">これは、既に存在するシャドウ処理に関する F # のセマンティクスと一致します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-150">This is consistent with F# semantics around shadowing that exist already.</span></span>

<span data-ttu-id="ad3b8-151">この機能は [、F # RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-151">This feature implements [F# RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).</span></span>

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a><span data-ttu-id="ad3b8-152">組み込みデータ型のスライス動作の一貫性</span><span class="sxs-lookup"><span data-stu-id="ad3b8-152">Consistent slicing behavior for built-in data types</span></span>

<span data-ttu-id="ad3b8-153">組み込み `FSharp.Core` データ型 (配列、リスト、文字列、2d 配列、3d 配列、4d 配列) を、F # 5 より前の一貫性がないようにスライスする動作。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-153">Behavior for slicing the built-in `FSharp.Core` data types (array, list, string, 2D array, 3D array, 4D array) used to not be consistent prior to F# 5.</span></span> <span data-ttu-id="ad3b8-154">一部のエッジケースの動作で例外がスローされましたが、何も発生しませんでした。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-154">Some edge-case behavior threw an exception and some wouldn't.</span></span> <span data-ttu-id="ad3b8-155">F # 5 では、すべての組み込み型で、生成できないスライスの空のスライスが返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-155">In F# 5, all built-in types now return empty slices for slices that are impossible to generate:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

<span data-ttu-id="ad3b8-156">この機能は [、F # RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-156">This feature implements [F# RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a><span data-ttu-id="ad3b8-157">Fsharp.core の3D および4D 配列の固定インデックススライス</span><span class="sxs-lookup"><span data-stu-id="ad3b8-157">Fixed-index slices for 3D and 4D arrays in FSharp.Core</span></span>

<span data-ttu-id="ad3b8-158">F # 5.0 では、組み込みの3D および4D 配列型の固定インデックスを使用したスライスのサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-158">F# 5.0 brings support for slicing with a fixed index in the built-in 3D and 4D array types.</span></span>

<span data-ttu-id="ad3b8-159">これを説明するために、次の3D 配列について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-159">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="ad3b8-160">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="ad3b8-160">*z = 0*</span></span>
| <span data-ttu-id="ad3b8-161">x\y</span><span class="sxs-lookup"><span data-stu-id="ad3b8-161">x\y</span></span>   | <span data-ttu-id="ad3b8-162">0</span><span class="sxs-lookup"><span data-stu-id="ad3b8-162">0</span></span> | <span data-ttu-id="ad3b8-163">1</span><span class="sxs-lookup"><span data-stu-id="ad3b8-163">1</span></span> |
|-------|---|---|
| <span data-ttu-id="ad3b8-164">**0**</span><span class="sxs-lookup"><span data-stu-id="ad3b8-164">**0**</span></span> | <span data-ttu-id="ad3b8-165">0</span><span class="sxs-lookup"><span data-stu-id="ad3b8-165">0</span></span> | <span data-ttu-id="ad3b8-166">1</span><span class="sxs-lookup"><span data-stu-id="ad3b8-166">1</span></span> |
| <span data-ttu-id="ad3b8-167">**1**</span><span class="sxs-lookup"><span data-stu-id="ad3b8-167">**1**</span></span> | <span data-ttu-id="ad3b8-168">2</span><span class="sxs-lookup"><span data-stu-id="ad3b8-168">2</span></span> | <span data-ttu-id="ad3b8-169">3</span><span class="sxs-lookup"><span data-stu-id="ad3b8-169">3</span></span> |

<span data-ttu-id="ad3b8-170">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="ad3b8-170">*z = 1*</span></span>
| <span data-ttu-id="ad3b8-171">x\y</span><span class="sxs-lookup"><span data-stu-id="ad3b8-171">x\y</span></span>   | <span data-ttu-id="ad3b8-172">0</span><span class="sxs-lookup"><span data-stu-id="ad3b8-172">0</span></span> | <span data-ttu-id="ad3b8-173">1</span><span class="sxs-lookup"><span data-stu-id="ad3b8-173">1</span></span> |
|-------|---|---|
| <span data-ttu-id="ad3b8-174">**0**</span><span class="sxs-lookup"><span data-stu-id="ad3b8-174">**0**</span></span> | <span data-ttu-id="ad3b8-175">4</span><span class="sxs-lookup"><span data-stu-id="ad3b8-175">4</span></span> | <span data-ttu-id="ad3b8-176">5</span><span class="sxs-lookup"><span data-stu-id="ad3b8-176">5</span></span> |
| <span data-ttu-id="ad3b8-177">**1**</span><span class="sxs-lookup"><span data-stu-id="ad3b8-177">**1**</span></span> | <span data-ttu-id="ad3b8-178">6</span><span class="sxs-lookup"><span data-stu-id="ad3b8-178">6</span></span> | <span data-ttu-id="ad3b8-179">7</span><span class="sxs-lookup"><span data-stu-id="ad3b8-179">7</span></span> |

<span data-ttu-id="ad3b8-180">配列からスライスを抽出する場合はどうすればよい `[| 4; 5 |]` でしょうか。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-180">What if you wanted to extract the slice `[| 4; 5 |]` from the array?</span></span> <span data-ttu-id="ad3b8-181">これは非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-181">This is now very simple!</span></span>

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

<span data-ttu-id="ad3b8-182">この機能は [、F # RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-182">This feature implements [F# RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).</span></span>

## <a name="f-quotations-improvements"></a><span data-ttu-id="ad3b8-183">F # による引用符の機能強化</span><span class="sxs-lookup"><span data-stu-id="ad3b8-183">F# quotations improvements</span></span>

<span data-ttu-id="ad3b8-184">F # の [コード引用符](../language-reference/code-quotations.md) で、型の制約情報を保持できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-184">F# [code quotations](../language-reference/code-quotations.md) now have the ability to retain type constraint information.</span></span> <span data-ttu-id="ad3b8-185">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-185">Consider the following example:</span></span>

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

<span data-ttu-id="ad3b8-186">関数によって生成される制約 `inline` は、コードに保持されます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-186">The constraint generated by the `inline` function is retained in the code qutoation.</span></span> <span data-ttu-id="ad3b8-187">関数の順序によって表さ `negate` れるフォームを評価できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-187">The `negate` function's quotated form can now be evaluated.</span></span>

<span data-ttu-id="ad3b8-188">この機能は [、F # RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-188">This feature implements [F# RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).</span></span>

## <a name="applicative-computation-expressions"></a><span data-ttu-id="ad3b8-189">アプリケーションの計算式</span><span class="sxs-lookup"><span data-stu-id="ad3b8-189">Applicative Computation Expressions</span></span>

<span data-ttu-id="ad3b8-190">[コンピュテーション式 (CEs)](../language-reference/computation-expressions.md) は、"コンテキスト計算" をモデル化するために現在使用されています。または、関数型プログラミングのわかりやすい用語である monadic の計算に使用されています。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-190">[Computation expressions (CEs)](../language-reference/computation-expressions.md) are used today to model "contextual computations", or in more functional programming friendly terminology, monadic computations.</span></span>

<span data-ttu-id="ad3b8-191">F # 5 では、別の計算モデルを提供するアプリケーションアプリケーションが導入されています。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-191">F# 5 introduces applicative CEs, which offer a different computational model.</span></span> <span data-ttu-id="ad3b8-192">アプリケーションを使用すると、すべての計算が独立しており、結果が最終的に蓄積されるため、より効率的な計算を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-192">Applicative CEs allow for more efficient computations provided that every computation is independent, and their results are accumulated at the end.</span></span> <span data-ttu-id="ad3b8-193">計算が相互に独立している場合は、それらも簡単に並列化できます。これにより、CE の作成者はより効率的なライブラリを記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-193">When computations are independent of one another, they are also trivially parallelizable, allowing CE authors to write more efficient libraries.</span></span> <span data-ttu-id="ad3b8-194">ただし、この特典には制限がありますが、以前に計算された値に依存する計算は使用できません。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-194">This benefit comes at a restriction, though: computations that depend on previously-computed values are not allowed.</span></span>

<span data-ttu-id="ad3b8-195">次の例は、型の基本的なアプリケーションを示して `Result` います。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-195">The follow example shows a basic applicative CE for the `Result` type.</span></span>

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

<span data-ttu-id="ad3b8-196">現在ライブラリで CEs を公開しているライブラリの作成者は、注意する必要がある追加の考慮事項がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-196">If you're a library author who exposes CEs in their library today, there are some additional considerations you'll need to be aware of.</span></span>

<span data-ttu-id="ad3b8-197">この機能は [、F # RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-197">This feature implements [F# RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).</span></span>

## <a name="interfaces-can-be-implemeneted-at-different-generic-instantiations"></a><span data-ttu-id="ad3b8-198">インターフェイスは、異なる汎用インスタンス化で implemeneted ことができます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-198">Interfaces can be implemeneted at different generic instantiations</span></span>

<span data-ttu-id="ad3b8-199">これで、異なる汎用インスタンス化で同じインターフェイスを実装できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-199">You can now implement the same interface at different generic instantiations:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

<span data-ttu-id="ad3b8-200">この機能は [、F # RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-200">This feature implements [F# RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).</span></span>

## <a name="default-interface-member-consumption"></a><span data-ttu-id="ad3b8-201">既定のインターフェイスメンバーの消費</span><span class="sxs-lookup"><span data-stu-id="ad3b8-201">Default interface member consumption</span></span>

<span data-ttu-id="ad3b8-202">F # 5 では、 [既定の実装でインターフェイス](../../csharp/tutorials/default-interface-methods-versions.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-202">F# 5 lets you consume [interfaces with default implementations](../../csharp/tutorials/default-interface-methods-versions.md).</span></span>

<span data-ttu-id="ad3b8-203">次のように、C# で定義されているインターフェイスについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-203">Consider an interface defined in C# like this:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="ad3b8-204">これは、インターフェイスを実装する標準の方法のいずれかを使用して F # で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-204">You can consume it in F# through any of the standard means of implementing an interface:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

<span data-ttu-id="ad3b8-205">これにより、ユーザーが既定の実装を使用できることが期待される場合に、最新の c# で記述された C# コードと .NET コンポーネントを安全に利用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-205">This lets you safely take advantage of C# code and .NET components written in modern C# when they expect users to be able to consume a default implementation.</span></span>

<span data-ttu-id="ad3b8-206">この機能は [、F # RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-206">This feature implements [F# RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).</span></span>

## <a name="simplified-interop-with-nullable-value-types"></a><span data-ttu-id="ad3b8-207">単純化と null 許容の値型との相互運用</span><span class="sxs-lookup"><span data-stu-id="ad3b8-207">Simplified interop with nullable value types</span></span>

<span data-ttu-id="ad3b8-208">[Null 許容型 (値) 型](https://docs.microsoft.com/dotnet/api/system.nullable-1) (以前は Null 許容型と呼ばれます) は F # でサポートされていますが、通常 `Nullable` は、値を渡すたびにまたはラッパーを構築する必要があるため、これらの型を操作するのはかなり困難でした `Nullable<SomeType>` 。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-208">[Nullable (value) types](https://docs.microsoft.com/dotnet/api/system.nullable-1) (called Nullable Types historically) have long been supported by F#, but interacting with them has traditionally been somewhat of a pain since you'd have to construct a `Nullable` or `Nullable<SomeType>` wrapper every time you wanted to pass a value.</span></span> <span data-ttu-id="ad3b8-209">これで、 `Nullable<ThatValueType>` ターゲットの型がと一致する場合、コンパイラは値型をに暗黙的に変換します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-209">Now the compiler will implicitly convert a value type into a `Nullable<ThatValueType>` if the target type matches.</span></span> <span data-ttu-id="ad3b8-210">現在、次のコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-210">The following code is now possible:</span></span>

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

<span data-ttu-id="ad3b8-211">この機能は [、F # RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-211">This feature implements [F# RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).</span></span>

## <a name="preview-reverse-indexes"></a><span data-ttu-id="ad3b8-212">プレビュー: インデックスの反転</span><span class="sxs-lookup"><span data-stu-id="ad3b8-212">Preview: reverse indexes</span></span>

<span data-ttu-id="ad3b8-213">F # 5 では、逆引きインデックスを許可するためのプレビューも導入されています。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-213">F# 5 also introduces a preview for allowing reverse indexes.</span></span> <span data-ttu-id="ad3b8-214">構文は `^idx` です。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-214">The syntax is `^idx`.</span></span> <span data-ttu-id="ad3b8-215">リストの末尾から要素1の値を指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-215">Here's how you can an element 1 value from the end of a list:</span></span>

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

<span data-ttu-id="ad3b8-216">また、独自の型の逆インデックスを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-216">You can also define reverse indexes for your own types.</span></span> <span data-ttu-id="ad3b8-217">これを行うには、次のメソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-217">To do so, you'll need to implement the following method:</span></span>

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

<span data-ttu-id="ad3b8-218">型の例を次に示し `Span<'T>` ます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-218">Here's an example for the `Span<'T>` type:</span></span>

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

<span data-ttu-id="ad3b8-219">この機能は [、F # RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-219">This feature implements [F# RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).</span></span>

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a><span data-ttu-id="ad3b8-220">プレビュー: コンピュテーション式におけるカスタムキーワードのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="ad3b8-220">Preview: overloads of custom keywords in computation expressions</span></span>

<span data-ttu-id="ad3b8-221">コンピュテーション式は、ライブラリおよびフレームワークの作成者にとって強力な機能です。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-221">Computation expressions are a powerful feature for library and framework authors.</span></span> <span data-ttu-id="ad3b8-222">よく知られているメンバーを定義し、作業中のドメインの DSL を形成することで、コンポーネントの表現力を大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-222">They allow you to greatly improve the expressiveness of your components by letting you define well-known members and form a DSL for the domain you're working in.</span></span>

<span data-ttu-id="ad3b8-223">F # 5 では、コンピュテーション式でカスタム操作をオーバーロードするためのプレビューサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-223">F# 5 adds preview support for overloading custom operations in Computation Expressions.</span></span> <span data-ttu-id="ad3b8-224">これにより、次のコードを書き込まれるして使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-224">It allows the following code to be writen and consumed:</span></span>

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

<span data-ttu-id="ad3b8-225">この変更の前には、型をそのまま記述でき `InputBuilder` ますが、この例で使用する方法を使用することはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-225">Prior to this change, you could write the `InputBuilder` type as it is, but you couldn't use it the way it's used in the example.</span></span> <span data-ttu-id="ad3b8-226">オーバーロード、省略可能なパラメーター、および現在の `System.ParamArray` 型は許可されているため、期待どおりに機能するだけです。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-226">Since overloads, optional parameters, and now `System.ParamArray` types are allowed, everything just works as you'd expect it to.</span></span>

<span data-ttu-id="ad3b8-227">この機能は [、F # RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3b8-227">This feature implements [F# RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).</span></span>
