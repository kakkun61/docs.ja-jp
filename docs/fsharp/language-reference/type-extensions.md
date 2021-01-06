---
title: 型拡張
description: 'F # の型拡張機能を使用して、以前に定義したオブジェクト型に新しいメンバーを追加する方法について説明します。'
ms.date: 02/05/2020
ms.openlocfilehash: c9adddb3133a4af57a12be0b09c22954a8bff6a7
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737269"
---
# <a name="type-extensions"></a><span data-ttu-id="a8a0c-103">型拡張</span><span class="sxs-lookup"><span data-stu-id="a8a0c-103">Type extensions</span></span>

<span data-ttu-id="a8a0c-104">型拡張機能 ( _拡張_ とも呼ばれます) は、以前に定義されたオブジェクト型に新しいメンバーを追加できるようにするための機能ファミリです。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="a8a0c-105">次の3つの機能があります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-105">The three features are:</span></span>

- <span data-ttu-id="a8a0c-106">組み込み型拡張機能</span><span class="sxs-lookup"><span data-stu-id="a8a0c-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="a8a0c-107">省略可能な型拡張</span><span class="sxs-lookup"><span data-stu-id="a8a0c-107">Optional type extensions</span></span>
- <span data-ttu-id="a8a0c-108">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="a8a0c-108">Extension methods</span></span>

<span data-ttu-id="a8a0c-109">各は異なるシナリオで使用でき、トレードオフも異なります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8a0c-110">構文</span><span class="sxs-lookup"><span data-stu-id="a8a0c-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [<Extension>]
    static member extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="a8a0c-111">組み込み型拡張機能</span><span class="sxs-lookup"><span data-stu-id="a8a0c-111">Intrinsic type extensions</span></span>

