---
title: .NET の汎用コレクション
ms.date: 02/15/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
ms.openlocfilehash: 256fddd6c35cb78e8e22562960580929e1230c34
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827348"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="af7ba-102">.NET の汎用コレクション</span><span class="sxs-lookup"><span data-stu-id="af7ba-102">Generic collections in .NET</span></span>

 <span data-ttu-id="af7ba-103">.NET クラス ライブラリでは、<xref:System.Collections.Generic> および <xref:System.Collections.ObjectModel> の名前空間に多数のジェネリック コレクション クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="af7ba-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="af7ba-104">各クラスについて詳しくは、「[一般的に使用されるコレクション型](../collections/commonly-used-collection-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af7ba-104">For more detailed information about these classes, see [Commonly Used Collection Types](../collections/commonly-used-collection-types.md).</span></span>  
  
## <a name="systemcollectionsgeneric"></a><span data-ttu-id="af7ba-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="af7ba-105">System.Collections.Generic</span></span>

 <span data-ttu-id="af7ba-106">ジェネリック コレクション型の多くは、非ジェネリック型に直接類似しています。</span><span class="sxs-lookup"><span data-stu-id="af7ba-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="af7ba-107"><xref:System.Collections.Generic.Dictionary%602> は、<xref:System.Collections.Hashtable> のジェネリック バージョンです。これは列挙体のために <xref:System.Collections.DictionaryEntry> ではなくジェネリック構造体 <xref:System.Collections.Generic.KeyValuePair%602> を使用します。</span><span class="sxs-lookup"><span data-stu-id="af7ba-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="af7ba-108"><xref:System.Collections.Generic.List%601> は <xref:System.Collections.ArrayList> のジェネリック バージョンです。</span><span class="sxs-lookup"><span data-stu-id="af7ba-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="af7ba-109">ジェネリックの <xref:System.Collections.Generic.Queue%601> および <xref:System.Collections.Generic.Stack%601> クラスには、非ジェネリックのバージョンに対応するものがあります。</span><span class="sxs-lookup"><span data-stu-id="af7ba-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="af7ba-110"><xref:System.Collections.Generic.SortedList%602> には、ジェネリックおよび非ジェネリックのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="af7ba-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="af7ba-111">どちらのバージョンも、ディクショナリとリストのハイブリッドです。</span><span class="sxs-lookup"><span data-stu-id="af7ba-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="af7ba-112"><xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラスは純粋なディクショナリであり、対応する非ジェネリックのバージョンはありません。</span><span class="sxs-lookup"><span data-stu-id="af7ba-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="af7ba-113"><xref:System.Collections.Generic.LinkedList%601> ジェネリック クラスは、実際のリンク リストです。</span><span class="sxs-lookup"><span data-stu-id="af7ba-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="af7ba-114">これには、対応する非ジェネリックのバージョンはありません。</span><span class="sxs-lookup"><span data-stu-id="af7ba-114">It has no nongeneric counterpart.</span></span>  
  
## <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="af7ba-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="af7ba-115">System.Collections.ObjectModel</span></span>

 <span data-ttu-id="af7ba-116"><xref:System.Collections.ObjectModel.Collection%601> ジェネリック クラスは、独自のジェネリック コレクション型を派生させるための基本クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="af7ba-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="af7ba-117"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> クラスは、<xref:System.Collections.Generic.IList%601> ジェネリック インターフェイスを実装する任意の型から、読み取り専用のコレクションを生成するための簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="af7ba-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="af7ba-118"><xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスは、独自のキーを含むオブジェクトを格納するための方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="af7ba-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="af7ba-119">その他のジェネリック型</span><span class="sxs-lookup"><span data-stu-id="af7ba-119">Other generic types</span></span>

 <span data-ttu-id="af7ba-120"><xref:System.Nullable%601> ジェネリック構造体により、`null` が割り当て可能であるかのように値型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="af7ba-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="af7ba-121">これは、値型が含まれるフィールドが欠落している可能性のあるデータベース クエリで作業するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="af7ba-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="af7ba-122">ジェネリック型パラメーターには、任意の値型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="af7ba-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af7ba-123">C# および Visual Basic には null 許容型の構文があるので、その言語では <xref:System.Nullable%601> を明示的に使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="af7ba-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="af7ba-124">「[null 許容値型 (C# リファレンス)](../../csharp/language-reference/builtin-types/nullable-value-types.md)」および「[null 許容値型 (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af7ba-124">See [Nullable value types (C# reference)](../../csharp/language-reference/builtin-types/nullable-value-types.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>
  
 <span data-ttu-id="af7ba-125"><xref:System.ArraySegment%601> ジェネリック構造体は、任意の型の 0 から始まる 1 次元の配列内で、要素の範囲を区切る方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="af7ba-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="af7ba-126">ジェネリック型パラメーターは、配列の要素の型です。</span><span class="sxs-lookup"><span data-stu-id="af7ba-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="af7ba-127"><xref:System.EventHandler%601> ジェネリック デリゲートにより、イベントが .NET によって使用されるイベント処理パターンに従う場合に、イベントを処理するためにデリゲート型を宣言する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="af7ba-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by .NET.</span></span> <span data-ttu-id="af7ba-128">たとえば、イベントのデータを保持するために、<xref:System.EventArgs> から派生した `MyEventArgs` クラスを作成したとします。</span><span class="sxs-lookup"><span data-stu-id="af7ba-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="af7ba-129">その場合、イベントを次のように宣言できます。</span><span class="sxs-lookup"><span data-stu-id="af7ba-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="af7ba-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="af7ba-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="af7ba-131">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="af7ba-131">Generics</span></span>](index.md)
- [<span data-ttu-id="af7ba-132">配列とリストの操作に使用する汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="af7ba-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="af7ba-133">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af7ba-133">Generic Interfaces</span></span>](interfaces.md)
