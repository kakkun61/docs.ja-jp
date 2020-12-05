---
title: 配列
description: 'F # プログラミング言語で配列を作成して使用する方法について説明します。'
ms.date: 08/13/2020
ms.openlocfilehash: 96b0d7eaf10d5afcd9a647681d5c2ef2d2fba335
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739752"
---
# <a name="arrays"></a><span data-ttu-id="49489-103">配列</span><span class="sxs-lookup"><span data-stu-id="49489-103">Arrays</span></span>

<span data-ttu-id="49489-104">配列は、0 から始まる一連のデータ要素の、固定サイズの変更可能なコレクションで、その型はすべて同じです。</span><span class="sxs-lookup"><span data-stu-id="49489-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="49489-105">配列の作成</span><span class="sxs-lookup"><span data-stu-id="49489-105">Create arrays</span></span>

<span data-ttu-id="49489-106">配列は複数の方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="49489-106">You can create arrays in several ways.</span></span> <span data-ttu-id="49489-107">`[|`次の例に示すように、との間に連続する値をセミコロンで区切って指定すると、小さい配列を作成でき `|]` ます。</span><span class="sxs-lookup"><span data-stu-id="49489-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="49489-108">各要素を別々の行に配置することもでき、その場合は、セミコロンの区切り記号を省略できます。</span><span class="sxs-lookup"><span data-stu-id="49489-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="49489-109">配列の要素の型は、使用されるリテラルから推論され、すべて同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="49489-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="49489-110">次のコードは、1.0 が浮動小数点数で、2 と 3 は整数であるため、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="49489-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="49489-111">シーケンス式を使用して配列を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="49489-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="49489-112">1 から 10 までの整数の 2 乗の配列を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="49489-113">すべての要素が 0 に初期化される配列を作成するには、`Array.zeroCreate` を使用します。</span><span class="sxs-lookup"><span data-stu-id="49489-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="49489-114">アクセス要素</span><span class="sxs-lookup"><span data-stu-id="49489-114">Access elements</span></span>

<span data-ttu-id="49489-115">配列要素には、ドット演算子 ( `.` ) と角かっこ (および) を使用してアクセスでき `[` `]` ます。</span><span class="sxs-lookup"><span data-stu-id="49489-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="49489-116">配列のインデックスは0から始まります。</span><span class="sxs-lookup"><span data-stu-id="49489-116">Array indexes start at 0.</span></span>

<span data-ttu-id="49489-117">また、スライス表記を使用して配列の要素にアクセスすることもできます。この方法では、配列のサブ範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="49489-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="49489-118">スライス表記の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="49489-119">スライス表記を使用するときは、配列の新しいコピーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="49489-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="49489-120">配列の型とモジュール</span><span class="sxs-lookup"><span data-stu-id="49489-120">Array types and modules</span></span>

<span data-ttu-id="49489-121">F# の配列の型はすべて、.NET Framework 型の <xref:System.Array?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="49489-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49489-122">したがって、F# の配列では、<xref:System.Array?displayProperty=nameWithType> で使用できるすべての機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="49489-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="49489-123">[ `Array` モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)は、1次元配列に対する操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="49489-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="49489-124">`Array2D`、`Array3D`、`Array4D` の各モジュールには、それぞれ、2 次元、3 次元、4 次元の配列の操作をサポートする関数があります。</span><span class="sxs-lookup"><span data-stu-id="49489-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="49489-125">4 より大きいランクの配列は、<xref:System.Array?displayProperty=nameWithType> を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="49489-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="49489-126">単純な関数</span><span class="sxs-lookup"><span data-stu-id="49489-126">Simple functions</span></span>

<span data-ttu-id="49489-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) 要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="49489-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="49489-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) 配列の長さを示します。</span><span class="sxs-lookup"><span data-stu-id="49489-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="49489-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 要素を指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="49489-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="49489-130">これらの関数の使い方を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="49489-131">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49489-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="49489-132">配列を作成する関数</span><span class="sxs-lookup"><span data-stu-id="49489-132">Functions that create arrays</span></span>

