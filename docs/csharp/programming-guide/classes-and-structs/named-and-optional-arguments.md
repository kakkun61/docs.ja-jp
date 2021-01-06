---
title: 名前付き引数と省略可能な引数 - C# プログラミング ガイド
description: C# の名前付き引数は、位置ではなく名前で引数を指定します。 省略可能な引数は省略できます。
ms.date: 09/25/2020
ms.custom: contperf-fy21q1
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: bb79d956124a610bac0de6825c1f42655789e98d
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513108"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="5f816-104">名前付き引数と省略可能な引数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5f816-104">Named and Optional Arguments (C# Programming Guide)</span></span>

<span data-ttu-id="5f816-105">C# 4 では、名前付き引数と省略可能な引数が導入されています。</span><span class="sxs-lookup"><span data-stu-id="5f816-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="5f816-106">"*名前付き引数*" を使用すると、引数をそのパラメーター リスト内の位置ではなく名前で照合することで、パラメーターの引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-106">*Named arguments* enable you to specify an argument for a parameter by matching the argument with its name rather than with its position in the parameter list.</span></span> <span data-ttu-id="5f816-107">*省略可能な引数* を使用すると、一部のパラメーターの引数を省略できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="5f816-108">両方の手法をメソッド、インデクサー、コンストラクター、デリゲートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>

<span data-ttu-id="5f816-109">名前付き引数と省略可能な引数を使用すると、引数は、パラメーター リストではなく、引数リストに記述されている順に評価されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>

<span data-ttu-id="5f816-110">名前付きパラメーターと省略可能なパラメーターを使用すると、選択したパラメーターの引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-110">Named and optional parameters enable you to supply arguments for selected parameters.</span></span> <span data-ttu-id="5f816-111">この機能により、Microsoft Office オートメーション API などの COM インターフェイスの呼び出しが大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-111">This capability greatly eases calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="5f816-112">名前付き引数</span><span class="sxs-lookup"><span data-stu-id="5f816-112">Named Arguments</span></span>

<span data-ttu-id="5f816-113">名前付き引数を使用すると、呼び出されたメソッドのパラメーター リスト内のパラメーターの順序を一致させる必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="5f816-113">Named arguments free you from matching the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="5f816-114">各引数のパラメーターはパラメーター名で指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="5f816-115">たとえば、注文の詳細 (販売者の名前、注文番号、製品名など) を出力する関数は、引数を位置によって、その関数で定義されている順序に従って渡すことで呼び出せます。</span><span class="sxs-lookup"><span data-stu-id="5f816-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called by sending arguments by position, in the order defined by the function.</span></span>

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

<span data-ttu-id="5f816-116">パラメーターの順序を覚えていなくても、それらの名前がわかっていれば、任意の順序で引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5f816-116">If you don't remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

<span data-ttu-id="5f816-117">また、名前付き引数を使用すると、各引数が表すものが識別しやすくなり、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="5f816-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="5f816-118">次のメソッド例では、`sellerName` は null にしたり、空白にしたりできません。</span><span class="sxs-lookup"><span data-stu-id="5f816-118">In the example method below, the `sellerName` can't be null or white space.</span></span> <span data-ttu-id="5f816-119">`sellerName` と `productName` はいずれも文字列型であり、引数を位置によって渡すより、名前付き引数を使用するほうが合理的です。2 つのあいまいさが取り除かれ、コードを読む人の混乱が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="5f816-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
<span data-ttu-id="5f816-120">名前付き引数は、位置引数と共に使用するとき、次の場合において有効となります</span><span class="sxs-lookup"><span data-stu-id="5f816-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="5f816-121">後ろに位置引数が続かない。</span><span class="sxs-lookup"><span data-stu-id="5f816-121">they're not followed by any positional arguments, or</span></span>

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- <span data-ttu-id="5f816-122">_C# 7.2 以降_。正しい位置で使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="5f816-123">下の例では、パラメーター `orderNum` は正しい位置にありますが、明示的に名前が付けられていません。</span><span class="sxs-lookup"><span data-stu-id="5f816-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

<span data-ttu-id="5f816-124">後に位置引数が続く場合、順序が正しくない名前付き引数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="5f816-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a><span data-ttu-id="5f816-125">例</span><span class="sxs-lookup"><span data-stu-id="5f816-125">Example</span></span>

<span data-ttu-id="5f816-126">次のコードでは、このセクションの例の実装し、さらにいくつかのプログラミングを追加しています。</span><span class="sxs-lookup"><span data-stu-id="5f816-126">The following code implements the examples from this section along with some additional ones.</span></span>  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a><span data-ttu-id="5f816-127">省略可能な引数</span><span class="sxs-lookup"><span data-stu-id="5f816-127">Optional Arguments</span></span>

<span data-ttu-id="5f816-128">メソッド、コンストラクター、インデクサー、デリゲートの定義では、そのパラメーターが必須であるか、省略可能であるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-128">The definition of a method, constructor, indexer, or delegate can specify its parameters are required or optional.</span></span> <span data-ttu-id="5f816-129">どの呼び出しでも、すべての必須パラメーターに対して引数を指定する必要があります。ただし、省略可能なパラメーターの引数は省略できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>

<span data-ttu-id="5f816-130">省略可能な各パラメーターには、パラメーターの定義に既定値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f816-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="5f816-131">そのパラメーターの引数を渡さない場合、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="5f816-132">既定値には、次のいずれかの種類の式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-132">A default value must be one of the following types of expressions:</span></span>
  
- <span data-ttu-id="5f816-133">定数式</span><span class="sxs-lookup"><span data-stu-id="5f816-133">a constant expression;</span></span>  
- <span data-ttu-id="5f816-134">`new ValType()` 形式の式です。`ValType` は、[enum](../../language-reference/builtin-types/enum.md) や [struct](../../language-reference/builtin-types/struct.md) のような値型になります。</span><span class="sxs-lookup"><span data-stu-id="5f816-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>
- <span data-ttu-id="5f816-135">[default(ValType)](../../language-reference/operators/default.md) 形式の式です。`ValType` は値型です。</span><span class="sxs-lookup"><span data-stu-id="5f816-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>

<span data-ttu-id="5f816-136">省略可能なパラメーターは、パラメーター リストの末尾で必須パラメーターの後に定義されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="5f816-137">呼び出し元は、連続する省略可能なパラメーターのいずれか 1 つに対して引数を指定する場合、先行するすべての省略可能なパラメーターに引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f816-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="5f816-138">引数リストでコンマで区切られたスペースを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5f816-138">Comma-separated gaps in the argument list aren't supported.</span></span> <span data-ttu-id="5f816-139">たとえば、次のコードでは、1 つの必須パラメーターと 2 つの省略可能パラメーターでインスタンス メソッド `ExampleMethod` が定義されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

<span data-ttu-id="5f816-140">次に示す `ExampleMethod` の呼び出しでは、3 つ目のパラメーターに引数が指定されていますが、2 つ目のパラメーターには指定されていないため、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5f816-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>

```csharp
//anExample.ExampleMethod(3, ,4);
```

<span data-ttu-id="5f816-141">ただし、3 つ目のパラメーターの名前がわかっている場合、名前付き引数を使用してタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

<span data-ttu-id="5f816-142">次の例に示すように、IntelliSense では、省略可能なパラメーターを角かっこで示します。</span><span class="sxs-lookup"><span data-stu-id="5f816-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>

![ExampleMethod メソッドの IntelliSense クイック インフォを示すスクリーンショット。](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> <span data-ttu-id="5f816-144">また、.NET <xref:System.Runtime.InteropServices.OptionalAttribute> クラスを使用して省略可能なパラメーターを宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f816-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="5f816-145">`OptionalAttribute` パラメーターに既定値は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5f816-145">`OptionalAttribute` parameters do not require a default value.</span></span>

## <a name="example"></a><span data-ttu-id="5f816-146">例</span><span class="sxs-lookup"><span data-stu-id="5f816-146">Example</span></span>

<span data-ttu-id="5f816-147">次の例では、`ExampleClass` のコンストラクターに省略可能なパラメーターが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="5f816-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="5f816-148">`ExampleMethod` インスタンス メソッドには、`required` という 1 つの必須パラメーターと、`optionalstr` と `optionalint` という 2 つの省略可能なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="5f816-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="5f816-149">`Main` のコードに示すように、いくつかの異なる方法でコンストラクターとメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5f816-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

<span data-ttu-id="5f816-150">上記のコードでは、省略可能なパラメーターが正しく適用されていない例がいくつか示されています。</span><span class="sxs-lookup"><span data-stu-id="5f816-150">The preceding code shows a number of examples where optional parameters aren't applied correctly.</span></span> <span data-ttu-id="5f816-151">最初の例は、必須である 1 番目のパラメーターに引数を指定する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="5f816-151">The first illustrates that an argument must be supplied for the first parameter, which is required.</span></span>
  
## <a name="com-interfaces"></a><span data-ttu-id="5f816-152">COM インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f816-152">COM Interfaces</span></span>

<span data-ttu-id="5f816-153">名前付き引数と省略可能な引数を動的オブジェクトのサポートと併用すると、Office オートメーション API などの COM API との相互運用性が大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="5f816-153">Named and optional arguments, along with support for dynamic objects, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>

<span data-ttu-id="5f816-154">たとえば、Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> インターフェイスの <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> メソッドには 7 つのパラメーターがあります。それらはすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f816-154">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="5f816-155">これらのパラメーターを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5f816-155">These parameters are shown in the following illustration:</span></span>

![AutoFormat メソッドの IntelliSense クイック インフォを示すスクリーンショット。](./media/named-and-optional-arguments/autoformat-method-parameters.png)

<span data-ttu-id="5f816-157">C# 3.0 以前のバージョンの C# では、次の例に示すように、各パラメーターの引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="5f816-157">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

<span data-ttu-id="5f816-158">ただし、C# 4.0 の導入により、名前付き引数と省略可能な引数を使用すると、`AutoFormat` の呼び出しを大幅に簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-158">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="5f816-159">名前付き引数と省略可能な引数を使用すると、パラメーターの既定値を変更する必要がない場合に、省略可能なパラメーターの引数を省略できます。</span><span class="sxs-lookup"><span data-stu-id="5f816-159">Named and optional arguments enable you to omit the argument for an optional parameter if you don't want to change the parameter's default value.</span></span> <span data-ttu-id="5f816-160">次の呼び出しでは、7 つのパラメーターのうちの 1 つのパラメーターのみに値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="5f816-160">In the following call, a value is specified for only one of the seven parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

<span data-ttu-id="5f816-161">詳細と例については、「[Office プログラミングで名前付き引数と省略可能な引数を使用する方法](./how-to-use-named-and-optional-arguments-in-office-programming.md)」と「[C# の機能を使用して Office 相互運用オブジェクトにアクセスする方法](../interop/how-to-access-office-onterop-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f816-161">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>
  
## <a name="overload-resolution"></a><span data-ttu-id="5f816-162">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="5f816-162">Overload Resolution</span></span>

<span data-ttu-id="5f816-163">名前付き引数と省略可能な引数を使用すると、オーバーロードの解決に次のように影響します。</span><span class="sxs-lookup"><span data-stu-id="5f816-163">Use of named and optional arguments affects overload resolution in the following ways:</span></span>

- <span data-ttu-id="5f816-164">メソッド、インデクサー、コンストラクターのパラメーターのそれぞれが任意であるか、名前か位置により、呼び出しステートメントの 1 つの引数に対応するとき、その引数がパラメーターの型に変換できる場合、メソッド、インデクサー、コンストラクターが実行の候補になります。</span><span class="sxs-lookup"><span data-stu-id="5f816-164">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
- <span data-ttu-id="5f816-165">複数の候補が見つかった場合、明示的に指定される引数には、優先変換に関するオーバーロード解決の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-165">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="5f816-166">任意のパラメーターの省略された引数は無視されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-166">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="5f816-167">2 つの候補が等しく良好であると判断された場合、呼び出しで引数が省略された省略可能なパラメーターのない候補が優先されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-167">If two candidates are judged to be equally good, preference goes to a candidate that doesn't have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="5f816-168">オーバーロードの解決では、一般的にパラメーターの少ない候補が優先されます。</span><span class="sxs-lookup"><span data-stu-id="5f816-168">Overload resolution generally prefers candidates that have fewer parameters.</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="5f816-169">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="5f816-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
