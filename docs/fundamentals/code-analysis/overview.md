---
title: .NET でのコード分析
titleSuffix: ''
description: .NET SDK のソースコード分析について説明します。
ms.date: 08/22/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: ca3a9cb914befbc8e0982070b818b27ee3143793
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "96593839"
---
# <a name="overview-of-net-source-code-analysis"></a><span data-ttu-id="aa242-103">.NET ソース コード分析の概要</span><span class="sxs-lookup"><span data-stu-id="aa242-103">Overview of .NET source code analysis</span></span>

<span data-ttu-id="aa242-104">.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コード品質やコード スタイルに関する問題を検査できます。</span><span class="sxs-lookup"><span data-stu-id="aa242-104">.NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="aa242-105">.NET 5.0 以降、これらのアナライザーは .NET SDK に含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="aa242-105">Starting in .NET 5.0, these analyzers are included with the .NET SDK.</span></span> <span data-ttu-id="aa242-106">(以前は、 [NuGet パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)としてコード品質アナライザーがインストールされており、コードスタイルアナライザーが Visual Studio と共にインストールされていました)。</span><span class="sxs-lookup"><span data-stu-id="aa242-106">(Previously, you installed code quality analyzers as a [NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), and code style analyzers were installed with Visual Studio.)</span></span>

