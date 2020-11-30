---
title: C# の予約済み属性:Conditional、Obsolete、AttributeUsage
ms.date: 04/09/2020
description: これらの属性はコンパイラによって解釈され、コンパイラによって生成されたコードに影響を与えます
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021769"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="081f7-103">予約済みの属性:ConditionalAttribute、ObsoleteAttribute、AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="081f7-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="081f7-104">これらの属性は、コード内の要素に適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="081f7-105">それによって、このような要素にセマンティックの意味が追加されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="081f7-106">コンパイラでは、これらのセマンティックの意味を使用して出力が変更され、コードを使用する開発者による間違いの可能性が報告されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="081f7-107">`Conditional` 属性</span><span class="sxs-lookup"><span data-stu-id="081f7-107">`Conditional` attribute</span></span>

<span data-ttu-id="081f7-108">`Conditional` 属性を使用すると、プリプロセス識別子に依存したメソッドの実行を指定できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="081f7-109">`Conditional` 属性は <xref:System.Diagnostics.ConditionalAttribute> の別名であり、メソッドまたは属性クラスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="081f7-110">次の例では、`Conditional` は、プログラム固有の診断情報の表示を有効または無効にするメソッドに適用されています。</span><span class="sxs-lookup"><span data-stu-id="081f7-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="081f7-111">`TRACE_ON` 識別子が定義されていない場合、トレース出力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="081f7-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="081f7-112">対話型ウィンドウで自分で探してください。</span><span class="sxs-lookup"><span data-stu-id="081f7-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="081f7-113">多くの場合、`Conditional` 属性は、リリース ビルドではなく、デバッグ ビルドのトレース機能とログ機能を有効にするために `DEBUG` 識別子と共に使用されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="081f7-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="081f7-114">条件付きの印が付いたメソッドが呼び出されると、指定のプリプロセッサ シンボルの有無に従って、呼び出しの実行か省略が決定されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="081f7-115">シンボルが定義されている場合は呼び出しが実行され、定義されていない場合は省略されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="081f7-116">条件付きメソッドは、クラスまたは構造体宣言のメソッドである必要があり、戻り値の型が `void` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="081f7-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="081f7-117">`Conditional` を使用すると、`#if…#endif` ブロック内にメソッドを含めるよりも、クリーンで洗練されており、エラーが発生しにくくなります。</span><span class="sxs-lookup"><span data-stu-id="081f7-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="081f7-118">メソッドに複数の `Conditional` 属性が付いている場合、そのメソッドの呼び出しは、1 つ以上の条件付きシンボルが定義されているときに実行されます (シンボルは OR 演算子によって論理的にリンクされています)。</span><span class="sxs-lookup"><span data-stu-id="081f7-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="081f7-119">次の例では、`A` または `B` が存在すると、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="081f7-120">属性クラスでの `Conditional` の使用</span><span class="sxs-lookup"><span data-stu-id="081f7-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="081f7-121">`Conditional` 属性は、属性クラスの定義にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="081f7-122">次の例では、カスタム属性 `Documentation` は、`DEBUG` が定義されている場合にのみ、情報をメタデータに追加します。</span><span class="sxs-lookup"><span data-stu-id="081f7-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="081f7-123">`Obsolete` 属性</span><span class="sxs-lookup"><span data-stu-id="081f7-123">`Obsolete` attribute</span></span>

