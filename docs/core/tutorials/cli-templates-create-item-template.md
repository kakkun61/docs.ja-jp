---
title: dotnet new 用の項目テンプレートを作成する - .NET CLI
titleSuffix: ''
description: dotnet new コマンド用の項目テンプレートを作成する方法を説明します。 項目テンプレートには、任意の数のファイルを含めることができます。
author: adegeo
ms.date: 12/11/2020
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: d213646a933c77bd0d9a3f1aa9b6b4948b66439b
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633664"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="eca23-104">チュートリアル: 項目テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="eca23-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="eca23-105">.NET を使用すると、プロジェクト、ファイル、さらにはリソースを生成するテンプレートを作成して配置することができます。</span><span class="sxs-lookup"><span data-stu-id="eca23-105">With .NET, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="eca23-106">このチュートリアルは、`dotnet new` コマンドで使用するテンプレートの作成、インストール、アンインストール方法を説明するシリーズのパート 1 です。</span><span class="sxs-lookup"><span data-stu-id="eca23-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="eca23-107">シリーズのこのパートで学習する内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eca23-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="eca23-108">項目テンプレートのクラスを作成する</span><span class="sxs-lookup"><span data-stu-id="eca23-108">Create a class for an item template</span></span>
> * <span data-ttu-id="eca23-109">テンプレートの構成フォルダーとファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="eca23-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="eca23-110">ファイル パスからテンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="eca23-110">Install a template from a file path</span></span>
> * <span data-ttu-id="eca23-111">項目テンプレートをテストする</span><span class="sxs-lookup"><span data-stu-id="eca23-111">Test an item template</span></span>
> * <span data-ttu-id="eca23-112">項目テンプレートをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="eca23-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eca23-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="eca23-113">Prerequisites</span></span>

* <span data-ttu-id="eca23-114">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="eca23-114">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or a later version.</span></span>
* <span data-ttu-id="eca23-115">参照記事「[dotnet new のカスタム テンプレート](../tools/custom-templates.md)」を確認しておきます。</span><span class="sxs-lookup"><span data-stu-id="eca23-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="eca23-116">この参照記事では、テンプレートの基本と、テンプレートをまとめる方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="eca23-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="eca23-117">ここでは、この情報の一部を繰り返して示します。</span><span class="sxs-lookup"><span data-stu-id="eca23-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="eca23-118">ターミナルを開いて、_working\templates_ フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="eca23-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="eca23-119">必要なフォルダーを作成する</span><span class="sxs-lookup"><span data-stu-id="eca23-119">Create the required folders</span></span>

<span data-ttu-id="eca23-120">このシリーズでは、テンプレートのソースが含まれる "作業フォルダー" と、テンプレートをテストするための "テスト フォルダー" を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca23-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="eca23-121">作業フォルダーとテスト フォルダーは、同じ親フォルダーの下に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca23-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="eca23-122">まず、親フォルダーを作成します。名前は何でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="eca23-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="eca23-123">次に、_working_ という名前のサブフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="eca23-124">_working_ フォルダー内に、_templates_ という名前のサブフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="eca23-125">次に、親フォルダーの下に _test_ という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="eca23-126">フォルダー構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="eca23-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="eca23-127">項目テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="eca23-127">Create an item template</span></span>

<span data-ttu-id="eca23-128">項目テンプレートは、1 つ以上のファイルを含む特定の種類のテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="eca23-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="eca23-129">この種類のテンプレートは、構成、コード、ソリューションなどのファイルを生成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eca23-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="eca23-130">この例では、文字列型に拡張メソッドを追加するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="eca23-131">ターミナルで、_working\templates_ フォルダーに移動し、_extensions_ という名前の新しいサブフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="eca23-132">このフォルダーに入ります。</span><span class="sxs-lookup"><span data-stu-id="eca23-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="eca23-133">_CommonExtensions.cs_ という名前の新しいファイルを作成し、お好みのテキスト エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="eca23-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="eca23-134">このクラスにより、文字列のコンテンツを反転させる `Reverse` という名前の拡張メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="eca23-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="eca23-135">次のコードを貼り付けて、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="eca23-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="eca23-136">テンプレートのコンテンツを作成したので、テンプレートのルート フォルダーでテンプレートの構成を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca23-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="eca23-137">テンプレートの構成を作成する</span><span class="sxs-lookup"><span data-stu-id="eca23-137">Create the template config</span></span>

