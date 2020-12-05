---
title: 結果
description: 'F # の "Result" 型を使用して、エラートレラントコードを記述する方法について説明します。'
ms.date: 08/13/2020
ms.openlocfilehash: 53b1db0c9224ae032d58c06cd3c58e3dbed03f7b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740225"
---
# <a name="results"></a><span data-ttu-id="b5154-103">結果</span><span class="sxs-lookup"><span data-stu-id="b5154-103">Results</span></span>

<span data-ttu-id="b5154-104">`Result<'T,'TFailure>`型を使用すると、構成可能なエラートレラントコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="b5154-104">The `Result<'T,'TFailure>` type lets you write error-tolerant code that can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5154-105">構文</span><span class="sxs-lookup"><span data-stu-id="b5154-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="b5154-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="b5154-106">Remarks</span></span>

<span data-ttu-id="b5154-107">の組み込み連結子については、モジュールを参照してください [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) `Result` 。</span><span class="sxs-lookup"><span data-stu-id="b5154-107">See the [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) module for the built-in combinators for the `Result`.</span></span> <span data-ttu-id="b5154-108">型のパラメーターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="b5154-108">type.</span></span>

<span data-ttu-id="b5154-109">結果の型は、 [構造体の判別共用体](discriminated-unions.md#struct-discriminated-unions)であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b5154-109">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions).</span></span> <span data-ttu-id="b5154-110">ここでは構造的等値セマンティクスが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b5154-110">Structural equality semantics apply here.</span></span>

<span data-ttu-id="b5154-111">この `Result` 型は、通常、monadic のエラー処理で使用されます。これは、F # コミュニティ内では、" [フロント指向" プログラミング](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) と呼ばれることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="b5154-111">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="b5154-112">次の簡単な例は、この方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5154-112">The following trivial example demonstrates this approach.</span></span>

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn $"My request was valid! Name: {req.Name} Email {req.Email}"  
    | Error e -> printfn $"Error: {e}"
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn $"My request was valid! Name: {req.Name} Email {req.Email}"  
    | Error e -> printfn $"Error: {e}"
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="b5154-113">ご覧のように、すべてを強制的にを返すようにすると、さまざまな検証関数を連結するのは非常に簡単です `Result` 。</span><span class="sxs-lookup"><span data-stu-id="b5154-113">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="b5154-114">これにより、このような機能を、必要に応じてコンポーザブルな小さな部分に分割できます。</span><span class="sxs-lookup"><span data-stu-id="b5154-114">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="b5154-115">これには、検証のラウンドの最後に [パターン一致](pattern-matching.md)の使用を *強制* するための追加の値も含まれます。これにより、より高度なプログラムの正確性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b5154-115">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5154-116">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="b5154-116">See also</span></span>

- [<span data-ttu-id="b5154-117">判別共用体</span><span class="sxs-lookup"><span data-stu-id="b5154-117">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="b5154-118">パターン一致</span><span class="sxs-lookup"><span data-stu-id="b5154-118">Pattern Matching</span></span>](pattern-matching.md)
