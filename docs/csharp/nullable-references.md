---
title: null 許容参照型
description: この記事では、C# 8.0 で追加された null 許容参照型の概要を説明します。 新規および既存のプロジェクトにおいて、その機能によって null 参照例外に対する安全性がどのように提供されるかを学習します。
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: cb9438db6364b6dc5d34f3a776d3ed7ec2e9978b
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440394"
---
# <a name="nullable-reference-types"></a><span data-ttu-id="3ee0c-104">null 許容参照型</span><span class="sxs-lookup"><span data-stu-id="3ee0c-104">Nullable reference types</span></span>

<span data-ttu-id="3ee0c-105">C# 8.0 で導入された **null 許容参照型** および **null 非許容参照型** を使用すると、参照型変数のプロパティについて重要なことを表明できます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-105">C# 8.0 introduces **nullable reference types** and **non-nullable reference types** that enable you to make important statements about the properties for reference type variables:</span></span>

- <span data-ttu-id="3ee0c-106">**参照が null になることはない**。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-106">**A reference isn't supposed to be null**.</span></span> <span data-ttu-id="3ee0c-107">変数が null にならない場合、コンパイラでは最初に変数が null ではないことをチェックしないで変数を逆参照しても安全であることを保証する規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-107">When variables aren't supposed to be null, the compiler enforces rules that ensure it's safe to dereference these variables without first checking that it isn't null:</span></span>
  - <span data-ttu-id="3ee0c-108">変数は、null 以外の値に初期化される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-108">The variable must be initialized to a non-null value.</span></span>
  - <span data-ttu-id="3ee0c-109">変数に値 `null` を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-109">The variable can never be assigned the value `null`.</span></span>
- <span data-ttu-id="3ee0c-110">**参照は null になることがある**。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-110">**A reference may be null**.</span></span> <span data-ttu-id="3ee0c-111">変数が null になる可能性がある場合、コンパイラでは別の規則が適用されて、null 参照を正しくチェックしていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-111">When variables may be null, the compiler enforces different rules to ensure that you've correctly checked for a null reference:</span></span>
  - <span data-ttu-id="3ee0c-112">値が null ではないことをコンパイラが保証できる場合にのみ、変数を逆参照できます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-112">The variable may only be dereferenced when the compiler can guarantee that the value isn't null.</span></span>
  - <span data-ttu-id="3ee0c-113">これらの変数は、既定値 `null` で初期化される場合があり、他のコードで値 `null` を割り当てられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-113">These variables may be initialized with the default `null` value and may be assigned the value `null` in other code.</span></span>

<span data-ttu-id="3ee0c-114">以前のバージョンの C# では変数の宣言から設計の意図を判断できなかったので、この新機能には参照変数の処理について大きなメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-114">This new feature provides significant benefits over the handling of reference variables in earlier versions of C# where the design intent can't be determined from the variable declaration.</span></span> <span data-ttu-id="3ee0c-115">コンパイラでは、参照型の null 参照例外に対する安全性は提供されませんでした。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-115">The compiler didn't provide safety against null reference exceptions for reference types:</span></span>

- <span data-ttu-id="3ee0c-116">**参照は null にできる**。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-116">**A reference can be null**.</span></span> <span data-ttu-id="3ee0c-117">参照型変数を `null` に初期化したり、後で `null` を割り当てたりしても、コンパイラから警告が発せられることはありません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-117">The compiler doesn't issue warnings when a reference-type variable is initialized to `null`, or later assigned `null`.</span></span> <span data-ttu-id="3ee0c-118">これらの変数が null チェックなしで逆参照されていると、コンパイラで警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-118">The compiler issues warnings when these variables are dereferenced without null checks.</span></span>
- <span data-ttu-id="3ee0c-119">**参照は null ではないと見なされる**。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-119">**A reference is assumed to be not null**.</span></span> <span data-ttu-id="3ee0c-120">参照型が逆参照されても、コンパイラでは警告は発行されません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-120">The compiler doesn't issue any warnings when reference types are dereferenced.</span></span> <span data-ttu-id="3ee0c-121">変数が null になる可能性のある式に設定されている場合、コンパイラで警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-121">The compiler issues warnings if a variable is set to an expression that may be null.</span></span>

