---
title: 列挙型 - C# リファレンス
description: 選択肢または選択肢の組み合わせを表す C# 列挙型について説明します
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 930efdbdc6a20ea301331c1ce6fc664da43bfc5f
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471851"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="78407-103">列挙型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="78407-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="78407-104">" *列挙型* " は、基になる [整数値](integral-numeric-types.md)型の一連の名前付き定数によって定義された [値の型](value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="78407-104">An *enumeration type* (or *enum type* ) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="78407-105">列挙型を定義するには、`enum` キーワードを使用して " *列挙型メンバー* " の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="78407-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members* :</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="78407-106">既定では、列挙型メンバーの関連する定数値の型は `int` で、0 から始まり、定義テキストの順序に従って 1 ずつ増加します。</span><span class="sxs-lookup"><span data-stu-id="78407-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="78407-107">他の任意の[整数値](integral-numeric-types.md)型を、列挙型の基になる型として明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="78407-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="78407-108">また、次の例に示すように、関連する定数値を明示的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="78407-108">You can also explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="78407-109">列挙型の定義内でメソッドを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="78407-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="78407-110">列挙型に機能を追加するには、[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)を作成します。</span><span class="sxs-lookup"><span data-stu-id="78407-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="78407-111">列挙型 `E` の既定値は、式 `(E)0` によって生成される値です。この値は、ゼロに対応する列挙メンバーがなくても生成されます。</span><span class="sxs-lookup"><span data-stu-id="78407-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="78407-112">列挙型を使用して、相互に排他的な一連の値の選択肢、または選択肢の組み合わせを表します。</span><span class="sxs-lookup"><span data-stu-id="78407-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="78407-113">選択肢の組み合わせを表すには、列挙型をビット フラグとして定義します。</span><span class="sxs-lookup"><span data-stu-id="78407-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="78407-114">ビット フラグとしての列挙型</span><span class="sxs-lookup"><span data-stu-id="78407-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="78407-115">列挙型で選択肢の組み合わせを表したいときは、個々の選択肢がビット フィールドになるように、列挙型メンバーをそれらの選択肢に対して定義します。</span><span class="sxs-lookup"><span data-stu-id="78407-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="78407-116">つまり、これらの列挙型メンバーの関連する値は、2 の累乗である必要があります。</span><span class="sxs-lookup"><span data-stu-id="78407-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="78407-117">次に、[ビットごとの論理演算子 `|` または `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) を使用し、選択肢を組み合わせたり、選択肢の組み合わせを交差させたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="78407-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="78407-118">列挙型によってビット フィールドが宣言されていることを示すには、[フラグ](xref:System.FlagsAttribute)属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="78407-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="78407-119">次の例に示すように、列挙型の定義に一般的な組み合わせをいくつか含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="78407-119">As the following example shows, you can also include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/shared/EnumType.cs#Flags)]

<span data-ttu-id="78407-120">詳細と例については、<xref:System.FlagsAttribute?displayProperty=nameWithType> API リファレンス ページ、および <xref:System.Enum?displayProperty=nameWithType> API リファレンス ページの「[非排他的メンバーと Flags 属性](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78407-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="78407-121">System.Enum 型と列挙型定数</span><span class="sxs-lookup"><span data-stu-id="78407-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="78407-122"><xref:System.Enum?displayProperty=nameWithType> 型は、すべての列挙型の抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="78407-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="78407-123">この型には、列挙型とその値に関する情報を取得するためのメソッドがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="78407-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="78407-124">詳細と例については、<xref:System.Enum?displayProperty=nameWithType> API リファレンス ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78407-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="78407-125">C# 7.3 以降、基底クラス制約 ([列挙の制約](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)と呼ばれます) で `System.Enum` を使用して、型パラメーターが列挙型であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="78407-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="78407-126">変換</span><span class="sxs-lookup"><span data-stu-id="78407-126">Conversions</span></span>

<span data-ttu-id="78407-127">列挙型については、列挙型とその基になる整数型との間に明示的な変換が存在します。</span><span class="sxs-lookup"><span data-stu-id="78407-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="78407-128">列挙値をその基になる型に[キャスト](../operators/type-testing-and-cast.md#cast-expression)すると、結果は列挙メンバーの関連する整数値になります。</span><span class="sxs-lookup"><span data-stu-id="78407-128">If you [cast](../operators/type-testing-and-cast.md#cast-expression) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/shared/EnumType.cs#Conversions)]

<span data-ttu-id="78407-129"><xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> メソッドを使用して、列挙型に、関連する特定の値を持つ列挙型メンバーが含まれているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="78407-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="78407-130">列挙型については、<xref:System.Enum?displayProperty=nameWithType> 型との間に[ボックス化とボックス化解除](../../programming-guide/types/boxing-and-unboxing.md)変換が存在します。</span><span class="sxs-lookup"><span data-stu-id="78407-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="78407-131">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="78407-131">C# language specification</span></span>

<span data-ttu-id="78407-132">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78407-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="78407-133">列挙型</span><span class="sxs-lookup"><span data-stu-id="78407-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="78407-134">列挙型の値と演算子</span><span class="sxs-lookup"><span data-stu-id="78407-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="78407-135">列挙論理演算子</span><span class="sxs-lookup"><span data-stu-id="78407-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="78407-136">列挙型比較演算子</span><span class="sxs-lookup"><span data-stu-id="78407-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="78407-137">明示的な列挙変換</span><span class="sxs-lookup"><span data-stu-id="78407-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="78407-138">暗黙的な列挙変換</span><span class="sxs-lookup"><span data-stu-id="78407-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="78407-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="78407-139">See also</span></span>

- [<span data-ttu-id="78407-140">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="78407-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="78407-141">列挙型書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="78407-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="78407-142">設計ガイドライン - 列挙型の設計</span><span class="sxs-lookup"><span data-stu-id="78407-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="78407-143">設計ガイドライン - 列挙型の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="78407-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="78407-144">switch ステートメント</span><span class="sxs-lookup"><span data-stu-id="78407-144">switch statement</span></span>](../keywords/switch.md)
