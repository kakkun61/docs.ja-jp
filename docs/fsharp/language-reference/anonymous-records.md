---
title: 匿名のレコード
description: データの操作に役立つ言語機能である、コンストラクトを使用して匿名レコードを使用する方法について説明します。
ms.date: 06/12/2019
ms.openlocfilehash: 13950048f02ab74362f8174725f5f8615d9d7654
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739816"
---
# <a name="anonymous-records"></a><span data-ttu-id="585c6-103">匿名のレコード</span><span class="sxs-lookup"><span data-stu-id="585c6-103">Anonymous Records</span></span>

<span data-ttu-id="585c6-104">匿名レコードは、使用前に宣言する必要のない名前付きの値の単純な集計です。</span><span class="sxs-lookup"><span data-stu-id="585c6-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="585c6-105">これらは、構造体または参照型として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="585c6-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="585c6-106">既定では、これらは参照型です。</span><span class="sxs-lookup"><span data-stu-id="585c6-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="585c6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="585c6-107">Syntax</span></span>

<span data-ttu-id="585c6-108">次の例は、匿名レコードの構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="585c6-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="585c6-109">として区切られた項目 `[item]` は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="585c6-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="585c6-110">基本的な使用方法</span><span class="sxs-lookup"><span data-stu-id="585c6-110">Basic usage</span></span>

<span data-ttu-id="585c6-111">匿名レコードは、インスタンス化の前に宣言する必要のない F # のレコード型として考えるのが最適です。</span><span class="sxs-lookup"><span data-stu-id="585c6-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="585c6-112">たとえば、匿名レコードを生成する関数と対話する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="585c6-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

<span data-ttu-id="585c6-113">次の例では、前の例のを、 `printCircleStats` 匿名レコードを入力として受け取る関数を使用して展開します。</span><span class="sxs-lookup"><span data-stu-id="585c6-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

<span data-ttu-id="585c6-114">`printCircleStats`入力型と同じ "shape" を持たない匿名レコード型を使用してを呼び出すと、コンパイルに失敗します。</span><span class="sxs-lookup"><span data-stu-id="585c6-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="585c6-115">構造体の匿名レコード</span><span class="sxs-lookup"><span data-stu-id="585c6-115">Struct anonymous records</span></span>

<span data-ttu-id="585c6-116">匿名レコードは、省略可能なキーワードを使用して構造体として定義することもでき `struct` ます。</span><span class="sxs-lookup"><span data-stu-id="585c6-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="585c6-117">次の例では、構造体の匿名レコードを生成して使用することにより、前のコードを強化します。</span><span class="sxs-lookup"><span data-stu-id="585c6-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a><span data-ttu-id="585c6-118">Structness の推論</span><span class="sxs-lookup"><span data-stu-id="585c6-118">Structness inference</span></span>

<span data-ttu-id="585c6-119">構造体の匿名レコードでは、呼び出しサイトでキーワードを指定する必要がない "structness の推定" も許可され `struct` ます。</span><span class="sxs-lookup"><span data-stu-id="585c6-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="585c6-120">この例では、を呼び出すときにキーワードを解除し `struct` `printCircleStats` ます。</span><span class="sxs-lookup"><span data-stu-id="585c6-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="585c6-121">逆パターン- `struct` 入力型が構造体の匿名レコードでない場合にを指定すると、コンパイルに失敗します。</span><span class="sxs-lookup"><span data-stu-id="585c6-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="585c6-122">他の型の中に匿名レコードを埋め込む</span><span class="sxs-lookup"><span data-stu-id="585c6-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="585c6-123">ケースがレコードである [判別共用体](discriminated-unions.md) を宣言すると便利です。</span><span class="sxs-lookup"><span data-stu-id="585c6-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="585c6-124">ただし、レコード内のデータが判別共用体と同じ型である場合は、すべての型を相互に再帰的に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="585c6-125">匿名レコードを使用すると、この制限を回避できます。</span><span class="sxs-lookup"><span data-stu-id="585c6-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="585c6-126">パターンが一致する型と関数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="585c6-126">What follows is an example type and function that pattern matches over it:</span></span>

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named record for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a><span data-ttu-id="585c6-127">式のコピーと更新</span><span class="sxs-lookup"><span data-stu-id="585c6-127">Copy and update expressions</span></span>

<span data-ttu-id="585c6-128">匿名レコードは [、コピー式および更新式](copy-and-update-record-expressions.md)を使用した構築をサポートします。</span><span class="sxs-lookup"><span data-stu-id="585c6-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="585c6-129">たとえば、既存のデータをコピーする匿名レコードの新しいインスタンスを作成する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="585c6-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="585c6-130">ただし、名前付きレコードとは異なり、匿名レコードでは、コピーと更新の式を使用して、まったく異なる形式を構築できます。</span><span class="sxs-lookup"><span data-stu-id="585c6-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="585c6-131">次の例では、前の例と同じ匿名レコードを取得し、新しい匿名レコードに展開します。</span><span class="sxs-lookup"><span data-stu-id="585c6-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="585c6-132">名前付きレコードのインスタンスから匿名レコードを構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="585c6-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="585c6-133">参照および構造体の匿名レコードとの間でデータをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="585c6-133">You can also copy data to and from reference and struct anonymous records:</span></span>

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="585c6-134">匿名レコードのプロパティ</span><span class="sxs-lookup"><span data-stu-id="585c6-134">Properties of anonymous records</span></span>

<span data-ttu-id="585c6-135">匿名レコードには、それらの使用方法を十分に理解するために不可欠ないくつかの特性があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="585c6-136">匿名レコードは公称</span><span class="sxs-lookup"><span data-stu-id="585c6-136">Anonymous records are nominal</span></span>