<span data-ttu-id="eca23-138">テンプレートは、テンプレートのルートに存在する特別なフォルダーと構成ファイルによって認識されます。</span><span class="sxs-lookup"><span data-stu-id="eca23-138">Templates are recognized by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="eca23-139">このチュートリアルでは、テンプレート フォルダーは _working\templates\extensions_ にあります。</span><span class="sxs-lookup"><span data-stu-id="eca23-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="eca23-140">テンプレートを作成すると、特別な構成フォルダーを除く、テンプレート フォルダー内のすべてのファイルとフォルダーがテンプレートの一部として含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca23-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="eca23-141">この構成フォルダーの名前は _.template.config_ です。</span><span class="sxs-lookup"><span data-stu-id="eca23-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="eca23-142">まず、 _.template.config_ という名前の新しいサブフォルダーを作成し、このフォルダーに入ります。</span><span class="sxs-lookup"><span data-stu-id="eca23-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="eca23-143">次に、_template.json_ という名前の新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="eca23-144">フォルダー構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="eca23-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="eca23-145">お好みのテキスト エディターで _template.json_ を開き、次の JSON コードを貼り付けて保存します。</span><span class="sxs-lookup"><span data-stu-id="eca23-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="eca23-146">この構成ファイルには、テンプレートのすべての設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca23-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="eca23-147">`name` や `shortName` などの基本設定を確認できますが、`item` に設定された `tags/type` 値もあります。</span><span class="sxs-lookup"><span data-stu-id="eca23-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="eca23-148">これにより、テンプレートが項目テンプレートとして分類されます。</span><span class="sxs-lookup"><span data-stu-id="eca23-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="eca23-149">作成するテンプレートの種類に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="eca23-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="eca23-150">`item` および `project` 値は、ユーザーが検索しているテンプレートの種類を簡単にフィルター処理できるように .NET で推奨されている一般的な名前です。</span><span class="sxs-lookup"><span data-stu-id="eca23-150">The `item` and `project` values are common names that .NET recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="eca23-151">`classifications` 項目は、`dotnet new` を実行してテンプレートの一覧を取得したときに表示される **tags** 列を表します。</span><span class="sxs-lookup"><span data-stu-id="eca23-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="eca23-152">ユーザーは分類タグに基づいて検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="eca23-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="eca23-153">\*.json ファイル内の `tags` プロパティと、`classifications` の tags 一覧を混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="eca23-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="eca23-154">これらは残念ながら同じ名前を付けられてしまった 2 つの異なるものです。</span><span class="sxs-lookup"><span data-stu-id="eca23-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="eca23-155">*template.json* ファイルの完全スキーマは [JSON Schema Store](http://json.schemastore.org/template) にあります。</span><span class="sxs-lookup"><span data-stu-id="eca23-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="eca23-156">*template.json* ファイルについて詳しくは、[dotnet テンプレート wiki](https://github.com/dotnet/templating/wiki) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eca23-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="eca23-157">有効な _.template.config/template.json_ ファイルを用意したので、テンプレートをインストールする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="eca23-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="eca23-158">ターミナルで _extensions_ フォルダーに移動し、次のコマンドを実行して現在のフォルダーにあるテンプレートをインストールします。</span><span class="sxs-lookup"><span data-stu-id="eca23-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="eca23-159">**Windows の場合**: `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="eca23-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="eca23-160">**Linux または macOS の場合**: `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="eca23-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="eca23-161">このコマンドにより、インストールされているテンプレートの一覧が出力されます。作成したテンプレートも含まれているはずです。</span><span class="sxs-lookup"><span data-stu-id="eca23-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Example templates: string extensions              stringext                [C#]              Common/Code
Console Application                               console                  [C#], F#, VB      Common/Console
Class library                                     classlib                 [C#], F#, VB      Common/Library
WPF Application                                   wpf                      [C#], VB          Common/WPF
```

## <a name="test-the-item-template"></a><span data-ttu-id="eca23-162">項目テンプレートをテストする</span><span class="sxs-lookup"><span data-stu-id="eca23-162">Test the item template</span></span>

<span data-ttu-id="eca23-163">項目テンプレートをインストールしたので、テストします。</span><span class="sxs-lookup"><span data-stu-id="eca23-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="eca23-164">_test/_ フォルダーに移動し、`dotnet new console` を使用して新しいコンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="eca23-165">これにより、`dotnet run` コマンドを使用して簡単にテストできる作業プロジェクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eca23-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="eca23-166">次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="eca23-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="eca23-167">以下を使用してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="eca23-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="eca23-168">次の出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="eca23-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="eca23-169">次に、`dotnet new stringext` を実行して、テンプレートから _CommonExtensions.cs_ を生成します。</span><span class="sxs-lookup"><span data-stu-id="eca23-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="eca23-170">次の出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="eca23-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="eca23-171">テンプレートによって提供される拡張メソッドを使用して、`"Hello World"` 文字列を反転するように _Program.cs_ 内のコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="eca23-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="eca23-172">プログラムをもう一度実行すると、結果が反転されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="eca23-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="eca23-173">次の出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="eca23-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="eca23-174">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="eca23-174">Congratulations!</span></span> <span data-ttu-id="eca23-175">.NET で項目テンプレートを作成し、配置しました。</span><span class="sxs-lookup"><span data-stu-id="eca23-175">You created and deployed an item template with .NET.</span></span> <span data-ttu-id="eca23-176">このチュートリアル シリーズの次のパートの準備として、作成したテンプレートをアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca23-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="eca23-177">また、必ず _test_ フォルダーからすべてのファイルを削除してください。</span><span class="sxs-lookup"><span data-stu-id="eca23-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="eca23-178">これにより、このチュートリアルの次の主要なセクションの準備が整った状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="eca23-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="eca23-179">テンプレートをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="eca23-179">Uninstall the template</span></span>

<span data-ttu-id="eca23-180">ファイル パスを使用してテンプレートをインストールしたので、**絶対** ファイル パスを使用してアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca23-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="eca23-181">`dotnet new -u` コマンドを実行すると、インストールされているテンプレートの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="eca23-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="eca23-182">作成したテンプレートは最後に表示されているはずです。</span><span class="sxs-lookup"><span data-stu-id="eca23-182">Your template should be listed last.</span></span> <span data-ttu-id="eca23-183">一覧にある `Uninstall Command` を利用してテンプレートをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="eca23-183">Use the `Uninstall Command` listed to uninstall your template.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="eca23-184">次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="eca23-184">You get output similar to the following.</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ProjectTemplates.2.2
    Details:
      NuGetPackageId: Microsoft.DotNet.Common.ProjectTemplates.2.2
      Version: 1.0.2-beta4
      Author: Microsoft
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
    Uninstall Command:
      dotnet new -u Microsoft.DotNet.Common.ProjectTemplates.2.2

... cut to save space ...

C:\Test\templatetutorial\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
    Uninstall Command:
      dotnet new -u C:\working\templates\extensions
```

<span data-ttu-id="eca23-185">作成したテンプレートをアンインストールするには、出力に表示されている `Uninstall Command` を実行します。</span><span class="sxs-lookup"><span data-stu-id="eca23-185">To uninstall the template that you created, run the `Uninstall Command` that is shown in the output.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="eca23-186">次の手順</span><span class="sxs-lookup"><span data-stu-id="eca23-186">Next steps</span></span>

<span data-ttu-id="eca23-187">このチュートリアルでは、項目テンプレートを作成しました。</span><span class="sxs-lookup"><span data-stu-id="eca23-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="eca23-188">プロジェクト テンプレートを作成する方法については、このチュートリアル シリーズの続きを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eca23-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eca23-189">プロジェクト テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="eca23-189">Create a project template</span></span>](cli-templates-create-project-template.md)
