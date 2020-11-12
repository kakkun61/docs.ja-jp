---
title: スライス
description: '既存の F # データ型にスライスを使用する方法、およびその他のデータ型用に独自のスライスを定義する方法について説明します。'
ms.date: 12/23/2019
ms.openlocfilehash: a3920ad9e1b205b506aaee92c4606bcebf94feba
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557078"
---
# <a name="slices"></a><span data-ttu-id="2ac8f-103">スライス</span><span class="sxs-lookup"><span data-stu-id="2ac8f-103">Slices</span></span>

<span data-ttu-id="2ac8f-104">F # では、スライスは、その `GetSlice` 定義またはスコープ内の [型拡張](type-extensions.md)でメソッドを持つ任意のデータ型のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="2ac8f-105">これは、F # の配列とリストで最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="2ac8f-106">この記事では、既存の F # 型からスライスを取得する方法と、独自のスライスを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="2ac8f-107">スライスは [インデクサー](./members/indexed-properties.md)に似ていますが、基になるデータ構造から1つの値を生成するのではなく、複数の値を生成します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="2ac8f-108">現在、F # には、文字列、リスト、配列、および2D 配列をスライスするための組み込みサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="2ac8f-109">F # リストと配列を使用した基本的なスライス</span><span class="sxs-lookup"><span data-stu-id="2ac8f-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="2ac8f-110">スライスされる最も一般的なデータ型は、F # のリストと配列です。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="2ac8f-111">次の例では、リストを使用してこれを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="2ac8f-112">配列のスライスは、スライスリストと同じです。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="2ac8f-113">多次元配列のスライス</span><span class="sxs-lookup"><span data-stu-id="2ac8f-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="2ac8f-114">F # は、F # コアライブラリの多次元配列をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="2ac8f-115">1次元配列の場合と同様に、多次元配列のスライスも役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="2ac8f-116">ただし、追加のディメンションの導入では、特定の行と列のスライスを取得できるように、若干異なる構文が必要になります。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="2ac8f-117">次の例は、2D 配列をスライスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="2ac8f-118">現在、F # コアライブラリでは、 `GetSlice` 3d 配列に対して定義されていません。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="2ac8f-119">3D 配列やその他の次元の配列をスライスする場合は、自分でメンバーを定義 `GetSlice` します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="2ac8f-120">他のデータ構造のスライスの定義</span><span class="sxs-lookup"><span data-stu-id="2ac8f-120">Defining slices for other data structures</span></span>

<span data-ttu-id="2ac8f-121">F # コアライブラリでは、型の限られたセットのスライスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="2ac8f-122">より多くのデータ型に対してスライスを定義する場合は、型定義自体または型拡張機能のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="2ac8f-123">たとえば、クラスのスライスを定義して、 <xref:System.ArraySegment%601> 便利なデータ操作を可能にする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

<span data-ttu-id="2ac8f-124">型と型を使用するもう1つの例を <xref:System.Span%601> <xref:System.ReadOnlySpan%601> 次に示します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-124">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

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

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="2ac8f-125">組み込みの F # スライスは両端を含みます</span><span class="sxs-lookup"><span data-stu-id="2ac8f-125">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="2ac8f-126">F # のすべての組み込みスライスは、終了します。つまり、上限がスライスに含まれます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-126">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="2ac8f-127">開始インデックスと終了インデックスを持つ特定のスライスの場合、結果として得られるスライスには `x` `y` *yth* 値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-127">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="2ac8f-128">組み込みの F # 空のスライス</span><span class="sxs-lookup"><span data-stu-id="2ac8f-128">Built-in F# empty slices</span></span>

<span data-ttu-id="2ac8f-129">F # のリスト、配列、シーケンス、文字列、2D 配列、3D 配列、および4D 配列では、存在しないスライスが生成される場合、空のスライスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-129">F# lists, arrays, sequences, strings, 2D arrays, 3D arrays, and 4D arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="2ac8f-130">以下、具体例に沿って説明します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-130">Consider the following:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

