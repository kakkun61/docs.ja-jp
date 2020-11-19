---
title: メモリとスパン
ms.date: 10/03/2018
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: 4b0464cc81cf0908a907f8305ea4e35b716c18fb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830663"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="4713d-102">メモリおよびスパンに関連する型</span><span class="sxs-lookup"><span data-stu-id="4713d-102">Memory- and span-related types</span></span>

<span data-ttu-id="4713d-103">.NET Core 2.1 以降、.NET には、任意のメモリの厳密に型指定された連続する領域を表す、相互に関連する型が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="4713d-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="4713d-104">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="4713d-104">These include:</span></span>

- <span data-ttu-id="4713d-105"><xref:System.Span%601?displayProperty=nameWithType>: メモリの連続した領域にアクセスするために使う型です。</span><span class="sxs-lookup"><span data-stu-id="4713d-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="4713d-106"><xref:System.Span%601> インスタンスは、`T` 型の配列、<xref:System.String>、[stackalloc](../../csharp/language-reference/operators/stackalloc.md) を使って割り当てたバッファー、またはアンマネージ メモリへのポインターによってバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="4713d-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="4713d-107">これはスタック上に割り当てる必要があるため、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="4713d-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="4713d-108">たとえば、クラス内のフィールドを <xref:System.Span%601> 型にすることはできませんし、非同期操作でスパンを使うこともできません。</span><span class="sxs-lookup"><span data-stu-id="4713d-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="4713d-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>: <xref:System.Span%601> 構造体の変更できないバージョンです。</span><span class="sxs-lookup"><span data-stu-id="4713d-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="4713d-110"><xref:System.Memory%601?displayProperty=nameWithType>: スタックではなくマネージド ヒープ上に割り当てられるメモリの連続する領域です。</span><span class="sxs-lookup"><span data-stu-id="4713d-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="4713d-111"><xref:System.Memory%601> インスタンスは、`T` 型の配列か <xref:System.String> によってバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="4713d-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="4713d-112">これはマネージド ヒープに格納できるため、<xref:System.Memory%601> には <xref:System.Span%601> の制限事項はありません。</span><span class="sxs-lookup"><span data-stu-id="4713d-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="4713d-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>: <xref:System.Memory%601> 構造体の変更できないバージョンです。</span><span class="sxs-lookup"><span data-stu-id="4713d-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="4713d-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>: メモリ プールの厳密に型指定されたメモリ ブロックを、所有者に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4713d-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="4713d-115"><xref:System.Buffers.IMemoryOwner%601> インスタンスは、<xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> を呼び出すことでプールから借りてくることができ、<xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> を呼び出すことでプールにリリースします。</span><span class="sxs-lookup"><span data-stu-id="4713d-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="4713d-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>: メモリ ブロックの所有者を表し、その有効期間の管理をコントロールします。</span><span class="sxs-lookup"><span data-stu-id="4713d-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="4713d-117"><xref:System.Buffers.MemoryManager%601>: <xref:System.Memory%601> をセーフ ハンドルなどのその他の型でバックアップできるようにするために、<xref:System.Memory%601> の実装を置き換えるために使用できる抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="4713d-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="4713d-118"><xref:System.Buffers.MemoryManager%601> は高度なシナリオ向けです。</span><span class="sxs-lookup"><span data-stu-id="4713d-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="4713d-119"><xref:System.ArraySegment%601>: 特定のインデックスから始まる、特定の数の配列要素のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="4713d-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="4713d-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>: 文字列、配列、および配列セグメントを、<xref:System.Memory%601> ブロックに変換するための拡張メソッドのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="4713d-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="4713d-121">以前のフレームワークでは、[System.Memory NuGet パッケージ](https://www.nuget.org/packages/System.Memory/)で <xref:System.Span%601> と <xref:System.Memory%601> を利用できます。</span><span class="sxs-lookup"><span data-stu-id="4713d-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="4713d-122">詳細については、「<xref:System.Buffers?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4713d-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="4713d-123">メモリとスパンを使った作業</span><span class="sxs-lookup"><span data-stu-id="4713d-123">Working with memory and span</span></span>

<span data-ttu-id="4713d-124">通常、メモリおよびスパンに関連する型は処理パイプラインにデータを格納するために使われます。そのため開発者は、<xref:System.Span%601>、<xref:System.Memory%601>、および関連する型を使う場合に、一連のベスト プラクティスに従うことが重要です。</span><span class="sxs-lookup"><span data-stu-id="4713d-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="4713d-125">これらのベスト プラクティスは、「[Memory\<T>T> と Span\<T>T> の使用ガイドライン](memory-t-usage-guidelines.md)」でドキュメント化されています。</span><span class="sxs-lookup"><span data-stu-id="4713d-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4713d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4713d-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
