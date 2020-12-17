---
title: コード分析規則の構成ファイル
description: コード分析規則を構成するためのさまざまな構成ファイルについて説明します。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 0d64df42ffb1763afed3e883c4f043755e158489
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633989"
---
# <a name="configuration-files-for-code-analysis-rules"></a><span data-ttu-id="6e888-103">コード分析規則の構成ファイル</span><span class="sxs-lookup"><span data-stu-id="6e888-103">Configuration files for code analysis rules</span></span>

<span data-ttu-id="6e888-104">コード分析規則には、さまざまな [構成オプション](configuration-options.md)があります。</span><span class="sxs-lookup"><span data-stu-id="6e888-104">Code analysis rules have various [configuration options](configuration-options.md).</span></span> <span data-ttu-id="6e888-105">これらのオプションは、次のいずれかのアナライザー構成ファイルのキーと値のペアとして指定します。</span><span class="sxs-lookup"><span data-stu-id="6e888-105">You specify these options as key-value pairs in one of the following analyzer configuration files:</span></span>

- <span data-ttu-id="6e888-106">[EditorConfig](#editorconfig) ファイル: ファイルベースまたはフォルダーベースの構成オプション。</span><span class="sxs-lookup"><span data-stu-id="6e888-106">[EditorConfig](#editorconfig) file: File-based or folder-based configuration options.</span></span>
- <span data-ttu-id="6e888-107">[Global AnalyzerConfig](#global-analyzerconfig) File: プロジェクトレベルの構成オプション。</span><span class="sxs-lookup"><span data-stu-id="6e888-107">[Global AnalyzerConfig](#global-analyzerconfig) file: Project-level configuration options.</span></span>

## EditorConfig

<span data-ttu-id="6e888-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) ファイルは、特定の **ソースファイルまたはフォルダーに適用されるオプション** を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) files are used to provide **options that apply to specific source files or folders**.</span></span> <span data-ttu-id="6e888-109">オプションは、該当するファイルとフォルダーを識別するために、セクションヘッダーの下に配置されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-109">Options are placed under section headers to identify the applicable files and folders.</span></span> <span data-ttu-id="6e888-110">構成する各規則のエントリを追加し、対応するファイル拡張子セクションの下に配置します。たとえば、のように `[*.cs]` します。</span><span class="sxs-lookup"><span data-stu-id="6e888-110">Add an entry for each rule you want to configure, and place it under the corresponding file extension section, for example, `[*.cs]`.</span></span>

```ini
[*.cs]
<option_name> = <option_value>
```

<span data-ttu-id="6e888-111">上の例で `[*.cs]` は、は editorconfig セクションヘッダーで、現在のフォルダー内のファイル拡張子を持つすべての C# ファイル `.cs` (サブフォルダーを含む) を選択します。</span><span class="sxs-lookup"><span data-stu-id="6e888-111">In the above example, `[*.cs]` is an editorconfig section header to select all C# files with `.cs` file extension within the current folder, including subfolders.</span></span> <span data-ttu-id="6e888-112">後続のエントリは、 `<option_name> = <option_value>` すべての C# ファイルに適用されるアナライザーオプションです。</span><span class="sxs-lookup"><span data-stu-id="6e888-112">The subsequent entry, `<option_name> = <option_value>`, is an analyzer option that will be applied to all the C# files.</span></span>

<span data-ttu-id="6e888-113">ファイル規則は、 EditorConfig 対応するディレクトリに配置することによって、フォルダー、プロジェクト、またはリポジトリ全体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="6e888-113">You can apply EditorConfig file conventions to a folder, a project, or an entire repo by placing the file in the corresponding directory.</span></span> <span data-ttu-id="6e888-114">これらのオプションは、ビルド時に分析を実行するときと、Visual Studio でコードを編集するときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-114">These options are applied when executing the analysis at build time and while you edit code in Visual Studio.</span></span>

<span data-ttu-id="6e888-115">インデントサイズや末尾の空白文字を削除するかどうかなど、エディターの設定に既存の *editorconfig* ファイルがある場合は、コード分析の構成オプションを同じファイルに配置できます。</span><span class="sxs-lookup"><span data-stu-id="6e888-115">If you have an existing *.editorconfig* file for editor settings such as indent size or whether to trim trailing whitespace, you can place your code analysis configuration options in the same file.</span></span>

> [!TIP]
> <span data-ttu-id="6e888-116">Visual Studio には、これらのファイルの1つをプロジェクトに簡単に追加できるようにする、editorconfig 項目テンプレートが用意されてい *ます。*</span><span class="sxs-lookup"><span data-stu-id="6e888-116">Visual Studio provides an *.editorconfig* item template that makes is easy to add one of these files to your project.</span></span> <span data-ttu-id="6e888-117">詳細については、「 [ EditorConfig プロジェクトへのファイルの追加](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e888-117">For more information, see [Add an EditorConfig file to a project](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span></span>

### <a name="example"></a><span data-ttu-id="6e888-118">例</span><span class="sxs-lookup"><span data-stu-id="6e888-118">Example</span></span>

<span data-ttu-id="6e888-119">EditorConfigオプションとルールの重要度を構成するファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6e888-119">Following is an example EditorConfig file to configure options and rule severity:</span></span>

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

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a><span data-ttu-id="6e888-120">グローバル AnalyzerConfig</span><span class="sxs-lookup"><span data-stu-id="6e888-120">Global AnalyzerConfig</span></span>

<span data-ttu-id="6e888-121">.NET 5 SDK (Visual Studio 2019 バージョン16.8 以降のバージョンでサポートされています) 以降では、グローバル _AnalyzerConfig_ ファイルを使用してアナライザーオプションを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6e888-121">Starting with the .NET 5 SDK (which is supported in Visual Studio 2019 version 16.8 and later versions), you can also configure analyzer options with global _AnalyzerConfig_ files.</span></span> <span data-ttu-id="6e888-122">これらのファイルは、ファイル名やファイルパスに関係なく、 **プロジェクト内のすべてのソースファイルに適用されるオプション** を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-122">These files are used to provide **options that apply to all the source files in a project**, regardless of their file names or file paths.</span></span>

<span data-ttu-id="6e888-123">ファイルとは異なり [EditorConfig](#editorconfig) 、グローバル構成ファイルを使用して、インデントサイズや末尾の空白をトリミングするかどうかなど、ide のエディタースタイル設定を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="6e888-123">Unlike [EditorConfig](#editorconfig) files, global config files can't be used to configure editor style settings for IDEs, such as indent size or whether to trim trailing whitespace.</span></span> <span data-ttu-id="6e888-124">代わりに、プロジェクトレベルのアナライザーの構成オプションを指定するために、純粋に設計されています。</span><span class="sxs-lookup"><span data-stu-id="6e888-124">Instead, they are designed purely for specifying project-level analyzer configuration options.</span></span>

### <a name="format"></a><span data-ttu-id="6e888-125">Format</span><span class="sxs-lookup"><span data-stu-id="6e888-125">Format</span></span>

<span data-ttu-id="6e888-126">EditorConfig該当するファイルとフォルダーを識別するためになどのセクションヘッダーを持つ必要があるファイルとは異なり `[*.cs]` 、グローバル AnalyzerConfig ファイルにはセクションヘッダーがありません。</span><span class="sxs-lookup"><span data-stu-id="6e888-126">Unlike EditorConfig files, which must have section headers, such as `[*.cs]`, to identify the applicable files and folders, global AnalyzerConfig files don't have section headers.</span></span> <span data-ttu-id="6e888-127">代わりに、 `is_global = true` 通常のファイルと区別するために、フォームの最上位レベルのエントリが必要 EditorConfig です。</span><span class="sxs-lookup"><span data-stu-id="6e888-127">Instead, they require a top level entry of the form `is_global = true` to differentiate them from regular EditorConfig files.</span></span> <span data-ttu-id="6e888-128">これは、ファイル内のすべてのオプションがプロジェクト全体に適用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="6e888-128">This indicates that all the options in the file apply to the entire project.</span></span> <span data-ttu-id="6e888-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6e888-129">For example:</span></span>

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a><span data-ttu-id="6e888-130">名前を付ける</span><span class="sxs-lookup"><span data-stu-id="6e888-130">Naming</span></span>

<span data-ttu-id="6e888-131">名前を付ける必要があるファイルとは異なり EditorConfig `.editorconfig` 、グローバル構成ファイルには、特定の名前や拡張子を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6e888-131">Unlike EditorConfig files, which must be named `.editorconfig`, global config files do not need to have a specific name or extension.</span></span> <span data-ttu-id="6e888-132">ただし、これらのファイルにという名前を付けた場合、 `.globalconfig` サブフォルダーを含む現在のフォルダー内のすべての C# および Visual Basic プロジェクトに暗黙的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-132">However, if you name these files as `.globalconfig` then they will be implicitly applied to all the C# and Visual Basic projects within the current folder, including subfolders.</span></span> <span data-ttu-id="6e888-133">それ以外の場合は、 `GlobalAnalyzerConfigFiles` MSBuild プロジェクトファイルに項目を明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e888-133">Otherwise, you must explicitly add the `GlobalAnalyzerConfigFiles` item to your MSBuild project file:</span></span>

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="6e888-134">ファイル名がの場合でも、最上位レベルのエントリ `is_global = true` が必要です `.globalconfig` 。</span><span class="sxs-lookup"><span data-stu-id="6e888-134">The top-level entry `is_global = true` is required even when the file is named `.globalconfig`.</span></span>

### <a name="example"></a><span data-ttu-id="6e888-135">例</span><span class="sxs-lookup"><span data-stu-id="6e888-135">Example</span></span>

<span data-ttu-id="6e888-136">次に示すのは、プロジェクトレベルでオプションとルールの重要度を構成するグローバル AnalyzerConfig ファイルの例です。</span><span class="sxs-lookup"><span data-stu-id="6e888-136">Following is an example global AnalyzerConfig file to configure options and rule severity at the project level:</span></span>

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a><span data-ttu-id="6e888-137">優先順位</span><span class="sxs-lookup"><span data-stu-id="6e888-137">Precedence</span></span>

<span data-ttu-id="6e888-138">EditorConfigファイルとグローバル AnalyzerConfig ファイルはどちらも、各オプションのキーと値のペアを指定します。</span><span class="sxs-lookup"><span data-stu-id="6e888-138">Both EditorConfig files and global AnalyzerConfig files specify a key-value pair for each option.</span></span> <span data-ttu-id="6e888-139">競合は、キーが同じで値が異なる複数のエントリが存在する場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="6e888-139">Conflicts arise when there are multiple entries with the same key but different values.</span></span>

### <a name="general-options"></a><span data-ttu-id="6e888-140">[全般] オプション</span><span class="sxs-lookup"><span data-stu-id="6e888-140">General options</span></span>

<span data-ttu-id="6e888-141">オプション間で競合が発生した場合は、次の優先順位ルールを使用して競合を解決します。</span><span class="sxs-lookup"><span data-stu-id="6e888-141">When conflicts arise between options, the following precedence rules are used to resolve the conflicts:</span></span>

- <span data-ttu-id="6e888-142">同じ構成ファイル内のエントリが競合しています。ファイル内で後で表示されるエントリが優先されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-142">Conflicting entries in the same configuration file: The entry that appears later in the file wins.</span></span> <span data-ttu-id="6e888-143">これは、1つのファイル内のエントリ EditorConfig と、1つのグローバル AnalyzerConfig ファイル内のエントリの競合にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="6e888-143">This is true for conflicting entries within a single EditorConfig file and also within a single global AnalyzerConfig file.</span></span>

- <span data-ttu-id="6e888-144">2つのファイル内のエントリが競合してい EditorConfig ます。ファイルシステムのより深いファイル内のエントリがあるため、ファイル EditorConfig パスが長くなります。</span><span class="sxs-lookup"><span data-stu-id="6e888-144">Conflicting entries in two EditorConfig files: The entry in the EditorConfig file that's deeper in the file system, and hence has a longer file path, wins.</span></span>

- <span data-ttu-id="6e888-145">2つのグローバル AnalyzerConfig ファイルで競合するエントリ: コンパイラの警告が報告され、両方のエントリが無視されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-145">Conflicting entries in two global AnalyzerConfig files: A compiler warning is reported and both entries are ignored.</span></span>

- <span data-ttu-id="6e888-146">ファイル内のエントリ EditorConfig とグローバル AnalyzerConfig ファイルが競合しています。ファイル内のエントリが優先され EditorConfig ます。</span><span class="sxs-lookup"><span data-stu-id="6e888-146">Conflicting entries in an EditorConfig file and a Global AnalyzerConfig file: The entry in the EditorConfig file wins.</span></span>

### <a name="severity-options"></a><span data-ttu-id="6e888-147">重要度オプション</span><span class="sxs-lookup"><span data-stu-id="6e888-147">Severity options</span></span>

<span data-ttu-id="6e888-148">前の [一般優先順位の規則](#general-options) は、構成ファイルで指定されているすべてのオプションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-148">The previous [general precedence rules](#general-options) apply for all options specified in configuration files.</span></span> <span data-ttu-id="6e888-149">[重要度の構成](configuration-options.md#severity-level)オプションについては、次の優先順位の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="6e888-149">For [severity configuration](configuration-options.md#severity-level) options, the following additional precedence rules apply:</span></span>

- <span data-ttu-id="6e888-150">コンパイラオプションとしてコマンドラインで指定された重大度オプション ( `/nowarn` または `/warnaserror` ) は、とグローバル AnalyzerConfig ファイルで指定された [重大度構成](configuration-options.md#severity-level) オプションを常にオーバーライドし EditorConfig ます。</span><span class="sxs-lookup"><span data-stu-id="6e888-150">Severity options specified at the command line as compiler options (`/nowarn` or `/warnaserror`) always override [severity configuration](configuration-options.md#severity-level) options specified in EditorConfig and global AnalyzerConfig files.</span></span>

- <span data-ttu-id="6e888-151">重大度オプションは、 [ルールセット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルと共に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="6e888-151">Severity options can also be specified with a [Ruleset](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) file.</span></span> <span data-ttu-id="6e888-152">ただし、およびグローバル AnalyzerConfig ファイルを優先する場合は、ルールセットファイルが非推奨とされ EditorConfig ます。</span><span class="sxs-lookup"><span data-stu-id="6e888-152">However, rulesets files are deprecated in favor of EditorConfig and global AnalyzerConfig files.</span></span> <span data-ttu-id="6e888-153">[ルールセットファイルを同等の EditorConfig ファイルに変換](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e888-153">It's recommended that you [convert ruleset files to an equivalent EditorConfig file](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span></span> <span data-ttu-id="6e888-154">ルールセットファイルとグローバル AnalyzerConfig ファイルの競合する重要度エントリの優先順位 EditorConfig は _定義_ されていません。</span><span class="sxs-lookup"><span data-stu-id="6e888-154">Precedence for conflicting severity entries from a ruleset file and EditorConfig or global AnalyzerConfig files is _undefined_.</span></span>

- <span data-ttu-id="6e888-155">異なるキーを持つ関連する重大度オプションの優先順位規則については、「 [コード分析の構成オプション](configuration-options.md#precedence)」を参照してください。たとえば、1つの規則に対して異なる重大度が指定されている場合などです。</span><span class="sxs-lookup"><span data-stu-id="6e888-155">For information about precedence rules for related severity options with different keys, for example, when different severities are specified for a single rule and for the category that rule falls under, see [Configuration options for code analysis](configuration-options.md#precedence).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e888-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e888-156">See also</span></span>

- [<span data-ttu-id="6e888-157">EditorConfig vs global AnalyzerConfig のデザインの問題</span><span class="sxs-lookup"><span data-stu-id="6e888-157">EditorConfig vs global AnalyzerConfig design issue</span></span>](https://github.com/dotnet/roslyn/issues/47707)