<span data-ttu-id="3ee0c-122">これらの警告は、コンパイル時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-122">These warnings are emitted at compile time.</span></span> <span data-ttu-id="3ee0c-123">コンパイラでは、null 許容コンテキストには、null チェックやその他のランタイム コンストラクトは追加されません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-123">The compiler doesn't add any null checks or other runtime constructs in a nullable context.</span></span> <span data-ttu-id="3ee0c-124">実行時には、null 許容参照と null 非許容参照は等価になります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-124">At runtime, a nullable reference and a non-nullable reference are equivalent.</span></span>

<span data-ttu-id="3ee0c-125">null 許容参照型の追加により、いっそう明確に意図を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-125">With the addition of nullable reference types, you can declare your intent more clearly.</span></span> <span data-ttu-id="3ee0c-126">`null` 値は、変数で値が参照されていないことを表すための正しい方法です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-126">The `null` value is the correct way to represent that a variable doesn't refer to a value.</span></span> <span data-ttu-id="3ee0c-127">コードからすべての `null` 値を削除するために、この機能を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-127">Don't use this feature to remove all `null` values from your code.</span></span> <span data-ttu-id="3ee0c-128">そうではなく、コンパイラと、コードを読む他の開発者に対し、自分の意図を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-128">Rather, you should declare your intent to the compiler and other developers that read your code.</span></span> <span data-ttu-id="3ee0c-129">意図を宣言することにより、その意図と矛盾するコードを記述すると、コンパイラによって通知されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-129">By declaring your intent, the compiler informs you when you write code that is inconsistent with that intent.</span></span>

<span data-ttu-id="3ee0c-130">**null 許容参照型** は、[null 許容値型](language-reference/builtin-types/nullable-value-types.md)と同じ構文を使用して記述し、変数の型の後に `?` を追加します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-130">A **nullable reference type** is noted using the same syntax as [nullable value types](language-reference/builtin-types/nullable-value-types.md): a `?` is appended to the type of the variable.</span></span> <span data-ttu-id="3ee0c-131">たとえば、次の変数宣言は、null 許容型の文字列変数 `name` を表します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-131">For example, the following variable declaration represents a nullable string variable, `name`:</span></span>

```csharp
string? name;
```

<span data-ttu-id="3ee0c-132">型の名前に `?` が追加されていないすべての変数は、**null 非許容参照型** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-132">Any variable where the `?` isn't appended to the type name is a **non-nullable reference type**.</span></span> <span data-ttu-id="3ee0c-133">この機能を有効にすると、既存のコードのすべての参照型変数がそれに含まれます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-133">That includes all reference type variables in existing code when you've enabled this feature.</span></span>

<span data-ttu-id="3ee0c-134">コンパイラでは、静的分析を使用して、null 許容参照が非 null として認識されているかどうかが判定されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-134">The compiler uses static analysis to determine if a nullable reference is known to be non-null.</span></span> <span data-ttu-id="3ee0c-135">コンパイラは、null の可能性があるときに null 許容参照を逆参照していると警告します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-135">The compiler warns you if you dereference a nullable reference when it may be null.</span></span> <span data-ttu-id="3ee0c-136">この動作は、変数名の後に [null 免除演算子](language-reference/operators/null-forgiving.md) `!` を使用することでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-136">You can override this behavior by using the [null-forgiving operator](language-reference/operators/null-forgiving.md) `!` following a variable name.</span></span> <span data-ttu-id="3ee0c-137">たとえば、変数 `name` は null ではないことがわかっているのに、コンパイラで警告が出る場合は、次のようにコードを記述することで、コンパイラの分析をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-137">For example, if you know the `name` variable isn't null but the compiler issues a warning, you can write the following code to override the compiler's analysis:</span></span>

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a><span data-ttu-id="3ee0c-138">型の null 値の許容</span><span class="sxs-lookup"><span data-stu-id="3ee0c-138">Nullability of types</span></span>

