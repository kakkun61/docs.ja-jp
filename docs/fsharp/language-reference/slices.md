---
title: スライス
description: '既存の F # データ型にスライスを使用する方法、およびその他のデータ型用に独自のスライスを定義する方法について説明します。'
ms.date: 11/20/2020
ms.openlocfilehash: 9c072648ed46ae29871f2be5cc64b493f6a9b857
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098958"
---
# <a name="slices"></a><span data-ttu-id="6103e-103">スライス</span><span class="sxs-lookup"><span data-stu-id="6103e-103">Slices</span></span>

<span data-ttu-id="6103e-104">この記事では、既存の F # 型からスライスを取得する方法と、独自のスライスを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6103e-104">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="6103e-105">F # では、スライスは任意のデータ型のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="6103e-105">In F#, a slice is a subset of any data type.</span></span>  <span data-ttu-id="6103e-106">スライスは [インデクサー](./members/indexed-properties.md)に似ていますが、基になるデータ構造から1つの値を生成するのではなく、複数の値を生成します。</span><span class="sxs-lookup"><span data-stu-id="6103e-106">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span> <span data-ttu-id="6103e-107">スライスでは、演算子の構文を使用して、 `..` データ型の指定されたインデックスの範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="6103e-107">Slices use the `..` operator syntax to select the range of specified indices in a data type.</span></span> <span data-ttu-id="6103e-108">詳細については、「 [ループ式のリファレンス](./loops-for-in-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6103e-108">For more information, see the [looping expression reference article](./loops-for-in-expression.md).</span></span>

<span data-ttu-id="6103e-109">現在、F # には、文字列、リスト、配列、多次元 (2D、3D、4D) 配列をスライスするための組み込みサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="6103e-109">F# currently has intrinsic support for slicing strings, lists, arrays, and multidimensional (2D, 3D, 4D) arrays.</span></span> <span data-ttu-id="6103e-110">スライスは、F # の配列とリストで最も一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6103e-110">Slicing is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="6103e-111">カスタムデータ型にスライスを追加するには、 `GetSlice` 型定義でメソッドを使用するか、スコープ内の [型拡張機能](type-extensions.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="6103e-111">You can add slicing to your custom data types by using the `GetSlice` method in your type definition or in an in-scope [type extension](type-extensions.md).</span></span>

## <a name="slicing-f-lists-and-arrays"></a><span data-ttu-id="6103e-112">F # リストと配列のスライス</span><span class="sxs-lookup"><span data-stu-id="6103e-112">Slicing F# lists and arrays</span></span>

<span data-ttu-id="6103e-113">スライスされる最も一般的なデータ型は、F # のリストと配列です。</span><span class="sxs-lookup"><span data-stu-id="6103e-113">The most common data types that are sliced are F# lists and arrays.</span></span>  <span data-ttu-id="6103e-114">次の例では、リストをスライスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6103e-114">The following example demonstrates how to slice lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="6103e-115">配列のスライスは、スライスリストと同じです。</span><span class="sxs-lookup"><span data-stu-id="6103e-115">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="6103e-116">多次元配列のスライス</span><span class="sxs-lookup"><span data-stu-id="6103e-116">Slicing multidimensional arrays</span></span>

<span data-ttu-id="6103e-117">F # は、F # コアライブラリの多次元配列をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6103e-117">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="6103e-118">1次元配列の場合と同様に、多次元配列のスライスも役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="6103e-118">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="6103e-119">ただし、追加のディメンションの導入では、特定の行と列のスライスを取得できるように、若干異なる構文が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6103e-119">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="6103e-120">次の例は、2D 配列をスライスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6103e-120">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="6103e-121">他のデータ構造のスライスの定義</span><span class="sxs-lookup"><span data-stu-id="6103e-121">Defining slices for other data structures</span></span>

<span data-ttu-id="6103e-122">F # コアライブラリでは、型の限られたセットのスライスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="6103e-122">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="6103e-123">より多くのデータ型に対してスライスを定義する場合は、型定義自体または型拡張機能のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6103e-123">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="6103e-124">たとえば、クラスのスライスを定義して、 <xref:System.ArraySegment%601> 便利なデータ操作を可能にする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6103e-124">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

<span data-ttu-id="6103e-125">型と型を使用するもう1つの例を <xref:System.Span%601> <xref:System.ReadOnlySpan%601> 次に示します。</span><span class="sxs-lookup"><span data-stu-id="6103e-125">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="6103e-126">組み込みの F # スライスは両端を含みます</span><span class="sxs-lookup"><span data-stu-id="6103e-126">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="6103e-127">F # のすべての組み込みスライスは、終了します。つまり、上限がスライスに含まれます。</span><span class="sxs-lookup"><span data-stu-id="6103e-127">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="6103e-128">開始インデックスと終了インデックスを持つ特定のスライスの場合、結果として得られるスライスには `x` `y` *yth* 値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6103e-128">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="6103e-129">組み込みの F # 空のスライス</span><span class="sxs-lookup"><span data-stu-id="6103e-129">Built-in F# empty slices</span></span>

