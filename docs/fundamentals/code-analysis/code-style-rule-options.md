---
title: .NET コードスタイル規則のオプション
description: .NET のコードスタイルオプションを指定する方法について説明します。
ms.date: 09/25/2020
ms.topic: conceptual
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 5e4d80ec55f7fbcd01e364bb2b9e2b4f49f820d5
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "96593796"
---
# <a name="code-style-rule-options"></a><span data-ttu-id="648da-103">コードスタイルルールのオプション</span><span class="sxs-lookup"><span data-stu-id="648da-103">Code style rule options</span></span>

<span data-ttu-id="648da-104">コードベースで一貫性のある *コードスタイル* を定義および維持するには、 [editorconfig](/visualstudio/ide/create-portable-custom-editor-options) ファイルで .net コードスタイルルールオプションを定義します。</span><span class="sxs-lookup"><span data-stu-id="648da-104">You can define and maintain consistent *code style* in your codebase by defining .NET code style rule options in an [EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) file.</span></span> <span data-ttu-id="648da-105">これらの規則は、コードを編集するときに、Visual Studio などのさまざまな開発 Ide によって表示されます。</span><span class="sxs-lookup"><span data-stu-id="648da-105">These rules are surfaced by various development IDEs, such as Visual Studio, as you edit your code.</span></span> <span data-ttu-id="648da-106">.NET プロジェクトの場合は、 [ビルド時に](overview.md#code-style-analysis)これらの規則を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="648da-106">For .NET projects, these rules can also be [enforced at build time](overview.md#code-style-analysis).</span></span> <span data-ttu-id="648da-107">個々のルールを有効または無効にしたり、各ルールを適用するレベルを重要度レベルで構成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="648da-107">You can enable or disable individual rules and configure the degree to which you want each rule enforced, via a severity level.</span></span>

> [!TIP]
>
> - <span data-ttu-id="648da-108">EditorConfig ファイルでコードスタイルオプションを定義するときは、コード [スタイルアナライザー](overview.md#code-style-analysis) でコードを分析する方法を構成します。</span><span class="sxs-lookup"><span data-stu-id="648da-108">When you define code style options in an EditorConfig file, you're configuring how you want the [code style analyzers](overview.md#code-style-analysis) to analyze your code.</span></span> <span data-ttu-id="648da-109">EditorConfig ファイルは、これらのアナライザーに対する構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="648da-109">The EditorConfig file is the configuration file for these analyzers.</span></span>
>
> - <span data-ttu-id="648da-110">コードスタイルのオプションは、Visual Studio の [ [テキストエディターのオプション](/visualstudio/ide/code-styles-and-code-cleanup) ] ダイアログで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="648da-110">Code style options can also be set in Visual Studio in the [Text editor options](/visualstudio/ide/code-styles-and-code-cleanup) dialog.</span></span> <span data-ttu-id="648da-111">これらは、Visual Studio での編集中にのみ適用されるユーザーごとのオプションです。</span><span class="sxs-lookup"><span data-stu-id="648da-111">These are per-user options that are only respected while editing in Visual Studio.</span></span> <span data-ttu-id="648da-112">これらのオプションは、ビルド時または他の Ide によって尊重されることはありません。</span><span class="sxs-lookup"><span data-stu-id="648da-112">These options are not respected at build time or by other IDEs.</span></span> <span data-ttu-id="648da-113">さらに、Visual Studio 内で開かれたプロジェクトまたはソリューションに EditorConfig ファイルがある場合は、EditorConfig ファイルのオプションが優先されます。</span><span class="sxs-lookup"><span data-stu-id="648da-113">Additionally, if the project or solution opened inside Visual Studio has an EditorConfig file, then options from the EditorConfig file take precedence.</span></span>

<span data-ttu-id="648da-114">コードスタイルの規則は、次のサブカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="648da-114">Code style rules are divided into following subcategories:</span></span>

- [<span data-ttu-id="648da-115">言語規則</span><span class="sxs-lookup"><span data-stu-id="648da-115">Language rules</span></span>](style-rules/language-rules.md)

- [<span data-ttu-id="648da-116">不要なコード規則</span><span class="sxs-lookup"><span data-stu-id="648da-116">Unnecessary code rules</span></span>](style-rules/unnecessary-code-rules.md)

- [<span data-ttu-id="648da-117">書式設定規則</span><span class="sxs-lookup"><span data-stu-id="648da-117">Formatting rules</span></span>](style-rules/formatting-rules.md)

- [<span data-ttu-id="648da-118">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="648da-118">Naming rules</span></span>](style-rules/naming-rules.md)

<span data-ttu-id="648da-119">これらの各サブカテゴリでは、オプションを指定するための独自の構文が定義されています。</span><span class="sxs-lookup"><span data-stu-id="648da-119">Each of these subcategories defines its own syntax for specifying options.</span></span> <span data-ttu-id="648da-120">これらの規則および対応するオプションの詳細については、「 [コードスタイル規則のリファレンス](style-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="648da-120">For more information about these rules and the corresponding options, see [Code style rule reference](style-rules/index.md).</span></span>

## <a name="example-editorconfig-file"></a><span data-ttu-id="648da-121">EditorConfig ファイルの例</span><span class="sxs-lookup"><span data-stu-id="648da-121">Example EditorConfig file</span></span>

<span data-ttu-id="648da-122">作業の開始に役立つように、ここでは既定のオプションを使用する *.editorconfig* ファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="648da-122">To help you get started, here is an example *.editorconfig* file with the default options.</span></span>

> [!TIP]
> <span data-ttu-id="648da-123">Visual Studio では、このファイルを生成してプロジェクトに保存するには、 **[ツール]**  >  **[オプション]**  >  **[テキスト エディター]** > **[C#]** または **[Basic]** > **[コード スタイル]**  >  **[全般]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="648da-123">In Visual Studio, you can generate this file and save it to a project at **Tools** > **Options** > **Text Editor** > [**C#** or  **Basic**] > **Code Style** > **General**.</span></span> <span data-ttu-id="648da-124">次に、 **[設定から editorconfig ファイルを生成]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="648da-124">Then, click the **Generate .editorconfig file from settings** button.</span></span> <span data-ttu-id="648da-125">詳細については、「[コードのスタイル設定](/visualstudio/ide/code-styles-and-code-cleanup)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="648da-125">For more information, see [Code style preferences](/visualstudio/ide/code-styles-and-code-cleanup).</span></span>

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### .NET Coding Conventions ####

# Organize usings
dotnet_separate_import_directive_groups = false
dotnet_sort_system_directives_first = false
file_header_template = unset

# this. and Me. preferences
dotnet_style_qualification_for_event = false:silent
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_property = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent

# Expression-level preferences
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_object_initializer = true:suggestion
dotnet_style_operator_placement_when_wrapping = beginning_of_line
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_compound_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:suggestion
dotnet_style_prefer_simplified_boolean_expressions = true:suggestion
dotnet_style_prefer_simplified_interpolation = true:suggestion

# Field preferences
dotnet_style_readonly_field = true:suggestion

# Parameter preferences
dotnet_code_quality_unused_parameters = all:suggestion

# Suppression preferences
dotnet_remove_unnecessary_suppression_exclusions = none

#### C# Coding Conventions ####

# var preferences
csharp_style_var_elsewhere = false:silent
csharp_style_var_for_built_in_types = false:silent
csharp_style_var_when_type_is_apparent = false:silent

# Expression-bodied members
csharp_style_expression_bodied_accessors = true:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent

# Pattern matching preferences
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_prefer_not_pattern = true:suggestion
csharp_style_prefer_pattern_matching = true:silent
csharp_style_prefer_switch_expression = true:suggestion

# Null-checking preferences
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_prefer_static_local_function = true:suggestion
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:silent

# Code-block preferences
csharp_prefer_braces = true:silent
csharp_prefer_simple_using_statement = true:suggestion

# Expression-level preferences
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
csharp_style_throw_expression = true:suggestion
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
csharp_style_unused_value_expression_statement_preference = discard_variable:silent

# 'using' directive preferences
csharp_using_directive_placement = inside_namespace:silent

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = true
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = suggestion
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i

dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case

dotnet_naming_rule.non_field_members_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.non_field_members_should_be_pascal_case.symbols = non_field_members
dotnet_naming_rule.non_field_members_should_be_pascal_case.style = pascal_case

# Symbol specifications

dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.interface.required_modifiers =

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.types.required_modifiers =

dotnet_naming_symbols.non_field_members.applicable_kinds = property, event, method
dotnet_naming_symbols.non_field_members.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.non_field_members.required_modifiers =

# Naming styles

dotnet_naming_style.pascal_case.required_prefix =
dotnet_naming_style.pascal_case.required_suffix =
dotnet_naming_style.pascal_case.word_separator =
dotnet_naming_style.pascal_case.capitalization = pascal_case

dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.required_suffix =
dotnet_naming_style.begins_with_i.word_separator =
dotnet_naming_style.begins_with_i.capitalization = pascal_case

```

## <a name="see-also"></a><span data-ttu-id="648da-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="648da-126">See also</span></span>

- [<span data-ttu-id="648da-127">コードスタイル分析規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="648da-127">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="648da-128">ビルドにコードスタイルを適用する</span><span class="sxs-lookup"><span data-stu-id="648da-128">Enforce code style on build</span></span>](overview.md#code-style-analysis)
- [<span data-ttu-id="648da-129">Visual Studio のクイック アクション</span><span class="sxs-lookup"><span data-stu-id="648da-129">Quick Actions in Visual Studio</span></span>](/visualstudio/ide/quick-actions)
- [<span data-ttu-id="648da-130">Visual Studio でポータブルカスタムエディターオプションを作成する</span><span class="sxs-lookup"><span data-stu-id="648da-130">Create portable custom editor options in Visual Studio</span></span>](/visualstudio/ide/create-portable-custom-editor-options)
- [<span data-ttu-id="648da-131">.NET Compiler Platform "Roslyn" .editorconfig ファイル</span><span class="sxs-lookup"><span data-stu-id="648da-131">.NET Compiler Platform "Roslyn" .editorconfig file</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
- [<span data-ttu-id="648da-132">.NET Compiler Platform ランタイム .editorconfig ファイル</span><span class="sxs-lookup"><span data-stu-id="648da-132">.NET Compiler Platform Runtime .editorconfig file</span></span>](https://github.com/dotnet/runtime/blob/master/.editorconfig)
