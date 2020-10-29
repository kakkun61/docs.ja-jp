---
description: override 修飾子 - C# リファレンス
title: override 修飾子 - C# リファレンス
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434879"
---
# <a name="override-c-reference"></a><span data-ttu-id="cf8b3-103">override (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="cf8b3-103">override (C# reference)</span></span>

<span data-ttu-id="cf8b3-104">`override` 修飾子は、継承したメソッド、プロパティ、インデクサー、またはイベントの抽象実装または仮想実装を拡張したり修飾したりする際に必要です。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

<span data-ttu-id="cf8b3-105">次の例では、`Square` クラスが `GetArea` のオーバーライドされる実装を提供する必要があります。これは、`GetArea` が `Shape` 抽象クラスから継承されているためです。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-105">In the following example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="cf8b3-106">`override` メソッドは、基底クラスから継承されるメソッドの新しい実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-106">An `override` method provides a new implementation of the method inherited from a base class.</span></span> <span data-ttu-id="cf8b3-107">`override` 宣言によってオーバーライドされるメソッドを、オーバーライドされる基本メソッドと言います。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="cf8b3-108">`override` メソッドには、オーバーライドされる基本メソッドと同じシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-108">An `override` method must have the same signature as the overridden base method.</span></span> <span data-ttu-id="cf8b3-109">C# 9.0 以降、共変の戻り値の型が `override` メソッドによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-109">Beginning with C# 9.0, `override` methods support covariant return types.</span></span> <span data-ttu-id="cf8b3-110">特に、`override` メソッドの戻り値の型は、対応する基本メソッドの戻り値の型から派生できます。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-110">In particular, the return type of an `override` method can derive from the return type of the corresponding base method.</span></span> <span data-ttu-id="cf8b3-111">C# 8.0 以前の場合、`override` メソッドとオーバーライドされた基本メソッドの戻り値の型は同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-111">In C# 8.0 and earlier, the return types of an `override` method and the overridden base method must be the same.</span></span>

<span data-ttu-id="cf8b3-112">非仮想メソッドまたは静的メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-112">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="cf8b3-113">オーバーライドされる基本メソッドは、`virtual`、`abstract`、`override` のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-113">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="cf8b3-114">`override` 宣言は、`virtual` メソッドのアクセシビリティを変更できません。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-114">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="cf8b3-115">`override` メソッドと `virtual` メソッドの両方に、同じ[アクセス レベル修飾子](access-modifiers.md)が必要です。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-115">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="cf8b3-116">`override` メソッドの修飾に、修飾子 `new`、`static`、または `virtual` は使用できません。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-116">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="cf8b3-117">オーバーライドするプロパティの宣言では、継承されるプロパティとまったく同じアクセス修飾子、型、および名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-117">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property.</span></span> <span data-ttu-id="cf8b3-118">C# 9.0 以降、共変の戻り値の型が読み取り専用のオーバーライドするプロパティによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-118">Beginning with C# 9.0, read-only overriding properties support covariant return types.</span></span> <span data-ttu-id="cf8b3-119">オーバーライドされたプロパティは、`virtual`、`abstract`、または `override` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-119">The overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="cf8b3-120">`override` キーワードの使い方の詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-120">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span> <span data-ttu-id="cf8b3-121">継承については、「[継承](../../programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-121">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf8b3-122">例</span><span class="sxs-lookup"><span data-stu-id="cf8b3-122">Example</span></span>

<span data-ttu-id="cf8b3-123">この例では、`Employee` という基底クラスと、`SalesEmployee` という派生クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-123">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="cf8b3-124">`SalesEmployee` クラスには追加のフィールド `salesbonus` があり、このフィールドを処理に含めるために、`CalculatePay` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-124">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="cf8b3-125">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="cf8b3-125">C# language specification</span></span>

<span data-ttu-id="cf8b3-126">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)に関するページの「[オーバーライド メソッド](~/_csharplang/spec/classes.md#override-methods)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-126">For more information, see the [Override methods](~/_csharplang/spec/classes.md#override-methods) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="cf8b3-127">共変の戻り値の型の詳細については、[機能提案メモ](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf8b3-127">For more information about covariant return types, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf8b3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf8b3-128">See also</span></span>

- [<span data-ttu-id="cf8b3-129">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="cf8b3-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cf8b3-130">継承</span><span class="sxs-lookup"><span data-stu-id="cf8b3-130">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="cf8b3-131">C# キーワード</span><span class="sxs-lookup"><span data-stu-id="cf8b3-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="cf8b3-132">修飾子</span><span class="sxs-lookup"><span data-stu-id="cf8b3-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="cf8b3-133">abstract</span><span class="sxs-lookup"><span data-stu-id="cf8b3-133">abstract</span></span>](abstract.md)
- [<span data-ttu-id="cf8b3-134">virtual</span><span class="sxs-lookup"><span data-stu-id="cf8b3-134">virtual</span></span>](virtual.md)
- [<span data-ttu-id="cf8b3-135">new (修飾子)</span><span class="sxs-lookup"><span data-stu-id="cf8b3-135">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="cf8b3-136">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="cf8b3-136">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
