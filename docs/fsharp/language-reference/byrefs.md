---
title: Byrefs
description: '下位レベルのプログラミングに使用される、F # の byref および byref に似た型について説明します。'
ms.date: 11/04/2019
ms.openlocfilehash: ff2c06d8940f7341d5d8b1d942be264bfac586c5
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740316"
---
# <a name="byrefs"></a><span data-ttu-id="07d9a-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="07d9a-103">Byrefs</span></span>

<span data-ttu-id="07d9a-104">F # には、低レベルのプログラミングの領域を処理する2つの主要な機能領域があります。</span><span class="sxs-lookup"><span data-stu-id="07d9a-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="07d9a-105">`byref` / `inref` / `outref` 型。マネージポインターです。</span><span class="sxs-lookup"><span data-stu-id="07d9a-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="07d9a-106">実行時に無効なプログラムをコンパイルできないように、使用方法に制限があります。</span><span class="sxs-lookup"><span data-stu-id="07d9a-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="07d9a-107">と同様の構造体 `byref` 。同様のセマンティクスと、と同じコンパイル時の制限を持つ [構造体](structures.md) です `byref<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="07d9a-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="07d9a-108">例と <xref:System.Span%601> して、があります。</span><span class="sxs-lookup"><span data-stu-id="07d9a-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="07d9a-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="07d9a-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="07d9a-110">Byref、inref、および outref</span><span class="sxs-lookup"><span data-stu-id="07d9a-110">Byref, inref, and outref</span></span>

<span data-ttu-id="07d9a-111">次の3つの形式があり `byref` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="07d9a-112">`inref<'T>`は、基になる値を読み取るためのマネージポインターです。</span><span class="sxs-lookup"><span data-stu-id="07d9a-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="07d9a-113">`outref<'T>`。基になる値に書き込むためのマネージポインター。</span><span class="sxs-lookup"><span data-stu-id="07d9a-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="07d9a-114">`byref<'T>`は、基になる値の読み取りと書き込みを行うためのマネージポインターです。</span><span class="sxs-lookup"><span data-stu-id="07d9a-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="07d9a-115">が必要な場合は、を `byref<'T>` 渡すことができ `inref<'T>` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="07d9a-116">同様に、 `byref<'T>` が必要な場合は、を渡すことができ `outref<'T>` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="07d9a-117">Byref の使用</span><span class="sxs-lookup"><span data-stu-id="07d9a-117">Using byrefs</span></span>