- [<span data-ttu-id="aa242-107">コード品質分析 ("CAxxxx" ルール)</span><span class="sxs-lookup"><span data-stu-id="aa242-107">Code quality analysis ("CAxxxx" rules)</span></span>](#code-quality-analysis)
- [<span data-ttu-id="aa242-108">コードスタイル分析 ("Ide Xxxx" 規則)</span><span class="sxs-lookup"><span data-stu-id="aa242-108">Code style analysis ("IDExxxx" rules)</span></span>](#code-style-analysis)

<span data-ttu-id="aa242-109">ルール違反が analyzer によって検出されると、各ルールの [構成](configuration-options.md)方法に応じて、候補、警告、またはエラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="aa242-109">If rule violations are found by an analyzer, they're reported as a suggestion, warning, or error, depending on how each rule is [configured](configuration-options.md).</span></span> <span data-ttu-id="aa242-110">コード分析違反は、コンパイラエラーと区別するために "CA" または "IDE" というプレフィックスで示されます。</span><span class="sxs-lookup"><span data-stu-id="aa242-110">Code analysis violations appear with the prefix "CA" or "IDE" to differentiate them from compiler errors.</span></span>

> [!TIP]
>
> - <span data-ttu-id="aa242-111">[StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [roslの ator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [Xunit](https://www.nuget.org/packages/xunit.analyzers/) [Analyzer、sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)などのサードパーティ製アナライザーをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="aa242-111">You can also install third party analyzers, such as [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), and [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).</span></span>
> - <span data-ttu-id="aa242-112">Visual Studio を使用している場合は、多くのアナライザールールに関連付けられている *コード修正プログラム* を適用して、問題を修正できます。</span><span class="sxs-lookup"><span data-stu-id="aa242-112">If you're using Visual Studio, many analyzer rules have associated *code fixes* that you can apply to correct the problem.</span></span> <span data-ttu-id="aa242-113">コード修正は、電球アイコンメニューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa242-113">Code fixes are shown in the light bulb icon menu.</span></span>

## <a name="code-quality-analysis"></a><span data-ttu-id="aa242-114">コード品質の分析</span><span class="sxs-lookup"><span data-stu-id="aa242-114">Code quality analysis</span></span>

<span data-ttu-id="aa242-115">_コード品質分析 ("CA") 規則_ は、セキュリティ、パフォーマンス、設計などの問題について、C# または Visual Basic コードを検査します。</span><span class="sxs-lookup"><span data-stu-id="aa242-115">_Code quality analysis ("CA") rules_ inspect your C# or Visual Basic code for security, performance, design and other issues.</span></span> <span data-ttu-id="aa242-116">.NET 5.0 以降を対象とするプロジェクトでは、既定で分析が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="aa242-116">Analysis is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="aa242-117">以前のバージョンの .NET を対象とするプロジェクトでは、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することにより、コード分析を有効にすることができ `true` ます。</span><span class="sxs-lookup"><span data-stu-id="aa242-117">You can enable code analysis on projects that target earlier .NET versions by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span> <span data-ttu-id="aa242-118">をに設定することにより、プロジェクトのコード分析を無効にすることもでき `EnableNETAnalyzers` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="aa242-118">You can also disable code analysis for your project by setting `EnableNETAnalyzers` to `false`.</span></span>

> [!TIP]
> <span data-ttu-id="aa242-119">Visual Studio では、プロジェクトプロパティウィンドウを使用してコード分析を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-119">In Visual Studio, you can enable or disable code analysis using the Project Properties window.</span></span> <span data-ttu-id="aa242-120">プロジェクトプロパティウィンドウにアクセスするにはソリューションエクスプローラー内のプロジェクトを右クリックし、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa242-120">To access the Project Properties window, right-click on a project within Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="aa242-121">次に、[ **コード分析** ] タブを選択し、[ **.Net アナライザーを有効** にする] チェックボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="aa242-121">Next, select the **Code Analysis** tab, and then either select or clear the checkbox to **Enable .NET analyzers**.</span></span>

### <a name="enabled-rules"></a><span data-ttu-id="aa242-122">有効なルール</span><span class="sxs-lookup"><span data-stu-id="aa242-122">Enabled rules</span></span>

<span data-ttu-id="aa242-123">.NET 5.0 Preview 8 では、既定で次のルールが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="aa242-123">The following rules are enabled, by default, in .NET 5.0 Preview 8.</span></span>

| <span data-ttu-id="aa242-124">診断 ID</span><span class="sxs-lookup"><span data-stu-id="aa242-124">Diagnostic ID</span></span> | <span data-ttu-id="aa242-125">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="aa242-125">Category</span></span> | <span data-ttu-id="aa242-126">重大度</span><span class="sxs-lookup"><span data-stu-id="aa242-126">Severity</span></span> | <span data-ttu-id="aa242-127">説明</span><span class="sxs-lookup"><span data-stu-id="aa242-127">Description</span></span> |
| - | - | - | - |
| [<span data-ttu-id="aa242-128">CA1416</span><span class="sxs-lookup"><span data-stu-id="aa242-128">CA1416</span></span>](/visualstudio/code-quality/ca1416) | <span data-ttu-id="aa242-129">相互運用性</span><span class="sxs-lookup"><span data-stu-id="aa242-129">Interoperability</span></span> | <span data-ttu-id="aa242-130">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-130">Warning</span></span> | <span data-ttu-id="aa242-131">プラットフォーム互換性アナライザー</span><span class="sxs-lookup"><span data-stu-id="aa242-131">Platform compatibility analyzer</span></span> |
| [<span data-ttu-id="aa242-132">CA1417</span><span class="sxs-lookup"><span data-stu-id="aa242-132">CA1417</span></span>](/visualstudio/code-quality/ca1417) | <span data-ttu-id="aa242-133">相互運用性</span><span class="sxs-lookup"><span data-stu-id="aa242-133">Interoperability</span></span> | <span data-ttu-id="aa242-134">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-134">Warning</span></span> | <span data-ttu-id="aa242-135">`OutAttribute`P/invoke に文字列パラメーターを使用しない</span><span class="sxs-lookup"><span data-stu-id="aa242-135">Do not use `OutAttribute` on string parameters for P/Invokes</span></span> |
| [<span data-ttu-id="aa242-136">CA1831</span><span class="sxs-lookup"><span data-stu-id="aa242-136">CA1831</span></span>](/visualstudio/code-quality/ca1831) | <span data-ttu-id="aa242-137">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="aa242-137">Performance</span></span> | <span data-ttu-id="aa242-138">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-138">Warning</span></span> | <span data-ttu-id="aa242-139">`AsSpan`必要に応じて、範囲ベースのインデクサーの代わりに文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa242-139">Use `AsSpan` instead of range-based indexers for string when appropriate</span></span> |
| [<span data-ttu-id="aa242-140">CA2013</span><span class="sxs-lookup"><span data-stu-id="aa242-140">CA2013</span></span>](/visualstudio/code-quality/ca2013) | <span data-ttu-id="aa242-141">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="aa242-141">Reliability</span></span> | <span data-ttu-id="aa242-142">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-142">Warning</span></span> | <span data-ttu-id="aa242-143">`ReferenceEquals`値型では使用しない</span><span class="sxs-lookup"><span data-stu-id="aa242-143">Do not use `ReferenceEquals` with value types</span></span> |
| [<span data-ttu-id="aa242-144">CA2014</span><span class="sxs-lookup"><span data-stu-id="aa242-144">CA2014</span></span>](/visualstudio/code-quality/ca2014) | <span data-ttu-id="aa242-145">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="aa242-145">Reliability</span></span> | <span data-ttu-id="aa242-146">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-146">Warning</span></span> | <span data-ttu-id="aa242-147">In ループを使用しない `stackalloc`</span><span class="sxs-lookup"><span data-stu-id="aa242-147">Do not use `stackalloc` in loops</span></span> |
| [<span data-ttu-id="aa242-148">CA2015</span><span class="sxs-lookup"><span data-stu-id="aa242-148">CA2015</span></span>](/visualstudio/code-quality/ca2015) | <span data-ttu-id="aa242-149">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="aa242-149">Reliability</span></span> | <span data-ttu-id="aa242-150">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-150">Warning</span></span> | <span data-ttu-id="aa242-151">から派生した型にはファイナライザーを定義しないでください。 <xref:System.Buffers.MemoryManager%601></span><span class="sxs-lookup"><span data-stu-id="aa242-151">Do not define finalizers for types derived from <xref:System.Buffers.MemoryManager%601></span></span> |
| [<span data-ttu-id="aa242-152">CA2200</span><span class="sxs-lookup"><span data-stu-id="aa242-152">CA2200</span></span>](/visualstudio/code-quality/ca2200) | <span data-ttu-id="aa242-153">使用</span><span class="sxs-lookup"><span data-stu-id="aa242-153">Usage</span></span> | <span data-ttu-id="aa242-154">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-154">Warning</span></span> | <span data-ttu-id="aa242-155">スタック詳細を保持するために再度スローします</span><span class="sxs-lookup"><span data-stu-id="aa242-155">Rethrow to preserve stack details</span></span>
| [<span data-ttu-id="aa242-156">CA2247</span><span class="sxs-lookup"><span data-stu-id="aa242-156">CA2247</span></span>](/visualstudio/code-quality/ca2247) | <span data-ttu-id="aa242-157">使用</span><span class="sxs-lookup"><span data-stu-id="aa242-157">Usage</span></span> | <span data-ttu-id="aa242-158">警告</span><span class="sxs-lookup"><span data-stu-id="aa242-158">Warning</span></span> | <span data-ttu-id="aa242-159">Taskのソースコンストラクターに渡される引数は、ではなく列挙型にする必要があり <xref:System.Threading.Tasks.TaskCreationOptions> ます <xref:System.Threading.Tasks.TaskContinuationOptions></span><span class="sxs-lookup"><span data-stu-id="aa242-159">Argument passed to TaskCompletionSource constructor should be <xref:System.Threading.Tasks.TaskCreationOptions> enum instead of <xref:System.Threading.Tasks.TaskContinuationOptions></span></span> |

<span data-ttu-id="aa242-160">これらのルールを無効にするか、エラーに昇格するように、これらのルールの重大度を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-160">You can change the severity of these rules to disable them or elevate them to errors.</span></span>

<span data-ttu-id="aa242-161">使用可能なコード品質ルールの完全な一覧については、「 [コード品質ルール](quality-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa242-161">For a full list of available code quality rules, see [Code quality rules](quality-rules/index.md).</span></span>

### <a name="enable-additional-rules"></a><span data-ttu-id="aa242-162">追加のルールを有効にする</span><span class="sxs-lookup"><span data-stu-id="aa242-162">Enable additional rules</span></span>

<span data-ttu-id="aa242-163">.NET 5.0 RC2 以降、.NET SDK には、すべての ["CA" コード品質ルール](/visualstudio/code-quality/code-analysis-for-managed-code-warnings)が付属しています。</span><span class="sxs-lookup"><span data-stu-id="aa242-163">Starting with .NET 5.0 RC2, the .NET SDK ships with all of the ["CA" code quality rules](/visualstudio/code-quality/code-analysis-for-managed-code-warnings).</span></span> <span data-ttu-id="aa242-164">各 .NET SDK バージョンに含まれる規則の完全な一覧については、「 [analyzer のリリース](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa242-164">For a full list of rules that are included with each .NET SDK version, see [analyzer releases](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>

#### <a name="default-analysis-mode"></a><span data-ttu-id="aa242-165">既定の分析モード</span><span class="sxs-lookup"><span data-stu-id="aa242-165">Default analysis mode</span></span>

<span data-ttu-id="aa242-166">既定の分析モードでは、一部のルールがビルド警告として [既定で有効になっ](#enabled-rules) ています。</span><span class="sxs-lookup"><span data-stu-id="aa242-166">In the default analysis mode, some rules are [enabled by default](#enabled-rules) as build warnings.</span></span> <span data-ttu-id="aa242-167">他の規則の中には、既定では Visual Studio IDE の提案としてのみ有効になっているものがあります。</span><span class="sxs-lookup"><span data-stu-id="aa242-167">Some other rules are enabled by default only as Visual Studio IDE suggestions with corresponding code fixes.</span></span> <span data-ttu-id="aa242-168">残りのルールは、既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="aa242-168">The remaining rules are disabled by default.</span></span> <span data-ttu-id="aa242-169">ルール [の完全な一覧](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md) には、各ルールの既定の重要度と、既定の分析モードでルールが既定で有効になっているかどうかが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa242-169">The [full list of rules](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md) includes each rule's default severity and whether or not the rule is enabled by default in the default analysis mode.</span></span>

#### <a name="custom-analysis-mode"></a><span data-ttu-id="aa242-170">カスタム分析モード</span><span class="sxs-lookup"><span data-stu-id="aa242-170">Custom analysis mode</span></span>

<span data-ttu-id="aa242-171">個々のルールまたはルールのカテゴリを有効または無効にするように、 [コード分析ルールを構成](configuration-options.md) することができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-171">You can [configure code analysis rules](configuration-options.md) to enable or disable an individual rule or a category of rules.</span></span> <span data-ttu-id="aa242-172">さらに、 [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) プロパティを使用して、次のいずれかのカスタム分析モードに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-172">Additionally, you can use the [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) property to switch to one of the following custom analysis modes:</span></span>

- <span data-ttu-id="aa242-173">_アグレッシブ_ モードまたは _オプトアウト_ モード: 既定では、すべてのルールがビルド警告として有効になります。</span><span class="sxs-lookup"><span data-stu-id="aa242-173">_Aggressive_ or _Opt-out_ mode: All rules are enabled by default as build warnings.</span></span> <span data-ttu-id="aa242-174">個々のルールを選択的に[オプトアウト](configuration-options.md)して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-174">You can selectively [opt out](configuration-options.md) of individual rules to disable them.</span></span>
- <span data-ttu-id="aa242-175">_控えめ_ または _オプトイン_ モード: 既定では、すべての規則が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="aa242-175">_Conservative_ or _Opt-in_ mode: All rules are disabled by default.</span></span> <span data-ttu-id="aa242-176">個々のルールを選択的に[オプトイン](configuration-options.md)して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-176">You can selectively [opt into](configuration-options.md) individual rules to enable them.</span></span>

### <a name="treat-warnings-as-errors"></a><span data-ttu-id="aa242-177">警告をエラーとして扱う</span><span class="sxs-lookup"><span data-stu-id="aa242-177">Treat warnings as errors</span></span>

<span data-ttu-id="aa242-178">`-warnaserror`プロジェクトをビルドするときにフラグを使用すると、コード分析のすべての警告もエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="aa242-178">If you use the `-warnaserror` flag when you build your projects, all code analysis warnings are also treated as errors.</span></span> <span data-ttu-id="aa242-179">コード品質警告 (CAxxxx) がの存在でエラーとして扱われないようにするには `-warnaserror` 、 `CodeAnalysisTreatWarningsAsErrors` プロジェクトファイルで MSBuild プロパティをに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="aa242-179">If you do not want code quality warnings (CAxxxx) to be treated as errors in presence of `-warnaserror`, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="aa242-180">コード分析の警告は引き続き表示されますが、ビルドが破損することはありません。</span><span class="sxs-lookup"><span data-stu-id="aa242-180">You'll still see any code analysis warnings, but they won't break your build.</span></span>

### <a name="latest-updates"></a><span data-ttu-id="aa242-181">最新の更新プログラム</span><span class="sxs-lookup"><span data-stu-id="aa242-181">Latest updates</span></span>

<span data-ttu-id="aa242-182">既定では、新しいバージョンの .NET SDK にアップグレードするときに、最新のコード分析規則と既定の規則の重大度を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa242-182">By default, you'll get the latest code analysis rules and default rule severities as you upgrade to newer versions of the .NET SDK.</span></span> <span data-ttu-id="aa242-183">この動作が望ましくない場合、たとえば、新しいルールが有効になっていないか無効になっていることを確認する場合は、次のいずれかの方法でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="aa242-183">If you don't want this behavior, for example, if you want to ensure that no new rules are enabled or disabled, you can override it in one of the following ways:</span></span>

- <span data-ttu-id="aa242-184">`AnalysisLevel`MSBuild プロパティを特定の値に設定して、そのセットに警告をロックします。</span><span class="sxs-lookup"><span data-stu-id="aa242-184">Set the `AnalysisLevel` MSBuild property to a specific value to lock the warnings to that set.</span></span> <span data-ttu-id="aa242-185">新しい SDK にアップグレードすると、これらの警告のバグ修正が引き続き行われますが、新しい警告は有効になりません。また、既存の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="aa242-185">When you upgrade to a newer SDK, you'll still get bug fixes for those warnings, but no new warnings will be enabled and no existing warnings will be disabled.</span></span> <span data-ttu-id="aa242-186">たとえば、.NET SDK のバージョン5.0 に付属するルールのセットをロックするには、プロジェクトファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="aa242-186">For example, to lock the set of rules to those that ship with version 5.0 of the .NET SDK, add the following entry to your project file.</span></span>

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > <span data-ttu-id="aa242-187">プロパティの既定値 `AnalysisLevel` はです `latest` 。これは、.net SDK の新しいバージョンに移行するときに、常に最新のコード分析規則を取得することを意味します。</span><span class="sxs-lookup"><span data-stu-id="aa242-187">The default value for the `AnalysisLevel` property is `latest`, which means you always get the latest code analysis rules as you move to newer versions of the .NET SDK.</span></span>

  <span data-ttu-id="aa242-188">詳細については、および使用可能な値の一覧については、「 [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa242-188">For more information, and to see a list of possible values, see [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).</span></span>

- <span data-ttu-id="aa242-189">.NET SDK の更新プログラムから規則の更新を分離するには、 [Microsoft Codeanalysis NuGet パッケージ](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="aa242-189">Install the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) to decouple rule updates from .NET SDK updates.</span></span> <span data-ttu-id="aa242-190">パッケージをインストールすると、組み込みの SDK アナライザーが無効になり、SDK に NuGet パッケージよりも新しいバージョンの analyzer アセンブリが含まれている場合は、ビルドの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="aa242-190">Installing the package turns off the built-in SDK analyzers and generates a build warning if the SDK contains a newer analyzer assembly version than that of the NuGet package.</span></span>

## <a name="code-style-analysis"></a><span data-ttu-id="aa242-191">コードスタイルの分析</span><span class="sxs-lookup"><span data-stu-id="aa242-191">Code style analysis</span></span>

<span data-ttu-id="aa242-192">[コードスタイル分析](/visualstudio/ide/editorconfig-code-style-settings-reference) ("ide xxxx" 規則) を使用すると、コードベースで一貫性のあるコードスタイルを定義および維持できます。</span><span class="sxs-lookup"><span data-stu-id="aa242-192">[Code style analysis](/visualstudio/ide/editorconfig-code-style-settings-reference) ("IDExxxx" rules) enables you to define and maintain consistent code style in your codebase.</span></span> <span data-ttu-id="aa242-193">既定の設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aa242-193">Following are the default settings:</span></span>

- <span data-ttu-id="aa242-194">コマンドラインビルド: コマンドラインビルドのすべての .NET プロジェクトに対して、コードスタイル分析が既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="aa242-194">Command line build: Code style analysis is disabled, by default, for all .NET projects on command-line builds.</span></span>
- <span data-ttu-id="aa242-195">Visual Studio: コードスタイル分析は、Visual Studio 内のすべての .NET プロジェクトに対して、 [コードリファクタリングクイックアクション](/visualstudio/ide/code-generation-in-visual-studio)として既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="aa242-195">Visual Studio: Code style analysis is enabled, by default, for all .NET projects inside Visual Studio as [code refactoring quick actions](/visualstudio/ide/code-generation-in-visual-studio).</span></span>

<span data-ttu-id="aa242-196">.NET 5.0 RC2 を開始すると、コマンドラインと Visual Studio の両方でビルドに対してコードスタイル分析を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-196">Starting .NET 5.0 RC2, you can enable code style analysis on build, both at the command line and inside Visual Studio.</span></span> <span data-ttu-id="aa242-197">コードスタイル違反は、"IDE" プレフィックスが付いた警告またはエラーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa242-197">Code style violations appear as warnings or errors with an "IDE" prefix.</span></span> <span data-ttu-id="aa242-198">これにより、ビルド時に一貫したコードスタイルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="aa242-198">This enables you to enforce consistent code styles at build time.</span></span>

> [!NOTE]
> <span data-ttu-id="aa242-199">コードスタイル分析機能は試験段階であり、.NET 5 リリースと .NET 6 リリース間で変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa242-199">The code style analysis feature is experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="aa242-200">ビルドでコードスタイル分析を有効にする手順:</span><span class="sxs-lookup"><span data-stu-id="aa242-200">Steps to enable code style analysis on build:</span></span>

1. <span data-ttu-id="aa242-201">MSBuild プロパティ [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) をに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="aa242-201">Set the MSBuild property [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) to `true`.</span></span>

1. <span data-ttu-id="aa242-202">*Editorconfig* ファイルで、ビルド時に実行する各 "IDE" コードスタイルルールを警告またはエラーとして [構成](configuration-options.md)します。</span><span class="sxs-lookup"><span data-stu-id="aa242-202">In an *.editorconfig* file, [configure](configuration-options.md) each "IDE" code style rule that you wish to run on build as a warning or an error.</span></span> <span data-ttu-id="aa242-203">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aa242-203">For example:</span></span>

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   <span data-ttu-id="aa242-204">または、[スタイル] カテゴリ全体を警告またはエラーとして構成し、既定では、ビルドで実行しない規則を選択的にオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa242-204">Alternatively, you can configure the entire "Style" category to be a warning or error, by default, and then selectively turn off rules that you don't want to run on build.</span></span> <span data-ttu-id="aa242-205">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aa242-205">For example:</span></span>

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

## <a name="suppress-a-warning"></a><span data-ttu-id="aa242-206">警告の非表示</span><span class="sxs-lookup"><span data-stu-id="aa242-206">Suppress a warning</span></span>

<span data-ttu-id="aa242-207">規則違反を抑制するには、その規則 ID の重大度オプションを `none` EditorConfig ファイルでに設定します。</span><span class="sxs-lookup"><span data-stu-id="aa242-207">To suppress a rule violation, set the severity option for that rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="aa242-208">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aa242-208">For example:</span></span>

```ini
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="aa242-209">Visual Studio には、コード分析規則からの警告を抑制するための追加の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="aa242-209">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="aa242-210">詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa242-210">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="aa242-211">規則の重大度の詳細については、「 [規則の重要度の構成](configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa242-211">For more information about rule severities, see [Configure rule severity](configuration-options.md#severity-level).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa242-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa242-212">See also</span></span>

- [<span data-ttu-id="aa242-213">コード品質分析ルールのリファレンス</span><span class="sxs-lookup"><span data-stu-id="aa242-213">Code quality analysis rule reference</span></span>](quality-rules/index.md)
- [<span data-ttu-id="aa242-214">コードスタイル分析規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="aa242-214">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="aa242-215">Visual Studio でのコード分析</span><span class="sxs-lookup"><span data-stu-id="aa242-215">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="aa242-216">.NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="aa242-216">.NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="aa242-217">チュートリアル: 最初のアナライザーとコード修正を作成する</span><span class="sxs-lookup"><span data-stu-id="aa242-217">Tutorial: Write your first analyzer and code fix</span></span>](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