<span data-ttu-id="6103e-130">F # リスト、配列、シーケンス、文字列、多次元 (2D、3D、4D) の各配列では、存在しないスライスが生成される可能性がある場合、空のスライスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6103e-130">F# lists, arrays, sequences, strings, multidimensional (2D, 3D, 4D) arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="6103e-131">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="6103e-131">Consider the following example:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

> [!IMPORTANT]
> <span data-ttu-id="6103e-132">C# 開発者は、空のスライスを生成するのではなく、例外をスローすることを期待できます。</span><span class="sxs-lookup"><span data-stu-id="6103e-132">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="6103e-133">これは、空のコレクションが F # で構成されるという事実をルートとする設計上の決定です。</span><span class="sxs-lookup"><span data-stu-id="6103e-133">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="6103e-134">空の F # リストは、別の F # リストで構成できます。また、空の文字列を既存の文字列に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="6103e-134">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="6103e-135">通常は、パラメーターとして渡された値に基づいてスライスを実行し、空のコレクションを生成して F # コードの合成特性に適合するようにすることで、範囲外の > を許容することができます。</span><span class="sxs-lookup"><span data-stu-id="6103e-135">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds > by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="6103e-136">3D および4D 配列の固定インデックススライス</span><span class="sxs-lookup"><span data-stu-id="6103e-136">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="6103e-137">F # 3D および4D 配列の場合は、特定のインデックスを "修正" し、そのインデックスが固定されている他のディメンションをスライスできます。</span><span class="sxs-lookup"><span data-stu-id="6103e-137">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="6103e-138">これを説明するために、次の3D 配列について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="6103e-138">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="6103e-139">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="6103e-139">*z = 0*</span></span>

| <span data-ttu-id="6103e-140">x\y</span><span class="sxs-lookup"><span data-stu-id="6103e-140">x\y</span></span>   | <span data-ttu-id="6103e-141">0</span><span class="sxs-lookup"><span data-stu-id="6103e-141">0</span></span> | <span data-ttu-id="6103e-142">1</span><span class="sxs-lookup"><span data-stu-id="6103e-142">1</span></span> |
|-------|---|---|
| <span data-ttu-id="6103e-143">**0**</span><span class="sxs-lookup"><span data-stu-id="6103e-143">**0**</span></span> | <span data-ttu-id="6103e-144">0</span><span class="sxs-lookup"><span data-stu-id="6103e-144">0</span></span> | <span data-ttu-id="6103e-145">1</span><span class="sxs-lookup"><span data-stu-id="6103e-145">1</span></span> |
| <span data-ttu-id="6103e-146">**1**</span><span class="sxs-lookup"><span data-stu-id="6103e-146">**1**</span></span> | <span data-ttu-id="6103e-147">2</span><span class="sxs-lookup"><span data-stu-id="6103e-147">2</span></span> | <span data-ttu-id="6103e-148">3</span><span class="sxs-lookup"><span data-stu-id="6103e-148">3</span></span> |

<span data-ttu-id="6103e-149">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="6103e-149">*z = 1*</span></span>

| <span data-ttu-id="6103e-150">x\y</span><span class="sxs-lookup"><span data-stu-id="6103e-150">x\y</span></span>   | <span data-ttu-id="6103e-151">0</span><span class="sxs-lookup"><span data-stu-id="6103e-151">0</span></span> | <span data-ttu-id="6103e-152">1</span><span class="sxs-lookup"><span data-stu-id="6103e-152">1</span></span> |
|-------|---|---|
| <span data-ttu-id="6103e-153">**0**</span><span class="sxs-lookup"><span data-stu-id="6103e-153">**0**</span></span> | <span data-ttu-id="6103e-154">4</span><span class="sxs-lookup"><span data-stu-id="6103e-154">4</span></span> | <span data-ttu-id="6103e-155">5</span><span class="sxs-lookup"><span data-stu-id="6103e-155">5</span></span> |
| <span data-ttu-id="6103e-156">**1**</span><span class="sxs-lookup"><span data-stu-id="6103e-156">**1**</span></span> | <span data-ttu-id="6103e-157">6</span><span class="sxs-lookup"><span data-stu-id="6103e-157">6</span></span> | <span data-ttu-id="6103e-158">7</span><span class="sxs-lookup"><span data-stu-id="6103e-158">7</span></span> |

<span data-ttu-id="6103e-159">配列からスライスを抽出する場合は `[| 4; 5 |]` 、固定インデックススライスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6103e-159">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

```fsharp
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

<span data-ttu-id="6103e-160">最後の行は、 `y` `z` 3d 配列のとインデックスを修正し、 `x` マトリックスに対応する残りの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6103e-160">The last line fixes the `y` and `z` indices of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="6103e-161">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="6103e-161">See also</span></span>

- [<span data-ttu-id="6103e-162">インデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="6103e-162">Indexed properties</span></span>](./members/indexed-properties.md)
