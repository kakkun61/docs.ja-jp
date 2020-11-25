---
title: クラスまたは構造体の選択
description: 型をクラスとしてデザインするか、構造体として型をデザインするかを決定する方法について説明します。 .NET での参照型と値型の違いについて説明します。
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
ms.openlocfilehash: 05ba9abbc9495d927b7f58ebb06f152c0c15772f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701251"
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="71e16-104">クラスまたは構造体の選択</span><span class="sxs-lookup"><span data-stu-id="71e16-104">Choosing Between Class and Struct</span></span>

<span data-ttu-id="71e16-105">すべてのフレームワークデザイナーの面で基本的な設計上の決定事項の1つは、型をクラスとしてデザインするか (参照型)、または構造体 (値型) として設計するかということです。</span><span class="sxs-lookup"><span data-stu-id="71e16-105">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="71e16-106">この選択を行うには、参照型と値型の動作の違いをよく理解していることが重要です。</span><span class="sxs-lookup"><span data-stu-id="71e16-106">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>

 <span data-ttu-id="71e16-107">参照型と値型の間の最初の違いは、参照型がヒープに割り当てられ、ガベージコレクトされるのに対し、値型はスタックまたはインラインの型に割り当てられ、スタックのアンワインドまたはそれを含んでいる型の割り当てが解除されるときに割り当てが解除されるという点です。</span><span class="sxs-lookup"><span data-stu-id="71e16-107">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="71e16-108">したがって、値型の割り当てと割り当て解除は、参照型の割り当てと割り当て解除よりも一般的に低コストです。</span><span class="sxs-lookup"><span data-stu-id="71e16-108">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>

 <span data-ttu-id="71e16-109">次に、参照型の配列はアウトオブラインで割り当てられます。つまり、配列要素は、ヒープに存在する参照型のインスタンスへの参照にすぎません。</span><span class="sxs-lookup"><span data-stu-id="71e16-109">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="71e16-110">値型の配列はインラインで割り当てられます。つまり、配列要素は値型の実際のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="71e16-110">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="71e16-111">したがって、値型の配列の割り当てと割り当て解除は、参照型の配列の割り当てと割り当て解除よりもはるかに安価です。</span><span class="sxs-lookup"><span data-stu-id="71e16-111">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="71e16-112">また、ほとんどの場合、値型の配列は参照の局所性が大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="71e16-112">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>

 <span data-ttu-id="71e16-113">次の相違点は、メモリ使用量に関連します。</span><span class="sxs-lookup"><span data-stu-id="71e16-113">The next difference is related to memory usage.</span></span> <span data-ttu-id="71e16-114">参照型または実装するインターフェイスのいずれかにキャストすると、値型はボックス化されます。</span><span class="sxs-lookup"><span data-stu-id="71e16-114">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="71e16-115">値型にキャストされると、ボックス化が解除されます。</span><span class="sxs-lookup"><span data-stu-id="71e16-115">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="71e16-116">ボックスはヒープに割り当てられ、ガベージコレクトされるオブジェクトであるため、ボックス化とボックス化解除が過剰になると、ヒープ、ガベージコレクター、および最終的にアプリケーションのパフォーマンスに悪影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="71e16-116">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="71e16-117">これに対し、参照型がキャストされると、このようなボックス化は行われません。</span><span class="sxs-lookup"><span data-stu-id="71e16-117">In contrast, no such boxing occurs as reference types are cast.</span></span> <span data-ttu-id="71e16-118">(詳細については、「 [ボックス化とボックス化解除](../../csharp/programming-guide/types/boxing-and-unboxing.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="71e16-118">(For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)).</span></span>

 <span data-ttu-id="71e16-119">次に、参照型の割り当てによって参照がコピーされます。一方、値型の割り当てでは、値全体がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="71e16-119">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="71e16-120">したがって、大きな参照型の割り当ては、大きな値型の割り当てよりもコストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="71e16-120">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>

 <span data-ttu-id="71e16-121">最後に、参照型は参照によって渡されるのに対し、値型は値によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="71e16-121">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="71e16-122">参照型のインスタンスへの変更は、そのインスタンスを指すすべての参照に影響します。</span><span class="sxs-lookup"><span data-stu-id="71e16-122">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="71e16-123">値型のインスタンスは、値によって渡されるときにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="71e16-123">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="71e16-124">値型のインスタンスが変更された場合、当然、そのインスタンスのコピーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="71e16-124">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="71e16-125">コピーはユーザーによって明示的に作成されるのではなく、引数が渡されるときに暗黙的に作成されるため、または戻り値が返される場合、変更可能な値型は多くのユーザーに混乱を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="71e16-125">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="71e16-126">したがって、値型は不変である必要があります。</span><span class="sxs-lookup"><span data-stu-id="71e16-126">Therefore, value types should be immutable.</span></span>

 <span data-ttu-id="71e16-127">経験則として、フレームワークのほとんどの型はクラスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="71e16-127">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="71e16-128">ただし、場合によっては、値型の特性によって、構造体を使用する方が適切であることがあります。</span><span class="sxs-lookup"><span data-stu-id="71e16-128">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>

 <span data-ttu-id="71e16-129">型のインスタンスが小さく、通常は短い有効期間であるか、または他のオブジェクトに埋め込まれている場合は、クラスではなく構造体を定義する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="71e16-129">✔️ CONSIDER defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>

 <span data-ttu-id="71e16-130">❌ 型に次の特性がすべて含まれている場合を除き、構造体を定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="71e16-130">❌ AVOID defining a struct unless the type has all of the following characteristics:</span></span>

- <span data-ttu-id="71e16-131">プリミティブ型 (、など) と同様に、論理的には単一の値を表し `int` `double` ます。</span><span class="sxs-lookup"><span data-stu-id="71e16-131">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>

- <span data-ttu-id="71e16-132">インスタンスのサイズは16バイト未満です。</span><span class="sxs-lookup"><span data-stu-id="71e16-132">It has an instance size under 16 bytes.</span></span>

- <span data-ttu-id="71e16-133">変更できません。</span><span class="sxs-lookup"><span data-stu-id="71e16-133">It is immutable.</span></span>

- <span data-ttu-id="71e16-134">頻繁にボックス化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="71e16-134">It will not have to be boxed frequently.</span></span>

 <span data-ttu-id="71e16-135">それ以外の場合は、型をクラスとして定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71e16-135">In all other cases, you should define your types as classes.</span></span>

 <span data-ttu-id="71e16-136">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="71e16-136">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="71e16-137">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="71e16-137">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="71e16-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="71e16-138">See also</span></span>

- [<span data-ttu-id="71e16-139">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="71e16-139">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="71e16-140">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="71e16-140">Framework Design Guidelines</span></span>](index.md)
