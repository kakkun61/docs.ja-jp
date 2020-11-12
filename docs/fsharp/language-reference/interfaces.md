---
title: インターフェイス
description: 'F # インターフェイスが、他のクラスが実装する関連メンバーのセットを指定する方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 0cef2932045dae401f5aa069107815543457ca4a
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557052"
---
# <a name="interfaces"></a><span data-ttu-id="0727e-103">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0727e-103">Interfaces</span></span>

<span data-ttu-id="0727e-104">*インターフェイス* は、他のクラスが実装する関連メンバーのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="0727e-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="0727e-105">構文</span><span class="sxs-lookup"><span data-stu-id="0727e-105">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="0727e-106">解説</span><span class="sxs-lookup"><span data-stu-id="0727e-106">Remarks</span></span>

<span data-ttu-id="0727e-107">インターフェイス宣言は、メンバーが実装されていないことを除いて、クラス宣言に似ています。</span><span class="sxs-lookup"><span data-stu-id="0727e-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="0727e-108">代わりに、キーワードによって示されているように、すべてのメンバーが抽象型に `abstract` なります。</span><span class="sxs-lookup"><span data-stu-id="0727e-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="0727e-109">抽象メソッドにメソッド本体を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="0727e-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="0727e-110">ただし、キーワードと共にメンバーの別の定義をメソッドとして含めることで、既定の実装を提供することもでき `default` ます。</span><span class="sxs-lookup"><span data-stu-id="0727e-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="0727e-111">これは、他の .NET 言語で基底クラスの仮想メソッドを作成することと同じです。</span><span class="sxs-lookup"><span data-stu-id="0727e-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="0727e-112">このような仮想メソッドは、インターフェイスを実装するクラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="0727e-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="0727e-113">インターフェイスの既定のアクセシビリティは `public` です。</span><span class="sxs-lookup"><span data-stu-id="0727e-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="0727e-114">必要に応じて、通常の F # 構文を使用して、各メソッドパラメーターに名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="0727e-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="0727e-115">上の例では、メソッドには、 `ISprintable` `Print` という名前の型の1つのパラメーターがあり `string` `format` ます。</span><span class="sxs-lookup"><span data-stu-id="0727e-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="0727e-116">インターフェイスを実装するには、オブジェクト式を使用する方法とクラス型を使用する方法の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="0727e-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="0727e-117">どちらの場合も、クラス型またはオブジェクト式は、インターフェイスの抽象メソッドにメソッド本体を提供します。</span><span class="sxs-lookup"><span data-stu-id="0727e-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="0727e-118">実装は、インターフェイスを実装する各型に固有です。</span><span class="sxs-lookup"><span data-stu-id="0727e-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="0727e-119">したがって、異なる型のインターフェイスメソッドは相互に異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0727e-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="0727e-120">`interface` `end` 簡易構文を使用する場合、定義の開始と終了をマークするキーワードとは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="0727e-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="0727e-121">これらのキーワードを使用しない場合、コンパイラは、使用するコンストラクトを分析することで、型がクラスであるかインターフェイスであるかを推論しようとします。</span><span class="sxs-lookup"><span data-stu-id="0727e-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="0727e-122">メンバーを定義する場合、または他のクラス構文を使用する場合、型はクラスとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="0727e-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="0727e-123">.NET のコーディングスタイルでは、すべてのインターフェイスを大文字で開始し `I` ます。</span><span class="sxs-lookup"><span data-stu-id="0727e-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

