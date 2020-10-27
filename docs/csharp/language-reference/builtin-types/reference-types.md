---
title: 組み込みの参照型 - C# リファレンス
description: 宣言するために使用できる C# キーワードがある参照型について説明します。
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223509"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="6ba86-103">組み込みの参照型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6ba86-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="6ba86-104">C# には複数の組み込み参照型があります。</span><span class="sxs-lookup"><span data-stu-id="6ba86-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="6ba86-105">それらには、.NET ライブラリでの型に対するシノニムであるキーワードまたは演算子があります。</span><span class="sxs-lookup"><span data-stu-id="6ba86-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span>

## <a name="the-object-type"></a><span data-ttu-id="6ba86-106">オブジェクトの型</span><span class="sxs-lookup"><span data-stu-id="6ba86-106">The object type</span></span>

<span data-ttu-id="6ba86-107">`object` 型は .NET での <xref:System.Object?displayProperty=nameWithType> の別名です。</span><span class="sxs-lookup"><span data-stu-id="6ba86-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="6ba86-108">C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値の型) が、直接または間接的に <xref:System.Object?displayProperty=nameWithType> を継承します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6ba86-109">`object` 型の変数には、任意の型の値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="6ba86-110">すべての `object` 変数には、リテラル `null` を使って既定値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="6ba86-111">値型の変数が object に変換されることを、 *ボックス化* されると言います。</span><span class="sxs-lookup"><span data-stu-id="6ba86-111">When a variable of a value type is converted to object, it is said to be *boxed* .</span></span> <span data-ttu-id="6ba86-112">`object` 型の変数が値型に変換されることを、 *ボックス化解除* されると言います。</span><span class="sxs-lookup"><span data-stu-id="6ba86-112">When a variable of type `object` is converted to a value type, it is said to be *unboxed* .</span></span> <span data-ttu-id="6ba86-113">詳細については、「[ボックス化とボックス化解除](../../programming-guide/types/boxing-and-unboxing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ba86-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="the-string-type"></a><span data-ttu-id="6ba86-114">文字列型</span><span class="sxs-lookup"><span data-stu-id="6ba86-114">The string type</span></span>

<span data-ttu-id="6ba86-115">`string` 型は、0 個以上の Unicode 文字のシーケンスを表します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="6ba86-116">`string` は .NET の <xref:System.String?displayProperty=nameWithType> の別名です。</span><span class="sxs-lookup"><span data-stu-id="6ba86-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="6ba86-117">`string` は参照型ですが、[等値演算子 `==` および `!=`](../operators/equality-operators.md#string-equality) は、`string` オブジェクトの参照ではなく、値を比較するように定義されています。</span><span class="sxs-lookup"><span data-stu-id="6ba86-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="6ba86-118">これにより、文字列が等しいかを直感的にテストできます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="6ba86-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="6ba86-120">文字列の内容が等しいので、"True"、"False" の順に表示されますが、`a` および `b` は同じ文字列インスタンスを参照しません。</span><span class="sxs-lookup"><span data-stu-id="6ba86-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="6ba86-121">[+ 演算子](../operators/addition-operator.md#string-concatenation)では、文字列が連結されます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="6ba86-122">これは、"good morning" を含む文字列オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="6ba86-123">文字列は " *変更不可* " です。文字列オブジェクトの作成後、そのコンテンツを変更することはできません。構文では変更可能に見えても、変更不可です。</span><span class="sxs-lookup"><span data-stu-id="6ba86-123">Strings are *immutable* --the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="6ba86-124">たとえば、このコードを作成すると、コンパイラによって新しい文字列オブジェクトを格納する新しいシーケンス オブジェクトが生成され、その新しいオブジェクトが `b` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="6ba86-125">`b` に割り当てられたメモリは (文字列 "h" が含まれている場合)、ガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="6ba86-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="6ba86-126">`[]` [演算子](../operators/member-access-operators.md#indexer-operator-)は、文字列の各文字への読み取り専用アクセスに使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a string.</span></span> <span data-ttu-id="6ba86-127">有効なインデックス値は `0` から始まり、文字列の長さ未満である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba86-127">Valid index values start at `0` and must be less than the length of the string:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="6ba86-128">同様に、`[]` 演算子を使って文字列内の各文字を反復処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a string:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

<span data-ttu-id="6ba86-129">文字列リテラルは `string` 型であり、二重引用符で囲む形式と、`@` 付きの二重引用符で囲む形式の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="6ba86-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="6ba86-130">二重引用符で囲む場合は、リテラル文字列の前後に二重引用符 (") を付けます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="6ba86-131">リテラル文字列には、任意の文字リテラルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-131">String literals can contain any character literal.</span></span> <span data-ttu-id="6ba86-132">これにはエスケープ シーケンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-132">Escape sequences are included.</span></span> <span data-ttu-id="6ba86-133">次の例では、円記号にエスケープ シーケンス `\\`、文字 f に `\u0066`、改行に `\n` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="6ba86-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> <span data-ttu-id="6ba86-134">エスケープ コード `\udddd` (`dddd` は 4 桁の数字) は、Unicode 文字 U +`dddd` を表します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="6ba86-135">8 桁の Unicode エスケープ コード `\Udddddddd` も認識できます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="6ba86-136">[verbatim 文字列リテラル](../tokens/verbatim.md)の場合は、先頭に `@` を付け、さらに前後に二重引用符を付けます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="6ba86-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="6ba86-138">verbatim 文字列の場合の利点は、エスケープ シーケンスが " *処理されない* " ため、たとえば、完全修飾 Windows ファイル名が書きやすくなることです。</span><span class="sxs-lookup"><span data-stu-id="6ba86-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="6ba86-139">@-quoted 文字列に二重引用符を含めるには、二重引用符を二重にします。</span><span class="sxs-lookup"><span data-stu-id="6ba86-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="6ba86-140">デリゲート型</span><span class="sxs-lookup"><span data-stu-id="6ba86-140">The delegate type</span></span>

<span data-ttu-id="6ba86-141">デリゲート型の宣言は、メソッド シグネチャに似ています。</span><span class="sxs-lookup"><span data-stu-id="6ba86-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="6ba86-142">戻り値 1 つのほか、任意の型のパラメーターをいくつでも指定することができます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="6ba86-143">.NET では、`System.Action` 型と `System.Func` 型により、多くの一般的なデリゲートに対するジェネリック定義が提供されます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="6ba86-144">おそらく、新しいカスタム デリゲート型を定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6ba86-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="6ba86-145">代わりに、提供されたジェネリック型のインスタンス化を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="6ba86-146">`delegate` は、名前付きメソッドまたは匿名メソッドをカプセル化することができる参照型です。</span><span class="sxs-lookup"><span data-stu-id="6ba86-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="6ba86-147">デリゲートは C++ の関数ポインターに似ていますが、タイプ セーフであり安全です。</span><span class="sxs-lookup"><span data-stu-id="6ba86-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="6ba86-148">デリゲートの使い方については、[デリゲート](../../programming-guide/delegates/index.md)と[汎用デリゲート](../../programming-guide/generics/generic-delegates.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ba86-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="6ba86-149">デリゲートは[イベント](../../programming-guide/events/index.md)の土台となる働きをします。</span><span class="sxs-lookup"><span data-stu-id="6ba86-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="6ba86-150">デリゲートは名前付きメソッドまたは匿名メソッドに関連付けることによって、インスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="6ba86-151">デリゲートは、適合する入力パラメーターと戻り値の型を持ったメソッドまたはラムダ式でインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba86-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="6ba86-152">メソッドのシグネチャでどの程度の変性が許容されるかについて詳しくは、[デリゲートの変性](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ba86-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="6ba86-153">匿名メソッドで使用する場合は、デリゲートとそれに関連付けるコードとを一緒に宣言します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span>

## <a name="the-dynamic-type"></a><span data-ttu-id="6ba86-154">dynamic 型</span><span class="sxs-lookup"><span data-stu-id="6ba86-154">The dynamic type</span></span>

<span data-ttu-id="6ba86-155">`dynamic` 型は、変数およびそのメンバーに対する参照の使用が、コンパイル時の型チェックをバイパスすることを示します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="6ba86-156">代わりに、演算は実行時に解決されます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="6ba86-157">`dynamic` 型により、Office オートメーション API などの COM API、IronPython ライブラリなどの動的 API、および HTML ドキュメント オブジェクト モデル (DOM: Document Object Model) へのアクセスが容易になります。</span><span class="sxs-lookup"><span data-stu-id="6ba86-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="6ba86-158">ほとんどの環境で、`dynamic` 型は `object` 型のように動作します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="6ba86-159">具体的には、null 以外の任意の式を `dynamic` 型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="6ba86-160">`dynamic` 型は `object` と異なり、`dynamic` 型の式を含む演算はコンパイラによって解決または型チェックされません。</span><span class="sxs-lookup"><span data-stu-id="6ba86-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="6ba86-161">コンパイラは演算に関する情報をまとめてパッケージ化します。その情報が後で実行時に演算を評価するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="6ba86-162">このプロセスの過程で、`dynamic` 型の変数は `object` 型の変数にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="6ba86-163">そのため、`dynamic` 型はコンパイル時にのみ存在し、実行時には存在しません。</span><span class="sxs-lookup"><span data-stu-id="6ba86-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="6ba86-164">`dynamic` 型の変数と `object` 型の変数の違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="6ba86-165">コンパイル時に各変数の型を確認するには、`WriteLine` ステートメントの `dyn` または `obj` にマウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="6ba86-166">IntelliSense が使用可能なエディターに、次のコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="6ba86-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="6ba86-167">IntelliSense 機能によって、`dyn` には **dynamic** 、`obj` には **object** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="6ba86-168"><xref:System.Console.WriteLine%2A> ステートメントは `dyn` および `obj` の実行時の型を表示します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="6ba86-169">その時点では、両方が同じ整数型を持ちます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="6ba86-170">次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="6ba86-171">コンパイル時の `dyn` と `obj` の違いを確認するには、前の例の宣言と `WriteLine` ステートメントの間に次の 2 行を追加します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="6ba86-172">式 `obj + 3` に整数およびオブジェクトを追加しようとしたことに対してコンパイル エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="6ba86-173">ただし、`dyn + 3` に関するエラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="6ba86-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="6ba86-174">`dyn` を含む式はコンパイル時にはチェックされません。これは、`dyn` の型が `dynamic` であるためです。</span><span class="sxs-lookup"><span data-stu-id="6ba86-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="6ba86-175">さまざまな宣言で `dynamic` を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6ba86-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="6ba86-176">また、`Main` メソッドで、コンパイル時の型チェックと実行時の型チェックの違いを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6ba86-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="6ba86-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ba86-177">See also</span></span>

- [<span data-ttu-id="6ba86-178">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6ba86-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ba86-179">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="6ba86-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="6ba86-180">イベント</span><span class="sxs-lookup"><span data-stu-id="6ba86-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="6ba86-181">dynamic 型の使用</span><span class="sxs-lookup"><span data-stu-id="6ba86-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="6ba86-182">文字列を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="6ba86-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="6ba86-183">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="6ba86-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="6ba86-184">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="6ba86-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="6ba86-185">型テストとキャスト演算子</span><span class="sxs-lookup"><span data-stu-id="6ba86-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="6ba86-186">パターン マッチング、is 演算子、as 演算子を使用して安全にキャストする方法</span><span class="sxs-lookup"><span data-stu-id="6ba86-186">How to safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="6ba86-187">チュートリアル: 動的オブジェクトの作成と使用</span><span class="sxs-lookup"><span data-stu-id="6ba86-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
