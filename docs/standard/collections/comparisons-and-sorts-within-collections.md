---
title: コレクション内での比較と並べ替え
description: .NET で System.Collections クラスを使用して比較と並べ替えを行います。これは、キーと値のペアの値を削除したり返したりする要素を検索するのに役立ちます。
ms.date: 04/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: e4d40568710498df811954c86bb36382d93057a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733543"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="36bd2-103">コレクション内での比較と並べ替え</span><span class="sxs-lookup"><span data-stu-id="36bd2-103">Comparisons and sorts within collections</span></span>

<span data-ttu-id="36bd2-104"><xref:System.Collections> クラスは、削除する要素を検索するか、キーと値のペアの値を返すかに関係なく、コレクションの管理に関連するほぼすべての処理において比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="36bd2-104">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>

<span data-ttu-id="36bd2-105">通常、コレクションは等値比較子か順序比較子、またはその両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="36bd2-105">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="36bd2-106">比較には 2 つのコンストラクターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="36bd2-106">Two constructs are used for comparisons.</span></span>

<a name="BKMK_Checkingforequality"></a>

## <a name="check-for-equality"></a><span data-ttu-id="36bd2-107">等しいかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="36bd2-107">Check for equality</span></span>

<span data-ttu-id="36bd2-108">`Contains`、 <xref:System.Collections.IList.IndexOf%2A>、 <xref:System.Collections.Generic.List%601.LastIndexOf%2A>、 `Remove` などのメソッドは、コレクション要素に対して等値比較子を使用します。</span><span class="sxs-lookup"><span data-stu-id="36bd2-108">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="36bd2-109">コレクションがジェネリックの場合、次のガイドラインに従ってアイテムの等価性が比較されます。</span><span class="sxs-lookup"><span data-stu-id="36bd2-109">If the collection is generic, then items are compared for equality according to the following guidelines:</span></span>

- <span data-ttu-id="36bd2-110">T 型で <xref:System.IEquatable%601> ジェネリック インターフェイスが実装されている場合、等値比較子はそのインターフェイスの <xref:System.IEquatable%601.Equals%2A> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="36bd2-110">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>

- <span data-ttu-id="36bd2-111">T 型で <xref:System.IEquatable%601>が実装されていない場合、 <xref:System.Object.Equals%2A?displayProperty=nameWithType> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="36bd2-111">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>

<span data-ttu-id="36bd2-112">また、ディクショナリ コレクションのコンストラクターの一部のオーバーロードでは、<xref:System.Collections.Generic.IEqualityComparer%601> の実装が受け付けられて、キーが等しいかどうかを比較するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="36bd2-112">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="36bd2-113">例については、 <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> コンストラクターに関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36bd2-113">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> constructor.</span></span>

<a name="BKMK_Determiningsortorder"></a>

## <a name="determine-sort-order"></a><span data-ttu-id="36bd2-114">並べ替え順序の決定</span><span class="sxs-lookup"><span data-stu-id="36bd2-114">Determine sort order</span></span>

<span data-ttu-id="36bd2-115">`BinarySearch` 、 `Sort` などのメソッドは、コレクション要素に対して順序比較子を使用します。</span><span class="sxs-lookup"><span data-stu-id="36bd2-115">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="36bd2-116">コレクションの要素間または要素と指定された値との間で比較を実行できます。</span><span class="sxs-lookup"><span data-stu-id="36bd2-116">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="36bd2-117">オブジェクトの比較には、 `default comparer` と `explicit comparer`の概念が適用されます。</span><span class="sxs-lookup"><span data-stu-id="36bd2-117">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>

<span data-ttu-id="36bd2-118">既定の比較子は、比較される 1 つ以上のオブジェクトに依存して **IComparable** インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="36bd2-118">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="36bd2-119">リスト コレクションの値として使用されるか、またはディクショナリ コレクションのキーとして使用されるすべてのクラスで、 **IComparable** を実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="36bd2-119">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="36bd2-120">ジェネリック コレクションの場合、等価比較は次の基準に従って決定されます。</span><span class="sxs-lookup"><span data-stu-id="36bd2-120">For a generic collection, equality comparison is determined according to the following:</span></span>

- <span data-ttu-id="36bd2-121">T 型で <xref:System.IComparable%601?displayProperty=nameWithType> ジェネリック インターフェイスが実装されている場合、既定の比較子はそのインターフェイスの <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="36bd2-121">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>

- <span data-ttu-id="36bd2-122">T 型で非ジェネリックの <xref:System.IComparable?displayProperty=nameWithType> インターフェイスが実装されている場合、既定の比較子はそのインターフェイスの <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="36bd2-122">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>

- <span data-ttu-id="36bd2-123">T 型でいずれのインターフェイスも実装されていない場合、既定の比較子は存在せず、比較子または比較デリゲートを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36bd2-123">If type T doesn't implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>

<span data-ttu-id="36bd2-124">明示的な比較を指定するために、一部のメソッドではパラメーターとして **IComparer** 実装を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="36bd2-124">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="36bd2-125">たとえば、 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> メソッドは <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 実装を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="36bd2-125">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>

<span data-ttu-id="36bd2-126">システムの現在のカルチャ設定は、コレクション内の比較と並べ替えに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="36bd2-126">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="36bd2-127">既定では、 **Collections** クラスの比較と並べ替えはカルチャに依存します。</span><span class="sxs-lookup"><span data-stu-id="36bd2-127">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="36bd2-128">カルチャ設定を無視して一貫した比較と並べ替えの結果を得るには、 <xref:System.Globalization.CultureInfo.InvariantCulture%2A> を受け取るメンバー オーバーロードと共に <xref:System.Globalization.CultureInfo>を使用します。</span><span class="sxs-lookup"><span data-stu-id="36bd2-128">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="36bd2-129">詳細については、[カルチャの影響を受けないコレクションの操作の実行](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)および[カルチャの影響を受けない配列の操作の実行](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36bd2-129">For more information, see [Performing Culture-Insensitive String Operations in Collections](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>

<a name="BKMK_Equalityandsortexample"></a>

## <a name="equality-and-sort-example"></a><span data-ttu-id="36bd2-130">等価性と並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="36bd2-130">Equality and sort example</span></span>

<span data-ttu-id="36bd2-131">次のコードは、単純なビジネス オブジェクトでの <xref:System.IEquatable%601> と <xref:System.IComparable%601> の実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="36bd2-131">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="36bd2-132">また、オブジェクトがリストに格納され、並べ替えられている場合、 <xref:System.Collections.Generic.List%601.Sort> メソッドを呼び出すと、結果的に `Part` 型の既定の比較子と、匿名メソッドを使用して実装された <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> メソッドを使用することになります。</span><span class="sxs-lookup"><span data-stu-id="36bd2-132">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>

[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
[!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="36bd2-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="36bd2-133">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
