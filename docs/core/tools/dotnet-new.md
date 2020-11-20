---
title: dotnet new コマンド
description: dotnet new コマンドを実行すると、指定したテンプレートに基づいて、新しい .NET プロジェクトが作成されます。
no-loc:
- Blazor
- WebAssembly
ms.date: 09/04/2020
ms.openlocfilehash: 3ee644f05ea5929ffc7b11054ef1d974b811f418
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634456"
---
# <a name="dotnet-new"></a><span data-ttu-id="416b9-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="416b9-103">dotnet new</span></span>

<span data-ttu-id="416b9-104">**この記事の対象:** ✔️ .NET Core 2.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="416b9-105">名前</span><span class="sxs-lookup"><span data-stu-id="416b9-105">Name</span></span>

<span data-ttu-id="416b9-106">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="416b9-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="416b9-107">構文</span><span class="sxs-lookup"><span data-stu-id="416b9-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="416b9-108">説明</span><span class="sxs-lookup"><span data-stu-id="416b9-108">Description</span></span>

<span data-ttu-id="416b9-109">`dotnet new` コマンドを実行すると、テンプレートに基づいて、.NET プロジェクトまたはその他の成果物が作成されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-109">The `dotnet new` command creates a .NET project or other artifacts based on a template.</span></span>