<span data-ttu-id="585c6-137">匿名レコードは [公称型](https://en.wikipedia.org/wiki/Nominal_type_system)です。</span><span class="sxs-lookup"><span data-stu-id="585c6-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="585c6-138">これらは、アップフロント宣言を必要としない名前付き [レコード](records.md) 型 (公称でもあります) として考えるのが最適です。</span><span class="sxs-lookup"><span data-stu-id="585c6-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="585c6-139">次の例では、2つの匿名レコード宣言を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="585c6-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="585c6-140">`x`との `y` 値の型が異なり、相互に互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="585c6-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="585c6-141">これらは equatable ではなく、比較できません。</span><span class="sxs-lookup"><span data-stu-id="585c6-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="585c6-142">これを説明するために、同等の名前付きレコードを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="585c6-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="585c6-143">型の等価性または比較に関係する場合、匿名レコードの名前付きレコードと比較しても、本質的に異なることはありません。</span><span class="sxs-lookup"><span data-stu-id="585c6-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="585c6-144">匿名レコードは構造的等価性と比較を使用する</span><span class="sxs-lookup"><span data-stu-id="585c6-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="585c6-145">レコードの種類と同様に、匿名レコードは構造的に equatable と比較できます。</span><span class="sxs-lookup"><span data-stu-id="585c6-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="585c6-146">これは、すべての構成型が、レコード型などの等値と比較をサポートしている場合にのみ当てはまります。</span><span class="sxs-lookup"><span data-stu-id="585c6-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="585c6-147">等値または比較をサポートするには、2つの匿名レコードの "shape" が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="585c6-148">匿名レコードはシリアル化可能</span><span class="sxs-lookup"><span data-stu-id="585c6-148">Anonymous records are serializable</span></span>

<span data-ttu-id="585c6-149">名前付きレコードの場合と同様に、匿名レコードをシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="585c6-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="585c6-150">[でNewtonsoft.Js](https://www.nuget.org/packages/Newtonsoft.Json/)を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="585c6-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn $"Name: {phillip.name} Age: %d{phillip.age}"
```

<span data-ttu-id="585c6-151">匿名レコードは、シリアル化または逆シリアル化された型のドメインを事前に定義しなくても、ネットワーク経由で軽量データを送信する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="585c6-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="585c6-152">匿名レコードと C# 匿名型の相互運用</span><span class="sxs-lookup"><span data-stu-id="585c6-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="585c6-153">[C# の匿名型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)を使用する必要がある .net API を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="585c6-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="585c6-154">C# の匿名型は、匿名レコードを使用してと相互運用するのが簡単です。</span><span class="sxs-lookup"><span data-stu-id="585c6-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="585c6-155">次の例は、匿名レコードを使用して、匿名型を必要とする [LINQ](../../csharp/programming-guide/concepts/linq/index.md) オーバーロードを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="585c6-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn $"{ng.Name} has first letter {ng.FirstLetter}"
```

<span data-ttu-id="585c6-156">.NET で使用される他の多くの Api では、匿名型を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="585c6-157">匿名レコードは、それらを操作するためのツールです。</span><span class="sxs-lookup"><span data-stu-id="585c6-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="585c6-158">制限事項</span><span class="sxs-lookup"><span data-stu-id="585c6-158">Limitations</span></span>

<span data-ttu-id="585c6-159">匿名レコードの使用にはいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="585c6-160">設計に固有のものもあれば、変更に対応しているものもあります。</span><span class="sxs-lookup"><span data-stu-id="585c6-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="585c6-161">パターン一致に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="585c6-161">Limitations with pattern matching</span></span>

<span data-ttu-id="585c6-162">匿名レコードは、名前付きレコードとは異なり、パターンマッチングをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="585c6-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="585c6-163">次の3つの理由があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-163">There are three reasons:</span></span>

1. <span data-ttu-id="585c6-164">パターンでは、名前付きレコードの種類とは異なり、匿名レコードのすべてのフィールドを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="585c6-165">これは、匿名レコードでは構造的サブタイプがサポートされていないためです。これは、標準型です。</span><span class="sxs-lookup"><span data-stu-id="585c6-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="585c6-166">(1) のため、パターン一致式に追加のパターンを含めることはできません。これは、個別のパターンがそれぞれ異なる匿名レコードの種類を示すためです。</span><span class="sxs-lookup"><span data-stu-id="585c6-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="585c6-167">(3) のため、匿名レコードパターンは、"ドット" 表記を使用した場合よりも詳細です。</span><span class="sxs-lookup"><span data-stu-id="585c6-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="585c6-168">コンテキストが制限されている場合、 [パターンマッチングを可能](https://github.com/fsharp/fslang-suggestions/issues/713)にするためのオープン言語の提案があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="585c6-169">互換性に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="585c6-169">Limitations with mutability</span></span>

<span data-ttu-id="585c6-170">現在、データを含む匿名レコードを定義することはできません `mutable` 。</span><span class="sxs-lookup"><span data-stu-id="585c6-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="585c6-171">変更可能なデータを許可する [オープン言語の推奨](https://github.com/fsharp/fslang-suggestions/issues/732) 事項があります。</span><span class="sxs-lookup"><span data-stu-id="585c6-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="585c6-172">構造体の匿名レコードに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="585c6-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="585c6-173">構造体の匿名レコードをまたはとして宣言することはできません `IsByRefLike` `IsReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="585c6-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="585c6-174">と匿名のレコードには、の [オープン言語の推奨](https://github.com/fsharp/fslang-suggestions/issues/712) 事項があり `IsByRefLike` `IsReadOnly` ます。</span><span class="sxs-lookup"><span data-stu-id="585c6-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
