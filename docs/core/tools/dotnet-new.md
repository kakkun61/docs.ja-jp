---
title: dotnet new コマンド
description: dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。
no-loc:
- 'Blazor'
- 'WebAssembly'
ms.date: 09/04/2020
ms.openlocfilehash: 2ee06c37cd950f3b9771db2f30fe353435641d67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400592"
---
# <a name="dotnet-new"></a><span data-ttu-id="e988c-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="e988c-103">dotnet new</span></span>

<span data-ttu-id="e988c-104">**この記事の対象:** ✔️ .NET Core 2.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e988c-105">名前</span><span class="sxs-lookup"><span data-stu-id="e988c-105">Name</span></span>

<span data-ttu-id="e988c-106">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e988c-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e988c-107">構文</span><span class="sxs-lookup"><span data-stu-id="e988c-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="e988c-108">説明</span><span class="sxs-lookup"><span data-stu-id="e988c-108">Description</span></span>

<span data-ttu-id="e988c-109">`dotnet new` コマンドは、テンプレートに基づいて、.NET Core プロジェクトまたはその他の成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="e988c-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="e988c-110">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="e988c-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="e988c-111">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="e988c-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e988c-112">引数</span><span class="sxs-lookup"><span data-stu-id="e988c-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="e988c-113">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="e988c-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="e988c-114">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e988c-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="e988c-115">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e988c-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="e988c-116">`dotnet new --list` または `dotnet new -l` を実行すると、インストールされているすべてのテンプレートの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="e988c-117">`TEMPLATE` の値が返されたテーブルの「 **テンプレート** 」列または「 **短い形式の名前** 」列のテキストと完全に一致しない場合、それら 2 つの列で部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="e988c-118">.NET Core 3.0 SDK 以降では、次の条件で `dotnet new` コマンドを呼び出すと、CLI によって NuGet.org 内のテンプレートが検索されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="e988c-119">`dotnet new` の呼び出し時に、CLI でテンプレートの一致を (部分的にも) 検出できない場合。</span><span class="sxs-lookup"><span data-stu-id="e988c-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="e988c-120">テンプレートの新しいバージョンが利用可能な場合。</span><span class="sxs-lookup"><span data-stu-id="e988c-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="e988c-121">この場合、プロジェクトまたは成果物が作成されますが、更新されたバージョンのテンプレートについて、CLI によって警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="e988c-122">次の表は、.NET Core SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e988c-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="e988c-123">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="e988c-124">短い名前のリンクをクリックすると、特定のテンプレート オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="e988c-125">テンプレート</span><span class="sxs-lookup"><span data-stu-id="e988c-125">Templates</span></span>                                    | <span data-ttu-id="e988c-126">短い名前</span><span class="sxs-lookup"><span data-stu-id="e988c-126">Short name</span></span>                      | <span data-ttu-id="e988c-127">言語</span><span class="sxs-lookup"><span data-stu-id="e988c-127">Language</span></span>     | <span data-ttu-id="e988c-128">Tags</span><span class="sxs-lookup"><span data-stu-id="e988c-128">Tags</span></span>                                  | <span data-ttu-id="e988c-129">導入時期</span><span class="sxs-lookup"><span data-stu-id="e988c-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="e988c-130">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e988c-130">Console Application</span></span>                          | [<span data-ttu-id="e988c-131">console</span><span class="sxs-lookup"><span data-stu-id="e988c-131">console</span></span>](#console)             | <span data-ttu-id="e988c-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e988c-132">[C#], F#, VB</span></span> | <span data-ttu-id="e988c-133">Common/Console</span><span class="sxs-lookup"><span data-stu-id="e988c-133">Common/Console</span></span>                        | <span data-ttu-id="e988c-134">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-134">1.0</span></span>        |
| <span data-ttu-id="e988c-135">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e988c-135">Class library</span></span>                                | [<span data-ttu-id="e988c-136">classlib</span><span class="sxs-lookup"><span data-stu-id="e988c-136">classlib</span></span>](#classlib)           | <span data-ttu-id="e988c-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e988c-137">[C#], F#, VB</span></span> | <span data-ttu-id="e988c-138">Common/Library</span><span class="sxs-lookup"><span data-stu-id="e988c-138">Common/Library</span></span>                        | <span data-ttu-id="e988c-139">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-139">1.0</span></span>        |
| <span data-ttu-id="e988c-140">WPF アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e988c-140">WPF Application</span></span>                              | [<span data-ttu-id="e988c-141">wpf</span><span class="sxs-lookup"><span data-stu-id="e988c-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="e988c-142">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="e988c-142">[C#], VB</span></span>     | <span data-ttu-id="e988c-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="e988c-143">Common/WPF</span></span>                            | <span data-ttu-id="e988c-144">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="e988c-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e988c-145">WPF クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e988c-145">WPF Class library</span></span>                            | [<span data-ttu-id="e988c-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="e988c-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="e988c-147">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="e988c-147">[C#], VB</span></span>     | <span data-ttu-id="e988c-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="e988c-148">Common/WPF</span></span>                            | <span data-ttu-id="e988c-149">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="e988c-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e988c-150">WPF カスタム コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e988c-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="e988c-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="e988c-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="e988c-152">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="e988c-152">[C#], VB</span></span>     | <span data-ttu-id="e988c-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="e988c-153">Common/WPF</span></span>                            | <span data-ttu-id="e988c-154">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="e988c-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e988c-155">WPF ユーザー コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e988c-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="e988c-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="e988c-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="e988c-157">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="e988c-157">[C#], VB</span></span>     | <span data-ttu-id="e988c-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="e988c-158">Common/WPF</span></span>                            | <span data-ttu-id="e988c-159">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="e988c-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e988c-160">Windows フォーム (WinForms) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e988c-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="e988c-161">winforms</span><span class="sxs-lookup"><span data-stu-id="e988c-161">winforms</span></span>](#winforms)           | <span data-ttu-id="e988c-162">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="e988c-162">[C#], VB</span></span>     | <span data-ttu-id="e988c-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="e988c-163">Common/WinForms</span></span>                       | <span data-ttu-id="e988c-164">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="e988c-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e988c-165">Windows フォーム (WinForms) クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e988c-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="e988c-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="e988c-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="e988c-167">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="e988c-167">[C#], VB</span></span>     | <span data-ttu-id="e988c-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="e988c-168">Common/WinForms</span></span>                       | <span data-ttu-id="e988c-169">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="e988c-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e988c-170">Worker Service</span><span class="sxs-lookup"><span data-stu-id="e988c-170">Worker Service</span></span>                               | [<span data-ttu-id="e988c-171">worker</span><span class="sxs-lookup"><span data-stu-id="e988c-171">worker</span></span>](#web-others)           | <span data-ttu-id="e988c-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-172">[C#]</span></span>         | <span data-ttu-id="e988c-173">Common/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="e988c-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="e988c-174">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-174">3.0</span></span>        |
| <span data-ttu-id="e988c-175">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="e988c-175">Unit Test Project</span></span>                            | [<span data-ttu-id="e988c-176">mstest</span><span class="sxs-lookup"><span data-stu-id="e988c-176">mstest</span></span>](#test)                 | <span data-ttu-id="e988c-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e988c-177">[C#], F#, VB</span></span> | <span data-ttu-id="e988c-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="e988c-178">Test/MSTest</span></span>                           | <span data-ttu-id="e988c-179">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-179">1.0</span></span>        |
| <span data-ttu-id="e988c-180">NUnit 3 テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="e988c-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="e988c-181">nunit</span><span class="sxs-lookup"><span data-stu-id="e988c-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="e988c-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e988c-182">[C#], F#, VB</span></span> | <span data-ttu-id="e988c-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="e988c-183">Test/NUnit</span></span>                            | <span data-ttu-id="e988c-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="e988c-184">2.1.400</span></span>    |
| <span data-ttu-id="e988c-185">NUnit 3 テスト項目</span><span class="sxs-lookup"><span data-stu-id="e988c-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="e988c-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e988c-186">[C#], F#, VB</span></span> | <span data-ttu-id="e988c-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="e988c-187">Test/NUnit</span></span>                            | <span data-ttu-id="e988c-188">2.2</span><span class="sxs-lookup"><span data-stu-id="e988c-188">2.2</span></span>        |
| <span data-ttu-id="e988c-189">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="e988c-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="e988c-190">xunit</span><span class="sxs-lookup"><span data-stu-id="e988c-190">xunit</span></span>](#test)                  | <span data-ttu-id="e988c-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e988c-191">[C#], F#, VB</span></span> | <span data-ttu-id="e988c-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="e988c-192">Test/xUnit</span></span>                            | <span data-ttu-id="e988c-193">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-193">1.0</span></span>        |
| <span data-ttu-id="e988c-194">Razor コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e988c-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="e988c-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-195">[C#]</span></span>         | <span data-ttu-id="e988c-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e988c-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="e988c-197">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-197">3.0</span></span>        |
| <span data-ttu-id="e988c-198">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="e988c-198">Razor Page</span></span>                                   | [<span data-ttu-id="e988c-199">page</span><span class="sxs-lookup"><span data-stu-id="e988c-199">page</span></span>](#page)                   | <span data-ttu-id="e988c-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-200">[C#]</span></span>         | <span data-ttu-id="e988c-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e988c-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="e988c-202">2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-202">2.0</span></span>        |
| <span data-ttu-id="e988c-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="e988c-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="e988c-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="e988c-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="e988c-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-205">[C#]</span></span>         | <span data-ttu-id="e988c-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e988c-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="e988c-207">2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-207">2.0</span></span>        |
| <span data-ttu-id="e988c-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="e988c-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="e988c-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-209">[C#]</span></span>         | <span data-ttu-id="e988c-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e988c-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="e988c-211">2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-211">2.0</span></span>        |
| <span data-ttu-id="e988c-212">Blazor サーバー アプリ</span><span class="sxs-lookup"><span data-stu-id="e988c-212">Blazor Server App</span></span>                            | [<span data-ttu-id="e988c-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="e988c-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="e988c-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-214">[C#]</span></span>         | <span data-ttu-id="e988c-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="e988c-215">Web/Blazor</span></span>                            | <span data-ttu-id="e988c-216">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-216">3.0</span></span>        |
| <span data-ttu-id="e988c-217">Blazor WebAssembly アプリ</span><span class="sxs-lookup"><span data-stu-id="e988c-217">Blazor WebAssembly App</span></span>                       | [<span data-ttu-id="e988c-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="e988c-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="e988c-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-219">[C#]</span></span>         | <span data-ttu-id="e988c-220">Web/Blazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="e988c-220">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="e988c-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="e988c-221">3.1.300</span></span>    |
| <span data-ttu-id="e988c-222">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="e988c-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="e988c-223">web</span><span class="sxs-lookup"><span data-stu-id="e988c-223">web</span></span>](#web)                     | <span data-ttu-id="e988c-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e988c-224">[C#], F#</span></span>     | <span data-ttu-id="e988c-225">Web/Empty</span><span class="sxs-lookup"><span data-stu-id="e988c-225">Web/Empty</span></span>                             | <span data-ttu-id="e988c-226">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-226">1.0</span></span>        |
| <span data-ttu-id="e988c-227">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="e988c-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="e988c-228">mvc</span><span class="sxs-lookup"><span data-stu-id="e988c-228">mvc</span></span>](#web-options)             | <span data-ttu-id="e988c-229">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e988c-229">[C#], F#</span></span>     | <span data-ttu-id="e988c-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="e988c-230">Web/MVC</span></span>                               | <span data-ttu-id="e988c-231">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-231">1.0</span></span>        |
| <span data-ttu-id="e988c-232">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="e988c-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="e988c-233">webapp、razor</span><span class="sxs-lookup"><span data-stu-id="e988c-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="e988c-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-234">[C#]</span></span>         | <span data-ttu-id="e988c-235">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="e988c-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="e988c-236">2.2、2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="e988c-237">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e988c-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="e988c-238">angular</span><span class="sxs-lookup"><span data-stu-id="e988c-238">angular</span></span>](#spa)                 | <span data-ttu-id="e988c-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-239">[C#]</span></span>         | <span data-ttu-id="e988c-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e988c-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e988c-241">2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-241">2.0</span></span>        |
| <span data-ttu-id="e988c-242">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e988c-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="e988c-243">react</span><span class="sxs-lookup"><span data-stu-id="e988c-243">react</span></span>](#spa)                   | <span data-ttu-id="e988c-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-244">[C#]</span></span>         | <span data-ttu-id="e988c-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e988c-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e988c-246">2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-246">2.0</span></span>        |
| <span data-ttu-id="e988c-247">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e988c-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="e988c-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="e988c-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="e988c-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-249">[C#]</span></span>         | <span data-ttu-id="e988c-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e988c-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e988c-251">2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-251">2.0</span></span>        |
| <span data-ttu-id="e988c-252">Razor クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e988c-252">Razor Class Library</span></span>                          | [<span data-ttu-id="e988c-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="e988c-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="e988c-254">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-254">[C#]</span></span>         | <span data-ttu-id="e988c-255">Web/Razor/Library/Razor Class Library</span><span class="sxs-lookup"><span data-stu-id="e988c-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="e988c-256">2.1</span><span class="sxs-lookup"><span data-stu-id="e988c-256">2.1</span></span>        |
| <span data-ttu-id="e988c-257">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="e988c-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="e988c-258">webapi</span><span class="sxs-lookup"><span data-stu-id="e988c-258">webapi</span></span>](#webapi)               | <span data-ttu-id="e988c-259">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e988c-259">[C#], F#</span></span>     | <span data-ttu-id="e988c-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="e988c-260">Web/WebAPI</span></span>                            | <span data-ttu-id="e988c-261">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-261">1.0</span></span>        |
| <span data-ttu-id="e988c-262">ASP.NET Core gRPC サービス</span><span class="sxs-lookup"><span data-stu-id="e988c-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="e988c-263">grpc</span><span class="sxs-lookup"><span data-stu-id="e988c-263">grpc</span></span>](#web-others)             | <span data-ttu-id="e988c-264">[C#]</span><span class="sxs-lookup"><span data-stu-id="e988c-264">[C#]</span></span>         | <span data-ttu-id="e988c-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="e988c-265">Web/gRPC</span></span>                              | <span data-ttu-id="e988c-266">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-266">3.0</span></span>        |
| <span data-ttu-id="e988c-267">dotnet gitignore ファイル</span><span class="sxs-lookup"><span data-stu-id="e988c-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="e988c-268">構成</span><span class="sxs-lookup"><span data-stu-id="e988c-268">Config</span></span>                                | <span data-ttu-id="e988c-269">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-269">3.0</span></span>        |
| <span data-ttu-id="e988c-270">global.json file</span><span class="sxs-lookup"><span data-stu-id="e988c-270">global.json file</span></span>                             | [<span data-ttu-id="e988c-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="e988c-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="e988c-272">構成</span><span class="sxs-lookup"><span data-stu-id="e988c-272">Config</span></span>                                | <span data-ttu-id="e988c-273">2.0</span><span class="sxs-lookup"><span data-stu-id="e988c-273">2.0</span></span>        |
| <span data-ttu-id="e988c-274">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="e988c-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="e988c-275">構成</span><span class="sxs-lookup"><span data-stu-id="e988c-275">Config</span></span>                                | <span data-ttu-id="e988c-276">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-276">1.0</span></span>        |
| <span data-ttu-id="e988c-277">dotnet ローカル ツール マニフェスト ファイル</span><span class="sxs-lookup"><span data-stu-id="e988c-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="e988c-278">構成</span><span class="sxs-lookup"><span data-stu-id="e988c-278">Config</span></span>                                | <span data-ttu-id="e988c-279">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-279">3.0</span></span>        |
| <span data-ttu-id="e988c-280">Web 構成</span><span class="sxs-lookup"><span data-stu-id="e988c-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="e988c-281">構成</span><span class="sxs-lookup"><span data-stu-id="e988c-281">Config</span></span>                                | <span data-ttu-id="e988c-282">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-282">1.0</span></span>        |
| <span data-ttu-id="e988c-283">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="e988c-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="e988c-284">ソリューション</span><span class="sxs-lookup"><span data-stu-id="e988c-284">Solution</span></span>                              | <span data-ttu-id="e988c-285">1.0</span><span class="sxs-lookup"><span data-stu-id="e988c-285">1.0</span></span>        |
| <span data-ttu-id="e988c-286">プロトコル バッファー ファイル</span><span class="sxs-lookup"><span data-stu-id="e988c-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="e988c-287">proto</span><span class="sxs-lookup"><span data-stu-id="e988c-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="e988c-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="e988c-288">Web/gRPC</span></span>                              | <span data-ttu-id="e988c-289">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="e988c-290">オプション</span><span class="sxs-lookup"><span data-stu-id="e988c-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="e988c-291">指定されたコマンドが実行されてテンプレートが作成された場合に起きることの概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="e988c-292">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="e988c-293">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="e988c-294">これは、選択されたテンプレートによって出力ディレクトリ内の既存のファイルがオーバーライドされる場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="e988c-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e988c-295">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="e988c-295">Prints out help for the command.</span></span> <span data-ttu-id="e988c-296">`dotnet new` コマンド自体、または任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e988c-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="e988c-297">たとえば、`dotnet new mvc --help` のようにします。</span><span class="sxs-lookup"><span data-stu-id="e988c-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="e988c-298">指定された `PATH` または `NUGET_ID` からテンプレート パックがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e988c-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e988c-299">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e988c-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="e988c-300">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="e988c-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="e988c-301">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e988c-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="e988c-302">このコマンドの実行時にテンプレートのバージョンが既にインストールされていたら、テンプレートは指定されたバージョンか、最新の安定したバージョン (バージョンが指定されていない場合) に更新されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="e988c-303">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e988c-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="e988c-304">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e988c-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="e988c-305">名前が指定されていない場合、すべてのテンプレートが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="e988c-306">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="e988c-306">The language of the template to create.</span></span> <span data-ttu-id="e988c-307">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="e988c-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="e988c-308">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="e988c-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e988c-309">一部のシェルは `#` を特殊文字として解釈します。</span><span class="sxs-lookup"><span data-stu-id="e988c-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="e988c-310">そのような場合は、言語パラメーター値を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="e988c-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="e988c-311">たとえば、`dotnet new console -lang "F#"` のようにします。</span><span class="sxs-lookup"><span data-stu-id="e988c-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="e988c-312">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="e988c-312">The name for the created output.</span></span> <span data-ttu-id="e988c-313">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="e988c-314">インストール中に使用する NuGet ソースを 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="e988c-314">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="e988c-315">.NET Core 2.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-315">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e988c-316">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="e988c-316">Location to place the generated output.</span></span> <span data-ttu-id="e988c-317">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="e988c-317">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="e988c-318">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="e988c-318">Filters templates based on available types.</span></span> <span data-ttu-id="e988c-319">事前定義されている値は `project` および `item` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-319">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="e988c-320">指定された `PATH` または `NUGET_ID` でテンプレート パックがアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e988c-320">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e988c-321">`<PATH|NUGET_ID>` 値が指定されないと、現在インストールされているすべてのテンプレート パックとそれらに関連付けられているテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-321">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="e988c-322">`NUGET_ID` を指定した場合、バージョン番号は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="e988c-322">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="e988c-323">このオプションにパラメーターを指定しないと、コマンドによって、インストールされたテンプレートとそれらに関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-323">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e988c-324">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e988c-324">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="e988c-325">たとえば、 *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、 *./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="e988c-325">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="e988c-326">テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="e988c-326">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="e988c-327">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認され、それらがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e988c-327">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="e988c-328">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-328">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="e988c-329">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-329">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="e988c-330">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-330">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="e988c-331">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="e988c-331">Template options</span></span>

<span data-ttu-id="e988c-332">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e988c-332">Each project template may have additional options available.</span></span> <span data-ttu-id="e988c-333">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="e988c-333">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="e988c-334">console</span><span class="sxs-lookup"><span data-stu-id="e988c-334">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e988c-335">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-335">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-336">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-336">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e988c-337">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-337">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-338">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-338">SDK version</span></span> | <span data-ttu-id="e988c-339">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-339">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-340">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-341">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e988c-342">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e988c-343">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="e988c-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e988c-344">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e988c-344">Not supported for F#.</span></span> <span data-ttu-id="e988c-345">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e988c-346">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e988c-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-347">指定した場合、プロジェクトの作成中には暗黙的な復元が実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="e988c-348">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="e988c-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="e988c-350">classlib</span><span class="sxs-lookup"><span data-stu-id="e988c-350">classlib</span></span>

- <span data-ttu-id="e988c-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e988c-352">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-353">値: .NET Core クラス ライブラリを作成するには `netcoreapp<version>`、.NET 標準クラス ライブラリを作成するには `netstandard<version>` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-353">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="e988c-354">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-354">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e988c-355">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e988c-356">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="e988c-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e988c-357">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e988c-357">Not supported for F#.</span></span> <span data-ttu-id="e988c-358">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e988c-359">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e988c-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-360">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="e988c-362">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="e988c-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="e988c-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e988c-364">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-365">既定値は `netcoreapp3.1` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-365">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="e988c-366">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e988c-367">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e988c-368">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="e988c-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e988c-369">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e988c-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-370">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="e988c-372">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="e988c-372">winforms, winformslib</span></span>

- <span data-ttu-id="e988c-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="e988c-374">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e988c-375">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="e988c-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e988c-376">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e988c-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-377">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="e988c-379">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="e988c-379">worker, grpc</span></span>

- <span data-ttu-id="e988c-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e988c-381">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-382">既定値は `netcoreapp3.1` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="e988c-383">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e988c-384">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-385">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="e988c-387">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="e988c-387">mstest, xunit</span></span>

- <span data-ttu-id="e988c-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e988c-389">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-390">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="e988c-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e988c-391">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-392">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-392">SDK version</span></span> | <span data-ttu-id="e988c-393">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-394">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-394">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-395">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-395">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e988c-396">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-397">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-397">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-398">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-398">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="e988c-399">nunit</span><span class="sxs-lookup"><span data-stu-id="e988c-399">nunit</span></span>

- <span data-ttu-id="e988c-400">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-400">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e988c-401">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-401">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e988c-402">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-402">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-403">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-403">SDK version</span></span> | <span data-ttu-id="e988c-404">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-404">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-405">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-405">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-406">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-406">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e988c-407">2.2</span><span class="sxs-lookup"><span data-stu-id="e988c-407">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="e988c-408">2.1</span><span class="sxs-lookup"><span data-stu-id="e988c-408">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e988c-409">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-409">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-410">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-410">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-411">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-411">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="e988c-412">ページ (page)</span><span class="sxs-lookup"><span data-stu-id="e988c-412">page</span></span>

- <span data-ttu-id="e988c-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="e988c-414">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="e988c-414">Namespace for the generated code.</span></span> <span data-ttu-id="e988c-415">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-415">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="e988c-416">PageModel なしでページが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-416">Creates the page without a PageModel.</span></span>

<span data-ttu-id="e988c-417">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-417">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="e988c-418">viewimports、proto</span><span class="sxs-lookup"><span data-stu-id="e988c-418">viewimports, proto</span></span>

- <span data-ttu-id="e988c-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="e988c-420">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="e988c-420">Namespace for the generated code.</span></span> <span data-ttu-id="e988c-421">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-421">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="e988c-422">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-422">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="e988c-423">blazorserver</span><span class="sxs-lookup"><span data-stu-id="e988c-423">blazorserver</span></span>

- <span data-ttu-id="e988c-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e988c-425">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="e988c-425">The type of authentication to use.</span></span> <span data-ttu-id="e988c-426">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-426">The possible values are:</span></span>

  - <span data-ttu-id="e988c-427">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="e988c-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e988c-428">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="e988c-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e988c-429">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e988c-430">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e988c-431">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="e988c-431">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e988c-432">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-432">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e988c-433">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="e988c-433">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e988c-434">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-434">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-435">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-435">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e988c-436">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-436">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e988c-437">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-437">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e988c-438">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-438">The reset password policy ID for this project.</span></span> <span data-ttu-id="e988c-439">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-439">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e988c-440">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-440">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e988c-441">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-441">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e988c-442">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e988c-442">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e988c-443">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-443">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e988c-444">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-444">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e988c-445">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-445">The Client ID for this project.</span></span> <span data-ttu-id="e988c-446">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-446">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e988c-447">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-447">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e988c-448">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="e988c-448">The domain for the directory tenant.</span></span> <span data-ttu-id="e988c-449">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-450">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-450">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e988c-451">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-451">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e988c-452">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-452">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-453">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-453">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e988c-454">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="e988c-454">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e988c-455">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-456">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-456">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e988c-457">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="e988c-457">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e988c-458">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-458">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e988c-459">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-459">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e988c-460">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e988c-460">Turns off HTTPS.</span></span> <span data-ttu-id="e988c-461">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が `--auth` 用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-461">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e988c-462">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-462">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e988c-463">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-463">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-464">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-464">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-465">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-465">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="e988c-466">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="e988c-466">blazorwasm</span></span>

- <span data-ttu-id="e988c-467">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-467">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e988c-468">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e988c-469">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-469">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-470">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-470">SDK version</span></span> | <span data-ttu-id="e988c-471">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-471">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-472">5.0</span><span class="sxs-lookup"><span data-stu-id="e988c-472">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e988c-473">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-473">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="e988c-474">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-474">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="e988c-475">Blazor WebAssembly アプリ用の ASP.NET Core ホストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e988c-475">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e988c-476">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="e988c-476">The type of authentication to use.</span></span> <span data-ttu-id="e988c-477">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-477">The possible values are:</span></span>

  - <span data-ttu-id="e988c-478">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="e988c-478">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e988c-479">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="e988c-479">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e988c-480">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-480">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e988c-481">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-481">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="e988c-482">OIDC プロバイダーの機関。</span><span class="sxs-lookup"><span data-stu-id="e988c-482">The authority of the OIDC provider.</span></span> <span data-ttu-id="e988c-483">`Individual` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-483">Use with `Individual` authentication.</span></span> <span data-ttu-id="e988c-484">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-484">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e988c-485">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="e988c-485">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e988c-486">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-486">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-487">既定値は `https://aadB2CInstance.b2clogin.com/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-487">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e988c-488">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-488">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e988c-489">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-489">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e988c-490">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e988c-490">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e988c-491">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-491">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-492">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-492">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e988c-493">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-493">The Client ID for this project.</span></span> <span data-ttu-id="e988c-494">スタンドアロンのシナリオで、`IndividualB2C`、`SingleOrg`、または `Individual` 認証と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-494">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="e988c-495">既定値は `33333333-3333-3333-33333333333333333` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-495">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e988c-496">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="e988c-496">The domain for the directory tenant.</span></span> <span data-ttu-id="e988c-497">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-497">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-498">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-498">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="e988c-499">呼び出すサーバー API のアプリ ID URI。</span><span class="sxs-lookup"><span data-stu-id="e988c-499">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="e988c-500">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-500">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-501">既定値は `api.id.uri` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-501">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="e988c-502">サーバーでホストされる API のクライアント ID。</span><span class="sxs-lookup"><span data-stu-id="e988c-502">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="e988c-503">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-503">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-504">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-504">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="e988c-505">アクセス トークンをプロビジョニングするためにクライアントが要求する必要のある API スコープ。</span><span class="sxs-lookup"><span data-stu-id="e988c-505">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="e988c-506">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-506">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-507">既定値は `user_impersonation` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-507">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e988c-508">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-508">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e988c-509">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-509">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-510">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-510">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e988c-511">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="e988c-511">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e988c-512">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-512">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e988c-513">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="e988c-514">インストールとオフライン使用をサポートするプログレッシブ Web アプリケーション (PWA) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-514">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="e988c-515">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e988c-515">Turns off HTTPS.</span></span> <span data-ttu-id="e988c-516">このオプションは、`Individual`、`IndividualB2C`、または `SingleOrg` が `--auth` 用に使用されていない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-516">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e988c-517">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e988c-518">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="e988c-519">Web アプリから呼び出すための API の URL。</span><span class="sxs-lookup"><span data-stu-id="e988c-519">URL of the API to call from the web app.</span></span> <span data-ttu-id="e988c-520">ASP.NET Core ホストが指定されていない `SingleOrg` または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-520">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e988c-521">既定値は `https://graph.microsoft.com/v1.0/me` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-521">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="e988c-522">Web アプリによって Microsoft Graph が呼び出されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e988c-522">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="e988c-523">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-523">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="e988c-524">Web アプリから API を呼び出すように要求するスコープ。</span><span class="sxs-lookup"><span data-stu-id="e988c-524">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="e988c-525">ASP.NET Core ホストが指定されていない `SingleOrg` または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-525">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e988c-526">既定値は、`user.read` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-526">The default is `user.read`.</span></span>

<span data-ttu-id="e988c-527">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-527">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="e988c-528">web</span><span class="sxs-lookup"><span data-stu-id="e988c-528">web</span></span>

- <span data-ttu-id="e988c-529">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-529">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="e988c-530">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e988c-531">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-532">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="e988c-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e988c-533">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-534">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-534">SDK version</span></span> | <span data-ttu-id="e988c-535">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-536">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-537">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e988c-538">2.1</span><span class="sxs-lookup"><span data-stu-id="e988c-538">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e988c-539">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e988c-540">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e988c-540">Turns off HTTPS.</span></span>

<span data-ttu-id="e988c-541">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-541">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="e988c-542">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="e988c-542">mvc, webapp</span></span>

- <span data-ttu-id="e988c-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e988c-544">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="e988c-544">The type of authentication to use.</span></span> <span data-ttu-id="e988c-545">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-545">The possible values are:</span></span>

  - <span data-ttu-id="e988c-546">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="e988c-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e988c-547">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="e988c-547">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e988c-548">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e988c-549">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e988c-550">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="e988c-550">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e988c-551">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e988c-552">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="e988c-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e988c-553">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-554">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e988c-555">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e988c-556">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-556">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e988c-557">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-557">The reset password policy ID for this project.</span></span> <span data-ttu-id="e988c-558">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-558">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e988c-559">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-559">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e988c-560">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-560">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e988c-561">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e988c-561">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e988c-562">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-562">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e988c-563">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-563">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e988c-564">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-564">The Client ID for this project.</span></span> <span data-ttu-id="e988c-565">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-565">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e988c-566">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-566">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e988c-567">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="e988c-567">The domain for the directory tenant.</span></span> <span data-ttu-id="e988c-568">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-568">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-569">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-569">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e988c-570">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-570">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e988c-571">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-571">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-572">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-572">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e988c-573">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="e988c-573">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e988c-574">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-574">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-575">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-575">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e988c-576">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="e988c-576">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e988c-577">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-577">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e988c-578">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-578">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e988c-579">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e988c-579">Turns off HTTPS.</span></span> <span data-ttu-id="e988c-580">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-580">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e988c-581">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-581">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e988c-582">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-582">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e988c-583">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-583">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-584">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="e988c-584">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e988c-585">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-585">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-586">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-586">SDK version</span></span> | <span data-ttu-id="e988c-587">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-587">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-588">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-588">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-589">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-589">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="e988c-590">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-590">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="e988c-591">プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="e988c-591">Includes BrowserLink in the project.</span></span> <span data-ttu-id="e988c-592">.NET Core 2.2 および 3.1 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="e988c-592">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="e988c-593">デバッグ ビルドで [Razor ランタイム コンパイル](/aspnet/core/mvc/views/view-compilation#runtime-compilation)を使用するようにプロジェクトが構成されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e988c-593">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="e988c-594">.NET Core 3.1.201 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="e988c-594">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="e988c-595">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-595">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="e988c-596">angular、react</span><span class="sxs-lookup"><span data-stu-id="e988c-596">angular, react</span></span>

- <span data-ttu-id="e988c-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e988c-598">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="e988c-598">The type of authentication to use.</span></span> <span data-ttu-id="e988c-599">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-599">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="e988c-600">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-600">The possible values are:</span></span>

  - <span data-ttu-id="e988c-601">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="e988c-601">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e988c-602">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="e988c-602">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e988c-603">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e988c-604">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-604">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e988c-605">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e988c-605">Turns off HTTPS.</span></span> <span data-ttu-id="e988c-606">このオプションは、認証が `None` の場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-606">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e988c-607">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e988c-608">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-608">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-609">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-609">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e988c-610">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-610">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-611">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="e988c-611">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e988c-612">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-612">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-613">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-613">SDK version</span></span> | <span data-ttu-id="e988c-614">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-614">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-615">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-616">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e988c-617">2.1</span><span class="sxs-lookup"><span data-stu-id="e988c-617">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="e988c-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-618">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="e988c-619">reactredux</span><span class="sxs-lookup"><span data-stu-id="e988c-619">reactredux</span></span>

- <span data-ttu-id="e988c-620">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-620">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="e988c-621">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-621">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e988c-622">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-622">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-623">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="e988c-623">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e988c-624">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-624">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-625">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-625">SDK version</span></span> | <span data-ttu-id="e988c-626">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-626">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-627">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-627">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-628">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-628">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e988c-629">2.1</span><span class="sxs-lookup"><span data-stu-id="e988c-629">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="e988c-630">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-630">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e988c-631">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e988c-631">Turns off HTTPS.</span></span>

<span data-ttu-id="e988c-632">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-632">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="e988c-633">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="e988c-633">razorclasslib</span></span>

- <span data-ttu-id="e988c-634">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-634">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="e988c-635">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-635">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="e988c-636">このライブラリへのコンポーネントに加え、従来の Razor ページとビューの追加がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e988c-636">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="e988c-637">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-637">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="e988c-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-638">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="e988c-639">webapi</span><span class="sxs-lookup"><span data-stu-id="e988c-639">webapi</span></span>

- <span data-ttu-id="e988c-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e988c-641">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="e988c-641">The type of authentication to use.</span></span> <span data-ttu-id="e988c-642">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e988c-642">The possible values are:</span></span>

  - <span data-ttu-id="e988c-643">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="e988c-643">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e988c-644">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-644">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e988c-645">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-645">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e988c-646">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="e988c-646">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e988c-647">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="e988c-647">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e988c-648">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-648">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e988c-649">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-649">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e988c-650">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-650">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e988c-651">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-651">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e988c-652">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="e988c-652">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e988c-653">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-653">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-654">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-654">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e988c-655">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-655">The Client ID for this project.</span></span> <span data-ttu-id="e988c-656">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-656">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-657">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-657">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e988c-658">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="e988c-658">The domain for the directory tenant.</span></span> <span data-ttu-id="e988c-659">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-659">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-660">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-660">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e988c-661">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="e988c-661">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e988c-662">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="e988c-662">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e988c-663">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="e988c-663">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e988c-664">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="e988c-664">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e988c-665">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-665">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e988c-666">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-666">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e988c-667">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e988c-667">Turns off HTTPS.</span></span> <span data-ttu-id="e988c-668">`app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-668">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="e988c-669">このオプションは、`IndividualB2C` または `SingleOrg` が認証用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-669">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e988c-670">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-670">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e988c-671">`IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-671">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e988c-672">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-672">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e988c-673">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="e988c-673">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e988c-674">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="e988c-674">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e988c-675">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="e988c-675">SDK version</span></span> | <span data-ttu-id="e988c-676">既定値</span><span class="sxs-lookup"><span data-stu-id="e988c-676">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e988c-677">3.1</span><span class="sxs-lookup"><span data-stu-id="e988c-677">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e988c-678">3.0</span><span class="sxs-lookup"><span data-stu-id="e988c-678">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e988c-679">2.1</span><span class="sxs-lookup"><span data-stu-id="e988c-679">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e988c-680">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e988c-680">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e988c-681">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e988c-681">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="e988c-682">globaljson</span><span class="sxs-lookup"><span data-stu-id="e988c-682">globaljson</span></span>

- <span data-ttu-id="e988c-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="e988c-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="e988c-684">*global.json* ファイル内で使用する .NET Core SDK のバージョンが指定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-684">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="e988c-685">使用例</span><span class="sxs-lookup"><span data-stu-id="e988c-685">Examples</span></span>

- <span data-ttu-id="e988c-686">テンプレート名を指定することによって、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e988c-686">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="e988c-687">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e988c-687">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="e988c-688">指定されたディレクトリ内に .NET Standard クラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-688">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="e988c-689">認証なしで、現在のディレクトリに新しい ASP.NET Core C# MVC プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e988c-689">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="e988c-690">新しい xUnit プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e988c-690">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="e988c-691">シングル ページ アプリケーション (SPA) テンプレートに使用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e988c-691">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="e988c-692">部分文字列 *we* に一致するすべてのテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="e988c-692">List all templates matching the *we* substring.</span></span> <span data-ttu-id="e988c-693">完全一致が見つからないので、短い名前と名前の両方の列に対して部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-693">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="e988c-694">*ng* に一致するテンプレートの呼び出しを試みます。</span><span class="sxs-lookup"><span data-stu-id="e988c-694">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="e988c-695">一致が 1 つだけでない場合、部分的に一致するテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="e988c-695">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="e988c-696">ASP.NET Core 用の SPA テンプレートのバージョン 2.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e988c-696">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="e988c-697">インストールされているテンプレートとそれらに関する詳細や、それらのアンインストール方法を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e988c-697">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="e988c-698">現在のディレクトリに *global.json* が作成され、SDK バージョンが 3.1.101 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e988c-698">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="e988c-699">関連項目</span><span class="sxs-lookup"><span data-stu-id="e988c-699">See also</span></span>

- [<span data-ttu-id="e988c-700">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="e988c-700">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="e988c-701">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="e988c-701">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="e988c-702">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="e988c-702">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="e988c-703">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="e988c-703">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
