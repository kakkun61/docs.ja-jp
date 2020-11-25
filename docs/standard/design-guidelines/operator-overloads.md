---
title: 演算子のオーバーロード
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 7757e6cfdb9ae31f6e94c26a2684f8176174499a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734817"
---
# <a name="operator-overloads"></a><span data-ttu-id="7443c-102">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="7443c-102">Operator Overloads</span></span>

<span data-ttu-id="7443c-103">演算子のオーバーロードでは、フレームワーク型を組み込みの言語プリミティブとして表示できます。</span><span class="sxs-lookup"><span data-stu-id="7443c-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="7443c-104">一部の状況では許可および便利ですが、演算子のオーバーロードは慎重に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7443c-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="7443c-105">多くの場合、演算子のオーバーロードは不正使用されています。たとえば、framework デザイナーが、単純なメソッドである必要がある操作に対して演算子の使用を開始した場合などです。</span><span class="sxs-lookup"><span data-stu-id="7443c-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="7443c-106">次のガイドラインは、演算子のオーバーロードを使用するタイミングと方法を決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7443c-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="7443c-107">❌ プリミティブ (組み込み) 型のように感じられる型以外は、演算子のオーバーロードを定義しないようにします。</span><span class="sxs-lookup"><span data-stu-id="7443c-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="7443c-108">プリミティブ型のように感じられる型に演算子のオーバーロードを定義する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="7443c-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="7443c-109">たとえば、に <xref:System.String?displayProperty=nameWithType> はがあり、が `operator==` `operator!=` 定義されています。</span><span class="sxs-lookup"><span data-stu-id="7443c-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="7443c-110">数値を表す構造体 (など) では、演算子のオーバーロードを定義✔️ <xref:System.Decimal?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="7443c-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="7443c-111">❌ 演算子のオーバーロードを定義する場合は、かわいらしいしないでください。</span><span class="sxs-lookup"><span data-stu-id="7443c-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="7443c-112">演算子のオーバーロードは、操作の結果がすぐにわかる場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7443c-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="7443c-113">たとえば、ある型を <xref:System.DateTime> 別のから減算してを取得できるようにすることは理にかなって `DateTime` <xref:System.TimeSpan> います。</span><span class="sxs-lookup"><span data-stu-id="7443c-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="7443c-114">ただし、2つのデータベースクエリを結合する場合や、shift 演算子を使用してストリームに書き込む場合は、論理和演算子を使用するのは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="7443c-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="7443c-115">❌ 少なくとも1つのオペランドがオーバーロードを定義する型でない限り、演算子のオーバーロードを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="7443c-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="7443c-116">✔️は、対称方式で演算子をオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="7443c-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="7443c-117">たとえば、をオーバーロードする場合は、 `operator==` もオーバーロードする必要があり `operator!=` ます。</span><span class="sxs-lookup"><span data-stu-id="7443c-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="7443c-118">同様に、をオーバーロードする場合は、も同様に `operator<` オーバーロードする必要があり `operator>` ます。</span><span class="sxs-lookup"><span data-stu-id="7443c-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="7443c-119">オーバーロードされた各演算子に対応するフレンドリ名を使用して、メソッドを指定する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="7443c-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="7443c-120">多くの言語では、演算子のオーバーロードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7443c-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="7443c-121">このため、オーバーロード演算子には、同等の機能を提供するドメイン固有の適切な名前を持つ二次的なメソッドが含まれていることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7443c-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="7443c-122">次の表に、演算子とそれに対応するわかりやすいメソッド名の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7443c-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="7443c-123">C# 演算子シンボル</span><span class="sxs-lookup"><span data-stu-id="7443c-123">C# Operator Symbol</span></span>|<span data-ttu-id="7443c-124">メタデータ名</span><span class="sxs-lookup"><span data-stu-id="7443c-124">Metadata Name</span></span>|<span data-ttu-id="7443c-125">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="7443c-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="7443c-126">オーバーロード演算子 = =</span><span class="sxs-lookup"><span data-stu-id="7443c-126">Overloading Operator ==</span></span>

 <span data-ttu-id="7443c-127">オーバーロード `operator ==` は非常に複雑です。</span><span class="sxs-lookup"><span data-stu-id="7443c-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="7443c-128">演算子のセマンティクスは、など、他のいくつかのメンバーと互換性がある必要があり <xref:System.Object.Equals%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="7443c-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="7443c-129">変換演算子</span><span class="sxs-lookup"><span data-stu-id="7443c-129">Conversion Operators</span></span>

 <span data-ttu-id="7443c-130">変換演算子は、ある型から別の型への変換を可能にする単項演算子です。</span><span class="sxs-lookup"><span data-stu-id="7443c-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="7443c-131">演算子は、オペランドまたは戻り値の型のいずれかの静的メンバーとして定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7443c-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="7443c-132">変換演算子には、暗黙的と明示的の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="7443c-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="7443c-133">❌ エンドユーザーがこのような変換を明確に想定していない場合は、変換演算子を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="7443c-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="7443c-134">❌ 型のドメインの外に変換演算子を定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="7443c-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="7443c-135">たとえば、、 <xref:System.Int32> 、 <xref:System.Double> およびは <xref:System.Decimal> すべて数値型ですが、 <xref:System.DateTime> はではありません。</span><span class="sxs-lookup"><span data-stu-id="7443c-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="7443c-136">したがって、をに変換する変換演算子は存在しない必要があり `Double(long)` `DateTime` ます。</span><span class="sxs-lookup"><span data-stu-id="7443c-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="7443c-137">このような場合は、コンストラクターを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7443c-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="7443c-138">❌ 変換が損失する可能性がある場合は、暗黙的な変換演算子を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="7443c-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="7443c-139">たとえば、からへの暗黙の型変換を行うことはできません `Double` `Int32` 。の `Double` 範囲がより大きくなるため `Int32` です。</span><span class="sxs-lookup"><span data-stu-id="7443c-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="7443c-140">変換が損失する可能性がある場合でも、明示的な変換演算子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7443c-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="7443c-141">❌ 暗黙のキャストから例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="7443c-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="7443c-142">変換が行われていることを認識していない可能性があるため、エンドユーザーは何が起こっているかを理解することは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="7443c-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="7443c-143">キャスト演算子の呼び出しによって損失を伴う変換が発生 <xref:System.InvalidCastException?displayProperty=nameWithType> し、演算子のコントラクトでは損失が生じない変換が許可されていない場合、✔️スローします。</span><span class="sxs-lookup"><span data-stu-id="7443c-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="7443c-144">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="7443c-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7443c-145">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="7443c-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7443c-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="7443c-146">See also</span></span>

- [<span data-ttu-id="7443c-147">メンバーデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7443c-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="7443c-148">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7443c-148">Framework Design Guidelines</span></span>](index.md)