<span data-ttu-id="07d9a-118">を使用するには `inref<'T>` 、次のようにポインター値を取得する必要があり `&` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="07d9a-119">またはを使用してポインターに書き込むに `outref<'T>` は、 `byref<'T>` ポインターを取得する値も設定する必要があり `mutable` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn $"Now: %O{dt}"
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="07d9a-120">ポインターを読み取る代わりに書き込みを行うだけの場合は、の代わりにを使用することを検討してください `outref<'T>` `byref<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="07d9a-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="07d9a-121">Inref セマンティクス</span><span class="sxs-lookup"><span data-stu-id="07d9a-121">Inref semantics</span></span>

<span data-ttu-id="07d9a-122">次のコードについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="07d9a-123">意味的には、これは次のことを意味します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="07d9a-124">ポインターの所有者は、 `x` それを使用して値を読み取ることしかできません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="07d9a-125">`struct`内の入れ子になったフィールドに対して取得されたポインターに `SomeStruct` は、型が指定され `inref<_>` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="07d9a-126">次のような場合もあります。</span><span class="sxs-lookup"><span data-stu-id="07d9a-126">The following is also true:</span></span>

* <span data-ttu-id="07d9a-127">他のスレッドまたは別名には、への書き込みアクセス権がないという意味はありません `x` 。</span><span class="sxs-lookup"><span data-stu-id="07d9a-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="07d9a-128">を持つ `SomeStruct` ことによって変更できない意味はありません `x` `inref` 。</span><span class="sxs-lookup"><span data-stu-id="07d9a-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="07d9a-129">ただし **、変更** できない F # 値型の場合、 `this` ポインターはとして推論され `inref` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="07d9a-130">これらの規則はすべて、ポインターの所有者 `inref` が、ポイントされているメモリの直接の内容を変更しない可能性があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="07d9a-131">Outref セマンティクス</span><span class="sxs-lookup"><span data-stu-id="07d9a-131">Outref semantics</span></span>

<span data-ttu-id="07d9a-132">の目的は `outref<'T>` 、ポインターを書き込むだけであることを示すことです。</span><span class="sxs-lookup"><span data-stu-id="07d9a-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="07d9a-133">予期せずに、名前に関係なく、 `outref<'T>` 基になる値の読み取りを許可します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="07d9a-134">これは、互換性のためのものです。</span><span class="sxs-lookup"><span data-stu-id="07d9a-134">This is for compatibility purposes.</span></span> <span data-ttu-id="07d9a-135">意味 `outref<'T>` 的には、とは異なり `byref<'T>` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="07d9a-136">C との相互運用\#</span><span class="sxs-lookup"><span data-stu-id="07d9a-136">Interop with C\#</span></span>

<span data-ttu-id="07d9a-137">C# では `in ref` 、 `out ref` 戻り値に加えて、キーワードとキーワードがサポートされてい `ref` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="07d9a-138">F # が C# の出力を解釈する方法を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="07d9a-139">C# コンストラクト</span><span class="sxs-lookup"><span data-stu-id="07d9a-139">C# construct</span></span>|<span data-ttu-id="07d9a-140">F # 推論</span><span class="sxs-lookup"><span data-stu-id="07d9a-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="07d9a-141">`ref` 戻り値</span><span class="sxs-lookup"><span data-stu-id="07d9a-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="07d9a-142">`ref readonly` 戻り値</span><span class="sxs-lookup"><span data-stu-id="07d9a-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="07d9a-143">`in ref` パラメーター</span><span class="sxs-lookup"><span data-stu-id="07d9a-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="07d9a-144">`out ref` パラメーター</span><span class="sxs-lookup"><span data-stu-id="07d9a-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="07d9a-145">F # が出力する内容を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="07d9a-146">F # コンストラクター</span><span class="sxs-lookup"><span data-stu-id="07d9a-146">F# construct</span></span>|<span data-ttu-id="07d9a-147">出力されたコンストラクト</span><span class="sxs-lookup"><span data-stu-id="07d9a-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="07d9a-148">`inref<'T>` 引数</span><span class="sxs-lookup"><span data-stu-id="07d9a-148">`inref<'T>` argument</span></span>|<span data-ttu-id="07d9a-149">`[In]` 引数の属性</span><span class="sxs-lookup"><span data-stu-id="07d9a-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="07d9a-150">`inref<'T>` 返し</span><span class="sxs-lookup"><span data-stu-id="07d9a-150">`inref<'T>` return</span></span>|<span data-ttu-id="07d9a-151">`modreq` 値の属性</span><span class="sxs-lookup"><span data-stu-id="07d9a-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="07d9a-152">`inref<'T>` 抽象スロットまたは実装内</span><span class="sxs-lookup"><span data-stu-id="07d9a-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="07d9a-153">`modreq` on 引数または return</span><span class="sxs-lookup"><span data-stu-id="07d9a-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="07d9a-154">`outref<'T>` 引数</span><span class="sxs-lookup"><span data-stu-id="07d9a-154">`outref<'T>` argument</span></span>|<span data-ttu-id="07d9a-155">`[Out]` 引数の属性</span><span class="sxs-lookup"><span data-stu-id="07d9a-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="07d9a-156">型の推定とオーバーロードの規則</span><span class="sxs-lookup"><span data-stu-id="07d9a-156">Type inference and overloading rules</span></span>