<span data-ttu-id="3ee0c-139">すべての参照型には、4 種類の "*null 値の許容*" のいずれかを指定でき、それぞれで警告が生成される場合が示されています。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-139">Any reference type can have one of four *nullabilities*, which describes when warnings are generated:</span></span>

- <span data-ttu-id="3ee0c-140">"*null 非許容*" : この型の変数には、null を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-140">*Nonnullable*: Null can't be assigned to variables of this type.</span></span> <span data-ttu-id="3ee0c-141">この型の変数については、逆参照する前に null チェックを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-141">Variables of this type don't need to be null-checked before dereferencing.</span></span>
- <span data-ttu-id="3ee0c-142">"*null 許容*" : この型の変数には、null を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-142">*Nullable*: Null can be assigned to variables of this type.</span></span> <span data-ttu-id="3ee0c-143">先に `null` をチェックしないでこの型の変数を逆参照すると、警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-143">Dereferencing variables of this type without first checking for `null` causes a warning.</span></span>
- <span data-ttu-id="3ee0c-144">"*無関係*" : 無関係は、C# 8.0 より前の状態です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-144">*Oblivious*: Oblivious is the pre-C# 8.0 state.</span></span> <span data-ttu-id="3ee0c-145">この型の変数を逆参照したり割り当てたりしても、警告は発生しません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-145">Variables of this type can be dereferenced or assigned without warnings.</span></span>
- <span data-ttu-id="3ee0c-146">"*不明*" : 不明は一般に、型が "*null 許容*" または "*null 非許容*" でなければならないことが制約によってコンパイラに指示されない、型パラメーターの場合です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-146">*Unknown*: Unknown is generally for type parameters where constraints don't tell the compiler that the type must be *nullable* or *nonnullable*.</span></span>

<span data-ttu-id="3ee0c-147">変数宣言での型の null 値の許容は、変数が宣言されている "*null 許容コンテキスト*" によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-147">The nullability of a type in a variable declaration is controlled by the *nullable context* in which the variable is declared.</span></span>

## <a name="nullable-contexts"></a><span data-ttu-id="3ee0c-148">null 許容コンテキスト</span><span class="sxs-lookup"><span data-stu-id="3ee0c-148">Nullable contexts</span></span>

<span data-ttu-id="3ee0c-149">null 許容コンテキストでは、コンパイラによる参照型変数の解釈方法を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-149">Nullable contexts enable fine-grained control for how the compiler interprets reference type variables.</span></span> <span data-ttu-id="3ee0c-150">指定されたソース行の **null 許容注釈コンテキスト** は、有効または無効です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-150">The **nullable annotation context** of any given source line is either enabled or disabled.</span></span> <span data-ttu-id="3ee0c-151">C# 8.0 より前のコンパイラでは、無効な null 許容コンテキストですべてのコードがコンパイルされると考えることができます。すべての参照型は null にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-151">You can think of the pre-C# 8.0 compiler as compiling all your code in a disabled nullable context: any reference type may be null.</span></span> <span data-ttu-id="3ee0c-152">**null 許容警告コンテキスト** も有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-152">The **nullable warnings context** may also be enabled or disabled.</span></span> <span data-ttu-id="3ee0c-153">null 許容警告コンテキストでは、フロー分析を使用するコンパイラによって生成される警告が指定されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-153">The nullable warnings context specifies the warnings generated by the compiler using its flow analysis.</span></span>

<span data-ttu-id="3ee0c-154">プロジェクトの null 許容注釈コンテキストと null 許容警告コンテキストは、 *.csproj* ファイルの `Nullable` 要素を使用して設定することができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-154">The nullable annotation context and nullable warning context can be set for a project using the `Nullable` element in your *.csproj* file.</span></span> <span data-ttu-id="3ee0c-155">この要素では、コンパイラによって型の null 値の許容が解釈される方法と、生成される警告を構成します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-155">This element configures how the compiler interprets the nullability of types and what warnings are generated.</span></span> <span data-ttu-id="3ee0c-156">有効な設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-156">Valid settings are:</span></span>

