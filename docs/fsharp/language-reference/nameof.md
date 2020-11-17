---
title: Nameof
description: ソースコード内の任意のシンボルの名前を生成できるメタプログラミング機能である、参照元の演算子について説明します。
ms.date: 11/12/2020
ms.openlocfilehash: 9947d7172d1b73db5c181297ec8b1131382e1f5e
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688632"
---
# <a name="nameof"></a><span data-ttu-id="57fd1-103">Nameof</span><span class="sxs-lookup"><span data-stu-id="57fd1-103">Nameof</span></span>

<span data-ttu-id="57fd1-104">式は、source 内の `nameof` ほぼすべての F # コンストラクトのソース内の名前と一致する文字列定数を生成します。</span><span class="sxs-lookup"><span data-stu-id="57fd1-104">The `nameof` expression produces a string constant that matches the name in source for nearly any F# construct in source.</span></span>

## <a name="syntax"></a><span data-ttu-id="57fd1-105">構文</span><span class="sxs-lookup"><span data-stu-id="57fd1-105">Syntax</span></span>

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a><span data-ttu-id="57fd1-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="57fd1-106">Remarks</span></span>

<span data-ttu-id="57fd1-107">`nameof` は、渡されたシンボルを解決して、ソースコード内で宣言されたシンボルの名前を生成することによって機能します。</span><span class="sxs-lookup"><span data-stu-id="57fd1-107">`nameof` works by resolving the symbol passed to it and produces the name of that symbol as it is declared in your source code.</span></span> <span data-ttu-id="57fd1-108">これは、ログ記録などのさまざまなシナリオで役立ち、ソースコードの変更に対するログ記録を保護します。</span><span class="sxs-lookup"><span data-stu-id="57fd1-108">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) ($"Value passed in was %d{month}.")

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="57fd1-109">最後の行は例外をスローし、 `"month"` エラーメッセージに表示されます。</span><span class="sxs-lookup"><span data-stu-id="57fd1-109">The last line will throw an exception and `"month"` will be shown in the error message.</span></span>

<span data-ttu-id="57fd1-110">ほぼすべての F # コンストラクトの名前を取得できます。</span><span class="sxs-lookup"><span data-stu-id="57fd1-110">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

<span data-ttu-id="57fd1-111">`nameof` がファーストクラス関数ではなく、そのように使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="57fd1-111">`nameof` is not a first-class function and cannot be used as such.</span></span> <span data-ttu-id="57fd1-112">つまり、このメソッドを部分的に適用することはできず、F # パイプライン演算子を使用して値をパイプすることはできません。</span><span class="sxs-lookup"><span data-stu-id="57fd1-112">That means it cannot be partially applied and values cannot be piped into it via F# pipeline operators.</span></span>

## <a name="nameof-on-operators"></a><span data-ttu-id="57fd1-113">演算子の場合</span><span class="sxs-lookup"><span data-stu-id="57fd1-113">Nameof on operators</span></span>

<span data-ttu-id="57fd1-114">F # の演算子は、演算子テキスト自体、またはコンパイルされたフォームを表す記号として2つの方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="57fd1-114">Operators in F# can be used in two ways, as an operator text itself, or a symbol representing the compiled form.</span></span> <span data-ttu-id="57fd1-115">`nameof` オペレーターは、ソースで宣言されている演算子の名前を生成します。</span><span class="sxs-lookup"><span data-stu-id="57fd1-115">`nameof` on an operator will produce the name of the operator as it is declared in source.</span></span> <span data-ttu-id="57fd1-116">コンパイルされた名前を取得するには、ソースのコンパイル済みの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="57fd1-116">To get the compiled name, use the compiled name in source:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a><span data-ttu-id="57fd1-117">ジェネリックのすべてのもの</span><span class="sxs-lookup"><span data-stu-id="57fd1-117">Nameof on generics</span></span>

<span data-ttu-id="57fd1-118">ジェネリック型パラメーターの名前を取得することもできますが、構文は異なります。</span><span class="sxs-lookup"><span data-stu-id="57fd1-118">You can also take a name of a generic type parameter, but the syntax is different:</span></span>

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

<span data-ttu-id="57fd1-119">`nameof<'TGeneric>` は、呼び出しサイトで置き換えられた型の名前ではなく、ソースで定義されているシンボルの名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="57fd1-119">`nameof<'TGeneric>` will take the name of the symbol as defined in source, not the name of the type substituted at a call site.</span></span>

<span data-ttu-id="57fd1-120">構文が異なる理由は、やなどの他の F # 組み込み演算子と一致させることです `typeof<>` `typedefof<>` 。</span><span class="sxs-lookup"><span data-stu-id="57fd1-120">The reason why the syntax is different is to align with other F# intrinsic operators like `typeof<>` and `typedefof<>`.</span></span> <span data-ttu-id="57fd1-121">これにより、ジェネリック型に作用する演算子と、ソース内の他のあらゆるものに対して F # の一貫性が確保されます。</span><span class="sxs-lookup"><span data-stu-id="57fd1-121">This makes F# consistent with respect to operators that act on generic types and anything else in source.</span></span>

## <a name="nameof-in-pattern-matching"></a><span data-ttu-id="57fd1-122">パターンマッチングのためのもの</span><span class="sxs-lookup"><span data-stu-id="57fd1-122">Nameof in pattern matching</span></span>

<span data-ttu-id="57fd1-123">[ `nameof` パターン](pattern-matching.md#nameof-pattern)を使用すると、 `nameof` パターンマッチ式で次のようにを使用できます。</span><span class="sxs-lookup"><span data-stu-id="57fd1-123">The [`nameof` pattern](pattern-matching.md#nameof-pattern) lets you use `nameof` in a pattern match expression like so:</span></span>

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```