<span data-ttu-id="07d9a-157">`inref<'T>`型は、次の場合に F # コンパイラによって推論されます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="07d9a-158">属性を持つ .NET パラメーターまたは戻り値の型 `IsReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="07d9a-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="07d9a-159">変更可能な `this` フィールドを持たない構造体型のポインター。</span><span class="sxs-lookup"><span data-stu-id="07d9a-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="07d9a-160">別のポインターから派生したメモリ位置のアドレス `inref<_>` 。</span><span class="sxs-lookup"><span data-stu-id="07d9a-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="07d9a-161">の暗黙的なアドレスを取得する場合、型の引数を `inref` 持つオーバーロードは、 `SomeType` 型の引数を持つオーバーロードに優先され `inref<SomeType>` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="07d9a-162">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="07d9a-163">どちらの場合も、取得するオーバーロードは、を `System.DateTime` 取得するオーバーロードではなく、解決され `inref<System.DateTime>` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="07d9a-164">Byref に似た構造体</span><span class="sxs-lookup"><span data-stu-id="07d9a-164">Byref-like structs</span></span>

<span data-ttu-id="07d9a-165">Trio に加えて `byref` / `inref` / `outref` 、同様のセマンティクスに従うことができる独自の構造体を定義することもでき `byref` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="07d9a-166">これは、属性を使用して行い <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="07d9a-167">`IsByRefLike` はを意味 `Struct` しません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="07d9a-168">両方とも型に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d9a-168">Both must be present on the type.</span></span>

<span data-ttu-id="07d9a-169">`byref`F # の "-like" 構造体は、スタックバインド値型です。</span><span class="sxs-lookup"><span data-stu-id="07d9a-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="07d9a-170">マネージヒープに割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="07d9a-171">と `byref` 同様の構造体は、有効期間と非キャプチャに関する厳密なチェックセットによって適用されるため、ハイパフォーマンスプログラミングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="07d9a-172">規則は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="07d9a-172">The rules are:</span></span>

* <span data-ttu-id="07d9a-173">これらは、関数パラメーター、メソッドパラメーター、ローカル変数、メソッドが返す値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="07d9a-174">これらは、クラスまたは通常の構造体の静的メンバーまたはインスタンスメンバーにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="07d9a-175">これらは、クロージャコンストラクト ( `async` メソッドまたはラムダ式) によってキャプチャすることはできません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="07d9a-176">これらは、ジェネリックパラメーターとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="07d9a-177">この最後の点は、 `|>` 入力の型をパラメーター化するジェネリック関数と同様に、F # パイプラインスタイルのプログラミングに不可欠です。</span><span class="sxs-lookup"><span data-stu-id="07d9a-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="07d9a-178">この制限は、インラインであるため `|>` 、その本体で非インラインジェネリック関数を呼び出すことがないため、将来は緩和される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="07d9a-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="07d9a-179">これらの規則は使用法を厳密に制限していますが、高パフォーマンスコンピューティングの約束を安全な方法で実現するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="07d9a-180">Byref の戻り値</span><span class="sxs-lookup"><span data-stu-id="07d9a-180">Byref returns</span></span>

<span data-ttu-id="07d9a-181">F # 関数から Byref が返されるか、メンバーを生成して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="07d9a-182">を `byref` 返すメソッドを使用する場合、値は暗黙的に逆参照されます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="07d9a-183">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
```

<span data-ttu-id="07d9a-184">値を表す値を返すには、値を含む変数が現在のスコープよりも長く有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d9a-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="07d9a-185">また、byref を返すには、 `&value` (value は現在のスコープよりも長い変数です) を使用します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="07d9a-186">複数のチェーン呼び出しを通じて参照を渡すなど、暗黙的な逆参照を回避するには、 `&x` ( `x` は値) を使用します。</span><span class="sxs-lookup"><span data-stu-id="07d9a-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="07d9a-187">また、戻り値に直接割り当てることもでき `byref` ます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="07d9a-188">次のような (非常に必須の) プログラムを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="07d9a-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn $"Original sequence: %O{c}"

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn $"New sequence:      %O{c}"

    0 // return an integer exit code
```

<span data-ttu-id="07d9a-189">出力結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="07d9a-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="07d9a-190">Byref のスコープ</span><span class="sxs-lookup"><span data-stu-id="07d9a-190">Scoping for byrefs</span></span>

<span data-ttu-id="07d9a-191">バインドされた値は、その `let` 参照が定義されているスコープを超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="07d9a-192">たとえば、次のような場合は許可されません。</span><span class="sxs-lookup"><span data-stu-id="07d9a-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="07d9a-193">これにより、最適化でコンパイルするかどうかによって、異なる結果が得られるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="07d9a-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
