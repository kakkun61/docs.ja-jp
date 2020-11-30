---
description: ':::no-loc text=interface::: (C# リファレンス)'
title: インターフェイス - C# リファレンス
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "89134589"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="317db-103">:::no-loc text="interface"::: (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="317db-103">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="317db-104">インターフェイスによりコントラクトが定義されます。</span><span class="sxs-lookup"><span data-stu-id="317db-104">An interface defines a contract.</span></span> <span data-ttu-id="317db-105">そのコントラクトを実装する [`class`](class.md) または [`struct`](../builtin-types/struct.md) では、インターフェイスで定義されているメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="317db-105">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="317db-106">C# 8.0 以降では、インターフェイスによってメンバーの既定の実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="317db-106">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="317db-107">共通の機能を 1 回で実装する目的で [`static`](static.md) メンバーも定義できます。</span><span class="sxs-lookup"><span data-stu-id="317db-107">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="317db-108">次の例の `ImplementationClass` クラスは、`SampleMethod` を返す、パラメーターのない `void` メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="317db-108">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="317db-109">使用例を含む詳細については、「[インターフェイス](../../programming-guide/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="317db-109">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="317db-110">例</span><span class="sxs-lookup"><span data-stu-id="317db-110">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="317db-111">インターフェイスには、名前空間またはクラスのメンバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="317db-111">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="317db-112">インターフェイス宣言には、次のメンバーの宣言を含めることができます (実装なしのシグネチャ)。</span><span class="sxs-lookup"><span data-stu-id="317db-112">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="317db-113">メソッド</span><span class="sxs-lookup"><span data-stu-id="317db-113">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="317db-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="317db-114">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="317db-115">インデクサー</span><span class="sxs-lookup"><span data-stu-id="317db-115">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="317db-116">イベント</span><span class="sxs-lookup"><span data-stu-id="317db-116">Events</span></span>](event.md)

<span data-ttu-id="317db-117">これらのメンバー宣言には通常、本文が含まれません。</span><span class="sxs-lookup"><span data-stu-id="317db-117">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="317db-118">C# 8.0 以降では、インターフェイス メンバーで本文を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="317db-118">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="317db-119">これは *既定の実装* と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="317db-119">This is called a *default implementation*.</span></span> <span data-ttu-id="317db-120">本文のあるメンバーでは、実装がオーバーライドされないクラスおよび構造体に "既定の" 実装を与えることがインターフェイスに許可されます。</span><span class="sxs-lookup"><span data-stu-id="317db-120">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="317db-121">また、C# 8.0 以降、インターフェイスには次を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="317db-121">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="317db-122">定数</span><span class="sxs-lookup"><span data-stu-id="317db-122">Constants</span></span>](const.md)
- [<span data-ttu-id="317db-123">オペレーター</span><span class="sxs-lookup"><span data-stu-id="317db-123">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="317db-124">[静的コンストラクター](../../programming-guide/classes-and-structs/constructors.md#static-constructors)。</span><span class="sxs-lookup"><span data-stu-id="317db-124">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="317db-125">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="317db-125">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="317db-126">静的フィールド、メソッド、プロパティ、インデクサー、イベント</span><span class="sxs-lookup"><span data-stu-id="317db-126">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="317db-127">明示的なインターフェイス実装構文を使用するメンバー宣言。</span><span class="sxs-lookup"><span data-stu-id="317db-127">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="317db-128">明示的なアクセス修飾子 (既定のアクセスは [`public`](access-modifiers.md))。</span><span class="sxs-lookup"><span data-stu-id="317db-128">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="317db-129">インターフェイスには、インスタンスの状態を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="317db-129">Interfaces may not contain instance state.</span></span> <span data-ttu-id="317db-130">静的フィールドが許可されるようになりましたが、インスタンス フィールドはインターフェイスでは許可されません。</span><span class="sxs-lookup"><span data-stu-id="317db-130">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="317db-131">[インスタンスの自動プロパティ](../../programming-guide/classes-and-structs/auto-implemented-properties.md)では暗黙的に隠しフィールドが宣言されることがあり、インターフェイスではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="317db-131">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="317db-132">このルールは、プロパティの宣言に微細な影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="317db-132">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="317db-133">インターフェイス宣言では、次のコードによって、`class` や `struct` の場合のように自動実装プロパティが宣言されることはありません。</span><span class="sxs-lookup"><span data-stu-id="317db-133">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="317db-134">その代わり、既定の実装が与えられないが、インターフェイスを実装する何らかの型で実装する必要があるプロパティが宣言されます。</span><span class="sxs-lookup"><span data-stu-id="317db-134">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="317db-135">インターフェイスは、1 つ以上の基底インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="317db-135">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="317db-136">あるインターフェイスで基底インターフェイスに実装されている[メソッドがオーバーライドされる](override.md)とき、そのインターフェイスでは[明示的なインターフェイス実装](../../programming-guide/interfaces/explicit-interface-implementation.md)構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="317db-136">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="317db-137">基本型のリストに基底クラスとインターフェイスが含まれる場合は、基底クラスがリストの最初に表示されます。</span><span class="sxs-lookup"><span data-stu-id="317db-137">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="317db-138">インターフェイスを実装するクラスは、そのインターフェイスのメンバーを明示的に実装できます。</span><span class="sxs-lookup"><span data-stu-id="317db-138">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="317db-139">明示的に実装されているメンバーには、クラス インスタンスではアクセスできません。インターフェイスのインスタンスを使用した場合にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="317db-139">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="317db-140">また、既定のインターフェイス メンバーには、インターフェイスのインスタンス経由でのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="317db-140">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="317db-141">明示的なインターフェイス実装の詳細については、「[明示的なインターフェイスの実装](../../programming-guide/interfaces/explicit-interface-implementation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="317db-141">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="317db-142">例</span><span class="sxs-lookup"><span data-stu-id="317db-142">Example</span></span>

<span data-ttu-id="317db-143">ここでは、インターフェイスの実装例を示します。</span><span class="sxs-lookup"><span data-stu-id="317db-143">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="317db-144">この例では、インターフェイスにプロパティ宣言が含まれ、クラスに実装が含まれます。</span><span class="sxs-lookup"><span data-stu-id="317db-144">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="317db-145">`IPoint` を実装するクラスのインスタンスには、整数プロパティ `x` および `y` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="317db-145">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="317db-146">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="317db-146">C# language specification</span></span>

<span data-ttu-id="317db-147">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[インターフェイス](~/_csharplang/spec/interfaces.md)」セクションと [C# 8.0 の既定のインターフェイス メンバー](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="317db-147">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="317db-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="317db-148">See also</span></span>

- [<span data-ttu-id="317db-149">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="317db-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="317db-150">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="317db-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="317db-151">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="317db-151">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="317db-152">参照型</span><span class="sxs-lookup"><span data-stu-id="317db-152">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="317db-153">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="317db-153">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="317db-154">プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="317db-154">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="317db-155">インデクサーの使用</span><span class="sxs-lookup"><span data-stu-id="317db-155">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