<span data-ttu-id="49489-133">既存の配列を必要とせずに配列を作成できる関数がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="49489-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="49489-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) 要素を含まない新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="49489-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) 指定されたサイズの配列を作成し、すべての要素を指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="49489-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="49489-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) 次元と要素を生成する関数を指定して、配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="49489-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) すべての要素が配列の型の0値に初期化される配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="49489-138">これらの関数の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="49489-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="49489-139">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49489-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="49489-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) 既存の配列からコピーされる要素を格納する新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="49489-141">コピーは簡易コピーです。つまり、要素の型が参照型である場合は、参照だけがコピーされ、基になっているオブジェクトはコピーされません。</span><span class="sxs-lookup"><span data-stu-id="49489-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="49489-142">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="49489-143">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="49489-144">`Test1` という文字列は、最初の配列にのみ表示されます。これは、`firstArray` の参照が、新しい要素を作成する操作によって上書きされるものの、空の文字列への元の参照は影響を受けず、`secondArray` にまだ存在しているためです。</span><span class="sxs-lookup"><span data-stu-id="49489-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="49489-145">`Test2` という文字列は、両方の配列で表示されます。これは、`Insert` 型に対する <xref:System.Text.StringBuilder?displayProperty=nameWithType> 操作は基になっている <xref:System.Text.StringBuilder?displayProperty=nameWithType> オブジェクトに影響を与え、このオブジェクトは両方の配列で参照されているためです。</span><span class="sxs-lookup"><span data-stu-id="49489-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="49489-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) 配列のサブ範囲から新しい配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="49489-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="49489-147">サブ範囲は、開始インデックスと長さで指定します。</span><span class="sxs-lookup"><span data-stu-id="49489-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="49489-148">`Array.sub` を使用したコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="49489-149">出力では、サブ配列が要素 5 から開始し、10 個の要素を含むことが示されています。</span><span class="sxs-lookup"><span data-stu-id="49489-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="49489-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) 2つの既存の配列を組み合わせることによって、新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="49489-151">次のコードは、 **Array. append** を示しています。</span><span class="sxs-lookup"><span data-stu-id="49489-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="49489-152">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="49489-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) 新しい配列に含める配列の要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="49489-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="49489-154">次のコードで `Array.choose` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="49489-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="49489-155">配列の要素の型は、オプションの型で返される値の型と一致している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="49489-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="49489-156">この例では、要素の型は `int` ですが、オプションは多項式関数 `elem*elem - 1` の結果であり、浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="49489-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="49489-157">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="49489-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) 既存の配列の各配列要素に対して指定された関数を実行し、関数によって生成された要素を収集し、それらを新しい配列に結合します。</span><span class="sxs-lookup"><span data-stu-id="49489-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="49489-159">次のコードで `Array.collect` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="49489-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="49489-160">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="49489-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) 配列のシーケンスを取得し、それらを1つの配列に結合します。</span><span class="sxs-lookup"><span data-stu-id="49489-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="49489-162">次のコードで `Array.concat` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="49489-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="49489-163">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="49489-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) ブール条件関数を受け取り、条件が true である入力配列の要素のみを含む新しい配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="49489-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="49489-165">次のコードで `Array.filter` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="49489-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="49489-166">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="49489-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) 既存の配列の順序を逆にして、新しい配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="49489-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="49489-168">次のコードで `Array.rev` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="49489-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="49489-169">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="49489-170">次の例に示すように、パイプライン演算子 () を使用して配列を変換する配列モジュールの関数を簡単に組み合わせることができ `|>` ます。</span><span class="sxs-lookup"><span data-stu-id="49489-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="49489-171">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="49489-172">多次元配列</span><span class="sxs-lookup"><span data-stu-id="49489-172">Multidimensional arrays</span></span>

