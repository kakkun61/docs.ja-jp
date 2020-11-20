---
title: 'チュートリアル: .NET ツールを作成する'
description: .NET ツールを作成する方法について説明します。 ツールは、.NET CLI を使用してインストールするコンソール アプリケーションです。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 93d0567f3d73707f828f84fad6128804debf6579
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633779"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a><span data-ttu-id="2ec24-104">チュートリアル: .NET CLI を使用して .NET ツールを作成する</span><span class="sxs-lookup"><span data-stu-id="2ec24-104">Tutorial: Create a .NET tool using the .NET CLI</span></span>

<span data-ttu-id="2ec24-105">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="2ec24-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="2ec24-106">このチュートリアルでは、.NET ツールを作成およびパッケージ化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-106">This tutorial teaches you how to create and package a .NET tool.</span></span> <span data-ttu-id="2ec24-107">.NET CLI では、他のユーザーがインストールおよび実行できる、コンソール アプリケーションをツールとして作成できます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-107">The .NET CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="2ec24-108">.NET ツールは、.NET CLI でインストールする NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="2ec24-108">.NET tools are NuGet packages that are installed from the .NET CLI.</span></span> <span data-ttu-id="2ec24-109">ツールの詳細については、[.NET ツールの概要](global-tools.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ec24-109">For more information about tools, see [.NET tools overview](global-tools.md).</span></span>

<span data-ttu-id="2ec24-110">作成するツールは、メッセージを入力として受け取り、ロボットの画像を作成するテキスト行と共にメッセージを表示するコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="2ec24-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="2ec24-111">これは、3 つのチュートリアル シリーズの第 1 回です。</span><span class="sxs-lookup"><span data-stu-id="2ec24-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="2ec24-112">このチュートリアルでは、ツールを作成してパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="2ec24-113">次の 2 つのチュートリアルでは、[グローバル ツールとしてツールを使用する](global-tools-how-to-use.md)方法と、[ローカル ツールとしてツールを使用する](local-tools-how-to-use.md)方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ec24-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2ec24-114">Prerequisites</span></span>

- <span data-ttu-id="2ec24-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="2ec24-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="2ec24-116">このチュートリアルと次の[グローバル ツールのチュートリアル](global-tools-how-to-use.md)は、.NET Core SDK 2.1 以降のバージョンに適用されます。これは、そのバージョンからグローバル ツールを使用できるようになったためです。</span><span class="sxs-lookup"><span data-stu-id="2ec24-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="2ec24-117">ただし、このチュートリアルでは、[ローカル ツールのチュートリアル](local-tools-how-to-use.md)に進むことができるように、3.1 以降がインストールされていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="2ec24-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="2ec24-118">ローカル ツールは .NET Core SDK 3.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="2ec24-119">ツールを作成する手順は、グローバル ツールとローカル ツールのどちらとして使用する場合でも同じです。</span><span class="sxs-lookup"><span data-stu-id="2ec24-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="2ec24-120">ユーザーが選んだテキスト エディターまたはコード エディター。</span><span class="sxs-lookup"><span data-stu-id="2ec24-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="2ec24-121">プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="2ec24-121">Create a project</span></span>

1. <span data-ttu-id="2ec24-122">コマンド プロンプトを開き、*repository* という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="2ec24-123">*repository* フォルダーに移動し、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-123">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   <span data-ttu-id="2ec24-124">このコマンドを実行すると、*repository* フォルダーの下に *microsoft.botsay* という名前の新しいフォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-124">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

1. <span data-ttu-id="2ec24-125">*microsoft.botsay* フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-125">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="2ec24-126">コードの追加</span><span class="sxs-lookup"><span data-stu-id="2ec24-126">Add the code</span></span>