<span data-ttu-id="0727e-124">F # スタイルとの2つの方法で、複数のパラメーターを指定できます。NET スタイル。</span><span class="sxs-lookup"><span data-stu-id="0727e-124">You can specify multiple parameters in two ways: F#-style and .NET-style.</span></span> <span data-ttu-id="0727e-125">どちらも .NET コンシューマーに対して同じようにコンパイルされますが、f # スタイルは f # の呼び出し元が f # スタイルのパラメーターアプリケーションとを使用するように強制します。NET スタイルでは、F # の呼び出し元がタプル引数アプリケーションを使用するように強制されます。</span><span class="sxs-lookup"><span data-stu-id="0727e-125">Both will compile the same way for .NET consumers, but F#-style will force F# callers to use F#-style parameter application and .NET-style will force F# callers to use tupled argument application.</span></span>

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="0727e-126">クラス型を使用したインターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="0727e-126">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="0727e-127">`interface`次のコードに示すように、キーワード、インターフェイスの名前、およびキーワードを使用して、クラス型に1つ以上のインターフェイスを実装することができ `with` ます。</span><span class="sxs-lookup"><span data-stu-id="0727e-127">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="0727e-128">インターフェイスの実装は継承されるため、派生クラスはそれらを再実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0727e-128">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="0727e-129">インターフェイスメソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="0727e-129">Calling Interface Methods</span></span>

<span data-ttu-id="0727e-130">インターフェイスメソッドを呼び出すことができるのは、インターフェイスを実装する型のオブジェクトではなく、インターフェイスのみです。</span><span class="sxs-lookup"><span data-stu-id="0727e-130">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="0727e-131">そのため、これらのメソッドを呼び出すには、演算子または演算子を使用して、インターフェイス型にアップキャストすることが必要になる場合があり `:>` `upcast` ます。</span><span class="sxs-lookup"><span data-stu-id="0727e-131">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="0727e-132">型のオブジェクトがある場合にインターフェイスメソッドを呼び出すには、 `SomeClass` 次のコードに示すように、オブジェクトをインターフェイス型にアップキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0727e-132">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="0727e-133">別の方法として、次の例のように、キャストしてインターフェイスメソッドを呼び出すオブジェクトに対してメソッドを宣言する方法があります。</span><span class="sxs-lookup"><span data-stu-id="0727e-133">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="0727e-134">オブジェクト式を使用したインターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="0727e-134">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="0727e-135">オブジェクト式は、インターフェイスを実装するための簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="0727e-135">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="0727e-136">これらは、名前付きの型を作成する必要がなく、インターフェイスメソッドをサポートするオブジェクトを必要とする場合に、追加のメソッドを使用しない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="0727e-136">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="0727e-137">オブジェクト式を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="0727e-137">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="0727e-138">インターフェイスの継承</span><span class="sxs-lookup"><span data-stu-id="0727e-138">Interface Inheritance</span></span>

<span data-ttu-id="0727e-139">インターフェイスは、1つまたは複数の基本インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="0727e-139">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a><span data-ttu-id="0727e-140">既定の実装でのインターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="0727e-140">Implementing interfaces with default implementations</span></span>

<span data-ttu-id="0727e-141">C# では、次のように、既定の実装でインターフェイスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0727e-141">C# supports defining interfaces with default implementations, like so:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="0727e-142">これらは F # から直接利用できます。</span><span class="sxs-lookup"><span data-stu-id="0727e-142">These are directly consumable from F#:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

<span data-ttu-id="0727e-143">仮想メンバーをオーバーライドするのと同様に、を使用して既定の実装をオーバーライドでき `override` ます。</span><span class="sxs-lookup"><span data-stu-id="0727e-143">You can override a default implementation with `override`, like overriding any virtual member.</span></span>

<span data-ttu-id="0727e-144">既定のを実装していないインターフェイスのメンバーは、引き続き明示的に実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0727e-144">Any members in an interface that do not have a default implementation must still be explicitly implemented.</span></span>

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a><span data-ttu-id="0727e-145">異なるジェネリックインスタンスでの同じインターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="0727e-145">Implementing the same interface at different generic instantiations</span></span>

<span data-ttu-id="0727e-146">F # では、次のように、異なるジェネリックインスタンスで同じインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="0727e-146">F# supports implementing the same interface at different generic instantiations like so:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="see-also"></a><span data-ttu-id="0727e-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="0727e-147">See also</span></span>

- [<span data-ttu-id="0727e-148">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="0727e-148">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0727e-149">オブジェクト式</span><span class="sxs-lookup"><span data-stu-id="0727e-149">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="0727e-150">クラス</span><span class="sxs-lookup"><span data-stu-id="0727e-150">Classes</span></span>](classes.md)
