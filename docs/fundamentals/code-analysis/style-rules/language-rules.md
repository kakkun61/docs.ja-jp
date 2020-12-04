---
title: コードスタイルの言語規則
description: C# および Visual Basic 言語構成要素を使用するためのさまざまなコードスタイル規則について説明します。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
- language rules
- EditorConfig language conventions
ms.openlocfilehash: b77d9aa2a528a6cf540babd5e5acc148e48c489c
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594163"
---
# <a name="language-rules"></a><span data-ttu-id="6beea-103">言語規則</span><span class="sxs-lookup"><span data-stu-id="6beea-103">Language rules</span></span>

<span data-ttu-id="6beea-104">コードスタイルの言語規則は、.NET プログラミング言語のさまざまな構造 (修飾子やかっこなど) が使用される方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="6beea-104">Code style language rules affect how various constructs of .NET programming languages, for example, modifiers and parentheses, are used.</span></span> <span data-ttu-id="6beea-105">規則は次のカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="6beea-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="6beea-106">[.Net スタイルルール](#net-style-rules): C# と Visual Basic の両方に適用される規則。</span><span class="sxs-lookup"><span data-stu-id="6beea-106">[.NET style rules](#net-style-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="6beea-107">これらの規則の EditorConfig オプション名は、 `dotnet_style_` prefix で始まります。</span><span class="sxs-lookup"><span data-stu-id="6beea-107">The EditorConfig option names for these rules start with `dotnet_style_` prefix.</span></span>
- <span data-ttu-id="6beea-108">[C# スタイルルール](#c-style-rules): c# 言語に固有の規則。</span><span class="sxs-lookup"><span data-stu-id="6beea-108">[C# style rules](#c-style-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="6beea-109">これらの規則の EditorConfig オプション名は、 `csharp_style_` prefix で始まります。</span><span class="sxs-lookup"><span data-stu-id="6beea-109">The EditorConfig option names for these rules start with `csharp_style_` prefix.</span></span>
- <span data-ttu-id="6beea-110">[Visual Basic スタイルルール](#visual-basic-style-rules): Visual bsic 言語のみに固有の規則。</span><span class="sxs-lookup"><span data-stu-id="6beea-110">[Visual Basic style rules](#visual-basic-style-rules): Rules that are specific to Visual Bsic language only.</span></span> <span data-ttu-id="6beea-111">これらの規則の EditorConfig オプション名は、 `visual_basic_style_` prefix で始まります。</span><span class="sxs-lookup"><span data-stu-id="6beea-111">The EditorConfig option names for these rules start with `visual_basic_style_` prefix.</span></span>

## <a name="option-format"></a><span data-ttu-id="6beea-112">オプションの形式</span><span class="sxs-lookup"><span data-stu-id="6beea-112">Option format</span></span>

<span data-ttu-id="6beea-113">言語ルールのオプションは、次の形式で EditorConfig ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="6beea-113">Options for language rules can be specified in an EditorConfig file with the following format:</span></span>

`option_name = value:severity`

- <span data-ttu-id="6beea-114">**値**: 各言語ルールで、スタイルを優先するかどうかを定義する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6beea-114">**Value**: For each language rule, you specify a value that defines if or when to prefer the style.</span></span> <span data-ttu-id="6beea-115">多くのルールでは、`true` (このスタイルを優先する) または `false` (このスタイルを優先しない) の値が受け付けられます。</span><span class="sxs-lookup"><span data-stu-id="6beea-115">Many rules accept a value of `true` (prefer this style) or `false` (do not prefer this style).</span></span> <span data-ttu-id="6beea-116">それ以外では、`when_on_single_line` や `never` などの値が受け付けられます。</span><span class="sxs-lookup"><span data-stu-id="6beea-116">Other rules accept values such as `when_on_single_line` or `never`.</span></span>
- <span data-ttu-id="6beea-117">**重要度**: ルールの2番目の部分では、ルールの [重大度レベル](../configuration-options.md#severity-level) を指定します。</span><span class="sxs-lookup"><span data-stu-id="6beea-117">**Severity**: The second part of the rule specifies the [severity level](../configuration-options.md#severity-level) for the rule.</span></span> <span data-ttu-id="6beea-118">上記のオプション構文の一部としての重要度の指定は、Visual Studio などの開発 Ide 内でのみ尊重されます。</span><span class="sxs-lookup"><span data-stu-id="6beea-118">Severity specification as part of the above option syntax is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="6beea-119">この設定は、C# または VB コンパイラで認識されないため、ビルド時には尊重されません。</span><span class="sxs-lookup"><span data-stu-id="6beea-119">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="6beea-120">代わりに、ビルドでコードスタイルルールを適用するには、アナライザーのルール ID ベースの重大度構成構文を使用して重大度を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6beea-120">Instead, to enforce code style rules on build, you should set the severity by using the rule ID-based severity configuration syntax for analyzers.</span></span> <span data-ttu-id="6beea-121">この構文では `dotnet_diagnostic.<rule ID>.severity = <severity>` 形式が使用されます。たとえば、`dotnet_diagnostic.IDE0040.severity = silent` のようになります。</span><span class="sxs-lookup"><span data-stu-id="6beea-121">The syntax takes the form `dotnet_diagnostic.<rule ID>.severity = <severity>`, for example, `dotnet_diagnostic.IDE0040.severity = silent`.</span></span> <span data-ttu-id="6beea-122">詳細については、[こちらの GitHub の問題](https://github.com/dotnet/roslyn/issues/44201)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6beea-122">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

> [!TIP]
>
> <span data-ttu-id="6beea-123">Visual Studio 2019 バージョン 16.3 以降、スタイル違反後、[[クイック アクション]](/visualstudio/ide/quick-actions) という電球メニューからコード スタイルの規則を構成できます。</span><span class="sxs-lookup"><span data-stu-id="6beea-123">Starting in Visual Studio 2019 version 16.3, you can configure code style rules from the [Quick Actions](/visualstudio/ide/quick-actions) light bulb menu after a style violation occurs.</span></span> <span data-ttu-id="6beea-124">詳細については、「 [Visual Studio でコードスタイルを自動的に構成する](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6beea-124">For more information, see [Automatically configure code styles in Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span></span>

## <a name="net-style-rules"></a><span data-ttu-id="6beea-125">.NET スタイルルール</span><span class="sxs-lookup"><span data-stu-id="6beea-125">.NET style rules</span></span>

<span data-ttu-id="6beea-126">このセクションのスタイル ルールは、C# および Visual Basic の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6beea-126">The style rules in this section are applicable to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="6beea-127">' this. ' 修飾子と ' Me. ' 修飾子</span><span class="sxs-lookup"><span data-stu-id="6beea-127">'this.' and 'Me.' qualifiers</span></span>](ide0003-ide0009.md)
  - [<span data-ttu-id="6beea-128">dotnet_style_qualification_for_field</span><span class="sxs-lookup"><span data-stu-id="6beea-128">dotnet_style_qualification_for_field</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [<span data-ttu-id="6beea-129">dotnet_style_qualification_for_property</span><span class="sxs-lookup"><span data-stu-id="6beea-129">dotnet_style_qualification_for_property</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [<span data-ttu-id="6beea-130">dotnet_style_qualification_for_method</span><span class="sxs-lookup"><span data-stu-id="6beea-130">dotnet_style_qualification_for_method</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [<span data-ttu-id="6beea-131">dotnet_style_qualification_for_event</span><span class="sxs-lookup"><span data-stu-id="6beea-131">dotnet_style_qualification_for_event</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [<span data-ttu-id="6beea-132">型参照のためのフレームワーク型名の代わりの言語キーワード</span><span class="sxs-lookup"><span data-stu-id="6beea-132">Language keywords instead of framework type names for type references</span></span>](ide0049.md)
  - [<span data-ttu-id="6beea-133">dotnet_style_predefined_type_for_locals_parameters_members</span><span class="sxs-lookup"><span data-stu-id="6beea-133">dotnet_style_predefined_type_for_locals_parameters_members</span></span>](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [<span data-ttu-id="6beea-134">dotnet_style_predefined_type_for_member_access</span><span class="sxs-lookup"><span data-stu-id="6beea-134">dotnet_style_predefined_type_for_member_access</span></span>](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [<span data-ttu-id="6beea-135">修飾子の基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-135">Modifier preferences</span></span>](modifier-preferences.md#net-modifier-preferences)
  - [<span data-ttu-id="6beea-136">dotnet_style_require_accessibility_modifiers</span><span class="sxs-lookup"><span data-stu-id="6beea-136">dotnet_style_require_accessibility_modifiers</span></span>](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [<span data-ttu-id="6beea-137">csharp_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="6beea-137">csharp_preferred_modifier_order</span></span>](ide0036.md#csharp_preferred_modifier_order)
  - [<span data-ttu-id="6beea-138">visual_basic_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="6beea-138">visual_basic_preferred_modifier_order</span></span>](ide0036.md#visual_basic_preferred_modifier_order)
  - [<span data-ttu-id="6beea-139">dotnet_style_readonly_field</span><span class="sxs-lookup"><span data-stu-id="6beea-139">dotnet_style_readonly_field</span></span>](ide0044.md#dotnet_style_readonly_field)
- [<span data-ttu-id="6beea-140">かっこの基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-140">Parentheses preferences</span></span>](ide0047-ide0048.md)
  - [<span data-ttu-id="6beea-141">dotnet_style_parentheses_in_arithmetic_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6beea-141">dotnet_style_parentheses_in_arithmetic_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [<span data-ttu-id="6beea-142">dotnet_style_parentheses_in_relational_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6beea-142">dotnet_style_parentheses_in_relational_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [<span data-ttu-id="6beea-143">dotnet_style_parentheses_in_other_binary_operators</span><span class="sxs-lookup"><span data-stu-id="6beea-143">dotnet_style_parentheses_in_other_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [<span data-ttu-id="6beea-144">dotnet_style_parentheses_in_other_operators</span><span class="sxs-lookup"><span data-stu-id="6beea-144">dotnet_style_parentheses_in_other_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [<span data-ttu-id="6beea-145">式レベル基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-145">Expression-level preferences</span></span>](expression-level-preferences.md#net-expression-level-preferences)
  - [<span data-ttu-id="6beea-146">dotnet_style_object_initializer</span><span class="sxs-lookup"><span data-stu-id="6beea-146">dotnet_style_object_initializer</span></span>](ide0017.md#dotnet_style_object_initializer)
  - [<span data-ttu-id="6beea-147">dotnet_style_collection_initializer</span><span class="sxs-lookup"><span data-stu-id="6beea-147">dotnet_style_collection_initializer</span></span>](ide0028.md#dotnet_style_collection_initializer)
  - [<span data-ttu-id="6beea-148">dotnet_style_explicit_tuple_names</span><span class="sxs-lookup"><span data-stu-id="6beea-148">dotnet_style_explicit_tuple_names</span></span>](ide0033.md#dotnet_style_explicit_tuple_names)
  - [<span data-ttu-id="6beea-149">dotnet_style_prefer_inferred_tuple_names</span><span class="sxs-lookup"><span data-stu-id="6beea-149">dotnet_style_prefer_inferred_tuple_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [<span data-ttu-id="6beea-150">dotnet_style_prefer_inferred_anonymous_type_member_names</span><span class="sxs-lookup"><span data-stu-id="6beea-150">dotnet_style_prefer_inferred_anonymous_type_member_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [<span data-ttu-id="6beea-151">dotnet_style_prefer_auto_properties</span><span class="sxs-lookup"><span data-stu-id="6beea-151">dotnet_style_prefer_auto_properties</span></span>](ide0032.md#dotnet_style_prefer_auto_properties)
  - [<span data-ttu-id="6beea-152">dotnet_style_prefer_conditional_expression_over_assignment</span><span class="sxs-lookup"><span data-stu-id="6beea-152">dotnet_style_prefer_conditional_expression_over_assignment</span></span>](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [<span data-ttu-id="6beea-153">dotnet_style_prefer_conditional_expression_over_return</span><span class="sxs-lookup"><span data-stu-id="6beea-153">dotnet_style_prefer_conditional_expression_over_return</span></span>](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [<span data-ttu-id="6beea-154">dotnet_style_prefer_compound_assignment</span><span class="sxs-lookup"><span data-stu-id="6beea-154">dotnet_style_prefer_compound_assignment</span></span>](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [<span data-ttu-id="6beea-155">dotnet_style_prefer_simplified_interpolation</span><span class="sxs-lookup"><span data-stu-id="6beea-155">dotnet_style_prefer_simplified_interpolation</span></span>](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [<span data-ttu-id="6beea-156">dotnet_style_prefer_simplified_boolean_expressions</span><span class="sxs-lookup"><span data-stu-id="6beea-156">dotnet_style_prefer_simplified_boolean_expressions</span></span>](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - <span data-ttu-id="6beea-157">[見つからないケースを switch ステートメントに追加](ide0010.md) します-このルールにはコードスタイルオプションがありません。</span><span class="sxs-lookup"><span data-stu-id="6beea-157">[Add missing cases to switch statement](ide0010.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="6beea-158">[匿名型からタプルへの変換](ide0050.md) -このルールにはコードスタイルオプションがありません。</span><span class="sxs-lookup"><span data-stu-id="6beea-158">[Convert anonymous type to tuple](ide0050.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="6beea-159">[' ハッシュコード ' を使用](ide0070.md) してください-このルールにはコードスタイルオプションがありません。</span><span class="sxs-lookup"><span data-stu-id="6beea-159">[Use 'System.HashCode.Combine'](ide0070.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="6beea-160">[' Typeof ' を ' 文字列型 ' に変換](ide0082.md) します。このルールにはコードスタイルオプションがありません。</span><span class="sxs-lookup"><span data-stu-id="6beea-160">[Convert 'typeof' to 'nameof'](ide0082.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="6beea-161">"Null" 検査設定</span><span class="sxs-lookup"><span data-stu-id="6beea-161">Null-checking preferences</span></span>](null-checking-preferences.md#net-null-checking-preferences)
  - [<span data-ttu-id="6beea-162">dotnet_style_coalesce_expression</span><span class="sxs-lookup"><span data-stu-id="6beea-162">dotnet_style_coalesce_expression</span></span>](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [<span data-ttu-id="6beea-163">dotnet_style_null_propagation</span><span class="sxs-lookup"><span data-stu-id="6beea-163">dotnet_style_null_propagation</span></span>](ide0031.md#dotnet_style_null_propagation)
  - [<span data-ttu-id="6beea-164">dotnet_style_prefer_is_null_check_over_reference_equality_method</span><span class="sxs-lookup"><span data-stu-id="6beea-164">dotnet_style_prefer_is_null_check_over_reference_equality_method</span></span>](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [<span data-ttu-id="6beea-165">ファイル ヘッダーの基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-165">File header preferences</span></span>](ide0073.md)
  - [<span data-ttu-id="6beea-166">file_header_template</span><span class="sxs-lookup"><span data-stu-id="6beea-166">file_header_template</span></span>](ide0073.md#file_header_template)

## <a name="c-style-rules"></a><span data-ttu-id="6beea-167">C# スタイル規則</span><span class="sxs-lookup"><span data-stu-id="6beea-167">C# style rules</span></span>

<span data-ttu-id="6beea-168">このセクションのスタイルルールは、C# 言語にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="6beea-168">The style rules in this section are applicable to C# language only.</span></span>

- [<span data-ttu-id="6beea-169">' var ' の設定</span><span class="sxs-lookup"><span data-stu-id="6beea-169">'var' preferences</span></span>](ide0007-ide0008.md)
  - [<span data-ttu-id="6beea-170">csharp_style_var_for_built_in_types</span><span class="sxs-lookup"><span data-stu-id="6beea-170">csharp_style_var_for_built_in_types</span></span>](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [<span data-ttu-id="6beea-171">csharp_style_var_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="6beea-171">csharp_style_var_when_type_is_apparent</span></span>](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [<span data-ttu-id="6beea-172">csharp_style_var_elsewhere</span><span class="sxs-lookup"><span data-stu-id="6beea-172">csharp_style_var_elsewhere</span></span>](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [<span data-ttu-id="6beea-173">式形式のメンバー</span><span class="sxs-lookup"><span data-stu-id="6beea-173">Expression-bodied members</span></span>](expression-bodied-members.md)
  - [<span data-ttu-id="6beea-174">csharp_style_expression_bodied_methods</span><span class="sxs-lookup"><span data-stu-id="6beea-174">csharp_style_expression_bodied_methods</span></span>](ide0022.md#csharp_style_expression_bodied_methods)
  - [<span data-ttu-id="6beea-175">csharp_style_expression_bodied_constructors</span><span class="sxs-lookup"><span data-stu-id="6beea-175">csharp_style_expression_bodied_constructors</span></span>](ide0021.md#csharp_style_expression_bodied_constructors)
  - [<span data-ttu-id="6beea-176">csharp_style_expression_bodied_operators</span><span class="sxs-lookup"><span data-stu-id="6beea-176">csharp_style_expression_bodied_operators</span></span>](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [<span data-ttu-id="6beea-177">csharp_style_expression_bodied_properties</span><span class="sxs-lookup"><span data-stu-id="6beea-177">csharp_style_expression_bodied_properties</span></span>](ide0025.md#csharp_style_expression_bodied_properties)
  - [<span data-ttu-id="6beea-178">csharp_style_expression_bodied_indexers</span><span class="sxs-lookup"><span data-stu-id="6beea-178">csharp_style_expression_bodied_indexers</span></span>](ide0026.md#csharp_style_expression_bodied_indexers)
  - [<span data-ttu-id="6beea-179">csharp_style_expression_bodied_accessors</span><span class="sxs-lookup"><span data-stu-id="6beea-179">csharp_style_expression_bodied_accessors</span></span>](ide0027.md#csharp_style_expression_bodied_accessors)
  - [<span data-ttu-id="6beea-180">csharp_style_expression_bodied_lambdas</span><span class="sxs-lookup"><span data-stu-id="6beea-180">csharp_style_expression_bodied_lambdas</span></span>](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [<span data-ttu-id="6beea-181">csharp_style_expression_bodied_local_functions</span><span class="sxs-lookup"><span data-stu-id="6beea-181">csharp_style_expression_bodied_local_functions</span></span>](ide0061.md#csharp_style_expression_bodied_local_functions)
- [<span data-ttu-id="6beea-182">パターン マッチング設定</span><span class="sxs-lookup"><span data-stu-id="6beea-182">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="6beea-183">csharp_style_pattern_matching_over_is_with_cast_check</span><span class="sxs-lookup"><span data-stu-id="6beea-183">csharp_style_pattern_matching_over_is_with_cast_check</span></span>](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [<span data-ttu-id="6beea-184">csharp_style_pattern_matching_over_as_with_null_check</span><span class="sxs-lookup"><span data-stu-id="6beea-184">csharp_style_pattern_matching_over_as_with_null_check</span></span>](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [<span data-ttu-id="6beea-185">csharp_style_prefer_switch_expression</span><span class="sxs-lookup"><span data-stu-id="6beea-185">csharp_style_prefer_switch_expression</span></span>](ide0066.md#csharp_style_prefer_switch_expression)
  - [<span data-ttu-id="6beea-186">csharp_style_prefer_pattern_matching</span><span class="sxs-lookup"><span data-stu-id="6beea-186">csharp_style_prefer_pattern_matching</span></span>](ide0078.md#csharp_style_prefer_pattern_matching)
  - [<span data-ttu-id="6beea-187">csharp_style_prefer_not_pattern</span><span class="sxs-lookup"><span data-stu-id="6beea-187">csharp_style_prefer_not_pattern</span></span>](ide0083.md#csharp_style_prefer_not_pattern)
- [<span data-ttu-id="6beea-188">式レベル基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-188">Expression-level preferences</span></span>](expression-level-preferences.md#c-expression-level-preferences)
  - [<span data-ttu-id="6beea-189">csharp_style_inlined_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="6beea-189">csharp_style_inlined_variable_declaration</span></span>](ide0018.md#csharp_style_inlined_variable_declaration)
  - [<span data-ttu-id="6beea-190">csharp_prefer_simple_default_expression</span><span class="sxs-lookup"><span data-stu-id="6beea-190">csharp_prefer_simple_default_expression</span></span>](ide0034.md#csharp_prefer_simple_default_expression)
  - [<span data-ttu-id="6beea-191">csharp_style_pattern_local_over_anonymous_function</span><span class="sxs-lookup"><span data-stu-id="6beea-191">csharp_style_pattern_local_over_anonymous_function</span></span>](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [<span data-ttu-id="6beea-192">csharp_style_deconstructed_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="6beea-192">csharp_style_deconstructed_variable_declaration</span></span>](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [<span data-ttu-id="6beea-193">csharp_style_prefer_index_operator</span><span class="sxs-lookup"><span data-stu-id="6beea-193">csharp_style_prefer_index_operator</span></span>](ide0056.md#csharp_style_prefer_index_operator)
  - [<span data-ttu-id="6beea-194">csharp_style_prefer_range_operator</span><span class="sxs-lookup"><span data-stu-id="6beea-194">csharp_style_prefer_range_operator</span></span>](ide0057.md#csharp_style_prefer_range_operator)
  - [<span data-ttu-id="6beea-195">csharp_style_implicit_object_creation_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="6beea-195">csharp_style_implicit_object_creation_when_type_is_apparent</span></span>](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - <span data-ttu-id="6beea-196">[不足しているケースを追加して式を切り替え](ide0072.md) ます-このルールにはコードスタイルオプションがありません。</span><span class="sxs-lookup"><span data-stu-id="6beea-196">[Add missing cases to switch expression](ide0072.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="6beea-197">"null" チェック設定</span><span class="sxs-lookup"><span data-stu-id="6beea-197">"Null" checking preferences</span></span>](null-checking-preferences.md#c-null-checking-preferences)
  - [<span data-ttu-id="6beea-198">csharp_style_throw_expression</span><span class="sxs-lookup"><span data-stu-id="6beea-198">csharp_style_throw_expression</span></span>](ide0016.md#csharp_style_throw_expression)
  - [<span data-ttu-id="6beea-199">csharp_style_conditional_delegate_call</span><span class="sxs-lookup"><span data-stu-id="6beea-199">csharp_style_conditional_delegate_call</span></span>](ide1005.md#csharp_style_conditional_delegate_call)
- [<span data-ttu-id="6beea-200">コード ブロック基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-200">Code block preferences</span></span>](code-block-preferences.md)
  - [<span data-ttu-id="6beea-201">csharp_prefer_braces</span><span class="sxs-lookup"><span data-stu-id="6beea-201">csharp_prefer_braces</span></span>](ide0011.md#csharp_prefer_braces)
  - [<span data-ttu-id="6beea-202">csharp_prefer_simple_using_statement</span><span class="sxs-lookup"><span data-stu-id="6beea-202">csharp_prefer_simple_using_statement</span></span>](ide0063.md#csharp_prefer_simple_using_statement)
- [<span data-ttu-id="6beea-203">' using ' ディレクティブの基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-203">'using' directive preferences</span></span>](ide0065.md)
  - [<span data-ttu-id="6beea-204">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="6beea-204">csharp_using_directive_placement</span></span>](ide0065.md#csharp_using_directive_placement)
- [<span data-ttu-id="6beea-205">修飾子の基本設定</span><span class="sxs-lookup"><span data-stu-id="6beea-205">Modifier preferences</span></span>](modifier-preferences.md#c-modifier-preferences)
  - [<span data-ttu-id="6beea-206">csharp_prefer_static_local_function</span><span class="sxs-lookup"><span data-stu-id="6beea-206">csharp_prefer_static_local_function</span></span>](ide0062.md#csharp_prefer_static_local_function)
  - <span data-ttu-id="6beea-207">[構造体のフィールドを書き込み可能](ide0064.md) にします。この規則にはコードスタイルオプションがありません。</span><span class="sxs-lookup"><span data-stu-id="6beea-207">[Make struct fields writable](ide0064.md) - This rule has no code style option.</span></span>

## <a name="visual-basic-style-rules"></a><span data-ttu-id="6beea-208">Visual Basic スタイルルール</span><span class="sxs-lookup"><span data-stu-id="6beea-208">Visual Basic style rules</span></span>

<span data-ttu-id="6beea-209">このセクションのスタイルルールは Visual Basic 言語にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="6beea-209">The style rules in this section are applicable to Visual Basic language only.</span></span>

- [<span data-ttu-id="6beea-210">パターン マッチング設定</span><span class="sxs-lookup"><span data-stu-id="6beea-210">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="6beea-211">visual_basic_style_prefer_isnot_expression</span><span class="sxs-lookup"><span data-stu-id="6beea-211">visual_basic_style_prefer_isnot_expression</span></span>](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a><span data-ttu-id="6beea-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="6beea-212">See also</span></span>

- [<span data-ttu-id="6beea-213">不要なコード規則</span><span class="sxs-lookup"><span data-stu-id="6beea-213">Unnecessary code rules</span></span>](unnecessary-code-rules.md)
- [<span data-ttu-id="6beea-214">書式設定規則</span><span class="sxs-lookup"><span data-stu-id="6beea-214">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="6beea-215">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="6beea-215">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="6beea-216">.NET コードスタイル規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="6beea-216">.NET code style rules reference</span></span>](index.md)