- <span data-ttu-id="3ee0c-157">`enable`:null 許容注釈コンテキストは **有効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-157">`enable`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="3ee0c-158">null 許容警告コンテキストは **有効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-158">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="3ee0c-159">参照型の変数 (`string` など) は、null 非許容です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-159">Variables of a reference type, `string` for example, are non-nullable.</span></span>  <span data-ttu-id="3ee0c-160">null 値の許容のすべての警告は有効です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-160">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="3ee0c-161">`warnings`:null 許容注釈コンテキストは **無効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-161">`warnings`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="3ee0c-162">null 許容警告コンテキストは **有効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-162">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="3ee0c-163">参照型の変数は、無関係です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-163">Variables of a reference type are oblivious.</span></span> <span data-ttu-id="3ee0c-164">null 値の許容のすべての警告は有効です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-164">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="3ee0c-165">`annotations`:null 許容注釈コンテキストは **有効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-165">`annotations`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="3ee0c-166">null 許容警告コンテキストは **無効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-166">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="3ee0c-167">参照型の変数 (文字列など) は、null 非許容です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-167">Variables of a reference type, string for example, are non-nullable.</span></span> <span data-ttu-id="3ee0c-168">null 値の許容のすべての警告は無効です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-168">All nullability warnings are disabled.</span></span>
- <span data-ttu-id="3ee0c-169">`disable`:null 許容注釈コンテキストは **無効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-169">`disable`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="3ee0c-170">null 許容警告コンテキストは **無効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-170">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="3ee0c-171">参照型の変数は無関係であり、以前のバージョンの C# と同じです。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-171">Variables of a reference type are oblivious, just like earlier versions of C#.</span></span> <span data-ttu-id="3ee0c-172">null 値の許容のすべての警告は無効です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-172">All nullability warnings are disabled.</span></span>

<span data-ttu-id="3ee0c-173">**例**:</span><span class="sxs-lookup"><span data-stu-id="3ee0c-173">**Example**:</span></span>

```xml
<Nullable>enable</Nullable>
```

<span data-ttu-id="3ee0c-174">ディレクティブを使用して、プロジェクト内の任意の場所にこれらと同じコンテキストを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-174">You can also use directives to set these same contexts anywhere in your project:</span></span>

- <span data-ttu-id="3ee0c-175">`#nullable enable`:null 許容注釈コンテキストと null 許容警告コンテキストを、**有効** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-175">`#nullable enable`: Sets the nullable annotation context and nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="3ee0c-176">`#nullable disable`:null 許容注釈コンテキストと null 許容警告コンテキストを、**無効** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-176">`#nullable disable`: Sets the nullable annotation context and nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="3ee0c-177">`#nullable restore`:null 許容注釈コンテキストと null 許容警告コンテキストを、プロジェクトの設定に戻します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-177">`#nullable restore`: Restores the nullable annotation context and nullable warning context to the project settings.</span></span>
- <span data-ttu-id="3ee0c-178">`#nullable disable warnings`:null 許容警告コンテキストを **無効** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-178">`#nullable disable warnings`: Set the nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="3ee0c-179">`#nullable enable warnings`:null 許容警告コンテキストを **有効** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-179">`#nullable enable warnings`: Set the nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="3ee0c-180">`#nullable restore warnings`:null 許容警告コンテキストをプロジェクトの設定に戻します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-180">`#nullable restore warnings`: Restores the nullable warning context to the project settings.</span></span>
- <span data-ttu-id="3ee0c-181">`#nullable disable annotations`:Null 許容の注釈コンテキストを **無効** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-181">`#nullable disable annotations`: Set the nullable annotation context to **disabled**.</span></span>
- <span data-ttu-id="3ee0c-182">`#nullable enable annotations`:Null 許容の注釈コンテキストを **有効** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-182">`#nullable enable annotations`: Set the nullable annotation context to **enabled**.</span></span>
- <span data-ttu-id="3ee0c-183">`#nullable restore annotations`:注釈の警告コンテキストをプロジェクト設定に復元します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-183">`#nullable restore annotations`: Restores the annotation warning context to the project settings.</span></span>