<span data-ttu-id="49489-173">多次元配列を作成できますが、多次元配列リテラルを記述するための構文はありません。</span><span class="sxs-lookup"><span data-stu-id="49489-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="49489-174">[`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html)配列要素のシーケンスのシーケンスから配列を作成するには、演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="49489-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="49489-175">シーケンスには、配列リテラルまたはリスト リテラルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="49489-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="49489-176">たとえば、次のコードでは 2 次元の配列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="49489-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="49489-177">また、関数を使用して [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) 2 次元の配列を初期化することもできます。また、3次元と4次元の配列でも同様の関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="49489-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="49489-178">これらの関数は、要素の作成に使用する関数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="49489-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="49489-179">関数を指定するのではなく、初期値に設定された要素を含む2次元配列を作成するには、関数を使用します。この関数は、 [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) 最大4次元の配列に対しても使用できます。</span><span class="sxs-lookup"><span data-stu-id="49489-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="49489-180">次のコード例では、まず、目的の要素を含む複数の配列から成る 1 つの配列を作成し、次に、`Array2D.init` を使用して目的の 2 次元配列を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="49489-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="49489-181">配列インデックスとスライス構文は、4 ランクまでの配列に使用できます。</span><span class="sxs-lookup"><span data-stu-id="49489-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="49489-182">複数の次元でインデックスを指定する場合は、次のコード例に示すように、コンマを使用してインデックスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="49489-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="49489-183">2 次元配列の型は `<type>[,]` として書き出され (`int[,]`、`double[,]` など)、3 次元配列の型は `<type>[,,]` として書き出されます。このように、次元が高くなるにつれ、書き出される型が変わります。</span><span class="sxs-lookup"><span data-stu-id="49489-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="49489-184">1 次元配列で使用できる関数のサブセットのうち、多次元配列でも使用できるのは一部だけです。</span><span class="sxs-lookup"><span data-stu-id="49489-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="49489-185">配列スライスと多次元配列</span><span class="sxs-lookup"><span data-stu-id="49489-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="49489-186">2次元配列 (マトリックス) では、範囲を指定し、ワイルドカード () 文字を使用して `*` 行または列全体を指定することによって、サブマトリックスを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="49489-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="49489-187">多次元配列を、同じまたは下位の次元のサブに分解することができます。</span><span class="sxs-lookup"><span data-stu-id="49489-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="49489-188">たとえば、単一の行または列を指定して、行列からベクターを取得できます。</span><span class="sxs-lookup"><span data-stu-id="49489-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="49489-189">このスライス構文は、要素アクセス演算子およびオーバーロードされた `GetSlice` メソッドを実装する型に使用できます。</span><span class="sxs-lookup"><span data-stu-id="49489-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="49489-190">たとえば、次のコードは、F# 2D 配列をラップし、配列のインデックスのサポートを提供する項目プロパティを実装し、3 つのバージョンの `GetSlice` を実装するマトリックス型を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="49489-191">マトリックス型のテンプレートとしてこのコードの使用が可能であれば、このセクションで説明するすべてのスライスの操作を使用できます。</span><span class="sxs-lookup"><span data-stu-id="49489-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn $"{submatrix}"

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn $"{firstCol}"
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="49489-192">ブール関数 (配列の)</span><span class="sxs-lookup"><span data-stu-id="49489-192">Boolean functions on arrays</span></span>

<span data-ttu-id="49489-193">関数 [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) と [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) テスト要素は、それぞれ1つまたは2つの配列にあります。</span><span class="sxs-lookup"><span data-stu-id="49489-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="49489-194">これらの関数は、テスト用の関数を受け取り、要素 (または `true` の場合は要素のペア) のうち、条件を満たす要素がある場合は `Array.exists2` を返します。</span><span class="sxs-lookup"><span data-stu-id="49489-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="49489-195">次のコードは、`Array.exists` と `Array.exists2` の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="49489-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="49489-196">これらの例では、ただ 1 つの引数 (この場合は関数引数) を適用することで、新しい関数を作成しています。</span><span class="sxs-lookup"><span data-stu-id="49489-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="49489-197">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="49489-198">同様に、関数は配列をテストして、 [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) すべての要素がブール条件を満たすかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="49489-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="49489-199">このバリエーションは、 [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) 同じ長さの2つの配列の要素を含むブール関数を使用することによって同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="49489-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="49489-200">これらの関数の使い方を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="49489-201">これらの例の出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49489-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="49489-202">配列の検索</span><span class="sxs-lookup"><span data-stu-id="49489-202">Search arrays</span></span>

