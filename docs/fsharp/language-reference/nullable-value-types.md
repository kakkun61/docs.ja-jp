---
title: null 許容値型
description: 'F # で null にすることもできる値の型を表す方法として、null 許容値型を使用する方法について説明します。'
ms.date: 11/19/2020
ms.openlocfilehash: da0cd85bd651db81ba98c02a9db31d92dc52a8c6
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740430"
---
# <a name="nullable-value-types"></a><span data-ttu-id="ddea3-103">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="ddea3-103">Nullable value types</span></span>

<span data-ttu-id="ddea3-104">_Null 許容値型_ は、 `Nullable<'T>` になる可能性がある任意の [構造体](structures.md)型を表し `null` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-104">A _nullable value type_ `Nullable<'T>` represents any [struct](structures.md) type that could also be `null`.</span></span> <span data-ttu-id="ddea3-105">これは、これらの種類の型 (整数など) を表すことができるようなライブラリやコンポーネントと対話する場合に便利です `null` 。</span><span class="sxs-lookup"><span data-stu-id="ddea3-105">This is helpful when interacting with libraries and components that may choose to represent these kinds of types, like integers, with a `null` value for efficiency reasons.</span></span> <span data-ttu-id="ddea3-106">このコンストラクトをバッキングする基になる型は <xref:System.Nullable%601?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="ddea3-106">The underlying type that backs this construct is <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span>

## <a name="syntax"></a><span data-ttu-id="ddea3-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ddea3-107">Syntax</span></span>

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a><span data-ttu-id="ddea3-108">値を指定して宣言して代入</span><span class="sxs-lookup"><span data-stu-id="ddea3-108">Declare and assign with values</span></span>

<span data-ttu-id="ddea3-109">Null 許容値型の宣言は、F # でのラッパーのような型の宣言と同じです。</span><span class="sxs-lookup"><span data-stu-id="ddea3-109">Declaring a nullable value type is just like declaring any wrapper-like type in F#:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

<span data-ttu-id="ddea3-110">ジェネリック型パラメーターを除外して、型の推定によって解決できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-110">You can also elide the generic type parameter and allow type inference to resolve it:</span></span>

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

<span data-ttu-id="ddea3-111">Null 許容値型に割り当てるには、明示的にする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ddea3-111">To assign to a nullable value type, you'll need to also be explicit.</span></span> <span data-ttu-id="ddea3-112">F # で定義された null 許容値型には暗黙的な変換はありません。</span><span class="sxs-lookup"><span data-stu-id="ddea3-112">There is no implicit conversion for F#-defined nullable value types:</span></span>

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a><span data-ttu-id="ddea3-113">Null を割り当てる</span><span class="sxs-lookup"><span data-stu-id="ddea3-113">Assign null</span></span>

<span data-ttu-id="ddea3-114">Null 許容値型に直接割り当てることはできません `null` 。</span><span class="sxs-lookup"><span data-stu-id="ddea3-114">You cannot directly assign `null` to a nullable value type.</span></span> <span data-ttu-id="ddea3-115">代わりにを使用し `Nullable()` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-115">Use `Nullable()` instead:</span></span>

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

<span data-ttu-id="ddea3-116">これは、に `Nullable<'T>` `null` 適切な値が設定されていないためです。</span><span class="sxs-lookup"><span data-stu-id="ddea3-116">This is because `Nullable<'T>` does not have `null` as a proper value.</span></span>

## <a name="pass-and-assign-to-members"></a><span data-ttu-id="ddea3-117">メンバーへの引き渡しと割り当て</span><span class="sxs-lookup"><span data-stu-id="ddea3-117">Pass and assign to members</span></span>

<span data-ttu-id="ddea3-118">メンバーを操作する場合と F # 値を使用する場合の主な違いは、メンバーを操作するときに null 許容値型を暗黙的に推論できることです。</span><span class="sxs-lookup"><span data-stu-id="ddea3-118">A key difference between working with members and F# values is that nullable value types can be implicitly inferred when you're working with members.</span></span> <span data-ttu-id="ddea3-119">Null 許容値型を入力として受け取る、次のような処理方法を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="ddea3-119">Consider the folling method that takes a nullable value type as input:</span></span>

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

