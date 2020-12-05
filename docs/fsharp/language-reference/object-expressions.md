---
title: オブジェクト式
description: '新しい名前付きの型を作成するために必要な追加のコードとオーバーヘッドを回避する必要がある場合に、F # オブジェクト式を使用する方法について説明します。'
ms.date: 02/08/2019
ms.openlocfilehash: 8a3e40b7833b551eefb95ec62b935acd1ba7b1f9
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740303"
---
# <a name="object-expressions"></a><span data-ttu-id="5aca1-103">オブジェクト式</span><span class="sxs-lookup"><span data-stu-id="5aca1-103">Object Expressions</span></span>

<span data-ttu-id="5aca1-104">*オブジェクト式* は、動的に作成された、既存の基本型、インターフェイス、またはインターフェイスのセットに基づく匿名オブジェクト型の新しいインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="5aca1-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="5aca1-105">構文</span><span class="sxs-lookup"><span data-stu-id="5aca1-105">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="5aca1-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="5aca1-106">Remarks</span></span>

<span data-ttu-id="5aca1-107">前の構文では、 *typename* は既存のクラス型またはインターフェイス型を表します。</span><span class="sxs-lookup"><span data-stu-id="5aca1-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="5aca1-108">*型-params* オプションのジェネリック型パラメーターを記述します。</span><span class="sxs-lookup"><span data-stu-id="5aca1-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="5aca1-109">*引数* は、コンストラクターパラメーターを必要とするクラス型に対してのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="5aca1-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="5aca1-110">*メンバー定義* は、基本クラスのメソッドのオーバーライド、または基本クラスまたはインターフェイスからの抽象メソッドの実装です。</span><span class="sxs-lookup"><span data-stu-id="5aca1-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="5aca1-111">次の例は、さまざまな種類のオブジェクト式を示しています。</span><span class="sxs-lookup"><span data-stu-id="5aca1-111">The following example illustrates several different types of object expressions.</span></span>

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn $"{obj1}"

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a><span data-ttu-id="5aca1-112">オブジェクト式の使用</span><span class="sxs-lookup"><span data-stu-id="5aca1-112">Using Object Expressions</span></span>

<span data-ttu-id="5aca1-113">新しい名前付きの型を作成するために必要な追加のコードやオーバーヘッドを回避するには、オブジェクト式を使用します。</span><span class="sxs-lookup"><span data-stu-id="5aca1-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="5aca1-114">オブジェクト式を使用してプログラムで作成される型の数を最小限に抑える場合は、コードの行数を減らし、型の不必要な急増を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="5aca1-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="5aca1-115">特定の状況に対処するためだけに多くの型を作成するのではなく、既存の型をカスタマイズするオブジェクト式を使用するか、特定のケースに対して適切なインターフェイスの実装を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="5aca1-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="5aca1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5aca1-116">See also</span></span>

- [<span data-ttu-id="5aca1-117">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="5aca1-117">F# Language Reference</span></span>](index.md)