<span data-ttu-id="49489-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) ブール型の関数を受け取り、その関数が返す最初の要素を返し `true` <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> ます。条件を満たす要素が見つからない場合は、を発生させます。</span><span class="sxs-lookup"><span data-stu-id="49489-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="49489-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) はと似てい `Array.find` ますが、要素自体の代わりに要素のインデックスを返す点が異なります。</span><span class="sxs-lookup"><span data-stu-id="49489-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="49489-205">次のコードでは、`Array.find` と `Array.findIndex` を使用して、完全平方かつ完全立方である値を探しています。</span><span class="sxs-lookup"><span data-stu-id="49489-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="49489-206">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49489-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="49489-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) はと似てい `Array.find` ますが、結果がオプションの型で `None` あり、要素が見つからない場合はを返します。</span><span class="sxs-lookup"><span data-stu-id="49489-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="49489-208">一致する要素が配列内にあるかどうかわからない場合は、`Array.tryFind` ではなく、`Array.find` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="49489-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="49489-209">同様に、 [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) はと似ていますが、 `Array.findIndex` オプションの型が戻り値である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="49489-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="49489-210">要素が見つからない場合、オプションは `None` です。</span><span class="sxs-lookup"><span data-stu-id="49489-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="49489-211">`Array.tryFind` を使用したコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="49489-212">このコードでは、前に示したコードを利用しています。</span><span class="sxs-lookup"><span data-stu-id="49489-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="49489-213">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49489-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="49489-214">[`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick)要素を検索するだけでなく、要素を変換する必要がある場合は、を使用します。</span><span class="sxs-lookup"><span data-stu-id="49489-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="49489-215">この関数の結果は、変換した要素をオプションの値として返した最初の要素になります。該当する要素が見つからない場合は、`None` を返します。</span><span class="sxs-lookup"><span data-stu-id="49489-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="49489-216">`Array.tryPick` の使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="49489-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="49489-217">この例では、ラムダ式の代わりに、複数のローカル ヘルパー関数を定義することでコードを簡単にしています。</span><span class="sxs-lookup"><span data-stu-id="49489-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="49489-218">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49489-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="49489-219">配列に対して計算を実行する</span><span class="sxs-lookup"><span data-stu-id="49489-219">Perform computations on arrays</span></span>

