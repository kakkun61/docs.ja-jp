---
title: dotnet new コマンド
description: dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。
no-loc:
- ':::no-loc(Blazor):::'
- ':::no-loc(WebAssembly):::'
ms.date: 09/01/2020
ms.openlocfilehash: 4a4c8e2806fee663b5f6aa255a6f24250a072a85
ms.sourcegitcommit: 532b03d5bbab764d63356193b04cd2281bc01239
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2020
ms.locfileid: "92526615"
---
# <a name="dotnet-new"></a><span data-ttu-id="33330-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="33330-103">dotnet new</span></span>

<span data-ttu-id="33330-104">**この記事の対象:** ✔️ .NET Core 2.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="33330-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="33330-105">名前</span><span class="sxs-lookup"><span data-stu-id="33330-105">Name</span></span>

<span data-ttu-id="33330-106">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="33330-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="33330-107">構文</span><span class="sxs-lookup"><span data-stu-id="33330-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="33330-108">説明</span><span class="sxs-lookup"><span data-stu-id="33330-108">Description</span></span>

<span data-ttu-id="33330-109">`dotnet new` コマンドは、テンプレートに基づいて、.NET Core プロジェクトまたはその他の成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="33330-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="33330-110">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="33330-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="33330-111">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="33330-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="33330-112">引数</span><span class="sxs-lookup"><span data-stu-id="33330-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="33330-113">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="33330-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="33330-114">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="33330-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="33330-115">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33330-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="33330-116">`dotnet new --list` または `dotnet new -l` を実行すると、インストールされているすべてのテンプレートの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="33330-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="33330-117">`TEMPLATE` の値が返されたテーブルの「 **テンプレート** 」列または「 **短い形式の名前** 」列のテキストと完全に一致しない場合、それら 2 つの列で部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="33330-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="33330-118">.NET Core 3.0 SDK 以降では、次の条件で `dotnet new` コマンドを呼び出すと、CLI によって NuGet.org 内のテンプレートが検索されます。</span><span class="sxs-lookup"><span data-stu-id="33330-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="33330-119">`dotnet new` の呼び出し時に、CLI でテンプレートの一致を (部分的にも) 検出できない場合。</span><span class="sxs-lookup"><span data-stu-id="33330-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="33330-120">テンプレートの新しいバージョンが利用可能な場合。</span><span class="sxs-lookup"><span data-stu-id="33330-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="33330-121">この場合、プロジェクトまたは成果物が作成されますが、更新されたバージョンのテンプレートについて、CLI によって警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33330-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="33330-122">次の表は、.NET Core SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="33330-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="33330-123">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="33330-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="33330-124">短い名前のリンクをクリックすると、特定のテンプレート オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33330-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="33330-125">テンプレート</span><span class="sxs-lookup"><span data-stu-id="33330-125">Templates</span></span>                                    | <span data-ttu-id="33330-126">短い名前</span><span class="sxs-lookup"><span data-stu-id="33330-126">Short name</span></span>                      | <span data-ttu-id="33330-127">言語</span><span class="sxs-lookup"><span data-stu-id="33330-127">Language</span></span>     | <span data-ttu-id="33330-128">Tags</span><span class="sxs-lookup"><span data-stu-id="33330-128">Tags</span></span>                                  | <span data-ttu-id="33330-129">導入時期</span><span class="sxs-lookup"><span data-stu-id="33330-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="33330-130">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="33330-130">Console Application</span></span>                          | [<span data-ttu-id="33330-131">console</span><span class="sxs-lookup"><span data-stu-id="33330-131">console</span></span>](#console)             | <span data-ttu-id="33330-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33330-132">[C#], F#, VB</span></span> | <span data-ttu-id="33330-133">Common/Console</span><span class="sxs-lookup"><span data-stu-id="33330-133">Common/Console</span></span>                        | <span data-ttu-id="33330-134">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-134">1.0</span></span>        |
| <span data-ttu-id="33330-135">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="33330-135">Class library</span></span>                                | [<span data-ttu-id="33330-136">classlib</span><span class="sxs-lookup"><span data-stu-id="33330-136">classlib</span></span>](#classlib)           | <span data-ttu-id="33330-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33330-137">[C#], F#, VB</span></span> | <span data-ttu-id="33330-138">Common/Library</span><span class="sxs-lookup"><span data-stu-id="33330-138">Common/Library</span></span>                        | <span data-ttu-id="33330-139">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-139">1.0</span></span>        |
| <span data-ttu-id="33330-140">WPF アプリケーション</span><span class="sxs-lookup"><span data-stu-id="33330-140">WPF Application</span></span>                              | [<span data-ttu-id="33330-141">wpf</span><span class="sxs-lookup"><span data-stu-id="33330-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="33330-142">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="33330-142">[C#], VB</span></span>     | <span data-ttu-id="33330-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="33330-143">Common/WPF</span></span>                            | <span data-ttu-id="33330-144">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="33330-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="33330-145">WPF クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="33330-145">WPF Class library</span></span>                            | [<span data-ttu-id="33330-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="33330-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="33330-147">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="33330-147">[C#], VB</span></span>     | <span data-ttu-id="33330-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="33330-148">Common/WPF</span></span>                            | <span data-ttu-id="33330-149">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="33330-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="33330-150">WPF カスタム コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="33330-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="33330-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="33330-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="33330-152">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="33330-152">[C#], VB</span></span>     | <span data-ttu-id="33330-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="33330-153">Common/WPF</span></span>                            | <span data-ttu-id="33330-154">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="33330-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="33330-155">WPF ユーザー コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="33330-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="33330-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="33330-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="33330-157">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="33330-157">[C#], VB</span></span>     | <span data-ttu-id="33330-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="33330-158">Common/WPF</span></span>                            | <span data-ttu-id="33330-159">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="33330-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="33330-160">Windows フォーム (WinForms) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="33330-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="33330-161">winforms</span><span class="sxs-lookup"><span data-stu-id="33330-161">winforms</span></span>](#winforms)           | <span data-ttu-id="33330-162">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="33330-162">[C#], VB</span></span>     | <span data-ttu-id="33330-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="33330-163">Common/WinForms</span></span>                       | <span data-ttu-id="33330-164">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="33330-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="33330-165">Windows フォーム (WinForms) クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="33330-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="33330-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="33330-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="33330-167">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="33330-167">[C#], VB</span></span>     | <span data-ttu-id="33330-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="33330-168">Common/WinForms</span></span>                       | <span data-ttu-id="33330-169">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="33330-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="33330-170">Worker Service</span><span class="sxs-lookup"><span data-stu-id="33330-170">Worker Service</span></span>                               | [<span data-ttu-id="33330-171">worker</span><span class="sxs-lookup"><span data-stu-id="33330-171">worker</span></span>](#web-others)           | <span data-ttu-id="33330-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-172">[C#]</span></span>         | <span data-ttu-id="33330-173">Common/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="33330-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="33330-174">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-174">3.0</span></span>        |
| <span data-ttu-id="33330-175">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="33330-175">Unit Test Project</span></span>                            | [<span data-ttu-id="33330-176">mstest</span><span class="sxs-lookup"><span data-stu-id="33330-176">mstest</span></span>](#test)                 | <span data-ttu-id="33330-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33330-177">[C#], F#, VB</span></span> | <span data-ttu-id="33330-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="33330-178">Test/MSTest</span></span>                           | <span data-ttu-id="33330-179">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-179">1.0</span></span>        |
| <span data-ttu-id="33330-180">NUnit 3 テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="33330-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="33330-181">nunit</span><span class="sxs-lookup"><span data-stu-id="33330-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="33330-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33330-182">[C#], F#, VB</span></span> | <span data-ttu-id="33330-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="33330-183">Test/NUnit</span></span>                            | <span data-ttu-id="33330-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="33330-184">2.1.400</span></span>    |
| <span data-ttu-id="33330-185">NUnit 3 テスト項目</span><span class="sxs-lookup"><span data-stu-id="33330-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="33330-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33330-186">[C#], F#, VB</span></span> | <span data-ttu-id="33330-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="33330-187">Test/NUnit</span></span>                            | <span data-ttu-id="33330-188">2.2</span><span class="sxs-lookup"><span data-stu-id="33330-188">2.2</span></span>        |
| <span data-ttu-id="33330-189">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="33330-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="33330-190">xunit</span><span class="sxs-lookup"><span data-stu-id="33330-190">xunit</span></span>](#test)                  | <span data-ttu-id="33330-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33330-191">[C#], F#, VB</span></span> | <span data-ttu-id="33330-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="33330-192">Test/xUnit</span></span>                            | <span data-ttu-id="33330-193">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-193">1.0</span></span>        |
| <span data-ttu-id="33330-194">Razor コンポーネント</span><span class="sxs-lookup"><span data-stu-id="33330-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="33330-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-195">[C#]</span></span>         | <span data-ttu-id="33330-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="33330-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="33330-197">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-197">3.0</span></span>        |
| <span data-ttu-id="33330-198">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="33330-198">Razor Page</span></span>                                   | [<span data-ttu-id="33330-199">page</span><span class="sxs-lookup"><span data-stu-id="33330-199">page</span></span>](#page)                   | <span data-ttu-id="33330-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-200">[C#]</span></span>         | <span data-ttu-id="33330-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="33330-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="33330-202">2.0</span><span class="sxs-lookup"><span data-stu-id="33330-202">2.0</span></span>        |
| <span data-ttu-id="33330-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="33330-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="33330-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="33330-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="33330-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-205">[C#]</span></span>         | <span data-ttu-id="33330-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="33330-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="33330-207">2.0</span><span class="sxs-lookup"><span data-stu-id="33330-207">2.0</span></span>        |
| <span data-ttu-id="33330-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="33330-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="33330-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-209">[C#]</span></span>         | <span data-ttu-id="33330-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="33330-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="33330-211">2.0</span><span class="sxs-lookup"><span data-stu-id="33330-211">2.0</span></span>        |
| <span data-ttu-id="33330-212">:::no-loc(Blazor)::: サーバー アプリ</span><span class="sxs-lookup"><span data-stu-id="33330-212">:::no-loc(Blazor)::: Server App</span></span>                            | [<span data-ttu-id="33330-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="33330-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="33330-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-214">[C#]</span></span>         | <span data-ttu-id="33330-215">Web/:::no-loc(Blazor):::</span><span class="sxs-lookup"><span data-stu-id="33330-215">Web/:::no-loc(Blazor):::</span></span>                            | <span data-ttu-id="33330-216">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-216">3.0</span></span>        |
| <span data-ttu-id="33330-217">:::no-loc(Blazor)::: :::no-loc(WebAssembly)::: アプリ</span><span class="sxs-lookup"><span data-stu-id="33330-217">:::no-loc(Blazor)::: :::no-loc(WebAssembly)::: App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="33330-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-218">[C#]</span></span>         | <span data-ttu-id="33330-219">Web/:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span><span class="sxs-lookup"><span data-stu-id="33330-219">Web/:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span></span>                | <span data-ttu-id="33330-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="33330-220">3.1.300</span></span>    |
| <span data-ttu-id="33330-221">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="33330-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="33330-222">web</span><span class="sxs-lookup"><span data-stu-id="33330-222">web</span></span>](#web)                     | <span data-ttu-id="33330-223">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="33330-223">[C#], F#</span></span>     | <span data-ttu-id="33330-224">Web/Empty</span><span class="sxs-lookup"><span data-stu-id="33330-224">Web/Empty</span></span>                             | <span data-ttu-id="33330-225">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-225">1.0</span></span>        |
| <span data-ttu-id="33330-226">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="33330-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="33330-227">mvc</span><span class="sxs-lookup"><span data-stu-id="33330-227">mvc</span></span>](#web-options)             | <span data-ttu-id="33330-228">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="33330-228">[C#], F#</span></span>     | <span data-ttu-id="33330-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="33330-229">Web/MVC</span></span>                               | <span data-ttu-id="33330-230">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-230">1.0</span></span>        |
| <span data-ttu-id="33330-231">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="33330-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="33330-232">webapp、razor</span><span class="sxs-lookup"><span data-stu-id="33330-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="33330-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-233">[C#]</span></span>         | <span data-ttu-id="33330-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="33330-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="33330-235">2.2、2.0</span><span class="sxs-lookup"><span data-stu-id="33330-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="33330-236">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="33330-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="33330-237">angular</span><span class="sxs-lookup"><span data-stu-id="33330-237">angular</span></span>](#spa)                 | <span data-ttu-id="33330-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-238">[C#]</span></span>         | <span data-ttu-id="33330-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="33330-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="33330-240">2.0</span><span class="sxs-lookup"><span data-stu-id="33330-240">2.0</span></span>        |
| <span data-ttu-id="33330-241">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="33330-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="33330-242">react</span><span class="sxs-lookup"><span data-stu-id="33330-242">react</span></span>](#spa)                   | <span data-ttu-id="33330-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-243">[C#]</span></span>         | <span data-ttu-id="33330-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="33330-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="33330-245">2.0</span><span class="sxs-lookup"><span data-stu-id="33330-245">2.0</span></span>        |
| <span data-ttu-id="33330-246">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="33330-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="33330-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="33330-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="33330-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-248">[C#]</span></span>         | <span data-ttu-id="33330-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="33330-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="33330-250">2.0</span><span class="sxs-lookup"><span data-stu-id="33330-250">2.0</span></span>        |
| <span data-ttu-id="33330-251">Razor クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="33330-251">Razor Class Library</span></span>                          | [<span data-ttu-id="33330-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="33330-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="33330-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-253">[C#]</span></span>         | <span data-ttu-id="33330-254">Web/Razor/Library/Razor Class Library</span><span class="sxs-lookup"><span data-stu-id="33330-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="33330-255">2.1</span><span class="sxs-lookup"><span data-stu-id="33330-255">2.1</span></span>        |
| <span data-ttu-id="33330-256">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="33330-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="33330-257">webapi</span><span class="sxs-lookup"><span data-stu-id="33330-257">webapi</span></span>](#webapi)               | <span data-ttu-id="33330-258">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="33330-258">[C#], F#</span></span>     | <span data-ttu-id="33330-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="33330-259">Web/WebAPI</span></span>                            | <span data-ttu-id="33330-260">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-260">1.0</span></span>        |
| <span data-ttu-id="33330-261">ASP.NET Core gRPC サービス</span><span class="sxs-lookup"><span data-stu-id="33330-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="33330-262">grpc</span><span class="sxs-lookup"><span data-stu-id="33330-262">grpc</span></span>](#web-others)             | <span data-ttu-id="33330-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="33330-263">[C#]</span></span>         | <span data-ttu-id="33330-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="33330-264">Web/gRPC</span></span>                              | <span data-ttu-id="33330-265">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-265">3.0</span></span>        |
| <span data-ttu-id="33330-266">dotnet gitignore ファイル</span><span class="sxs-lookup"><span data-stu-id="33330-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="33330-267">構成</span><span class="sxs-lookup"><span data-stu-id="33330-267">Config</span></span>                                | <span data-ttu-id="33330-268">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-268">3.0</span></span>        |
| <span data-ttu-id="33330-269">global.json file</span><span class="sxs-lookup"><span data-stu-id="33330-269">global.json file</span></span>                             | [<span data-ttu-id="33330-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="33330-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="33330-271">構成</span><span class="sxs-lookup"><span data-stu-id="33330-271">Config</span></span>                                | <span data-ttu-id="33330-272">2.0</span><span class="sxs-lookup"><span data-stu-id="33330-272">2.0</span></span>        |
| <span data-ttu-id="33330-273">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="33330-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="33330-274">構成</span><span class="sxs-lookup"><span data-stu-id="33330-274">Config</span></span>                                | <span data-ttu-id="33330-275">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-275">1.0</span></span>        |
| <span data-ttu-id="33330-276">dotnet ローカル ツール マニフェスト ファイル</span><span class="sxs-lookup"><span data-stu-id="33330-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="33330-277">構成</span><span class="sxs-lookup"><span data-stu-id="33330-277">Config</span></span>                                | <span data-ttu-id="33330-278">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-278">3.0</span></span>        |
| <span data-ttu-id="33330-279">Web 構成</span><span class="sxs-lookup"><span data-stu-id="33330-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="33330-280">構成</span><span class="sxs-lookup"><span data-stu-id="33330-280">Config</span></span>                                | <span data-ttu-id="33330-281">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-281">1.0</span></span>        |
| <span data-ttu-id="33330-282">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="33330-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="33330-283">ソリューション</span><span class="sxs-lookup"><span data-stu-id="33330-283">Solution</span></span>                              | <span data-ttu-id="33330-284">1.0</span><span class="sxs-lookup"><span data-stu-id="33330-284">1.0</span></span>        |
| <span data-ttu-id="33330-285">プロトコル バッファー ファイル</span><span class="sxs-lookup"><span data-stu-id="33330-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="33330-286">proto</span><span class="sxs-lookup"><span data-stu-id="33330-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="33330-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="33330-287">Web/gRPC</span></span>                              | <span data-ttu-id="33330-288">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="33330-289">オプション</span><span class="sxs-lookup"><span data-stu-id="33330-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="33330-290">指定されたコマンドが実行されてテンプレートが作成された場合に起きることの概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33330-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="33330-291">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="33330-292">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="33330-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="33330-293">これは、選択されたテンプレートによって出力ディレクトリ内の既存のファイルがオーバーライドされる場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="33330-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="33330-294">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="33330-294">Prints out help for the command.</span></span> <span data-ttu-id="33330-295">`dotnet new` コマンド自体、または任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="33330-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="33330-296">たとえば、`dotnet new mvc --help` のようにします。</span><span class="sxs-lookup"><span data-stu-id="33330-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="33330-297">指定された `PATH` または `NUGET_ID` からテンプレート パックがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="33330-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="33330-298">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33330-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="33330-299">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="33330-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="33330-300">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33330-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="33330-301">このコマンドの実行時にテンプレートのバージョンが既にインストールされていたら、テンプレートは指定されたバージョンか、最新の安定したバージョン (バージョンが指定されていない場合) に更新されます。</span><span class="sxs-lookup"><span data-stu-id="33330-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="33330-302">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33330-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="33330-303">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="33330-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="33330-304">名前が指定されていない場合、すべてのテンプレートが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="33330-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="33330-305">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="33330-305">The language of the template to create.</span></span> <span data-ttu-id="33330-306">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="33330-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="33330-307">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="33330-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="33330-308">一部のシェルは `#` を特殊文字として解釈します。</span><span class="sxs-lookup"><span data-stu-id="33330-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="33330-309">そのような場合は、言語パラメーター値を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="33330-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="33330-310">たとえば、`dotnet new console -lang "F#"` のようにします。</span><span class="sxs-lookup"><span data-stu-id="33330-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="33330-311">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="33330-311">The name for the created output.</span></span> <span data-ttu-id="33330-312">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="33330-313">インストール中に使用する NuGet ソースを 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="33330-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="33330-314">.NET Core 2.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="33330-315">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="33330-315">Location to place the generated output.</span></span> <span data-ttu-id="33330-316">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="33330-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="33330-317">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="33330-317">Filters templates based on available types.</span></span> <span data-ttu-id="33330-318">事前定義されている値は `project` および `item` です。</span><span class="sxs-lookup"><span data-stu-id="33330-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="33330-319">指定された `PATH` または `NUGET_ID` でテンプレート パックがアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="33330-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="33330-320">`<PATH|NUGET_ID>` 値が指定されないと、現在インストールされているすべてのテンプレート パックとそれらに関連付けられているテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33330-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="33330-321">`NUGET_ID` を指定した場合、バージョン番号は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="33330-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="33330-322">このオプションにパラメーターを指定しないと、コマンドによって、インストールされたテンプレートとそれらに関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33330-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="33330-323">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33330-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="33330-324">たとえば、 *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、 *./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="33330-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="33330-325">テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="33330-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="33330-326">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認され、それらがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="33330-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="33330-327">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="33330-328">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認されます。</span><span class="sxs-lookup"><span data-stu-id="33330-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="33330-329">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="33330-330">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="33330-330">Template options</span></span>

<span data-ttu-id="33330-331">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="33330-331">Each project template may have additional options available.</span></span> <span data-ttu-id="33330-332">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="33330-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="33330-333">console</span><span class="sxs-lookup"><span data-stu-id="33330-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33330-334">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-335">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="33330-336">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-337">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-337">SDK version</span></span> | <span data-ttu-id="33330-338">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-339">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-340">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="33330-341">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33330-342">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="33330-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="33330-343">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="33330-343">Not supported for F#.</span></span> <span data-ttu-id="33330-344">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33330-345">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33330-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-346">指定した場合、プロジェクトの作成中には暗黙的な復元が実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="33330-347">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-347">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="33330-348">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-348">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="33330-349">classlib</span><span class="sxs-lookup"><span data-stu-id="33330-349">classlib</span></span>

- <span data-ttu-id="33330-350">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-350">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="33330-351">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-351">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-352">値: .NET Core クラス ライブラリを作成するには `netcoreapp<version>`、.NET 標準クラス ライブラリを作成するには `netstandard<version>` です。</span><span class="sxs-lookup"><span data-stu-id="33330-352">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="33330-353">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="33330-353">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="33330-354">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-354">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33330-355">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="33330-355">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="33330-356">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="33330-356">Not supported for F#.</span></span> <span data-ttu-id="33330-357">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-357">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33330-358">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33330-358">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-359">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-359">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-360">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-360">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="33330-361">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="33330-361">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="33330-362">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-362">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="33330-363">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-363">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-364">既定値は `netcoreapp3.1` です。</span><span class="sxs-lookup"><span data-stu-id="33330-364">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="33330-365">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-365">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="33330-366">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-366">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33330-367">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="33330-367">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="33330-368">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33330-368">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-369">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-369">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-370">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-370">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="33330-371">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="33330-371">winforms, winformslib</span></span>

- <span data-ttu-id="33330-372">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-372">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="33330-373">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-373">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33330-374">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="33330-374">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="33330-375">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33330-375">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-376">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-376">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-377">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-377">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="33330-378">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="33330-378">worker, grpc</span></span>

- <span data-ttu-id="33330-379">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-379">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="33330-380">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-380">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-381">既定値は `netcoreapp3.1` です。</span><span class="sxs-lookup"><span data-stu-id="33330-381">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="33330-382">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-382">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33330-383">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="33330-383">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-384">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-384">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-385">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-385">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="33330-386">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="33330-386">mstest, xunit</span></span>

- <span data-ttu-id="33330-387">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-387">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="33330-388">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-389">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="33330-389">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="33330-390">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-390">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-391">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-391">SDK version</span></span> | <span data-ttu-id="33330-392">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-392">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-393">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-393">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-394">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-394">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="33330-395">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="33330-395">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-396">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-396">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-397">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-397">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="33330-398">nunit</span><span class="sxs-lookup"><span data-stu-id="33330-398">nunit</span></span>

- <span data-ttu-id="33330-399">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-399">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="33330-400">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-400">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="33330-401">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-401">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-402">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-402">SDK version</span></span> | <span data-ttu-id="33330-403">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-403">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-404">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-404">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-405">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-405">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33330-406">2.2</span><span class="sxs-lookup"><span data-stu-id="33330-406">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="33330-407">2.1</span><span class="sxs-lookup"><span data-stu-id="33330-407">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="33330-408">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="33330-408">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-409">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-409">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-410">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-410">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="33330-411">ページ (page)</span><span class="sxs-lookup"><span data-stu-id="33330-411">page</span></span>

- <span data-ttu-id="33330-412">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-412">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="33330-413">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="33330-413">Namespace for the generated code.</span></span> <span data-ttu-id="33330-414">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="33330-414">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="33330-415">PageModel なしでページが作成されます。</span><span class="sxs-lookup"><span data-stu-id="33330-415">Creates the page without a PageModel.</span></span>

<span data-ttu-id="33330-416">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-416">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="33330-417">viewimports、proto</span><span class="sxs-lookup"><span data-stu-id="33330-417">viewimports, proto</span></span>

- <span data-ttu-id="33330-418">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-418">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="33330-419">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="33330-419">Namespace for the generated code.</span></span> <span data-ttu-id="33330-420">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="33330-420">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="33330-421">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-421">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="33330-422">blazorserver</span><span class="sxs-lookup"><span data-stu-id="33330-422">blazorserver</span></span>

- <span data-ttu-id="33330-423">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-423">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="33330-424">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="33330-424">The type of authentication to use.</span></span> <span data-ttu-id="33330-425">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="33330-425">The possible values are:</span></span>

  - <span data-ttu-id="33330-426">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="33330-426">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33330-427">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="33330-427">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="33330-428">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="33330-428">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="33330-429">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="33330-429">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="33330-430">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="33330-430">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="33330-431">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="33330-431">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="33330-432">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="33330-432">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="33330-433">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-433">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-434">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="33330-434">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="33330-435">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-435">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="33330-436">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-436">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="33330-437">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-437">The reset password policy ID for this project.</span></span> <span data-ttu-id="33330-438">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-438">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="33330-439">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-439">The edit profile policy ID for this project.</span></span> <span data-ttu-id="33330-440">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-440">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="33330-441">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="33330-441">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="33330-442">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-442">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="33330-443">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="33330-443">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="33330-444">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-444">The Client ID for this project.</span></span> <span data-ttu-id="33330-445">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-445">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="33330-446">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="33330-446">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="33330-447">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="33330-447">The domain for the directory tenant.</span></span> <span data-ttu-id="33330-448">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-448">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-449">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="33330-449">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="33330-450">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-450">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="33330-451">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-451">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33330-452">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="33330-452">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="33330-453">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="33330-453">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="33330-454">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-454">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-455">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="33330-455">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="33330-456">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="33330-456">Allows this application read-access to the directory.</span></span> <span data-ttu-id="33330-457">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-457">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33330-458">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="33330-458">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="33330-459">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="33330-459">Turns off HTTPS.</span></span> <span data-ttu-id="33330-460">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が `--auth` 用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-460">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33330-461">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-461">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33330-462">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-462">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-463">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-463">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-464">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-464">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="33330-465">web</span><span class="sxs-lookup"><span data-stu-id="33330-465">web</span></span>

- <span data-ttu-id="33330-466">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-466">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="33330-467">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="33330-467">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33330-468">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-469">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="33330-469">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33330-470">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-470">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-471">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-471">SDK version</span></span> | <span data-ttu-id="33330-472">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-472">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-473">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-473">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-474">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-474">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33330-475">2.1</span><span class="sxs-lookup"><span data-stu-id="33330-475">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="33330-476">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="33330-477">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="33330-477">Turns off HTTPS.</span></span>

<span data-ttu-id="33330-478">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-478">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="33330-479">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="33330-479">mvc, webapp</span></span>

- <span data-ttu-id="33330-480">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-480">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="33330-481">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="33330-481">The type of authentication to use.</span></span> <span data-ttu-id="33330-482">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="33330-482">The possible values are:</span></span>

  - <span data-ttu-id="33330-483">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="33330-483">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33330-484">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="33330-484">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="33330-485">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="33330-485">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="33330-486">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="33330-486">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="33330-487">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="33330-487">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="33330-488">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="33330-488">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="33330-489">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="33330-489">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="33330-490">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-490">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-491">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="33330-491">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="33330-492">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-492">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="33330-493">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-493">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="33330-494">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-494">The reset password policy ID for this project.</span></span> <span data-ttu-id="33330-495">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-495">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="33330-496">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-496">The edit profile policy ID for this project.</span></span> <span data-ttu-id="33330-497">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-497">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="33330-498">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="33330-498">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="33330-499">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-499">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="33330-500">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="33330-500">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="33330-501">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-501">The Client ID for this project.</span></span> <span data-ttu-id="33330-502">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-502">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="33330-503">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="33330-503">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="33330-504">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="33330-504">The domain for the directory tenant.</span></span> <span data-ttu-id="33330-505">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-506">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="33330-506">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="33330-507">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-507">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="33330-508">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-508">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33330-509">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="33330-509">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="33330-510">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="33330-510">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="33330-511">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-511">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-512">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="33330-512">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="33330-513">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="33330-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="33330-514">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-514">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33330-515">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="33330-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="33330-516">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="33330-516">Turns off HTTPS.</span></span> <span data-ttu-id="33330-517">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-517">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33330-518">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33330-519">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33330-520">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-521">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="33330-521">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="33330-522">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-523">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-523">SDK version</span></span> | <span data-ttu-id="33330-524">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-525">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-526">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-526">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="33330-527">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-527">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="33330-528">プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="33330-528">Includes BrowserLink in the project.</span></span> <span data-ttu-id="33330-529">.NET Core 2.2 および 3.1 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="33330-529">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="33330-530">デバッグ ビルドで [Razor ランタイム コンパイル](/aspnet/core/mvc/views/view-compilation#runtime-compilation)を使用するようにプロジェクトが構成されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="33330-530">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="33330-531">.NET Core 3.1.201 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="33330-531">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="33330-532">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-532">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="33330-533">angular、react</span><span class="sxs-lookup"><span data-stu-id="33330-533">angular, react</span></span>

- <span data-ttu-id="33330-534">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-534">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="33330-535">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="33330-535">The type of authentication to use.</span></span> <span data-ttu-id="33330-536">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-536">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="33330-537">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="33330-537">The possible values are:</span></span>

  - <span data-ttu-id="33330-538">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="33330-538">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33330-539">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="33330-539">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33330-540">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="33330-540">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="33330-541">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="33330-542">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="33330-542">Turns off HTTPS.</span></span> <span data-ttu-id="33330-543">このオプションは、認証が `None` の場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-543">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33330-544">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-544">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33330-545">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-545">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-546">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-546">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33330-547">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-547">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-548">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="33330-548">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33330-549">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-549">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-550">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-550">SDK version</span></span> | <span data-ttu-id="33330-551">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-551">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-552">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-552">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-553">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-553">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33330-554">2.1</span><span class="sxs-lookup"><span data-stu-id="33330-554">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="33330-555">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-555">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="33330-556">reactredux</span><span class="sxs-lookup"><span data-stu-id="33330-556">reactredux</span></span>

- <span data-ttu-id="33330-557">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-557">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="33330-558">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="33330-558">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33330-559">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-559">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-560">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="33330-560">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33330-561">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-561">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-562">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-562">SDK version</span></span> | <span data-ttu-id="33330-563">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-563">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-564">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-564">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-565">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-565">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33330-566">2.1</span><span class="sxs-lookup"><span data-stu-id="33330-566">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="33330-567">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-567">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="33330-568">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="33330-568">Turns off HTTPS.</span></span>

<span data-ttu-id="33330-569">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-569">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="33330-570">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="33330-570">razorclasslib</span></span>

- <span data-ttu-id="33330-571">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-571">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="33330-572">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-572">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="33330-573">このライブラリへのコンポーネントに加え、従来の Razor ページとビューの追加がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="33330-573">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="33330-574">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="33330-574">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="33330-575">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-575">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="33330-576">webapi</span><span class="sxs-lookup"><span data-stu-id="33330-576">webapi</span></span>

- <span data-ttu-id="33330-577">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-577">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="33330-578">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="33330-578">The type of authentication to use.</span></span> <span data-ttu-id="33330-579">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="33330-579">The possible values are:</span></span>

  - <span data-ttu-id="33330-580">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="33330-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33330-581">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="33330-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="33330-582">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="33330-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="33330-583">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="33330-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="33330-584">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="33330-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="33330-585">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="33330-586">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="33330-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="33330-587">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="33330-588">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="33330-589">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="33330-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="33330-590">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33330-591">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="33330-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="33330-592">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-592">The Client ID for this project.</span></span> <span data-ttu-id="33330-593">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="33330-594">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="33330-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="33330-595">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="33330-595">The domain for the directory tenant.</span></span> <span data-ttu-id="33330-596">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="33330-597">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="33330-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="33330-598">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="33330-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="33330-599">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="33330-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33330-600">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="33330-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="33330-601">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="33330-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="33330-602">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33330-603">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="33330-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="33330-604">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="33330-604">Turns off HTTPS.</span></span> <span data-ttu-id="33330-605">`app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。</span><span class="sxs-lookup"><span data-stu-id="33330-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="33330-606">このオプションは、`IndividualB2C` または `SingleOrg` が認証用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33330-607">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33330-608">`IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="33330-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33330-609">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33330-610">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="33330-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33330-611">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="33330-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33330-612">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="33330-612">SDK version</span></span> | <span data-ttu-id="33330-613">既定値</span><span class="sxs-lookup"><span data-stu-id="33330-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33330-614">3.1</span><span class="sxs-lookup"><span data-stu-id="33330-614">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33330-615">3.0</span><span class="sxs-lookup"><span data-stu-id="33330-615">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33330-616">2.1</span><span class="sxs-lookup"><span data-stu-id="33330-616">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="33330-617">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="33330-617">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="33330-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="33330-618">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="33330-619">globaljson</span><span class="sxs-lookup"><span data-stu-id="33330-619">globaljson</span></span>

- <span data-ttu-id="33330-620">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="33330-620">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="33330-621">*global.json* ファイル内で使用する .NET Core SDK のバージョンが指定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-621">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="33330-622">使用例</span><span class="sxs-lookup"><span data-stu-id="33330-622">Examples</span></span>

- <span data-ttu-id="33330-623">テンプレート名を指定することによって、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="33330-623">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="33330-624">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="33330-624">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="33330-625">指定されたディレクトリ内に .NET Standard クラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="33330-625">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="33330-626">認証なしで、現在のディレクトリに新しい ASP.NET Core C# MVC プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="33330-626">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="33330-627">新しい xUnit プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="33330-627">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="33330-628">シングル ページ アプリケーション (SPA) テンプレートに使用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="33330-628">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="33330-629">部分文字列 *we* に一致するすべてのテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="33330-629">List all templates matching the *we* substring.</span></span> <span data-ttu-id="33330-630">完全一致が見つからないので、短い名前と名前の両方の列に対して部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="33330-630">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="33330-631">*ng* に一致するテンプレートの呼び出しを試みます。</span><span class="sxs-lookup"><span data-stu-id="33330-631">Attempt to invoke the template matching *ng* .</span></span> <span data-ttu-id="33330-632">一致が 1 つだけでない場合、部分的に一致するテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="33330-632">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="33330-633">ASP.NET Core 用の SPA テンプレートのバージョン 2.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="33330-633">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="33330-634">インストールされているテンプレートとそれらに関する詳細や、それらのアンインストール方法を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="33330-634">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="33330-635">現在のディレクトリに *global.json* が作成され、SDK バージョンが 3.1.101 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="33330-635">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="33330-636">関連項目</span><span class="sxs-lookup"><span data-stu-id="33330-636">See also</span></span>

- [<span data-ttu-id="33330-637">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="33330-637">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="33330-638">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="33330-638">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="33330-639">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="33330-639">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="33330-640">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="33330-640">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