<span data-ttu-id="a8a0c-112">組み込み型拡張は、ユーザー定義型を拡張する型の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="a8a0c-113">組み込み型拡張は、拡張する型と同じファイル **と** 同じ名前空間またはモジュールで定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="a8a0c-114">その他の定義では、 [省略可能な型拡張](type-extensions.md#optional-type-extensions)になります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="a8a0c-115">組み込み型の拡張機能は、型宣言から機能を分離するために、明確な方法である場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="a8a0c-116">次の例は、組み込み型拡張を定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="a8a0c-117">型拡張を使用すると、次の各項目を分離できます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="a8a0c-118">型の宣言 `Variant`</span><span class="sxs-lookup"><span data-stu-id="a8a0c-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="a8a0c-119">`Variant`"Shape" に応じてクラスを印刷する機能</span><span class="sxs-lookup"><span data-stu-id="a8a0c-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="a8a0c-120">印刷機能にオブジェクト形式の表記でアクセスする方法 `.`</span><span class="sxs-lookup"><span data-stu-id="a8a0c-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="a8a0c-121">これは、すべてをのメンバーとして定義する方法の1つです `Variant` 。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="a8a0c-122">これは本質的には優れたアプローチではありませんが、状況によっては機能が明確に表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="a8a0c-123">組み込み型の拡張は、それが拡張する型のメンバーとしてコンパイルされ、リフレクションによって型が検証されるときに型に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="a8a0c-124">省略可能な型拡張</span><span class="sxs-lookup"><span data-stu-id="a8a0c-124">Optional type extensions</span></span>

<span data-ttu-id="a8a0c-125">省略可能な型拡張は、拡張される型の元のモジュール、名前空間、またはアセンブリの外側に表示される拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="a8a0c-126">省略可能な型拡張は、自分で定義していない型を拡張する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="a8a0c-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="a8a0c-128">これで、使用している `RepeatElements` <xref:System.Collections.Generic.IEnumerable%601> `Extensions` スコープでモジュールが開かれている限り、にアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="a8a0c-129">リフレクションによってチェックされる場合、拡張型にはオプションの拡張機能は表示されません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="a8a0c-130">オプションの拡張機能はモジュール内に存在する必要があり、拡張機能を含むモジュールが開いている場合、またはそれ以外の場合はスコープ内にある場合にのみスコープに含まれます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="a8a0c-131">任意拡張のメンバーはコンパイルされると、静的メンバーになります。このメンバーに対する最初のパラメーターとして、オブジェクト インスタンスが暗黙で渡されます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="a8a0c-132">ただし、これらは、それらが宣言されている方法に従って、インスタンスメンバーまたは静的メンバーであるかのように動作します。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="a8a0c-133">オプションの拡張メンバーは、C# または Visual Basic コンシューマーにも表示されません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="a8a0c-134">他の F # コードでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="a8a0c-135">組み込みおよびオプションの型拡張の一般的な制限</span><span class="sxs-lookup"><span data-stu-id="a8a0c-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="a8a0c-136">型変数が制限されているジェネリック型に対して型拡張を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="a8a0c-137">要件は、拡張宣言の制約が宣言された型の制約と一致することです。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="a8a0c-138">ただし、宣言された型と型拡張の間で制約が一致した場合でも、宣言された型よりも型パラメーターに対して異なる要件を課す拡張メンバーの本体によって制約が推論される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="a8a0c-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="a8a0c-140">このコードを取得して、オプションの型拡張機能を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="a8a0c-141">そのように、 `Sum` メンバーは、型拡張機能で定義されているものとは異なる制約を `'T` ( `static member get_Zero` および) 持ち `static member (+)` ます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="a8a0c-142">と同じ制約を持つように型拡張を変更すると、 `Sum` で定義されている制約とは一致しなくなり `IEnumerable<'T>` ます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="a8a0c-143">`member this.Sum`をに変更する `member inline this.Sum` と、型制約が一致しないというエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="a8a0c-144">必要なのは、"スペースで浮動小数点" を使用する静的メソッドであり、型を拡張するかのように表示できます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="a8a0c-145">ここで拡張メソッドが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="a8a0c-146">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="a8a0c-146">Extension methods</span></span>

<span data-ttu-id="a8a0c-147">最後に、拡張メソッド ("C# スタイル拡張メンバー" とも呼ばれます) は、F # でクラスの静的メンバーメソッドとして宣言できます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="a8a0c-148">拡張メソッドは、型変数を制約するジェネリック型の拡張機能を定義する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="a8a0c-149">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Collections.Generic
open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="a8a0c-150">このコードを使用すると、 `Sum` が <xref:System.Collections.Generic.IEnumerable%601> 開かれている `Extensions` かスコープ内にある限り、がに定義されているかのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

<span data-ttu-id="a8a0c-151">VB.NET code で拡張機能を使用できるようにするに `ExtensionAttribute` は、アセンブリレベルで追加のが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-151">For the extension to be available to VB.NET code, an extra `ExtensionAttribute` is required at the assembly level:</span></span>

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a><span data-ttu-id="a8a0c-152">その他の解説</span><span class="sxs-lookup"><span data-stu-id="a8a0c-152">Other remarks</span></span>

<span data-ttu-id="a8a0c-153">型拡張には、次の属性もあります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-153">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="a8a0c-154">アクセス可能なすべての型を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-154">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="a8a0c-155">組み込みおよびオプションの型拡張では、メソッドだけでなく、 _任意_ のメンバー型を定義できます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-155">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="a8a0c-156">たとえば、拡張機能のプロパティも可能です。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-156">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="a8a0c-157">`self-identifier`[構文](type-extensions.md#syntax)のトークンは、通常のメンバーと同じように、呼び出される型のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-157">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="a8a0c-158">拡張メンバーは、静的メンバーまたはインスタンスメンバーにすることができます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-158">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="a8a0c-159">型の拡張機能の型変数は、宣言された型の制約と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-159">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="a8a0c-160">型拡張機能には、次の制限もあります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-160">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="a8a0c-161">型拡張は、仮想メソッドまたは抽象メソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-161">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="a8a0c-162">型拡張は、拡張としてのオーバーライドメソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-162">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="a8a0c-163">型拡張は、 [静的に解決される型パラメーター](./generics/statically-resolved-type-parameters.md)をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-163">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="a8a0c-164">省略可能な型拡張は、拡張としてのコンストラクターをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-164">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="a8a0c-165">型の拡張子を型の [省略形](type-abbreviations.md)に対して定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-165">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="a8a0c-166">型拡張は、では有効ではありません `byref<'T>` (ただし、宣言することはできます)。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-166">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="a8a0c-167">型拡張は、属性に対しては有効ではありません (ただし、宣言することはできます)。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-167">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="a8a0c-168">同じ名前の他のメソッドをオーバーロードする拡張機能を定義できますが、あいまいな呼び出しがある場合は、F # コンパイラによって非拡張メソッドが優先されます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-168">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="a8a0c-169">最後に、1つの型に対して複数の組み込み型拡張が存在する場合は、すべてのメンバーが一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-169">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="a8a0c-170">オプション型拡張の場合は、1 つの型に対する複数の型拡張が存在する場合でも、各メンバーに同じ名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-170">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="a8a0c-171">クライアント コードで同じメンバー名が定義されている 2 つの異なるスコープを開いている場合にのみ、あいまいさに対するエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a8a0c-171">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8a0c-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8a0c-172">See also</span></span>

- [<span data-ttu-id="a8a0c-173">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="a8a0c-173">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a8a0c-174">メンバー</span><span class="sxs-lookup"><span data-stu-id="a8a0c-174">Members</span></span>](./members/index.md)