<span data-ttu-id="3ee0c-184">既定の null 許容注釈および警告コンテキストは、新しいプロジェクトも含めて **無効** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-184">By default, nullable annotation and warning contexts are **disabled**, including new projects.</span></span> <span data-ttu-id="3ee0c-185">これは、既存のコードを変更せずにコンパイルできて新しい警告は生成されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-185">That means that your existing code compiles without changes and without generating any new warnings.</span></span>

<span data-ttu-id="3ee0c-186">これらのオプションでは、null 許容参照型を使用するように[既存のコードベースを更新する](nullable-migration-strategies.md)ための 2 つの方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-186">These options provide two distinct strategies to [update an existing codebase](nullable-migration-strategies.md) to use nullable reference types.</span></span>

## <a name="nullable-annotation-context"></a><span data-ttu-id="3ee0c-187">null 許容注釈コンテキスト</span><span class="sxs-lookup"><span data-stu-id="3ee0c-187">Nullable annotation context</span></span>

<span data-ttu-id="3ee0c-188">null 許容注釈コンテキストが無効になっていると、コンパイラでは次の規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-188">The compiler uses the following rules in a disabled nullable annotation context:</span></span>

- <span data-ttu-id="3ee0c-189">無効コンテキスト内で null 許容参照を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-189">You can't declare nullable references in a disabled context.</span></span>
- <span data-ttu-id="3ee0c-190">すべての参照変数には、null 値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-190">All reference variables may be assigned a value of null.</span></span>
- <span data-ttu-id="3ee0c-191">参照型の変数が逆参照されても、警告は生成されません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-191">No warnings are generated when a variable of a reference type is dereferenced.</span></span>
- <span data-ttu-id="3ee0c-192">無効コンテキスト内では、null 免除演算子を使用できません。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-192">The null-forgiving operator may not be used in a disabled context.</span></span>

<span data-ttu-id="3ee0c-193">動作は、以前のバージョンの C# と同じです。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-193">The behavior is the same as previous versions of C#.</span></span>

<span data-ttu-id="3ee0c-194">null 許容注釈コンテキストが有効になっていると、コンパイラでは次の規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-194">The compiler uses the following rules in an enabled nullable annotation context:</span></span>

- <span data-ttu-id="3ee0c-195">参照型のすべての変数は、**null 非許容参照** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-195">Any variable of a reference type is a **non-nullable reference**.</span></span>
- <span data-ttu-id="3ee0c-196">すべての null 非許容参照は、安全に逆参照できます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-196">Any non-nullable reference may be dereferenced safely.</span></span>
- <span data-ttu-id="3ee0c-197">すべての null 許容参照型 (変数宣言で型の後に `?` を付けて示されているもの) は、null にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-197">Any nullable reference type (noted by `?` after the type in the variable declaration) may be null.</span></span> <span data-ttu-id="3ee0c-198">静的分析によって、逆参照されるときに値が null 以外であることがわかっているかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-198">Static analysis determines if the value is known to be non-null when it's dereferenced.</span></span> <span data-ttu-id="3ee0c-199">そうでない場合、コンパイラで警告が出ます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-199">If not, the compiler warns you.</span></span>
- <span data-ttu-id="3ee0c-200">null 免除演算子を使用して、null 許容参照が null ではないことを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-200">You can use the null-forgiving operator to declare that a nullable reference isn't null.</span></span>