<span data-ttu-id="49489-220">関数は、 [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) 配列内の各要素の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="49489-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="49489-221">この関数を使用できるのは、整数による正確な除算がサポートされている要素型だけです。そのため、浮動小数点型では使用できますが、整数型では使用できません。</span><span class="sxs-lookup"><span data-stu-id="49489-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="49489-222">関数は、 [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) 各要素に対して関数を呼び出した結果の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="49489-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="49489-223">整数型の配列の場合は、`Array.averageBy` を使用し、この関数で各要素を浮動小数点型に変換して計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="49489-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="49489-224">[`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max)要素型でサポートされている場合は、またはを使用して、 [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) 要素の最大値または最小値を取得します。</span><span class="sxs-lookup"><span data-stu-id="49489-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="49489-225">同様に、 [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) とを使用すると、最初に関数を実行して [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) 、比較をサポートする型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="49489-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="49489-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) 配列の要素を追加し、 [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) 各要素に対して関数を呼び出し、結果を加算します。</span><span class="sxs-lookup"><span data-stu-id="49489-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="49489-227">戻り値を格納せずに、配列内の各要素に対して関数を実行するには、を使用し [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) ます。</span><span class="sxs-lookup"><span data-stu-id="49489-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="49489-228">同じ長さの2つの配列を含む関数の場合は、を使用 [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) します。</span><span class="sxs-lookup"><span data-stu-id="49489-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="49489-229">関数の結果の配列も保持する必要がある場合 [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) は、またはを使用し [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) ます。これは、一度に2つの配列を操作します。</span><span class="sxs-lookup"><span data-stu-id="49489-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="49489-230">バリエーションを [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) 使用して、 [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) 要素のインデックスを計算に含めることができます。との場合も同様です [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) 。</span><span class="sxs-lookup"><span data-stu-id="49489-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="49489-231">、、、、、およびの各関数は、 [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) 配列のすべての要素を含むアルゴリズムを実行します。</span><span class="sxs-lookup"><span data-stu-id="49489-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="49489-232">同様に、バリエーション [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) とは [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) 2 つの配列に対して計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="49489-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="49489-233">計算を実行するためのこれらの関数は、 [List モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)内の同じ名前の関数に対応しています。</span><span class="sxs-lookup"><span data-stu-id="49489-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="49489-234">使用例については、「 [リスト](lists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49489-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="49489-235">配列の変更</span><span class="sxs-lookup"><span data-stu-id="49489-235">Modify arrays</span></span>

<span data-ttu-id="49489-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 要素を指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="49489-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="49489-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) 配列内の要素の範囲を、指定した値に設定します。</span><span class="sxs-lookup"><span data-stu-id="49489-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="49489-238">`Array.fill` のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="49489-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="49489-239">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49489-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="49489-240">を使用すると、 [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) ある配列のサブセクションを別の配列にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="49489-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="49489-241">他の型との間での変換</span><span class="sxs-lookup"><span data-stu-id="49489-241">Convert to and from other types</span></span>

<span data-ttu-id="49489-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) リストから配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="49489-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) シーケンスから配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="49489-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="49489-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) および [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) は、配列型から他のコレクション型に変換します。</span><span class="sxs-lookup"><span data-stu-id="49489-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="49489-245">配列の並べ替え</span><span class="sxs-lookup"><span data-stu-id="49489-245">Sort arrays</span></span>

<span data-ttu-id="49489-246">[`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort)ジェネリック比較関数を使用して配列を並べ替えるには、を使用します。</span><span class="sxs-lookup"><span data-stu-id="49489-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="49489-247">キー [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) と呼ばれる値を生成する関数を指定するために *key* 使用します。この関数は、キーの汎用比較関数を使用して並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="49489-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="49489-248">[`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith)カスタム比較関数を指定する場合は、を使用します。</span><span class="sxs-lookup"><span data-stu-id="49489-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="49489-249">`Array.sort`、`Array.sortBy`、および `Array.sortWith` は、いずれも、並べ替えた配列を新しい配列として返します。</span><span class="sxs-lookup"><span data-stu-id="49489-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="49489-250">、、およびのバリエーションにより、 [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) 新しい配列が返される代わりに、 [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) 既存の配列が変更されます。</span><span class="sxs-lookup"><span data-stu-id="49489-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="49489-251">配列と組</span><span class="sxs-lookup"><span data-stu-id="49489-251">Arrays and tuples</span></span>

<span data-ttu-id="49489-252">関数とは、 [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) 組のペアの配列を配列のタプルに変換します。逆の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="49489-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="49489-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) とは似ていますが、3つの [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) 要素または3つの配列の組で動作する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="49489-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="49489-254">配列に対する並列計算</span><span class="sxs-lookup"><span data-stu-id="49489-254">Parallel computations on arrays</span></span>

<span data-ttu-id="49489-255">モジュールには、 [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) 配列に対して並列計算を実行する関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="49489-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="49489-256">このモジュールは、Version 4 より前の .NET Framework を対象とするアプリケーションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="49489-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="49489-257">関連項目</span><span class="sxs-lookup"><span data-stu-id="49489-257">See also</span></span>

- [<span data-ttu-id="49489-258">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="49489-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="49489-259">F# の型</span><span class="sxs-lookup"><span data-stu-id="49489-259">F# Types</span></span>](fsharp-types.md)
