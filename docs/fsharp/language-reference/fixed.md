---
title: Fixed キーワード
description: "F # の ' fixed ' キーワードを使用してコレクションを防止するために、ローカルのをスタックに \"固定\" する方法について説明します。"
ms.date: 08/15/2020
ms.openlocfilehash: b4b0d1ae101d5f7b65bff80fa070c9fd54de8d66
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740355"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="48239-103">Fixed キーワード</span><span class="sxs-lookup"><span data-stu-id="48239-103">The fixed keyword</span></span>

<span data-ttu-id="48239-104">`fixed`キーワードを使用すると、ローカルのをスタックに "固定" し、ガベージコレクション中に収集または移動できないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="48239-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="48239-105">これは、低レベルのプログラミングシナリオに使用されます。</span><span class="sxs-lookup"><span data-stu-id="48239-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="48239-106">構文</span><span class="sxs-lookup"><span data-stu-id="48239-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="48239-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="48239-107">Remarks</span></span>

<span data-ttu-id="48239-108">これにより、式の構文が拡張され、ポインターを抽出して、ガベージコレクション中に収集または移動できない名前にバインドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="48239-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="48239-109">キーワードを使用して式からのポインターが固定されている場合は、キーワードを使用して `fixed` 識別子にバインドされ `use` ます。</span><span class="sxs-lookup"><span data-stu-id="48239-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="48239-110">このセマンティクスは、キーワードを使用したリソース管理に似てい `use` ます。</span><span class="sxs-lookup"><span data-stu-id="48239-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="48239-111">ポインターはスコープ内にある間は固定され、スコープ外になると修正されなくなります。</span><span class="sxs-lookup"><span data-stu-id="48239-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="48239-112">`fixed` は、バインドのコンテキストの外部では使用できません `use` 。</span><span class="sxs-lookup"><span data-stu-id="48239-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="48239-113">ポインターは、を使用して名前にバインドする必要があり `use` ます。</span><span class="sxs-lookup"><span data-stu-id="48239-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="48239-114">`fixed`は、関数またはメソッドの式の中で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48239-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="48239-115">スクリプトレベルまたはモジュールレベルのスコープでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="48239-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="48239-116">すべてのポインターコードと同様に、これは安全でない機能であり、使用すると警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="48239-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="48239-117">例</span><span class="sxs-lookup"><span data-stu-id="48239-117">Example</span></span>

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn $"pnt before - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn $"pnt after - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="48239-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="48239-118">See also</span></span>

- [<span data-ttu-id="48239-119">モジュール</span><span class="sxs-lookup"><span data-stu-id="48239-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
