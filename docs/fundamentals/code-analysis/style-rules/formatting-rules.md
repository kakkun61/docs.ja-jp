---
title: コードスタイルの書式規則
description: インデント、スペース、および改行を書式設定するためのコードスタイル規則について説明します。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE0055
- formatting rules
helpviewer_keywords:
- IDE0055
- formatting code style rules [EditorConfig]
- formatting rules
- EditorConfig formatting conventions
ms.openlocfilehash: 61e6f6a6afdc6aaf9710eef3143af8ae700ef612
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "96591727"
---
# <a name="formatting-rules"></a><span data-ttu-id="21cce-103">書式設定規則</span><span class="sxs-lookup"><span data-stu-id="21cce-103">Formatting rules</span></span>

<span data-ttu-id="21cce-104">書式設定規則は、.NET プログラミング言語の構造に合わせてインデント、スペース、および改行を揃える方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="21cce-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="21cce-105">規則は次のカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="21cce-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="21cce-106">[.Net 書式設定規則](#net-formatting-rules): C# と Visual Basic の両方に適用される規則。</span><span class="sxs-lookup"><span data-stu-id="21cce-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="21cce-107">これらの規則の EditorConfig オプション名は、 `dotnet_` prefix で始まります。</span><span class="sxs-lookup"><span data-stu-id="21cce-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="21cce-108">[C# の書式規則](#c-formatting-rules): c# 言語に固有の規則。</span><span class="sxs-lookup"><span data-stu-id="21cce-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="21cce-109">これらの規則の EditorConfig オプション名は、 `csharp_` prefix で始まります。</span><span class="sxs-lookup"><span data-stu-id="21cce-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="21cce-110">ルール ID: "IDE0055" (書式設定の修正)</span><span class="sxs-lookup"><span data-stu-id="21cce-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="21cce-111">すべての書式設定オプションには、ルール ID `IDE0055` とタイトルがあり `Fix formatting` ます。</span><span class="sxs-lookup"><span data-stu-id="21cce-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="21cce-112">次の構成行を使用して、EditorConfig ファイルの形式違反の重大度を設定します。</span><span class="sxs-lookup"><span data-stu-id="21cce-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="21cce-113">重大度値は、 `warning` `error` [ビルドで適用](../overview.md#code-style-analysis)される必要があります。</span><span class="sxs-lookup"><span data-stu-id="21cce-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="21cce-114">可能なすべての重要度の値については、「 [重大度レベル](../configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21cce-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="21cce-115">オプションの形式</span><span class="sxs-lookup"><span data-stu-id="21cce-115">Option format</span></span>

<span data-ttu-id="21cce-116">書式設定規則のオプションは、EditorConfig ファイルで次の形式で指定できます。</span><span class="sxs-lookup"><span data-stu-id="21cce-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="21cce-117">多くのルールでは、`value` に対して `true` (このスタイルを優先する) または `false` (このスタイルを優先しない) を指定します。</span><span class="sxs-lookup"><span data-stu-id="21cce-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="21cce-118">他のルールでは、`flush_left` や `before_and_after` のような値を指定して、ルールを適用する状況と場所を記述します。</span><span class="sxs-lookup"><span data-stu-id="21cce-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="21cce-119">重要度は指定しません。</span><span class="sxs-lookup"><span data-stu-id="21cce-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="21cce-120">.NET の書式規則</span><span class="sxs-lookup"><span data-stu-id="21cce-120">.NET formatting rules</span></span>

<span data-ttu-id="21cce-121">このセクションの書式ルールは、C# と Visual Basic の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="21cce-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="21cce-122">using の整理</span><span class="sxs-lookup"><span data-stu-id="21cce-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="21cce-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="21cce-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="21cce-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="21cce-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="21cce-125">using ディレクティブの整理</span><span class="sxs-lookup"><span data-stu-id="21cce-125">Organize using directives</span></span>

<span data-ttu-id="21cce-126">これらの書式ルールは、`using` ディレクティブと `Imports` ステートメントの並べ替えと表示に関係します。</span><span class="sxs-lookup"><span data-stu-id="21cce-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="21cce-127">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="21cce-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="21cce-128">dotnet\_sort\_system\_directives_first</span><span class="sxs-lookup"><span data-stu-id="21cce-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="21cce-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-129">Property</span></span>|<span data-ttu-id="21cce-130">値</span><span class="sxs-lookup"><span data-stu-id="21cce-130">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-131">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-131">**Option name**</span></span> | <span data-ttu-id="21cce-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="21cce-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="21cce-133">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-133">**Applicable languages**</span></span> | <span data-ttu-id="21cce-134">C# および Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21cce-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="21cce-135">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-135">**Introduced version**</span></span> | <span data-ttu-id="21cce-136">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-137">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-137">**Option values**</span></span> | <span data-ttu-id="21cce-138">`true` - `System.*` `using` ディレクティブをアルファベット順に並べ替え、他の using ディレクティブの前に配置します。</span><span class="sxs-lookup"><span data-stu-id="21cce-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="21cce-139">`false` - `System.*` `using` ディレクティブを他のディレクティブの前に配置しないで `using` ください。</span><span class="sxs-lookup"><span data-stu-id="21cce-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="21cce-140">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-140">Code examples:</span></span>

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="21cce-141">dotnet\_separate\_import\_directive\_groups</span><span class="sxs-lookup"><span data-stu-id="21cce-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="21cce-142">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-142">Property</span></span>|<span data-ttu-id="21cce-143">値</span><span class="sxs-lookup"><span data-stu-id="21cce-143">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-144">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-144">**Option name**</span></span> | <span data-ttu-id="21cce-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="21cce-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="21cce-146">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-146">**Applicable languages**</span></span> | <span data-ttu-id="21cce-147">C# および Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21cce-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="21cce-148">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-148">**Introduced version**</span></span> | <span data-ttu-id="21cce-149">Visual Studio 2017 バージョン 15.5</span><span class="sxs-lookup"><span data-stu-id="21cce-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="21cce-150">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-150">**Option values**</span></span> | <span data-ttu-id="21cce-151">`true` - `using` ディレクティブ グループの間に空白行を配置します。</span><span class="sxs-lookup"><span data-stu-id="21cce-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="21cce-152">`false` - `using` ディレクティブ グループの間に空白行を配置しません。</span><span class="sxs-lookup"><span data-stu-id="21cce-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="21cce-153">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-153">Code examples:</span></span>

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-rules"></a><span data-ttu-id="21cce-154">C# の書式規則</span><span class="sxs-lookup"><span data-stu-id="21cce-154">C# formatting rules</span></span>

<span data-ttu-id="21cce-155">このセクションの書式ルールは、C# コードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="21cce-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="21cce-156">改行オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="21cce-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="21cce-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="21cce-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="21cce-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="21cce-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="21cce-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="21cce-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="21cce-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="21cce-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="21cce-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="21cce-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="21cce-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="21cce-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="21cce-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="21cce-164">インデント オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="21cce-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="21cce-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="21cce-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="21cce-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="21cce-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="21cce-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="21cce-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="21cce-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="21cce-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="21cce-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="21cce-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="21cce-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="21cce-171">スペース オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="21cce-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="21cce-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="21cce-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="21cce-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="21cce-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="21cce-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="21cce-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="21cce-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="21cce-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="21cce-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="21cce-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="21cce-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="21cce-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="21cce-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="21cce-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="21cce-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="21cce-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="21cce-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="21cce-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="21cce-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="21cce-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="21cce-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="21cce-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="21cce-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="21cce-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="21cce-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="21cce-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="21cce-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="21cce-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="21cce-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="21cce-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="21cce-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="21cce-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="21cce-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="21cce-194">折り返しオプション</span><span class="sxs-lookup"><span data-stu-id="21cce-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="21cce-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="21cce-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="21cce-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="21cce-197">using ディレクティブ オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="21cce-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="21cce-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="21cce-199">改行オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-199">New-line options</span></span>

<span data-ttu-id="21cce-200">これらの書式ルールは、コードの書式を設定する場合の改行の使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="21cce-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="21cce-201">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="21cce-201">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="21cce-202">csharp\_new\_line\_before\_open_brace</span><span class="sxs-lookup"><span data-stu-id="21cce-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="21cce-203">このルールは、左中かっこ (`{`) を前のコードと同じ行に配置するか、新しい行に配置するかに関するものです。</span><span class="sxs-lookup"><span data-stu-id="21cce-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="21cce-204">このルールでは、**all**、**none**、または **methods** や **properties** などの 1 つ以上のコード要素を指定して、このルールを適用する必要があるタイミングを定義します。</span><span class="sxs-lookup"><span data-stu-id="21cce-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="21cce-205">複数のコード要素を指定するには、コンマ (,) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="21cce-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="21cce-206">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-206">Property</span></span>|<span data-ttu-id="21cce-207">値</span><span class="sxs-lookup"><span data-stu-id="21cce-207">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-208">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-208">**Option name**</span></span> | <span data-ttu-id="21cce-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="21cce-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="21cce-210">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-210">**Applicable languages**</span></span> | <span data-ttu-id="21cce-211">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-211">C#</span></span> |
| <span data-ttu-id="21cce-212">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-212">**Introduced version**</span></span> | <span data-ttu-id="21cce-213">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-214">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-214">**Option values**</span></span> | <span data-ttu-id="21cce-215">`all` - 中かっこはすべての式の新しい行に配置する必要があります ("Allman" スタイル)。</span><span class="sxs-lookup"><span data-stu-id="21cce-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="21cce-216">`none` - 中かっこはすべての式の同じ行に配置する必要があります ("K&R")。</span><span class="sxs-lookup"><span data-stu-id="21cce-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="21cce-217">`accessors`、`anonymous_methods`、`anonymous_types`、`control_blocks`、`events`、`indexers`、`lambdas`、`local_functions`、`methods`、`object_collection_array_initializers`、`properties`、`types` - 中かっこは指定されたコード要素の新しい行に配置する必要があります ("Allman" スタイル)。</span><span class="sxs-lookup"><span data-stu-id="21cce-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="21cce-218">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-218">Code examples:</span></span>

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="21cce-219">csharp\_new\_line\_before_else</span><span class="sxs-lookup"><span data-stu-id="21cce-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="21cce-220">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-220">Property</span></span>|<span data-ttu-id="21cce-221">値</span><span class="sxs-lookup"><span data-stu-id="21cce-221">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-222">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-222">**Option name**</span></span> | <span data-ttu-id="21cce-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="21cce-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="21cce-224">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-224">**Applicable languages**</span></span> | <span data-ttu-id="21cce-225">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-225">C#</span></span> |
| <span data-ttu-id="21cce-226">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-226">**Introduced version**</span></span> | <span data-ttu-id="21cce-227">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-228">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-228">**Option values**</span></span> | <span data-ttu-id="21cce-229">`true` - 新しい行に `else` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="21cce-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="21cce-230">`false` - 同じ行に `else` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="21cce-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="21cce-231">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-231">Code examples:</span></span>

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="21cce-232">csharp\_new\_line\_before_catch</span><span class="sxs-lookup"><span data-stu-id="21cce-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="21cce-233">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-233">Property</span></span>|<span data-ttu-id="21cce-234">値</span><span class="sxs-lookup"><span data-stu-id="21cce-234">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-235">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-235">**Option name**</span></span> | <span data-ttu-id="21cce-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="21cce-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="21cce-237">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-237">**Applicable languages**</span></span> | <span data-ttu-id="21cce-238">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-238">C#</span></span> |
| <span data-ttu-id="21cce-239">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-239">**Introduced version**</span></span> | <span data-ttu-id="21cce-240">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-241">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-241">**Option values**</span></span> | <span data-ttu-id="21cce-242">`true` - 新しい行に `catch` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="21cce-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="21cce-243">`false` - 同じ行に `catch` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="21cce-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="21cce-244">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-244">Code examples:</span></span>

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="21cce-245">csharp\_new\_line\_before_finally</span><span class="sxs-lookup"><span data-stu-id="21cce-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="21cce-246">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-246">Property</span></span>|<span data-ttu-id="21cce-247">値</span><span class="sxs-lookup"><span data-stu-id="21cce-247">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-248">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-248">**Option name**</span></span> | <span data-ttu-id="21cce-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="21cce-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="21cce-250">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-250">**Applicable languages**</span></span> | <span data-ttu-id="21cce-251">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-251">C#</span></span> |
| <span data-ttu-id="21cce-252">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-252">**Introduced version**</span></span> | <span data-ttu-id="21cce-253">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-254">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-254">**Option values**</span></span> | <span data-ttu-id="21cce-255">`true` - `finally` ステートメントを右中かっこの後の新しい行に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21cce-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="21cce-256">`false` - `finally` ステートメントを右中かっこと同じ行に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21cce-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="21cce-257">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-257">Code examples:</span></span>

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="21cce-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span><span class="sxs-lookup"><span data-stu-id="21cce-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="21cce-259">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-259">Property</span></span>|<span data-ttu-id="21cce-260">値</span><span class="sxs-lookup"><span data-stu-id="21cce-260">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-261">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-261">**Option name**</span></span> | <span data-ttu-id="21cce-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="21cce-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="21cce-263">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-263">**Applicable languages**</span></span> | <span data-ttu-id="21cce-264">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-264">C#</span></span> |
| <span data-ttu-id="21cce-265">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-265">**Introduced version**</span></span> | <span data-ttu-id="21cce-266">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-267">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-267">**Option values**</span></span> | <span data-ttu-id="21cce-268">`true` - オブジェクト初期化子のメンバーを別の行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="21cce-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="21cce-269">`false` - オブジェクト初期化子のメンバーを同じ行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="21cce-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="21cce-270">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-270">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="21cce-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="21cce-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="21cce-272">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-272">Property</span></span>|<span data-ttu-id="21cce-273">値</span><span class="sxs-lookup"><span data-stu-id="21cce-273">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-274">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-274">**Option name**</span></span> | <span data-ttu-id="21cce-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="21cce-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="21cce-276">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-276">**Applicable languages**</span></span> | <span data-ttu-id="21cce-277">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-277">C#</span></span> |
| <span data-ttu-id="21cce-278">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-278">**Introduced version**</span></span> | <span data-ttu-id="21cce-279">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-280">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-280">**Option values**</span></span> | <span data-ttu-id="21cce-281">`true` - 匿名型のメンバーを別の行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="21cce-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="21cce-282">`false` - 匿名型のメンバーを同じ行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="21cce-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="21cce-283">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-283">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="21cce-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="21cce-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="21cce-285">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-285">Property</span></span>|<span data-ttu-id="21cce-286">値</span><span class="sxs-lookup"><span data-stu-id="21cce-286">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-287">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-287">**Option name**</span></span> | <span data-ttu-id="21cce-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="21cce-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="21cce-289">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-289">**Applicable languages**</span></span> | <span data-ttu-id="21cce-290">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-290">C#</span></span> |
| <span data-ttu-id="21cce-291">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-291">**Introduced version**</span></span> | <span data-ttu-id="21cce-292">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-293">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-293">**Option values**</span></span> | <span data-ttu-id="21cce-294">`true` - クエリ式の句の要素を別の行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="21cce-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="21cce-295">`false` - クエリ式の句の要素を同じ行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="21cce-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="21cce-296">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="21cce-297">インデント オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-297">Indentation options</span></span>

<span data-ttu-id="21cce-298">これらの書式ルールは、コードの書式を設定する場合のインデントの使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="21cce-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="21cce-299">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="21cce-299">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="21cce-300">csharp\_indent\_case_contents</span><span class="sxs-lookup"><span data-stu-id="21cce-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="21cce-301">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-301">Property</span></span>|<span data-ttu-id="21cce-302">値</span><span class="sxs-lookup"><span data-stu-id="21cce-302">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-303">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-303">**Option name**</span></span> | <span data-ttu-id="21cce-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="21cce-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="21cce-305">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-305">**Applicable languages**</span></span> | <span data-ttu-id="21cce-306">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-306">C#</span></span> |
| <span data-ttu-id="21cce-307">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-307">**Introduced version**</span></span> | <span data-ttu-id="21cce-308">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-309">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-309">**Option values**</span></span> | <span data-ttu-id="21cce-310">`true` - `switch` ケース コンテンツにインデントを付けます</span><span class="sxs-lookup"><span data-stu-id="21cce-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="21cce-311">`false` - `switch` ケース コンテンツにインデントを付けません</span><span class="sxs-lookup"><span data-stu-id="21cce-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="21cce-312">このルールが **true** に設定されている場合は、i。</span><span class="sxs-lookup"><span data-stu-id="21cce-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="21cce-313">このルールが **false** に設定されている場合は、d。</span><span class="sxs-lookup"><span data-stu-id="21cce-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="21cce-314">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-314">Code examples:</span></span>

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="21cce-315">csharp\_indent\_switch_labels</span><span class="sxs-lookup"><span data-stu-id="21cce-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="21cce-316">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-316">Property</span></span>|<span data-ttu-id="21cce-317">値</span><span class="sxs-lookup"><span data-stu-id="21cce-317">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-318">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-318">**Option name**</span></span> | <span data-ttu-id="21cce-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="21cce-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="21cce-320">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-320">**Applicable languages**</span></span> | <span data-ttu-id="21cce-321">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-321">C#</span></span> |
| <span data-ttu-id="21cce-322">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-322">**Introduced version**</span></span> | <span data-ttu-id="21cce-323">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-324">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-324">**Option values**</span></span> | <span data-ttu-id="21cce-325">`true` - `switch` ラベルをインデントします</span><span class="sxs-lookup"><span data-stu-id="21cce-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="21cce-326">`false` - `switch` ラベルをインデントしません</span><span class="sxs-lookup"><span data-stu-id="21cce-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="21cce-327">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-327">Code examples:</span></span>

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a><span data-ttu-id="21cce-328">csharp\_indent_labels</span><span class="sxs-lookup"><span data-stu-id="21cce-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="21cce-329">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-329">Property</span></span>|<span data-ttu-id="21cce-330">値</span><span class="sxs-lookup"><span data-stu-id="21cce-330">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-331">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-331">**Option name**</span></span> | <span data-ttu-id="21cce-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="21cce-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="21cce-333">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-333">**Applicable languages**</span></span> | <span data-ttu-id="21cce-334">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-334">C#</span></span> |
| <span data-ttu-id="21cce-335">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-335">**Introduced version**</span></span> | <span data-ttu-id="21cce-336">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-337">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-337">**Option values**</span></span> | <span data-ttu-id="21cce-338">`flush_left` - ラベルは左端の列に配置されます</span><span class="sxs-lookup"><span data-stu-id="21cce-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="21cce-339">`one_less_than_current` - ラベルは、現在のコンテキストのインデントを 1 つ減らした位置に配置されます</span><span class="sxs-lookup"><span data-stu-id="21cce-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="21cce-340">`no_change` - ラベルは、現在のコンテキストと同じインデントで配置されます</span><span class="sxs-lookup"><span data-stu-id="21cce-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="21cce-341">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-341">Code examples:</span></span>

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="21cce-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="21cce-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="21cce-343">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-343">Property</span></span>|<span data-ttu-id="21cce-344">値</span><span class="sxs-lookup"><span data-stu-id="21cce-344">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-345">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-345">**Option name**</span></span> | <span data-ttu-id="21cce-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="21cce-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="21cce-347">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-347">**Applicable languages**</span></span> | <span data-ttu-id="21cce-348">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-348">C#</span></span> |
| <span data-ttu-id="21cce-349">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="21cce-350">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-350">Code examples:</span></span>

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a><span data-ttu-id="21cce-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="21cce-351">csharp_indent_braces</span></span>

|<span data-ttu-id="21cce-352">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-352">Property</span></span>|<span data-ttu-id="21cce-353">値</span><span class="sxs-lookup"><span data-stu-id="21cce-353">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-354">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-354">**Option name**</span></span> | <span data-ttu-id="21cce-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="21cce-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="21cce-356">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-356">**Applicable languages**</span></span> | <span data-ttu-id="21cce-357">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-357">C#</span></span> |
| <span data-ttu-id="21cce-358">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="21cce-359">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-359">Code examples:</span></span>

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="21cce-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="21cce-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="21cce-361">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-361">Property</span></span>|<span data-ttu-id="21cce-362">値</span><span class="sxs-lookup"><span data-stu-id="21cce-362">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-363">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-363">**Option name**</span></span> | <span data-ttu-id="21cce-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="21cce-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="21cce-365">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-365">**Applicable languages**</span></span> | <span data-ttu-id="21cce-366">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-366">C#</span></span> |
| <span data-ttu-id="21cce-367">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="21cce-368">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-368">Code examples:</span></span>

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a><span data-ttu-id="21cce-369">スペース オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-369">Spacing options</span></span>

<span data-ttu-id="21cce-370">これらの書式ルールは、コードの書式を設定する場合の空白文字の使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="21cce-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="21cce-371">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="21cce-371">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="21cce-372">csharp\_space\_after_cast</span><span class="sxs-lookup"><span data-stu-id="21cce-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="21cce-373">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-373">Property</span></span>|<span data-ttu-id="21cce-374">値</span><span class="sxs-lookup"><span data-stu-id="21cce-374">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-375">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-375">**Option name**</span></span> | <span data-ttu-id="21cce-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="21cce-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="21cce-377">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-377">**Applicable languages**</span></span> | <span data-ttu-id="21cce-378">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-378">C#</span></span> |
| <span data-ttu-id="21cce-379">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-379">**Introduced version**</span></span> | <span data-ttu-id="21cce-380">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-381">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-381">**Option values**</span></span> | <span data-ttu-id="21cce-382">`true` - キャストと値の間に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="21cce-383">`false` - キャストと値の間の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="21cce-384">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="21cce-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="21cce-386">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-386">Property</span></span>|<span data-ttu-id="21cce-387">値</span><span class="sxs-lookup"><span data-stu-id="21cce-387">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-388">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-388">**Option name**</span></span> | <span data-ttu-id="21cce-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="21cce-390">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-390">**Applicable languages**</span></span> | <span data-ttu-id="21cce-391">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-391">C#</span></span> |
| <span data-ttu-id="21cce-392">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-392">**Introduced version**</span></span> | <span data-ttu-id="21cce-393">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-394">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-394">**Option values**</span></span> | <span data-ttu-id="21cce-395">`true` - `for` ループなど、制御フロー ステートメントのキーワードの後に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="21cce-396">`false` - `for` ループなど、制御フロー ステートメントのキーワードの後の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="21cce-397">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="21cce-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="21cce-399">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-399">Property</span></span>|<span data-ttu-id="21cce-400">値</span><span class="sxs-lookup"><span data-stu-id="21cce-400">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-401">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-401">**Option name**</span></span> | <span data-ttu-id="21cce-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="21cce-403">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-403">**Applicable languages**</span></span> | <span data-ttu-id="21cce-404">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-404">C#</span></span> |
| <span data-ttu-id="21cce-405">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-405">**Introduced version**</span></span> | <span data-ttu-id="21cce-406">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-407">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-407">**Option values**</span></span> | <span data-ttu-id="21cce-408">`control_flow_statements` - 制御フロー ステートメントのかっこの間にスペースを配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="21cce-409">`expressions` - 式のかっこの間にスペースを配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="21cce-410">`type_casts` - 型キャストのかっこの間にスペースを配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="21cce-411">このルールを省略するか、`control_flow_statements`、`expressions`、または `type_casts` 以外の値を使用する場合、設定は適用されません。</span><span class="sxs-lookup"><span data-stu-id="21cce-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="21cce-412">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="21cce-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="21cce-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="21cce-414">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-414">Property</span></span>|<span data-ttu-id="21cce-415">値</span><span class="sxs-lookup"><span data-stu-id="21cce-415">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-416">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-416">**Option name**</span></span> | <span data-ttu-id="21cce-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="21cce-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="21cce-418">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-418">**Applicable languages**</span></span> | <span data-ttu-id="21cce-419">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-419">C#</span></span> |
| <span data-ttu-id="21cce-420">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-420">**Introduced version**</span></span> | <span data-ttu-id="21cce-421">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="21cce-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="21cce-422">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-422">**Option values**</span></span> | <span data-ttu-id="21cce-423">`true` - 型宣言ではベースまたはインターフェイスのコロンの前に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="21cce-424">`false` - 型宣言ではベースまたはインターフェイスのコロンの前の空白文字を除去します</span><span class="sxs-lookup"><span data-stu-id="21cce-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="21cce-425">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-425">Code examples:</span></span>

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="21cce-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="21cce-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="21cce-427">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-427">Property</span></span>|<span data-ttu-id="21cce-428">値</span><span class="sxs-lookup"><span data-stu-id="21cce-428">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-429">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-429">**Option name**</span></span> | <span data-ttu-id="21cce-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="21cce-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="21cce-431">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-431">**Applicable languages**</span></span> | <span data-ttu-id="21cce-432">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-432">C#</span></span> |
| <span data-ttu-id="21cce-433">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-433">**Introduced version**</span></span> | <span data-ttu-id="21cce-434">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="21cce-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="21cce-435">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-435">**Option values**</span></span> | <span data-ttu-id="21cce-436">`true` - 型宣言ではベースまたはインターフェイスのコロンの後に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="21cce-437">`false` - 型宣言ではベースまたはインターフェイスのコロンの後の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="21cce-438">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-438">Code examples:</span></span>

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="21cce-439">csharp\_space\_around\_binary_operators</span><span class="sxs-lookup"><span data-stu-id="21cce-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="21cce-440">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-440">Property</span></span>|<span data-ttu-id="21cce-441">値</span><span class="sxs-lookup"><span data-stu-id="21cce-441">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-442">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-442">**Option name**</span></span> | <span data-ttu-id="21cce-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="21cce-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="21cce-444">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-444">**Applicable languages**</span></span> | <span data-ttu-id="21cce-445">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-445">C#</span></span> |
| <span data-ttu-id="21cce-446">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-446">**Introduced version**</span></span> | <span data-ttu-id="21cce-447">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="21cce-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="21cce-448">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-448">**Option values**</span></span> | <span data-ttu-id="21cce-449">`before_and_after` - バイナリ演算子の前後にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="21cce-450">`none` - バイナリ演算子の前後のスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="21cce-451">`ignore` - バイナリ演算子の前後のスペースを無視します</span><span class="sxs-lookup"><span data-stu-id="21cce-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="21cce-452">このルールを省略するか、`before_and_after`、`none`、または `ignore` 以外の値を使用する場合、設定は適用されません。</span><span class="sxs-lookup"><span data-stu-id="21cce-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="21cce-453">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="21cce-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="21cce-455">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-455">Property</span></span>|<span data-ttu-id="21cce-456">値</span><span class="sxs-lookup"><span data-stu-id="21cce-456">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-457">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-457">**Option name**</span></span> | <span data-ttu-id="21cce-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="21cce-459">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-459">**Applicable languages**</span></span> | <span data-ttu-id="21cce-460">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-460">C#</span></span> |
| <span data-ttu-id="21cce-461">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-461">**Introduced version**</span></span> | <span data-ttu-id="21cce-462">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-463">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-463">**Option values**</span></span> | <span data-ttu-id="21cce-464">`true` - メソッド宣言パラメーター リストの始めかっこの後と終わりかっこの前に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="21cce-465">`false` - メソッド宣言パラメーター リストの始めかっこの後と終わりかっこの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="21cce-466">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="21cce-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="21cce-468">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-468">Property</span></span>|<span data-ttu-id="21cce-469">値</span><span class="sxs-lookup"><span data-stu-id="21cce-469">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-470">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-470">**Option name**</span></span> | <span data-ttu-id="21cce-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="21cce-472">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-472">**Applicable languages**</span></span> | <span data-ttu-id="21cce-473">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-473">C#</span></span> |
| <span data-ttu-id="21cce-474">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-474">**Introduced version**</span></span> | <span data-ttu-id="21cce-475">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="21cce-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="21cce-476">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-476">**Option values**</span></span> | <span data-ttu-id="21cce-477">`true` - メソッド宣言の空のパラメーター リストのかっこ内にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="21cce-478">`false` - メソッド宣言の空のパラメーター リストのかっこ内にスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="21cce-479">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-479">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="21cce-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="21cce-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="21cce-481">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-481">Property</span></span>|<span data-ttu-id="21cce-482">値</span><span class="sxs-lookup"><span data-stu-id="21cce-482">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-483">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-483">**Option name**</span></span> | <span data-ttu-id="21cce-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="21cce-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="21cce-485">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-485">**Applicable languages**</span></span> | <span data-ttu-id="21cce-486">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-486">C#</span></span> |
| <span data-ttu-id="21cce-487">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-487">**Option values**</span></span> | <span data-ttu-id="21cce-488">`true` - メソッド宣言のメソッド名と始めかっこの間に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="21cce-489">`false` - メソッド宣言のメソッド名と始めかっこの間の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="21cce-490">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="21cce-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="21cce-492">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-492">Property</span></span>|<span data-ttu-id="21cce-493">値</span><span class="sxs-lookup"><span data-stu-id="21cce-493">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-494">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-494">**Option name**</span></span> | <span data-ttu-id="21cce-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="21cce-496">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-496">**Applicable languages**</span></span> | <span data-ttu-id="21cce-497">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-497">C#</span></span> |
| <span data-ttu-id="21cce-498">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-498">**Introduced version**</span></span> | <span data-ttu-id="21cce-499">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-500">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-500">**Option values**</span></span> | <span data-ttu-id="21cce-501">`true` - メソッド呼び出しの始めかっこの後と終わりかっこの前に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="21cce-502">`false` - メソッド呼び出しの始めかっこの後と終わりかっこの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="21cce-503">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="21cce-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="21cce-505">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-505">Property</span></span>|<span data-ttu-id="21cce-506">値</span><span class="sxs-lookup"><span data-stu-id="21cce-506">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-507">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-507">**Option name**</span></span> | <span data-ttu-id="21cce-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="21cce-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="21cce-509">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-509">**Applicable languages**</span></span> | <span data-ttu-id="21cce-510">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-510">C#</span></span> |
| <span data-ttu-id="21cce-511">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-511">**Introduced version**</span></span> | <span data-ttu-id="21cce-512">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="21cce-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="21cce-513">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-513">**Option values**</span></span> | <span data-ttu-id="21cce-514">`true` - 空の引数リストのかっこ内にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="21cce-515">`false` - 空の引数リストのかっこ内にスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="21cce-516">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-516">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="21cce-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="21cce-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="21cce-518">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-518">Property</span></span>|<span data-ttu-id="21cce-519">値</span><span class="sxs-lookup"><span data-stu-id="21cce-519">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-520">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-520">**Option name**</span></span> | <span data-ttu-id="21cce-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="21cce-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="21cce-522">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-522">**Applicable languages**</span></span> | <span data-ttu-id="21cce-523">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-523">C#</span></span> |
| <span data-ttu-id="21cce-524">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-524">**Introduced version**</span></span> | <span data-ttu-id="21cce-525">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="21cce-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="21cce-526">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-526">**Option values**</span></span> | <span data-ttu-id="21cce-527">`true` - メソッド呼び出し名と左かっこの間にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="21cce-528">`false` - メソッド呼び出し名と左かっこの間にスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="21cce-529">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-529">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="21cce-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="21cce-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="21cce-531">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-531">Property</span></span>|<span data-ttu-id="21cce-532">値</span><span class="sxs-lookup"><span data-stu-id="21cce-532">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-533">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-533">**Option name**</span></span> | <span data-ttu-id="21cce-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="21cce-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="21cce-535">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-535">**Applicable languages**</span></span> | <span data-ttu-id="21cce-536">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-536">C#</span></span> |
| <span data-ttu-id="21cce-537">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-537">**Option values**</span></span> | <span data-ttu-id="21cce-538">`true` - コンマの後にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="21cce-539">`false` - コンマの後のスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="21cce-540">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="21cce-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="21cce-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="21cce-542">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-542">Property</span></span>|<span data-ttu-id="21cce-543">値</span><span class="sxs-lookup"><span data-stu-id="21cce-543">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-544">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-544">**Option name**</span></span> | <span data-ttu-id="21cce-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="21cce-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="21cce-546">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-546">**Applicable languages**</span></span> | <span data-ttu-id="21cce-547">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-547">C#</span></span> |
| <span data-ttu-id="21cce-548">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-548">**Option values**</span></span> | <span data-ttu-id="21cce-549">`true` - コンマの前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="21cce-550">`false` - コンマの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="21cce-551">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="21cce-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="21cce-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="21cce-553">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-553">Property</span></span>|<span data-ttu-id="21cce-554">値</span><span class="sxs-lookup"><span data-stu-id="21cce-554">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-555">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-555">**Option name**</span></span> | <span data-ttu-id="21cce-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="21cce-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="21cce-557">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-557">**Applicable languages**</span></span> | <span data-ttu-id="21cce-558">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-558">C#</span></span> |
| <span data-ttu-id="21cce-559">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-559">**Option values**</span></span> | <span data-ttu-id="21cce-560">`true` - ドットの後にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="21cce-561">`false` - ドットの後のスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="21cce-562">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="21cce-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="21cce-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="21cce-564">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-564">Property</span></span>|<span data-ttu-id="21cce-565">値</span><span class="sxs-lookup"><span data-stu-id="21cce-565">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-566">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-566">**Option name**</span></span> | <span data-ttu-id="21cce-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="21cce-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="21cce-568">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-568">**Applicable languages**</span></span> | <span data-ttu-id="21cce-569">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-569">C#</span></span> |
| <span data-ttu-id="21cce-570">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-570">**Option values**</span></span> | <span data-ttu-id="21cce-571">`true` - ドットの前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="21cce-572">`false` - ドットの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="21cce-573">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="21cce-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="21cce-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="21cce-575">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-575">Property</span></span>|<span data-ttu-id="21cce-576">値</span><span class="sxs-lookup"><span data-stu-id="21cce-576">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-577">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-577">**Option name**</span></span> | <span data-ttu-id="21cce-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="21cce-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="21cce-579">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-579">**Applicable languages**</span></span> | <span data-ttu-id="21cce-580">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-580">C#</span></span> |
| <span data-ttu-id="21cce-581">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-581">**Option values**</span></span> | <span data-ttu-id="21cce-582">`true` - `for` ステートメントの各セミコロンの後に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="21cce-583">`false` - `for` ステートメントの各セミコロンの後の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="21cce-584">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="21cce-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="21cce-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="21cce-586">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-586">Property</span></span>|<span data-ttu-id="21cce-587">値</span><span class="sxs-lookup"><span data-stu-id="21cce-587">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-588">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-588">**Option name**</span></span> | <span data-ttu-id="21cce-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="21cce-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="21cce-590">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-590">**Applicable languages**</span></span> | <span data-ttu-id="21cce-591">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-591">C#</span></span> |
| <span data-ttu-id="21cce-592">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-592">**Option values**</span></span> | <span data-ttu-id="21cce-593">`true` - `for` ステートメントの各セミコロンの前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="21cce-594">`false` - `for` ステートメントの各セミコロンの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="21cce-595">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="21cce-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="21cce-597">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-597">Property</span></span>|<span data-ttu-id="21cce-598">値</span><span class="sxs-lookup"><span data-stu-id="21cce-598">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-599">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-599">**Option name**</span></span> | <span data-ttu-id="21cce-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="21cce-601">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-601">**Applicable languages**</span></span> | <span data-ttu-id="21cce-602">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-602">C#</span></span> |
| <span data-ttu-id="21cce-603">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-603">**Option values**</span></span> | <span data-ttu-id="21cce-604">`ignore` - 宣言ステートメント内の余分な空白文字を削除しません</span><span class="sxs-lookup"><span data-stu-id="21cce-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="21cce-605">`false` - 宣言ステートメント内の余分な空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="21cce-606">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="21cce-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="21cce-608">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-608">Property</span></span>|<span data-ttu-id="21cce-609">値</span><span class="sxs-lookup"><span data-stu-id="21cce-609">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-610">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-610">**Option name**</span></span> | <span data-ttu-id="21cce-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="21cce-612">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-612">**Applicable languages**</span></span> | <span data-ttu-id="21cce-613">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-613">C#</span></span> |
| <span data-ttu-id="21cce-614">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-614">**Option values**</span></span> | <span data-ttu-id="21cce-615">`true` - 始め角かっこ `[` の前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="21cce-616">`false` - 始め角かっこ `[` の前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="21cce-617">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="21cce-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="21cce-619">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-619">Property</span></span>|<span data-ttu-id="21cce-620">値</span><span class="sxs-lookup"><span data-stu-id="21cce-620">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-621">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-621">**Option name**</span></span> | <span data-ttu-id="21cce-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="21cce-623">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-623">**Applicable languages**</span></span> | <span data-ttu-id="21cce-624">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-624">C#</span></span> |
| <span data-ttu-id="21cce-625">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-625">**Option values**</span></span> | <span data-ttu-id="21cce-626">`true` - 空の角かっこ `[ ]` の間に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="21cce-627">`false` - 空の角かっこ `[]` の間の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="21cce-628">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="21cce-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="21cce-630">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-630">Property</span></span>|<span data-ttu-id="21cce-631">値</span><span class="sxs-lookup"><span data-stu-id="21cce-631">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-632">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-632">**Option name**</span></span> | <span data-ttu-id="21cce-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="21cce-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="21cce-634">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-634">**Applicable languages**</span></span> | <span data-ttu-id="21cce-635">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-635">C#</span></span> |
| <span data-ttu-id="21cce-636">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-636">**Option values**</span></span> | <span data-ttu-id="21cce-637">`true` - 空ではない角かっこ `[ 0 ]` に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="21cce-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="21cce-638">`false` - 空ではない角かっこ `[0]` の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="21cce-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="21cce-639">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="21cce-640">折り返しオプション</span><span class="sxs-lookup"><span data-stu-id="21cce-640">Wrap options</span></span>

<span data-ttu-id="21cce-641">これらの書式ルールは、ステートメントとコード ブロックでの 1 行と別の行の使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="21cce-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="21cce-642">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="21cce-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="21cce-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="21cce-644">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-644">Property</span></span>|<span data-ttu-id="21cce-645">値</span><span class="sxs-lookup"><span data-stu-id="21cce-645">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-646">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-646">**Option name**</span></span> | <span data-ttu-id="21cce-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="21cce-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="21cce-648">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-648">**Applicable languages**</span></span> | <span data-ttu-id="21cce-649">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-649">C#</span></span> |
| <span data-ttu-id="21cce-650">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-650">**Introduced version**</span></span> | <span data-ttu-id="21cce-651">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-652">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-652">**Option values**</span></span> | <span data-ttu-id="21cce-653">`true` - 1 行に複数のステートメントとメンバー宣言を表示します</span><span class="sxs-lookup"><span data-stu-id="21cce-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="21cce-654">`false` - 別の行にステートメントとメンバー宣言を表示します</span><span class="sxs-lookup"><span data-stu-id="21cce-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="21cce-655">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="21cce-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="21cce-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="21cce-657">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-657">Property</span></span>|<span data-ttu-id="21cce-658">値</span><span class="sxs-lookup"><span data-stu-id="21cce-658">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-659">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-659">**Option name**</span></span> | <span data-ttu-id="21cce-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="21cce-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="21cce-661">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-661">**Applicable languages**</span></span> | <span data-ttu-id="21cce-662">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-662">C#</span></span> |
| <span data-ttu-id="21cce-663">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-663">**Introduced version**</span></span> | <span data-ttu-id="21cce-664">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="21cce-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="21cce-665">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-665">**Option values**</span></span> | <span data-ttu-id="21cce-666">`true` - コード ブロックを単一行に配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="21cce-667">`false` - コード ブロックを別の行に配置します</span><span class="sxs-lookup"><span data-stu-id="21cce-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="21cce-668">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="21cce-669">using ディレクティブ オプション</span><span class="sxs-lookup"><span data-stu-id="21cce-669">Using directive options</span></span>

<span data-ttu-id="21cce-670">この書式ルールは、名前空間の内部と外部に配置される using ディレクティブの使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="21cce-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="21cce-671">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="21cce-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="21cce-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="21cce-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="21cce-673">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21cce-673">Property</span></span>|<span data-ttu-id="21cce-674">値</span><span class="sxs-lookup"><span data-stu-id="21cce-674">Value</span></span>|
|-|-|
| <span data-ttu-id="21cce-675">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="21cce-675">**Option name**</span></span> | <span data-ttu-id="21cce-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="21cce-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="21cce-677">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="21cce-677">**Applicable languages**</span></span> | <span data-ttu-id="21cce-678">C#</span><span class="sxs-lookup"><span data-stu-id="21cce-678">C#</span></span> |
| <span data-ttu-id="21cce-679">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="21cce-679">**Introduced version**</span></span> | <span data-ttu-id="21cce-680">Visual Studio 2019 バージョン 16.1</span><span class="sxs-lookup"><span data-stu-id="21cce-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="21cce-681">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="21cce-681">**Option values**</span></span> | <span data-ttu-id="21cce-682">`outside_namespace` - 名前空間の外部のディレクティブが使用されます</span><span class="sxs-lookup"><span data-stu-id="21cce-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="21cce-683">`inside_namespace` - 名前空間の内部のディレクティブが使用されます</span><span class="sxs-lookup"><span data-stu-id="21cce-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="21cce-684">コード例:</span><span class="sxs-lookup"><span data-stu-id="21cce-684">Code examples:</span></span>

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a><span data-ttu-id="21cce-685">関連項目</span><span class="sxs-lookup"><span data-stu-id="21cce-685">See also</span></span>

- [<span data-ttu-id="21cce-686">言語規則</span><span class="sxs-lookup"><span data-stu-id="21cce-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="21cce-687">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="21cce-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="21cce-688">.NET コードスタイル規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="21cce-688">.NET code style rules reference</span></span>](index.md)