<span data-ttu-id="081f7-124">`Obsolete` 属性は、コード要素の使用が推奨されなくなったことを示します。</span><span class="sxs-lookup"><span data-stu-id="081f7-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="081f7-125">非推奨とマークされたエンティティを使用すると、警告またはエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="081f7-126">`Obsolete` 属性は、1 回だけ使用できる属性であり、属性を使用できる任意のエンティティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="081f7-127">`Obsolete` は <xref:System.ObsoleteAttribute> の別名です。</span><span class="sxs-lookup"><span data-stu-id="081f7-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="081f7-128">次の例では、`Obsolete` 属性がクラス `A` およびメソッド `B.OldMethod` に適用されています。</span><span class="sxs-lookup"><span data-stu-id="081f7-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="081f7-129">`B.OldMethod` に適用された属性コンストラクターの 2 番目の引数が `true` に設定されているため、このメソッドではコンパイル エラーが発生します。一方、クラス `A` が使用されると、警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="081f7-130">しかし、`B.NewMethod` の呼び出しでは、警告もエラーも生成されません。</span><span class="sxs-lookup"><span data-stu-id="081f7-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="081f7-131">たとえば、前の定義でこれを使用すると、次のコードで 2 つの警告と 1 つのエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="081f7-132">最初の引数として属性コンストラクターに指定された文字列は、警告またはエラーの一部として表示されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="081f7-133">クラス `A` の警告が 2 つ生成されます。1 つはクラス参照の宣言の警告で、もう 1 つはクラス コンストラクターの警告です。</span><span class="sxs-lookup"><span data-stu-id="081f7-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="081f7-134">`Obsolete` 属性は引数なしで使用できますが、代わりに何を使用するかの説明を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="081f7-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="081f7-135">`AttributeUsage` 属性</span><span class="sxs-lookup"><span data-stu-id="081f7-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="081f7-136">`AttributeUsage` 属性によって、カスタム属性クラスの使用方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="081f7-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="081f7-137"><xref:System.AttributeUsageAttribute> は、カスタム属性定義に適用する属性です。</span><span class="sxs-lookup"><span data-stu-id="081f7-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="081f7-138">`AttributeUsage` 属性を使用すると、以下を制御できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="081f7-139">適用できるプログラム要素属性。</span><span class="sxs-lookup"><span data-stu-id="081f7-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="081f7-140">使用法を制限しない限り、属性は以下のプログラム要素のいずれかに適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="081f7-141">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="081f7-141">assembly</span></span>
  - <span data-ttu-id="081f7-142">name</span><span class="sxs-lookup"><span data-stu-id="081f7-142">module</span></span>
  - <span data-ttu-id="081f7-143">フィールド</span><span class="sxs-lookup"><span data-stu-id="081f7-143">field</span></span>
  - <span data-ttu-id="081f7-144">event</span><span class="sxs-lookup"><span data-stu-id="081f7-144">event</span></span>
  - <span data-ttu-id="081f7-145">メソッド</span><span class="sxs-lookup"><span data-stu-id="081f7-145">method</span></span>
  - <span data-ttu-id="081f7-146">param</span><span class="sxs-lookup"><span data-stu-id="081f7-146">param</span></span>
  - <span data-ttu-id="081f7-147">property</span><span class="sxs-lookup"><span data-stu-id="081f7-147">property</span></span>
  - <span data-ttu-id="081f7-148">return</span><span class="sxs-lookup"><span data-stu-id="081f7-148">return</span></span>
  - <span data-ttu-id="081f7-149">型</span><span class="sxs-lookup"><span data-stu-id="081f7-149">type</span></span>
- <span data-ttu-id="081f7-150">1 つのプログラム要素に属性を複数回適用できるかどうか。</span><span class="sxs-lookup"><span data-stu-id="081f7-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="081f7-151">属性が派生クラスに継承されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="081f7-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="081f7-152">明示的に適用すると、既定の設定は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="081f7-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="081f7-153">この例で `NewAttribute` クラスはサポートされている任意のプログラム要素に適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="081f7-154">ただし、各エンティティに適用できるのは 1 回のみです。</span><span class="sxs-lookup"><span data-stu-id="081f7-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="081f7-155">基底クラスに適用すると、属性は派生クラスに継承されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="081f7-156"><xref:System.AttributeUsageAttribute.AllowMultiple> 引数と <xref:System.AttributeUsageAttribute.Inherited> 引数は省略できるので、次のコードは同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="081f7-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="081f7-157">最初の <xref:System.AttributeUsageAttribute> 引数は、<xref:System.AttributeTargets> 列挙型の 1 つまたは複数の要素でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="081f7-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="081f7-158">次の例のように、複数のターゲット型を OR 演算子で 1 つにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="081f7-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="081f7-159">C# 7.3 以降、プロパティ、または自動実装バッキング フィールドに属性を適用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="081f7-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="081f7-160">属性に `field` 指定子を指定しない限り、属性はプロパティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="081f7-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="081f7-161">その両方の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="081f7-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="081f7-162"><xref:System.AttributeUsageAttribute.AllowMultiple> 引数が `true` の場合、次の例のように、結果の属性を 1 つのエンティティに複数回適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="081f7-163">この例では、`AllowMultiple` が `true` に設定されているので、`MultiUseAttribute` を繰り返し適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="081f7-164">示されているどちらの形式でも、複数の属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="081f7-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="081f7-165"><xref:System.AttributeUsageAttribute.Inherited> が `false` の場合、属性は属性クラスから派生したクラスに継承されません。</span><span class="sxs-lookup"><span data-stu-id="081f7-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="081f7-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="081f7-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="081f7-167">この例で、`NonInheritedAttribute` は継承によって `DClass` に適用されません。</span><span class="sxs-lookup"><span data-stu-id="081f7-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="081f7-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="081f7-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="081f7-169">属性</span><span class="sxs-lookup"><span data-stu-id="081f7-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="081f7-170">リフレクション</span><span class="sxs-lookup"><span data-stu-id="081f7-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
