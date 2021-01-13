---
title: ジャグ配列 - C# プログラミング ガイド
description: C# のジャグ配列は、その要素がさまざまなサイズからなる配列です。 ジャグ配列の宣言、初期化、アクセスの方法について説明します。
ms.date: 12/18/2020
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 6d4fb939fb6594c7644a80eb688ea852ddf8a5c5
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737282"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="dd72f-104">ジャグ配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="dd72f-104">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="dd72f-105">ジャグ配列は、その要素がサイズが異なる場合がある配列からなる配列です。</span><span class="sxs-lookup"><span data-stu-id="dd72f-105">A jagged array is an array whose elements are arrays, possibly of different sizes.</span></span> <span data-ttu-id="dd72f-106">ジャグ配列は、"配列の配列" と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="dd72f-106">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="dd72f-107">次の例では、ジャグ配列の宣言、初期化、およびアクセスの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd72f-107">The following examples show how to declare, initialize, and access jagged arrays.</span></span>

 <span data-ttu-id="dd72f-108">次の 3 つの要素を持つ 1 次元配列の宣言では、それぞれが整数の 1 次元配列になっています。</span><span class="sxs-lookup"><span data-stu-id="dd72f-108">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>

 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]

 <span data-ttu-id="dd72f-109">`jaggedArray` を使用する前に、その要素を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd72f-109">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="dd72f-110">次のように要素を初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-110">You can initialize the elements like this:</span></span>

 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]

 <span data-ttu-id="dd72f-111">各要素は、整数の 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="dd72f-111">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="dd72f-112">最初の要素は 5 つの整数の配列で、2 番目の要素は 4 つの整数の配列であり、3 番目の要素は 2 つの整数の配列です。</span><span class="sxs-lookup"><span data-stu-id="dd72f-112">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>

 <span data-ttu-id="dd72f-113">初期化子を使って配列の要素に値を格納することもできます。この場合、配列のサイズは不要です。</span><span class="sxs-lookup"><span data-stu-id="dd72f-113">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="dd72f-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="dd72f-114">For example:</span></span>

 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]

 <span data-ttu-id="dd72f-115">次のように宣言時に配列を初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-115">You can also initialize the array upon declaration like this:</span></span>

 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]

 <span data-ttu-id="dd72f-116">次の短い形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-116">You can use the following shorthand form.</span></span> <span data-ttu-id="dd72f-117">要素の既定の初期化はないので、`new` 演算子を要素の初期化から省略することはできません。</span><span class="sxs-lookup"><span data-stu-id="dd72f-117">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>

 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]

 <span data-ttu-id="dd72f-118">ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-118">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>

 <span data-ttu-id="dd72f-119">これらの例のように配列の各要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-119">You can access individual array elements like these examples:</span></span>

 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]

 <span data-ttu-id="dd72f-120">ジャグ配列と多次元配列を混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-120">It's possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="dd72f-121">異なるサイズの 3 つの 2 次元の配列要素を含む 1 次元のジャグ配列の宣言と初期化を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dd72f-121">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="dd72f-122">詳細については、「[多次元配列](./multidimensional-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd72f-122">For more information, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>

 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]

 <span data-ttu-id="dd72f-123">この例に示すように個々の要素にアクセスすることができます。この場合、最初の配列の要素 `[1,0]` の値 (値 `5`) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-123">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>

 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]

 <span data-ttu-id="dd72f-124">メソッド `Length` は、ジャグ配列に含まれる配列の数を返します。</span><span class="sxs-lookup"><span data-stu-id="dd72f-124">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="dd72f-125">たとえば、前の配列を宣言し、次のコマンド ラインを実行したとします。</span><span class="sxs-lookup"><span data-stu-id="dd72f-125">For example, assuming you have declared the previous array, this line:</span></span>

 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]

 <span data-ttu-id="dd72f-126">この場合は値 3 が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd72f-126">returns a value of 3.</span></span>

## <a name="example"></a><span data-ttu-id="dd72f-127">例</span><span class="sxs-lookup"><span data-stu-id="dd72f-127">Example</span></span>

 <span data-ttu-id="dd72f-128">この例では、要素自体が配列である配列を構築します。</span><span class="sxs-lookup"><span data-stu-id="dd72f-128">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="dd72f-129">配列の要素のそれぞれのサイズが異なります。</span><span class="sxs-lookup"><span data-stu-id="dd72f-129">Each one of the array elements has a different size.</span></span>

 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]

## <a name="see-also"></a><span data-ttu-id="dd72f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd72f-130">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="dd72f-131">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="dd72f-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dd72f-132">配列</span><span class="sxs-lookup"><span data-stu-id="dd72f-132">Arrays</span></span>](./index.md)
- [<span data-ttu-id="dd72f-133">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="dd72f-133">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="dd72f-134">多次元配列</span><span class="sxs-lookup"><span data-stu-id="dd72f-134">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