<span data-ttu-id="3ee0c-201">null 許容注釈コンテキストが有効になっていると、参照型に追加された `?` 文字により、**null 許容参照型** が宣言されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-201">In an enabled nullable annotation context, the `?` character appended to a reference type declares a **nullable reference type**.</span></span> <span data-ttu-id="3ee0c-202">**null 免除演算子** `!` を式に追加して、式が null ではないことを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-202">The **null-forgiving operator** `!` may be appended to an expression to declare that the expression isn't null.</span></span>

## <a name="nullable-warning-context"></a><span data-ttu-id="3ee0c-203">null 許容警告コンテキスト</span><span class="sxs-lookup"><span data-stu-id="3ee0c-203">Nullable warning context</span></span>

<span data-ttu-id="3ee0c-204">null 許容警告コンテキストは、null 許容注釈コンテキストとは異なります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-204">The nullable warning context is distinct from the nullable annotation context.</span></span> <span data-ttu-id="3ee0c-205">新しい注釈が無効になっている場合でも、警告を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-205">Warnings can be enabled even when the new annotations are disabled.</span></span> <span data-ttu-id="3ee0c-206">コンパイラでは、静的フロー解析を使用して、参照の **null 状態** が決定されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-206">The compiler uses static flow analysis to determine the **null state** of any reference.</span></span> <span data-ttu-id="3ee0c-207">*null 許容警告コンテキスト* が **無効** ではない場合、null 状態は **null ではない** または **null かもしれない** です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-207">The null state is either **not null** or **maybe null** when the *nullable warning context* isn't **disabled**.</span></span> <span data-ttu-id="3ee0c-208">コンパイラが **null かもしれない** と判断したときに、参照を逆参照した場合は、コンパイラで警告が出ます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-208">If you dereference a reference when the compiler has determined it's **maybe null**, the compiler warns you.</span></span> <span data-ttu-id="3ee0c-209">コンパイラが次の 2 つの条件のいずれかであると判断できない場合、参照の状態は **null かもしれない** になります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-209">The state of a reference is **maybe null** unless the compiler can determine one of two conditions:</span></span>

1. <span data-ttu-id="3ee0c-210">変数に null 以外の値が確実に割り当てられている。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-210">The variable has been definitely assigned a non-null value.</span></span>
1. <span data-ttu-id="3ee0c-211">変数または式は、それを逆参照する前に null かどうかをチェックされている。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-211">The variable or expression has been checked against null before de-referencing it.</span></span>

<span data-ttu-id="3ee0c-212">null 許容警告コンテキストで **null かもしれない** 変数または式を逆参照すると、コンパイラで警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-212">The compiler generates warnings when you dereference a variable or expression that is **maybe null** in a nullable warning context.</span></span> <span data-ttu-id="3ee0c-213">さらに、null 許容注釈が有効にされたコンテキストで **null かもしれない** 変数または式に null 非許容参照型変数を割り当てると、コンパイラで警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-213">Furthermore, the compiler generates warnings when a nonnullable reference-type variable is assigned a **maybe null** variable or expression in an enabled nullable annotation context.</span></span>

## <a name="attributes-describe-apis"></a><span data-ttu-id="3ee0c-214">属性で API を記述する</span><span class="sxs-lookup"><span data-stu-id="3ee0c-214">Attributes describe APIs</span></span>

<span data-ttu-id="3ee0c-215">引数または戻り値を null にできるとき、またはできないときについての詳細情報をコンパイラに提供する属性を、API に追加します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-215">You add attributes to APIs that provide the compiler more information about when arguments or return values can or can't be null.</span></span> <span data-ttu-id="3ee0c-216">これらの属性の詳細については、[null 許容属性](language-reference/attributes/nullable-analysis.md)について説明されている言語リファレンスの記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-216">You can learn more about these attributes in our article in the language reference covering the [nullable attributes](language-reference/attributes/nullable-analysis.md).</span></span> <span data-ttu-id="3ee0c-217">これらの属性は、現在および今後のリリースで .NET ライブラリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-217">These attributes are being added to .NET libraries over current and upcoming releases.</span></span> <span data-ttu-id="3ee0c-218">最もよく使用される API が最初に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-218">The most commonly used APIs are being updated first.</span></span>