<span data-ttu-id="416b9-110">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="416b9-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="416b9-111">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="416b9-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="416b9-112">引数</span><span class="sxs-lookup"><span data-stu-id="416b9-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="416b9-113">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="416b9-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="416b9-114">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="416b9-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="416b9-115">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="416b9-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="416b9-116">`dotnet new --list` または `dotnet new -l` を実行すると、インストールされているすべてのテンプレートの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="416b9-117">`TEMPLATE` の値が返されたテーブルの「**テンプレート**」列または「**短い形式の名前**」列のテキストと完全に一致しない場合、それら 2 つの列で部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="416b9-118">.NET Core 3.0 SDK 以降では、次の条件で `dotnet new` コマンドを呼び出すと、CLI によって NuGet.org 内のテンプレートが検索されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="416b9-119">`dotnet new` の呼び出し時に、CLI でテンプレートの一致を (部分的にも) 検出できない場合。</span><span class="sxs-lookup"><span data-stu-id="416b9-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="416b9-120">テンプレートの新しいバージョンが利用可能な場合。</span><span class="sxs-lookup"><span data-stu-id="416b9-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="416b9-121">この場合、プロジェクトまたは成果物が作成されますが、更新されたバージョンのテンプレートについて、CLI によって警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="416b9-122">次の表は、.NET SDK にプレインストールされているテンプレートを示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-122">The following table shows the templates that come pre-installed with the .NET SDK.</span></span> <span data-ttu-id="416b9-123">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="416b9-124">短い名前のリンクをクリックすると、特定のテンプレート オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="416b9-125">テンプレート</span><span class="sxs-lookup"><span data-stu-id="416b9-125">Templates</span></span>                                    | <span data-ttu-id="416b9-126">短い名前</span><span class="sxs-lookup"><span data-stu-id="416b9-126">Short name</span></span>                      | <span data-ttu-id="416b9-127">言語</span><span class="sxs-lookup"><span data-stu-id="416b9-127">Language</span></span>     | <span data-ttu-id="416b9-128">Tags</span><span class="sxs-lookup"><span data-stu-id="416b9-128">Tags</span></span>                                  | <span data-ttu-id="416b9-129">導入時期</span><span class="sxs-lookup"><span data-stu-id="416b9-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="416b9-130">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="416b9-130">Console Application</span></span>                          | [<span data-ttu-id="416b9-131">console</span><span class="sxs-lookup"><span data-stu-id="416b9-131">console</span></span>](#console)             | <span data-ttu-id="416b9-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="416b9-132">[C#], F#, VB</span></span> | <span data-ttu-id="416b9-133">Common/Console</span><span class="sxs-lookup"><span data-stu-id="416b9-133">Common/Console</span></span>                        | <span data-ttu-id="416b9-134">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-134">1.0</span></span>        |
| <span data-ttu-id="416b9-135">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="416b9-135">Class library</span></span>                                | [<span data-ttu-id="416b9-136">classlib</span><span class="sxs-lookup"><span data-stu-id="416b9-136">classlib</span></span>](#classlib)           | <span data-ttu-id="416b9-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="416b9-137">[C#], F#, VB</span></span> | <span data-ttu-id="416b9-138">Common/Library</span><span class="sxs-lookup"><span data-stu-id="416b9-138">Common/Library</span></span>                        | <span data-ttu-id="416b9-139">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-139">1.0</span></span>        |
| <span data-ttu-id="416b9-140">WPF アプリケーション</span><span class="sxs-lookup"><span data-stu-id="416b9-140">WPF Application</span></span>                              | [<span data-ttu-id="416b9-141">wpf</span><span class="sxs-lookup"><span data-stu-id="416b9-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="416b9-142">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="416b9-142">[C#], VB</span></span>     | <span data-ttu-id="416b9-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="416b9-143">Common/WPF</span></span>                            | <span data-ttu-id="416b9-144">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="416b9-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="416b9-145">WPF クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="416b9-145">WPF Class library</span></span>                            | [<span data-ttu-id="416b9-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="416b9-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="416b9-147">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="416b9-147">[C#], VB</span></span>     | <span data-ttu-id="416b9-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="416b9-148">Common/WPF</span></span>                            | <span data-ttu-id="416b9-149">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="416b9-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="416b9-150">WPF カスタム コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="416b9-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="416b9-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="416b9-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="416b9-152">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="416b9-152">[C#], VB</span></span>     | <span data-ttu-id="416b9-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="416b9-153">Common/WPF</span></span>                            | <span data-ttu-id="416b9-154">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="416b9-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="416b9-155">WPF ユーザー コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="416b9-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="416b9-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="416b9-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="416b9-157">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="416b9-157">[C#], VB</span></span>     | <span data-ttu-id="416b9-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="416b9-158">Common/WPF</span></span>                            | <span data-ttu-id="416b9-159">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="416b9-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="416b9-160">Windows フォーム (WinForms) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="416b9-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="416b9-161">winforms</span><span class="sxs-lookup"><span data-stu-id="416b9-161">winforms</span></span>](#winforms)           | <span data-ttu-id="416b9-162">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="416b9-162">[C#], VB</span></span>     | <span data-ttu-id="416b9-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="416b9-163">Common/WinForms</span></span>                       | <span data-ttu-id="416b9-164">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="416b9-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="416b9-165">Windows フォーム (WinForms) クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="416b9-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="416b9-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="416b9-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="416b9-167">[C#]、VB</span><span class="sxs-lookup"><span data-stu-id="416b9-167">[C#], VB</span></span>     | <span data-ttu-id="416b9-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="416b9-168">Common/WinForms</span></span>                       | <span data-ttu-id="416b9-169">3.0 (VB の場合は 5.0)</span><span class="sxs-lookup"><span data-stu-id="416b9-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="416b9-170">Worker Service</span><span class="sxs-lookup"><span data-stu-id="416b9-170">Worker Service</span></span>                               | [<span data-ttu-id="416b9-171">worker</span><span class="sxs-lookup"><span data-stu-id="416b9-171">worker</span></span>](#web-others)           | <span data-ttu-id="416b9-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-172">[C#]</span></span>         | <span data-ttu-id="416b9-173">Common/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="416b9-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="416b9-174">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-174">3.0</span></span>        |
| <span data-ttu-id="416b9-175">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="416b9-175">Unit Test Project</span></span>                            | [<span data-ttu-id="416b9-176">mstest</span><span class="sxs-lookup"><span data-stu-id="416b9-176">mstest</span></span>](#test)                 | <span data-ttu-id="416b9-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="416b9-177">[C#], F#, VB</span></span> | <span data-ttu-id="416b9-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="416b9-178">Test/MSTest</span></span>                           | <span data-ttu-id="416b9-179">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-179">1.0</span></span>        |
| <span data-ttu-id="416b9-180">NUnit 3 テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="416b9-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="416b9-181">nunit</span><span class="sxs-lookup"><span data-stu-id="416b9-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="416b9-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="416b9-182">[C#], F#, VB</span></span> | <span data-ttu-id="416b9-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="416b9-183">Test/NUnit</span></span>                            | <span data-ttu-id="416b9-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="416b9-184">2.1.400</span></span>    |
| <span data-ttu-id="416b9-185">NUnit 3 テスト項目</span><span class="sxs-lookup"><span data-stu-id="416b9-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="416b9-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="416b9-186">[C#], F#, VB</span></span> | <span data-ttu-id="416b9-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="416b9-187">Test/NUnit</span></span>                            | <span data-ttu-id="416b9-188">2.2</span><span class="sxs-lookup"><span data-stu-id="416b9-188">2.2</span></span>        |
| <span data-ttu-id="416b9-189">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="416b9-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="416b9-190">xunit</span><span class="sxs-lookup"><span data-stu-id="416b9-190">xunit</span></span>](#test)                  | <span data-ttu-id="416b9-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="416b9-191">[C#], F#, VB</span></span> | <span data-ttu-id="416b9-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="416b9-192">Test/xUnit</span></span>                            | <span data-ttu-id="416b9-193">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-193">1.0</span></span>        |
| <span data-ttu-id="416b9-194">Razor コンポーネント</span><span class="sxs-lookup"><span data-stu-id="416b9-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="416b9-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-195">[C#]</span></span>         | <span data-ttu-id="416b9-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="416b9-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="416b9-197">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-197">3.0</span></span>        |
| <span data-ttu-id="416b9-198">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="416b9-198">Razor Page</span></span>                                   | [<span data-ttu-id="416b9-199">page</span><span class="sxs-lookup"><span data-stu-id="416b9-199">page</span></span>](#page)                   | <span data-ttu-id="416b9-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-200">[C#]</span></span>         | <span data-ttu-id="416b9-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="416b9-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="416b9-202">2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-202">2.0</span></span>        |
| <span data-ttu-id="416b9-203">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="416b9-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="416b9-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="416b9-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="416b9-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-205">[C#]</span></span>         | <span data-ttu-id="416b9-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="416b9-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="416b9-207">2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-207">2.0</span></span>        |
| <span data-ttu-id="416b9-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="416b9-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="416b9-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-209">[C#]</span></span>         | <span data-ttu-id="416b9-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="416b9-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="416b9-211">2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-211">2.0</span></span>        |
| <span data-ttu-id="416b9-212">Blazor サーバー アプリ</span><span class="sxs-lookup"><span data-stu-id="416b9-212">Blazor Server App</span></span>                            | [<span data-ttu-id="416b9-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="416b9-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="416b9-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-214">[C#]</span></span>         | <span data-ttu-id="416b9-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="416b9-215">Web/Blazor</span></span>                            | <span data-ttu-id="416b9-216">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-216">3.0</span></span>        |
| <span data-ttu-id="416b9-217">Blazor WebAssembly アプリ</span><span class="sxs-lookup"><span data-stu-id="416b9-217">Blazor WebAssembly App</span></span>                       | [<span data-ttu-id="416b9-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="416b9-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="416b9-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-219">[C#]</span></span>         | <span data-ttu-id="416b9-220">Web/Blazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="416b9-220">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="416b9-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="416b9-221">3.1.300</span></span>    |
| <span data-ttu-id="416b9-222">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="416b9-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="416b9-223">web</span><span class="sxs-lookup"><span data-stu-id="416b9-223">web</span></span>](#web)                     | <span data-ttu-id="416b9-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="416b9-224">[C#], F#</span></span>     | <span data-ttu-id="416b9-225">Web/Empty</span><span class="sxs-lookup"><span data-stu-id="416b9-225">Web/Empty</span></span>                             | <span data-ttu-id="416b9-226">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-226">1.0</span></span>        |
| <span data-ttu-id="416b9-227">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="416b9-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="416b9-228">mvc</span><span class="sxs-lookup"><span data-stu-id="416b9-228">mvc</span></span>](#web-options)             | <span data-ttu-id="416b9-229">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="416b9-229">[C#], F#</span></span>     | <span data-ttu-id="416b9-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="416b9-230">Web/MVC</span></span>                               | <span data-ttu-id="416b9-231">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-231">1.0</span></span>        |
| <span data-ttu-id="416b9-232">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="416b9-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="416b9-233">webapp、razor</span><span class="sxs-lookup"><span data-stu-id="416b9-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="416b9-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-234">[C#]</span></span>         | <span data-ttu-id="416b9-235">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="416b9-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="416b9-236">2.2、2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="416b9-237">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="416b9-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="416b9-238">angular</span><span class="sxs-lookup"><span data-stu-id="416b9-238">angular</span></span>](#spa)                 | <span data-ttu-id="416b9-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-239">[C#]</span></span>         | <span data-ttu-id="416b9-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="416b9-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="416b9-241">2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-241">2.0</span></span>        |
| <span data-ttu-id="416b9-242">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="416b9-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="416b9-243">react</span><span class="sxs-lookup"><span data-stu-id="416b9-243">react</span></span>](#spa)                   | <span data-ttu-id="416b9-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-244">[C#]</span></span>         | <span data-ttu-id="416b9-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="416b9-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="416b9-246">2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-246">2.0</span></span>        |
| <span data-ttu-id="416b9-247">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="416b9-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="416b9-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="416b9-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="416b9-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-249">[C#]</span></span>         | <span data-ttu-id="416b9-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="416b9-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="416b9-251">2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-251">2.0</span></span>        |
| <span data-ttu-id="416b9-252">Razor クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="416b9-252">Razor Class Library</span></span>                          | [<span data-ttu-id="416b9-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="416b9-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="416b9-254">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-254">[C#]</span></span>         | <span data-ttu-id="416b9-255">Web/Razor/Library/Razor Class Library</span><span class="sxs-lookup"><span data-stu-id="416b9-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="416b9-256">2.1</span><span class="sxs-lookup"><span data-stu-id="416b9-256">2.1</span></span>        |
| <span data-ttu-id="416b9-257">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="416b9-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="416b9-258">webapi</span><span class="sxs-lookup"><span data-stu-id="416b9-258">webapi</span></span>](#webapi)               | <span data-ttu-id="416b9-259">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="416b9-259">[C#], F#</span></span>     | <span data-ttu-id="416b9-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="416b9-260">Web/WebAPI</span></span>                            | <span data-ttu-id="416b9-261">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-261">1.0</span></span>        |
| <span data-ttu-id="416b9-262">ASP.NET Core gRPC サービス</span><span class="sxs-lookup"><span data-stu-id="416b9-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="416b9-263">grpc</span><span class="sxs-lookup"><span data-stu-id="416b9-263">grpc</span></span>](#web-others)             | <span data-ttu-id="416b9-264">[C#]</span><span class="sxs-lookup"><span data-stu-id="416b9-264">[C#]</span></span>         | <span data-ttu-id="416b9-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="416b9-265">Web/gRPC</span></span>                              | <span data-ttu-id="416b9-266">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-266">3.0</span></span>        |
| <span data-ttu-id="416b9-267">dotnet gitignore ファイル</span><span class="sxs-lookup"><span data-stu-id="416b9-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="416b9-268">構成</span><span class="sxs-lookup"><span data-stu-id="416b9-268">Config</span></span>                                | <span data-ttu-id="416b9-269">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-269">3.0</span></span>        |
| <span data-ttu-id="416b9-270">global.json file</span><span class="sxs-lookup"><span data-stu-id="416b9-270">global.json file</span></span>                             | [<span data-ttu-id="416b9-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="416b9-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="416b9-272">構成</span><span class="sxs-lookup"><span data-stu-id="416b9-272">Config</span></span>                                | <span data-ttu-id="416b9-273">2.0</span><span class="sxs-lookup"><span data-stu-id="416b9-273">2.0</span></span>        |
| <span data-ttu-id="416b9-274">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="416b9-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="416b9-275">構成</span><span class="sxs-lookup"><span data-stu-id="416b9-275">Config</span></span>                                | <span data-ttu-id="416b9-276">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-276">1.0</span></span>        |
| <span data-ttu-id="416b9-277">dotnet ローカル ツール マニフェスト ファイル</span><span class="sxs-lookup"><span data-stu-id="416b9-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="416b9-278">構成</span><span class="sxs-lookup"><span data-stu-id="416b9-278">Config</span></span>                                | <span data-ttu-id="416b9-279">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-279">3.0</span></span>        |
| <span data-ttu-id="416b9-280">Web 構成</span><span class="sxs-lookup"><span data-stu-id="416b9-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="416b9-281">構成</span><span class="sxs-lookup"><span data-stu-id="416b9-281">Config</span></span>                                | <span data-ttu-id="416b9-282">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-282">1.0</span></span>        |
| <span data-ttu-id="416b9-283">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="416b9-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="416b9-284">ソリューション</span><span class="sxs-lookup"><span data-stu-id="416b9-284">Solution</span></span>                              | <span data-ttu-id="416b9-285">1.0</span><span class="sxs-lookup"><span data-stu-id="416b9-285">1.0</span></span>        |
| <span data-ttu-id="416b9-286">プロトコル バッファー ファイル</span><span class="sxs-lookup"><span data-stu-id="416b9-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="416b9-287">proto</span><span class="sxs-lookup"><span data-stu-id="416b9-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="416b9-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="416b9-288">Web/gRPC</span></span>                              | <span data-ttu-id="416b9-289">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="416b9-290">オプション</span><span class="sxs-lookup"><span data-stu-id="416b9-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="416b9-291">指定されたコマンドが実行されてテンプレートが作成された場合に起きることの概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="416b9-292">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="416b9-293">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="416b9-294">これは、選択されたテンプレートによって出力ディレクトリ内の既存のファイルがオーバーライドされる場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="416b9-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="416b9-295">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="416b9-295">Prints out help for the command.</span></span> <span data-ttu-id="416b9-296">`dotnet new` コマンド自体、または任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="416b9-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="416b9-297">たとえば、`dotnet new mvc --help` のようにします。</span><span class="sxs-lookup"><span data-stu-id="416b9-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="416b9-298">指定された `PATH` または `NUGET_ID` からテンプレート パックがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="416b9-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="416b9-299">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="416b9-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="416b9-300">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="416b9-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="416b9-301">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="416b9-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="416b9-302">このコマンドの実行時にテンプレートのバージョンが既にインストールされていたら、テンプレートは指定されたバージョンか、最新の安定したバージョン (バージョンが指定されていない場合) に更新されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="416b9-303">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="416b9-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="416b9-304">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="416b9-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="416b9-305">名前が指定されていない場合、すべてのテンプレートが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="416b9-306">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="416b9-306">The language of the template to create.</span></span> <span data-ttu-id="416b9-307">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="416b9-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="416b9-308">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="416b9-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="416b9-309">一部のシェルは `#` を特殊文字として解釈します。</span><span class="sxs-lookup"><span data-stu-id="416b9-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="416b9-310">そのような場合は、言語パラメーター値を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="416b9-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="416b9-311">たとえば、`dotnet new console -lang "F#"` のようにします。</span><span class="sxs-lookup"><span data-stu-id="416b9-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="416b9-312">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="416b9-312">The name for the created output.</span></span> <span data-ttu-id="416b9-313">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="416b9-314">インストール中に使用する NuGet ソースを 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="416b9-314">Specifies a NuGet source to use during install.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="416b9-315">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="416b9-315">Location to place the generated output.</span></span> <span data-ttu-id="416b9-316">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="416b9-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="416b9-317">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="416b9-317">Filters templates based on available types.</span></span> <span data-ttu-id="416b9-318">事前定義されている値は `project` および `item` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="416b9-319">指定された `PATH` または `NUGET_ID` でテンプレート パックがアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="416b9-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="416b9-320">`<PATH|NUGET_ID>` 値が指定されないと、現在インストールされているすべてのテンプレート パックとそれらに関連付けられているテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="416b9-321">`NUGET_ID` を指定した場合、バージョン番号は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="416b9-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="416b9-322">このオプションにパラメーターを指定しないと、コマンドによって、インストールされたテンプレートとそれらに関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="416b9-323">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="416b9-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="416b9-324">たとえば、*C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、 *./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="416b9-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="416b9-325">テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="416b9-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="416b9-326">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認され、それらがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="416b9-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="416b9-327">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="416b9-328">現在インストールされているテンプレート パックに利用できる更新プログラムがあるかどうか確認されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="416b9-329">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="416b9-330">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="416b9-330">Template options</span></span>

<span data-ttu-id="416b9-331">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="416b9-331">Each project template may have additional options available.</span></span> <span data-ttu-id="416b9-332">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="416b9-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="416b9-333">console</span><span class="sxs-lookup"><span data-stu-id="416b9-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="416b9-334">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-335">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="416b9-336">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-337">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-337">SDK version</span></span> | <span data-ttu-id="416b9-338">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-339">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-339">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-340">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-341">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="416b9-342">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="416b9-343">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="416b9-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="416b9-344">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="416b9-344">Not supported for F#.</span></span> <span data-ttu-id="416b9-345">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="416b9-346">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="416b9-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-347">指定した場合、プロジェクトの作成中には暗黙的な復元が実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="416b9-348">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="416b9-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="416b9-350">classlib</span><span class="sxs-lookup"><span data-stu-id="416b9-350">classlib</span></span>

- <span data-ttu-id="416b9-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="416b9-352">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-353">値: .NET クラス ライブラリを作成するには `net5.0` または `netcoreapp<version>`、.NET Standard クラス ライブラリを作成するには `netstandard<version>`。</span><span class="sxs-lookup"><span data-stu-id="416b9-353">Values: `net5.0` or `netcoreapp<version>` to create a .NET Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="416b9-354">.NET 5.0 SDK の既定値は `net5.0` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-354">The default value for .NET 5.0 SDK is `net5.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="416b9-355">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="416b9-356">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="416b9-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="416b9-357">F# に対してはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="416b9-357">Not supported for F#.</span></span> <span data-ttu-id="416b9-358">.NET Core 2.2 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="416b9-359">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="416b9-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-360">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="416b9-362">wpf、wpflib、wpfcustomcontrollib、wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="416b9-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="416b9-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="416b9-364">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-365">既定値は `net5.0` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-365">The default value is `net5.0`.</span></span> <span data-ttu-id="416b9-366">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="416b9-367">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="416b9-368">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="416b9-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="416b9-369">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="416b9-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-370">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="416b9-372">winforms、winformslib</span><span class="sxs-lookup"><span data-stu-id="416b9-372">winforms, winformslib</span></span>

- <span data-ttu-id="416b9-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="416b9-374">作成されたプロジェクト ファイルの `LangVersion` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="416b9-375">たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。</span><span class="sxs-lookup"><span data-stu-id="416b9-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="416b9-376">既定の C# バージョンの一覧については、「[既定値](../../csharp/language-reference/configure-language-version.md#defaults)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="416b9-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-377">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="416b9-379">worker、grpc</span><span class="sxs-lookup"><span data-stu-id="416b9-379">worker, grpc</span></span>

- <span data-ttu-id="416b9-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="416b9-381">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-382">既定値は `netcoreapp3.1` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="416b9-383">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="416b9-384">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-385">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="416b9-387">mstest、xunit</span><span class="sxs-lookup"><span data-stu-id="416b9-387">mstest, xunit</span></span>

- <span data-ttu-id="416b9-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="416b9-389">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-390">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="416b9-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="416b9-391">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-392">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-392">SDK version</span></span> | <span data-ttu-id="416b9-393">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-394">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-394">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-395">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-395">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-396">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-396">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="416b9-397">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-397">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-398">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-398">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-399">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-399">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="416b9-400">nunit</span><span class="sxs-lookup"><span data-stu-id="416b9-400">nunit</span></span>

- <span data-ttu-id="416b9-401">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-401">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="416b9-402">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-402">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="416b9-403">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-403">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-404">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-404">SDK version</span></span> | <span data-ttu-id="416b9-405">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-405">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-406">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-406">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-407">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-407">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-408">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-408">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="416b9-409">2.2</span><span class="sxs-lookup"><span data-stu-id="416b9-409">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="416b9-410">2.1</span><span class="sxs-lookup"><span data-stu-id="416b9-410">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="416b9-411">[dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化が有効化されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-411">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-412">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-412">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-413">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-413">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="416b9-414">ページ (page)</span><span class="sxs-lookup"><span data-stu-id="416b9-414">page</span></span>

- <span data-ttu-id="416b9-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="416b9-416">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="416b9-416">Namespace for the generated code.</span></span> <span data-ttu-id="416b9-417">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-417">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="416b9-418">PageModel なしでページが作成されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-418">Creates the page without a PageModel.</span></span>

<span data-ttu-id="416b9-419">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-419">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="416b9-420">viewimports、proto</span><span class="sxs-lookup"><span data-stu-id="416b9-420">viewimports, proto</span></span>

- <span data-ttu-id="416b9-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="416b9-422">生成されるコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="416b9-422">Namespace for the generated code.</span></span> <span data-ttu-id="416b9-423">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-423">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="416b9-424">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-424">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="416b9-425">blazorserver</span><span class="sxs-lookup"><span data-stu-id="416b9-425">blazorserver</span></span>

- <span data-ttu-id="416b9-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="416b9-427">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="416b9-427">The type of authentication to use.</span></span> <span data-ttu-id="416b9-428">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-428">The possible values are:</span></span>

  - <span data-ttu-id="416b9-429">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="416b9-429">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="416b9-430">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="416b9-430">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="416b9-431">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-431">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="416b9-432">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-432">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="416b9-433">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="416b9-433">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="416b9-434">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-434">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="416b9-435">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="416b9-435">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="416b9-436">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-436">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-437">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-437">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="416b9-438">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-438">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="416b9-439">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-439">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="416b9-440">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-440">The reset password policy ID for this project.</span></span> <span data-ttu-id="416b9-441">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-441">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="416b9-442">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-442">The edit profile policy ID for this project.</span></span> <span data-ttu-id="416b9-443">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-443">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="416b9-444">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="416b9-444">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="416b9-445">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-445">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="416b9-446">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-446">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="416b9-447">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-447">The Client ID for this project.</span></span> <span data-ttu-id="416b9-448">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-448">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="416b9-449">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-449">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="416b9-450">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="416b9-450">The domain for the directory tenant.</span></span> <span data-ttu-id="416b9-451">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-451">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-452">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-452">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="416b9-453">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-453">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="416b9-454">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-454">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-455">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-455">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="416b9-456">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="416b9-456">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="416b9-457">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-457">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-458">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-458">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="416b9-459">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="416b9-459">Allows this application read-access to the directory.</span></span> <span data-ttu-id="416b9-460">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-460">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="416b9-461">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-461">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="416b9-462">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="416b9-462">Turns off HTTPS.</span></span> <span data-ttu-id="416b9-463">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が `--auth` 用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-463">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="416b9-464">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-464">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="416b9-465">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-465">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-466">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-466">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-467">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-467">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="416b9-468">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="416b9-468">blazorwasm</span></span>

- <span data-ttu-id="416b9-469">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-469">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="416b9-470">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-470">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="416b9-471">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-471">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-472">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-472">SDK version</span></span> | <span data-ttu-id="416b9-473">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-473">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-474">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-474">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-475">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-475">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="416b9-476">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="416b9-477">Blazor WebAssembly アプリ用の ASP.NET Core ホストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="416b9-477">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="416b9-478">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="416b9-478">The type of authentication to use.</span></span> <span data-ttu-id="416b9-479">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-479">The possible values are:</span></span>

  - <span data-ttu-id="416b9-480">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="416b9-480">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="416b9-481">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="416b9-481">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="416b9-482">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-482">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="416b9-483">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-483">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="416b9-484">OIDC プロバイダーの機関。</span><span class="sxs-lookup"><span data-stu-id="416b9-484">The authority of the OIDC provider.</span></span> <span data-ttu-id="416b9-485">`Individual` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-485">Use with `Individual` authentication.</span></span> <span data-ttu-id="416b9-486">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-486">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="416b9-487">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="416b9-487">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="416b9-488">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-488">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-489">既定値は `https://aadB2CInstance.b2clogin.com/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-489">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="416b9-490">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-490">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="416b9-491">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-491">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="416b9-492">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="416b9-492">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="416b9-493">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-493">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-494">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-494">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="416b9-495">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-495">The Client ID for this project.</span></span> <span data-ttu-id="416b9-496">スタンドアロンのシナリオで、`IndividualB2C`、`SingleOrg`、または `Individual` 認証と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-496">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="416b9-497">既定値は `33333333-3333-3333-33333333333333333` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-497">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="416b9-498">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="416b9-498">The domain for the directory tenant.</span></span> <span data-ttu-id="416b9-499">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-499">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-500">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-500">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="416b9-501">呼び出すサーバー API のアプリ ID URI。</span><span class="sxs-lookup"><span data-stu-id="416b9-501">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="416b9-502">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-502">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-503">既定値は `api.id.uri` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-503">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="416b9-504">サーバーでホストされる API のクライアント ID。</span><span class="sxs-lookup"><span data-stu-id="416b9-504">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="416b9-505">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-506">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-506">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="416b9-507">アクセス トークンをプロビジョニングするためにクライアントが要求する必要のある API スコープ。</span><span class="sxs-lookup"><span data-stu-id="416b9-507">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="416b9-508">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-508">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-509">既定値は `user_impersonation` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-509">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="416b9-510">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-510">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="416b9-511">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-511">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-512">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-512">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="416b9-513">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="416b9-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="416b9-514">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-514">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="416b9-515">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="416b9-516">インストールとオフライン使用をサポートするプログレッシブ Web アプリケーション (PWA) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-516">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="416b9-517">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="416b9-517">Turns off HTTPS.</span></span> <span data-ttu-id="416b9-518">このオプションは、`Individual`、`IndividualB2C`、または `SingleOrg` が `--auth` 用に使用されていない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-518">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="416b9-519">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-519">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="416b9-520">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-520">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="416b9-521">Web アプリから呼び出すための API の URL。</span><span class="sxs-lookup"><span data-stu-id="416b9-521">URL of the API to call from the web app.</span></span> <span data-ttu-id="416b9-522">ASP.NET Core ホストが指定されていない `SingleOrg` または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-522">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="416b9-523">既定値は `https://graph.microsoft.com/v1.0/me` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-523">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="416b9-524">Web アプリによって Microsoft Graph が呼び出されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="416b9-524">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="416b9-525">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-525">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="416b9-526">Web アプリから API を呼び出すように要求するスコープ。</span><span class="sxs-lookup"><span data-stu-id="416b9-526">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="416b9-527">ASP.NET Core ホストが指定されていない `SingleOrg` または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-527">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="416b9-528">既定値は、`user.read` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-528">The default is `user.read`.</span></span>

<span data-ttu-id="416b9-529">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-529">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="416b9-530">web</span><span class="sxs-lookup"><span data-stu-id="416b9-530">web</span></span>

- <span data-ttu-id="416b9-531">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-531">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="416b9-532">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="416b9-533">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-534">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="416b9-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="416b9-535">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-536">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-536">SDK version</span></span> | <span data-ttu-id="416b9-537">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-538">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-538">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-539">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-539">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-540">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-540">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="416b9-541">2.1</span><span class="sxs-lookup"><span data-stu-id="416b9-541">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="416b9-542">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="416b9-543">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="416b9-543">Turns off HTTPS.</span></span>

<span data-ttu-id="416b9-544">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-544">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="416b9-545">mvc、webapp</span><span class="sxs-lookup"><span data-stu-id="416b9-545">mvc, webapp</span></span>

- <span data-ttu-id="416b9-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="416b9-547">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="416b9-547">The type of authentication to use.</span></span> <span data-ttu-id="416b9-548">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-548">The possible values are:</span></span>

  - <span data-ttu-id="416b9-549">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="416b9-549">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="416b9-550">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="416b9-550">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="416b9-551">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="416b9-552">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="416b9-553">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="416b9-553">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="416b9-554">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-554">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="416b9-555">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="416b9-555">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="416b9-556">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-556">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-557">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-557">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="416b9-558">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-558">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="416b9-559">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-559">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="416b9-560">このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-560">The reset password policy ID for this project.</span></span> <span data-ttu-id="416b9-561">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-561">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="416b9-562">このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-562">The edit profile policy ID for this project.</span></span> <span data-ttu-id="416b9-563">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-563">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="416b9-564">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="416b9-564">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="416b9-565">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-565">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="416b9-566">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-566">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="416b9-567">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-567">The Client ID for this project.</span></span> <span data-ttu-id="416b9-568">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-568">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="416b9-569">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-569">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="416b9-570">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="416b9-570">The domain for the directory tenant.</span></span> <span data-ttu-id="416b9-571">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-571">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-572">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-572">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="416b9-573">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-573">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="416b9-574">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-574">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-575">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-575">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="416b9-576">リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="416b9-576">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="416b9-577">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-577">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-578">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-578">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="416b9-579">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="416b9-579">Allows this application read-access to the directory.</span></span> <span data-ttu-id="416b9-580">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-580">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="416b9-581">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-581">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="416b9-582">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="416b9-582">Turns off HTTPS.</span></span> <span data-ttu-id="416b9-583">このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-583">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="416b9-584">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-584">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="416b9-585">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-585">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="416b9-586">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-586">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-587">.NET Core 3.0 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="416b9-587">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="416b9-588">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-588">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-589">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-589">SDK version</span></span> | <span data-ttu-id="416b9-590">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-590">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-591">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-591">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-592">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-592">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-593">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-593">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="416b9-594">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-594">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="416b9-595">プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="416b9-595">Includes BrowserLink in the project.</span></span> <span data-ttu-id="416b9-596">.NET Core 2.2 および 3.1 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="416b9-596">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="416b9-597">デバッグ ビルドで [Razor ランタイム コンパイル](/aspnet/core/mvc/views/view-compilation#runtime-compilation)を使用するようにプロジェクトが構成されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="416b9-597">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="416b9-598">.NET Core 3.1.201 SDK 以降で利用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="416b9-598">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="416b9-599">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-599">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="416b9-600">angular、react</span><span class="sxs-lookup"><span data-stu-id="416b9-600">angular, react</span></span>

- <span data-ttu-id="416b9-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="416b9-602">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="416b9-602">The type of authentication to use.</span></span> <span data-ttu-id="416b9-603">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-603">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="416b9-604">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-604">The possible values are:</span></span>

  - <span data-ttu-id="416b9-605">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="416b9-605">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="416b9-606">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="416b9-606">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="416b9-607">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-607">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="416b9-608">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-608">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="416b9-609">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="416b9-609">Turns off HTTPS.</span></span> <span data-ttu-id="416b9-610">このオプションは、認証が `None` の場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-610">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="416b9-611">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-611">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="416b9-612">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-612">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-613">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-613">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="416b9-614">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-614">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-615">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="416b9-615">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="416b9-616">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-616">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-617">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-617">SDK version</span></span> | <span data-ttu-id="416b9-618">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-618">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-619">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-619">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-620">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-620">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-621">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-621">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="416b9-622">2.1</span><span class="sxs-lookup"><span data-stu-id="416b9-622">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="416b9-623">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-623">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="416b9-624">reactredux</span><span class="sxs-lookup"><span data-stu-id="416b9-624">reactredux</span></span>

- <span data-ttu-id="416b9-625">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-625">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="416b9-626">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-626">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="416b9-627">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-627">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-628">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="416b9-628">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="416b9-629">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-629">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-630">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-630">SDK version</span></span> | <span data-ttu-id="416b9-631">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-631">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-632">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-632">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-633">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-633">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-634">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-634">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="416b9-635">2.1</span><span class="sxs-lookup"><span data-stu-id="416b9-635">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="416b9-636">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-636">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="416b9-637">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="416b9-637">Turns off HTTPS.</span></span>

<span data-ttu-id="416b9-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-638">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="416b9-639">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="416b9-639">razorclasslib</span></span>

- <span data-ttu-id="416b9-640">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-640">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="416b9-641">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-641">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="416b9-642">このライブラリへのコンポーネントに加え、従来の Razor ページとビューの追加がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="416b9-642">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="416b9-643">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-643">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="416b9-644">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-644">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="416b9-645">webapi</span><span class="sxs-lookup"><span data-stu-id="416b9-645">webapi</span></span>

- <span data-ttu-id="416b9-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="416b9-647">使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="416b9-647">The type of authentication to use.</span></span> <span data-ttu-id="416b9-648">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="416b9-648">The possible values are:</span></span>

  - <span data-ttu-id="416b9-649">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="416b9-649">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="416b9-650">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-650">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="416b9-651">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-651">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="416b9-652">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="416b9-652">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="416b9-653">接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="416b9-653">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="416b9-654">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-654">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="416b9-655">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-655">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="416b9-656">このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-656">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="416b9-657">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-657">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="416b9-658">接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="416b9-658">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="416b9-659">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-659">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-660">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-660">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="416b9-661">このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-661">The Client ID for this project.</span></span> <span data-ttu-id="416b9-662">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-662">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-663">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-663">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="416b9-664">ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="416b9-664">The domain for the directory tenant.</span></span> <span data-ttu-id="416b9-665">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-665">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-666">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-666">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="416b9-667">接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="416b9-667">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="416b9-668">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="416b9-668">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="416b9-669">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="416b9-669">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="416b9-670">このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="416b9-670">Allows this application read-access to the directory.</span></span> <span data-ttu-id="416b9-671">`SingleOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-671">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="416b9-672">生成されたテンプレートから *launchSettings.json* が除外されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-672">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="416b9-673">HTTPS を無効にします。</span><span class="sxs-lookup"><span data-stu-id="416b9-673">Turns off HTTPS.</span></span> <span data-ttu-id="416b9-674">`app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-674">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="416b9-675">このオプションは、`IndividualB2C` または `SingleOrg` が認証用に使用されない場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-675">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="416b9-676">SQLite ではなく LocalDB が使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-676">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="416b9-677">`IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-677">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="416b9-678">ターゲットにする[フレームワーク](../../standard/frameworks.md)が指定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-678">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="416b9-679">.NET Core 2.2 SDK では使用できません。</span><span class="sxs-lookup"><span data-stu-id="416b9-679">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="416b9-680">次の表は、使用する SDK バージョン番号に対応した既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="416b9-680">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="416b9-681">SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="416b9-681">SDK version</span></span> | <span data-ttu-id="416b9-682">既定値</span><span class="sxs-lookup"><span data-stu-id="416b9-682">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="416b9-683">5.0</span><span class="sxs-lookup"><span data-stu-id="416b9-683">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="416b9-684">3.1</span><span class="sxs-lookup"><span data-stu-id="416b9-684">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="416b9-685">3.0</span><span class="sxs-lookup"><span data-stu-id="416b9-685">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="416b9-686">2.1</span><span class="sxs-lookup"><span data-stu-id="416b9-686">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="416b9-687">プロジェクトの作成中に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="416b9-687">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="416b9-688">\*\*_</span><span class="sxs-lookup"><span data-stu-id="416b9-688">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="416b9-689">globaljson</span><span class="sxs-lookup"><span data-stu-id="416b9-689">globaljson</span></span>

- <span data-ttu-id="416b9-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="416b9-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="416b9-691">*global.json* ファイル内で使用する .NET SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="416b9-691">Specifies the version of the .NET SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="416b9-692">使用例</span><span class="sxs-lookup"><span data-stu-id="416b9-692">Examples</span></span>

- <span data-ttu-id="416b9-693">テンプレート名を指定することによって、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="416b9-693">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="416b9-694">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="416b9-694">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="416b9-695">指定されたディレクトリ内に .NET Standard クラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-695">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="416b9-696">認証なしで、現在のディレクトリに新しい ASP.NET Core C# MVC プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="416b9-696">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="416b9-697">新しい xUnit プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="416b9-697">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="416b9-698">シングル ページ アプリケーション (SPA) テンプレートに使用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="416b9-698">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="416b9-699">部分文字列 *we* に一致するすべてのテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="416b9-699">List all templates matching the *we* substring.</span></span> <span data-ttu-id="416b9-700">完全一致が見つからないので、短い名前と名前の両方の列に対して部分文字列一致が実行されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-700">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="416b9-701">*ng* に一致するテンプレートの呼び出しを試みます。</span><span class="sxs-lookup"><span data-stu-id="416b9-701">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="416b9-702">一致が 1 つだけでない場合、部分的に一致するテンプレートの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="416b9-702">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="416b9-703">ASP.NET Core 用の SPA テンプレートのバージョン 2.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="416b9-703">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="416b9-704">インストールされているテンプレートとそれらに関する詳細や、それらのアンインストール方法を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="416b9-704">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="416b9-705">現在のディレクトリに *global.json* が作成され、SDK バージョンが 3.1.101 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="416b9-705">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="416b9-706">関連項目</span><span class="sxs-lookup"><span data-stu-id="416b9-706">See also</span></span>

- [<span data-ttu-id="416b9-707">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="416b9-707">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="416b9-708">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="416b9-708">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="416b9-709">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="416b9-709">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="416b9-710">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="416b9-710">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