<span data-ttu-id="ddea3-120">前の例では、メソッドにを渡すことができ `12` `M` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-120">In the previous example, you can pass `12` to the method `M`.</span></span> <span data-ttu-id="ddea3-121">自動プロパティに割り当てることもでき `12` `NVT` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-121">You can also assign `12` to the auto property `NVT`.</span></span> <span data-ttu-id="ddea3-122">F # コンパイラは、入力を nullabel 値型として構築できる場合、対象の型が入力と一致するときに、このような呼び出しまたは代入を暗黙的に変換します。</span><span class="sxs-lookup"><span data-stu-id="ddea3-122">The F# compiler will implicitly convert a call or assignment like this when the target type matches the input, if the input can be constructed as a nullabel value type.</span></span>

## <a name="examine-a-nullable-value-type-instance"></a><span data-ttu-id="ddea3-123">Null 許容値型インスタンスを調べる</span><span class="sxs-lookup"><span data-stu-id="ddea3-123">Examine a nullable value type instance</span></span>

<span data-ttu-id="ddea3-124">使用可能な値を表す一般化されたコンストラクトである [オプション](options.md)とは異なり、null 許容値型はパターンマッチングでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="ddea3-124">Unlike [Options](options.md), which are a generalized construct for representing a possible value, nullable value types are not used with pattern matching.</span></span> <span data-ttu-id="ddea3-125">代わりに、式を使用してプロパティを確認する必要があり [`if`](conditional-expressions-if-then-else.md) `HasValue` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-125">Instead, you need to use an [`if`](conditional-expressions-if-then-else.md) expression and check the `HasValue` property.</span></span>

<span data-ttu-id="ddea3-126">基になる値を取得するには、次のよう `Value` に、チェックの後にプロパティを使用し `HasValue` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-126">To get the underlying value, use the `Value` property after a `HasValue` check, like so:</span></span>

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a><span data-ttu-id="ddea3-127">Null 許容の演算子</span><span class="sxs-lookup"><span data-stu-id="ddea3-127">Nullable operators</span></span>

<span data-ttu-id="ddea3-128">算術または比較など、null 許容値型に対する操作では、 [null 許容演算子](symbol-and-operator-reference/nullable-operators.md)を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddea3-128">Operations on nullable value types, such as arithmetic or comparison, can require the use of [nullable operators](symbol-and-operator-reference/nullable-operators.md).</span></span>

<span data-ttu-id="ddea3-129">名前空間の変換演算子を使用して、null 許容値型から別の型に変換でき `FSharp.Linq` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-129">You can convert from one nullable value type to another using conversion operators from the `FSharp.Linq` namespace:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

<span data-ttu-id="ddea3-130">また、適切な null 非許容演算子を使用してプリミティブ型に変換し、値がない場合は例外が発生しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-130">You can also use an appropriate non-nullable operator to convert to a primitive type, risking an exception if it has no value:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

<span data-ttu-id="ddea3-131">また、次のように、null 値を許容する演算子を使用することもでき `HasValue` `Value` ます。</span><span class="sxs-lookup"><span data-stu-id="ddea3-131">You can also use nullable operators as a short-hand for checking `HasValue` and `Value`:</span></span>

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

<span data-ttu-id="ddea3-132">比較では、 `?>` 左辺が null 値が許容されるかどうかを確認し、値がある場合にのみ成功します。</span><span class="sxs-lookup"><span data-stu-id="ddea3-132">The `?>` comparison checks if the left-hand side is nullable and only succeeds if it has a value.</span></span> <span data-ttu-id="ddea3-133">これは、その後の行に相当します。</span><span class="sxs-lookup"><span data-stu-id="ddea3-133">It is equivalent to the line that follows it.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddea3-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddea3-134">See also</span></span>

- [<span data-ttu-id="ddea3-135">構造体</span><span class="sxs-lookup"><span data-stu-id="ddea3-135">Structures</span></span>](structures.md)
- [<span data-ttu-id="ddea3-136">F # オプション</span><span class="sxs-lookup"><span data-stu-id="ddea3-136">F# Options</span></span>](options.md)