## <a name="known-pitfalls"></a><span data-ttu-id="3ee0c-219">既知の落とし穴</span><span class="sxs-lookup"><span data-stu-id="3ee0c-219">Known pitfalls</span></span>

<span data-ttu-id="3ee0c-220">参照型を含む配列および構造体は、null 許容参照型機能の既知の落とし穴です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-220">Arrays and structs that contain reference types are known pitfalls in nullable reference types feature.</span></span>

### <a name="structs"></a><span data-ttu-id="3ee0c-221">構造体</span><span class="sxs-lookup"><span data-stu-id="3ee0c-221">Structs</span></span>

<span data-ttu-id="3ee0c-222">null 非許容の参照型を含む構造体により、警告なしで `default` を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-222">A struct that contains non-nullable reference types allows assigning `default` for it without any warnings.</span></span> <span data-ttu-id="3ee0c-223">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-223">Consider the following example:</span></span>

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

<span data-ttu-id="3ee0c-224">前の例では `PrintStudent(default)` に警告はありませんが、null 非許容の参照型 `FirstName` と `LastName` は null です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-224">In the preceding example, there is no warning in `PrintStudent(default)` while the non-nullable reference types `FirstName` and `LastName` are null.</span></span>

<span data-ttu-id="3ee0c-225">もう 1 つの一般的なケースは、ジェネリック構造体を扱う場合です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-225">Another more common case is when you deal with generic structs.</span></span> <span data-ttu-id="3ee0c-226">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-226">Consider the following example:</span></span>

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

<span data-ttu-id="3ee0c-227">前の例では、プロパティ `Bar` は実行時に `null` になり、null 非許容の文字列には警告なしで割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-227">In the preceding example, the property `Bar` is going to be `null` at runtime, and it's assigned to non-nullable string without any warnings.</span></span>

### <a name="arrays"></a><span data-ttu-id="3ee0c-228">配列</span><span class="sxs-lookup"><span data-stu-id="3ee0c-228">Arrays</span></span>

<span data-ttu-id="3ee0c-229">配列も null 許容参照型の既知の落とし穴です。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-229">Arrays are also a known pitfall in nullable reference types.</span></span> <span data-ttu-id="3ee0c-230">警告が生成されない次の例を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-230">Consider the following example which doesn't produce any warnings:</span></span>

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

<span data-ttu-id="3ee0c-231">前の例では、null 非許容の文字列が保持され、その要素がすべて null に初期化されることが配列の宣言からわかります。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-231">In the preceding example, the declaration of the array shows it holds non-nullable strings, while its elements are all initialized to null.</span></span> <span data-ttu-id="3ee0c-232">その後、変数 `s` に null 値が割り当てられます (配列の最初の要素)。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-232">Then, the variable `s` is assigned a null value (the first element of the array).</span></span> <span data-ttu-id="3ee0c-233">最後に、変数 `s` が逆参照され、ランタイム例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="3ee0c-233">Finally, the variable `s` is dereferenced causing a runtime exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee0c-234">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ee0c-234">See also</span></span>

- [<span data-ttu-id="3ee0c-235">null 許容参照型仕様の下書き</span><span class="sxs-lookup"><span data-stu-id="3ee0c-235">Draft nullable reference types specification</span></span>](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [<span data-ttu-id="3ee0c-236">null 許容参照の概要チュートリアル</span><span class="sxs-lookup"><span data-stu-id="3ee0c-236">Intro to nullable references tutorial</span></span>](tutorials/nullable-reference-types.md)
- [<span data-ttu-id="3ee0c-237">既存のコードベースを null 許容参照に移行する</span><span class="sxs-lookup"><span data-stu-id="3ee0c-237">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="3ee0c-238">-nullable (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="3ee0c-238">-nullable (C# Compiler option)</span></span>](language-reference/compiler-options/nullable-compiler-option.md)