1. <span data-ttu-id="2ec24-127">コード エディターを使用して `Program.cs` ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-127">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="2ec24-128">次の `using` ディレクティブをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-128">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="2ec24-129">`Main` メソッドを次のコードに置き換えて、アプリケーションのコマンドライン引数を処理します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-129">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   <span data-ttu-id="2ec24-130">引数が渡されなかった場合、短いヘルプ メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-130">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="2ec24-131">それ以外の場合、次の手順で作成する `ShowBot` メソッドを呼び出すと、すべての引数が 1 つの文字列に連結され、出力されます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-131">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="2ec24-132">文字列パラメーターを受け取る `ShowBot` という新しいメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-132">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="2ec24-133">このメソッドを実行すると、テキストの行を使用してメッセージとロボットの画像を出力されます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-133">The method prints out the message and an image of a robot using lines of text.</span></span>

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. <span data-ttu-id="2ec24-134">変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-134">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="2ec24-135">アプリケーションをテストする</span><span class="sxs-lookup"><span data-stu-id="2ec24-135">Test the application</span></span>

<span data-ttu-id="2ec24-136">プロジェクトを実行して出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-136">Run the project and see the output.</span></span> <span data-ttu-id="2ec24-137">次のようにコマンド ラインを変えて、異なる結果を表示してみてください。</span><span class="sxs-lookup"><span data-stu-id="2ec24-137">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="2ec24-138">区切り記号 `--` の後の引数は、すべてアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-138">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="2ec24-139">ツールをパッケージ化する</span><span class="sxs-lookup"><span data-stu-id="2ec24-139">Package the tool</span></span>

<span data-ttu-id="2ec24-140">アプリケーションをパッケージ化してツールとして配布する前に、プロジェクト ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ec24-140">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="2ec24-141">*microsoft.botsay.csproj* ファイルを開き、3 つの新しい XML ノードを `<PropertyGroup>` ノードの最後に追加します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-141">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="2ec24-142">`<ToolCommandName>` は、インストール後にツールを呼び出すコマンドを指定する省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="2ec24-142">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="2ec24-143">この要素を指定しない場合、ツールのコマンド名は、 *.csproj* 拡張子のないプロジェクト ファイル名になります。</span><span class="sxs-lookup"><span data-stu-id="2ec24-143">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="2ec24-144">`<PackageOutputPath>` は、NuGet パッケージが生成される場所を決定する省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="2ec24-144">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="2ec24-145">NuGet パッケージは、.NET Core CLI でツールのインストールに使用されるものです。</span><span class="sxs-lookup"><span data-stu-id="2ec24-145">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="2ec24-146">プロジェクト ファイルは次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="2ec24-146">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="2ec24-147">[dotnet pack](dotnet-pack.md) コマンドを実行して、NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ec24-147">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="2ec24-148">*microsoft.botsay.1.0.0.nupkg* ファイルは、*microsoft.botsay.csproj* ファイルの `<PackageOutputPath>` 値で識別されるフォルダー (この例では、 *./nupkg* フォルダー) に作成されます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-148">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="2ec24-149">ツールをリリースする場合は、`https://www.nuget.org` にアップロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-149">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="2ec24-150">NuGet 上でツールを使用できるようになると、開発者は [dotnet tool install](dotnet-tool-install.md) コマンドを使用してツールをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-150">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="2ec24-151">このチュートリアルでは、ローカルの *nupkg* フォルダーからパッケージを直接インストールするため、NuGet にパッケージをアップロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2ec24-151">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="2ec24-152">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2ec24-152">Troubleshoot</span></span>

<span data-ttu-id="2ec24-153">チュートリアルの実行中にエラー メッセージが表示された場合は、「[.NET ツールの使用に関する問題のトラブルシューティング](troubleshoot-usage-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ec24-153">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ec24-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="2ec24-154">Next steps</span></span>

<span data-ttu-id="2ec24-155">このチュートリアルでは、コンソール アプリケーションを作成し、ツールとしてパッケージ化しました。</span><span class="sxs-lookup"><span data-stu-id="2ec24-155">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="2ec24-156">このツールをグローバル ツールとして使用する方法については、次のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="2ec24-156">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ec24-157">グローバル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="2ec24-157">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="2ec24-158">必要に応じて、グローバル ツール チュートリアルをスキップし、ローカル ツール チュートリアルに直接移動できます。</span><span class="sxs-lookup"><span data-stu-id="2ec24-158">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ec24-159">ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="2ec24-159">Install and use a local tool</span></span>](local-tools-how-to-use.md)