<span data-ttu-id="2ac8f-131">C# 開発者は、空のスライスを生成するのではなく、例外をスローすることを期待できます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-131">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="2ac8f-132">これは、空のコレクションが F # で構成されるという事実をルートとする設計上の決定です。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-132">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="2ac8f-133">空の F # リストは、別の F # リストで構成できます。また、空の文字列を既存の文字列に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-133">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="2ac8f-134">パラメーターとして渡された値に基づいてスライスを取り、空のコレクションを生成することによって、F # コードの合成特性に適合するようにすることは、一般的な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-134">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="2ac8f-135">3D および4D 配列の固定インデックススライス</span><span class="sxs-lookup"><span data-stu-id="2ac8f-135">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="2ac8f-136">F # 3D および4D 配列の場合は、特定のインデックスを "修正" し、そのインデックスが固定されている他のディメンションをスライスできます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-136">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="2ac8f-137">これを説明するために、次の3D 配列について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-137">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="2ac8f-138">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="2ac8f-138">*z = 0*</span></span>
| <span data-ttu-id="2ac8f-139">x\y</span><span class="sxs-lookup"><span data-stu-id="2ac8f-139">x\y</span></span>   | <span data-ttu-id="2ac8f-140">0</span><span class="sxs-lookup"><span data-stu-id="2ac8f-140">0</span></span> | <span data-ttu-id="2ac8f-141">1</span><span class="sxs-lookup"><span data-stu-id="2ac8f-141">1</span></span> |
|-------|---|---|
| <span data-ttu-id="2ac8f-142">**0**</span><span class="sxs-lookup"><span data-stu-id="2ac8f-142">**0**</span></span> | <span data-ttu-id="2ac8f-143">0</span><span class="sxs-lookup"><span data-stu-id="2ac8f-143">0</span></span> | <span data-ttu-id="2ac8f-144">1</span><span class="sxs-lookup"><span data-stu-id="2ac8f-144">1</span></span> |
| <span data-ttu-id="2ac8f-145">**1**</span><span class="sxs-lookup"><span data-stu-id="2ac8f-145">**1**</span></span> | <span data-ttu-id="2ac8f-146">2</span><span class="sxs-lookup"><span data-stu-id="2ac8f-146">2</span></span> | <span data-ttu-id="2ac8f-147">3</span><span class="sxs-lookup"><span data-stu-id="2ac8f-147">3</span></span> |

<span data-ttu-id="2ac8f-148">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="2ac8f-148">*z = 1*</span></span>
| <span data-ttu-id="2ac8f-149">x\y</span><span class="sxs-lookup"><span data-stu-id="2ac8f-149">x\y</span></span>   | <span data-ttu-id="2ac8f-150">0</span><span class="sxs-lookup"><span data-stu-id="2ac8f-150">0</span></span> | <span data-ttu-id="2ac8f-151">1</span><span class="sxs-lookup"><span data-stu-id="2ac8f-151">1</span></span> |
|-------|---|---|
| <span data-ttu-id="2ac8f-152">**0**</span><span class="sxs-lookup"><span data-stu-id="2ac8f-152">**0**</span></span> | <span data-ttu-id="2ac8f-153">4</span><span class="sxs-lookup"><span data-stu-id="2ac8f-153">4</span></span> | <span data-ttu-id="2ac8f-154">5</span><span class="sxs-lookup"><span data-stu-id="2ac8f-154">5</span></span> |
| <span data-ttu-id="2ac8f-155">**1**</span><span class="sxs-lookup"><span data-stu-id="2ac8f-155">**1**</span></span> | <span data-ttu-id="2ac8f-156">6</span><span class="sxs-lookup"><span data-stu-id="2ac8f-156">6</span></span> | <span data-ttu-id="2ac8f-157">7</span><span class="sxs-lookup"><span data-stu-id="2ac8f-157">7</span></span> |

<span data-ttu-id="2ac8f-158">配列からスライスを抽出する場合は `[| 4; 5 |]` 、固定インデックススライスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-158">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

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

<span data-ttu-id="2ac8f-159">最後の行は、 `y` `z` 3d 配列のと決まっを修正し、 `x` マトリックスに対応する残りの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2ac8f-159">The last line fixes the `y` and `z` indicies of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ac8f-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ac8f-160">See also</span></span>

- [<span data-ttu-id="2ac8f-161">インデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="2ac8f-161">Indexed properties</span></span>](./members/indexed-properties.md)
