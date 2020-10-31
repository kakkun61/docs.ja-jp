---
title: F# インタラクティブ (dotnet) リファレンス
description: F# インタラクティブ (dotnet fsi) を使用して、コンソールで F# コードを対話形式で実行したり、F# スクリプトを実行したりする方法について説明します。
ms.date: 08/20/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: b1020d8ab8f2282c792fb5d00656b6d43c2c6610
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064120"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="319f0-103">F\# による対話型プログラミング</span><span class="sxs-lookup"><span data-stu-id="319f0-103">Interactive programming with F\#</span></span>

<span data-ttu-id="319f0-104">F# インタラクティブ (dotnet fsi) は、コンソールで F# コードを対話形式で実行したり、F# スクリプトを実行したりするために使用します。</span><span class="sxs-lookup"><span data-stu-id="319f0-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="319f0-105">つまり、F# Interactive は、F# 言語の REPL (Read、Evaluate、Print Loop) を実行します。</span><span class="sxs-lookup"><span data-stu-id="319f0-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="319f0-106">コンソールから F# インタラクティブを実行するには、`dotnet fsi` を実行します。</span><span class="sxs-lookup"><span data-stu-id="319f0-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="319f0-107">`dotnet fsi` はすべての .NET SDK に備わっています。</span><span class="sxs-lookup"><span data-stu-id="319f0-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="319f0-108">使用できるコマンド ライン オプションについては、「[F# Interactive Options](../../language-reference/fsharp-interactive-options.md)」 (F# Interactive オプション) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="319f0-108">For information about command line options available, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

<span data-ttu-id="319f0-109">Visual Studio で F# Interactive を実行するには、ツール バーの **[F# Interactive]** というボタンをクリックするか、 **Ctrl + Alt + F** キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="319f0-109">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive** , or use the keys **Ctrl+Alt+F** .</span></span> <span data-ttu-id="319f0-110">この操作により、対話形式のウィンドウが開きます。このウィンドウは、F# Interactive セッションを実行するツール ウィンドウです</span><span class="sxs-lookup"><span data-stu-id="319f0-110">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="319f0-111">対話形式のウィンドウで実行するコードを選択し、 **Alt + Enter** キーの組み合わせを押す方法もあります。</span><span class="sxs-lookup"><span data-stu-id="319f0-111">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter** .</span></span> <span data-ttu-id="319f0-112">F# インタラクティブが **[F# Interactive]** というツール ウィンドウで開始されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-112">F# Interactive starts in a tool window labeled **F# Interactive** .</span></span> <span data-ttu-id="319f0-113">このショートカット キーを使用するときは、エディター ウィンドウにフォーカスがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="319f0-113">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="319f0-114">コンソールと Visual Studio のどちらを使用している場合でも、コマンド プロンプトが表示され、入力待ちの状態になります。</span><span class="sxs-lookup"><span data-stu-id="319f0-114">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="319f0-115">コード ファイルと同じようにコードを入力できます。</span><span class="sxs-lookup"><span data-stu-id="319f0-115">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="319f0-116">コードをコンパイルして実行するには、2 つのセミコロン ( **;;** ) を入力して、入力行を終了します。</span><span class="sxs-lookup"><span data-stu-id="319f0-116">To compile and execute the code, enter two semicolons ( **;;** ) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="319f0-117">F# Interactive によってコードがコンパイルされ、成功すると、コードが実行され、コンパイルされた型のシグネチャと値が出力されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-117">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="319f0-118">エラーが発生した場合は、エラー メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-118">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="319f0-119">同じセッションで入力したコードからは、前に入力したどの構成要素にもアクセスできるため、プログラムの構築が可能です。</span><span class="sxs-lookup"><span data-stu-id="319f0-119">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="319f0-120">ツール ウィンドウには十分なバッファーが用意されており、必要に応じてコードをファイルにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="319f0-120">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="319f0-121">Visual Studio で実行する場合、F# Interactive はプロジェクトとは独立して動作します。このため、たとえば、プロジェクトで定義された構成要素を F# Interactive で使用することはできません。使用するには、関数のコードを対話形式のウィンドウにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="319f0-121">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="319f0-122">あるライブラリを参照するプロジェクトを開くと、 **ソリューション エクスプローラー** で、F# Interactive のライブラリを参照できます。</span><span class="sxs-lookup"><span data-stu-id="319f0-122">If you have a project open that references some libraries, you can reference these in F# Interactive through **Solution Explorer** .</span></span> <span data-ttu-id="319f0-123">F# Interactive のライブラリを参照するには、 **[参照]** ノードを展開し、ライブラリのショートカット メニューを開き、 **[F# Interactive に送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="319f0-123">To reference a library in F# Interactive, expand the **References** node, open the shortcut menu for the library, and choose **Send to F# Interactive** .</span></span>

<span data-ttu-id="319f0-124">設定を調整することで、F# Interactive コマンド ライン引数 (オプション) を制御できます。</span><span class="sxs-lookup"><span data-stu-id="319f0-124">You can control the F# Interactive command line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="319f0-125">**[ツール]** メニューの **[オプション]** をクリックし、 **[F# ツール]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="319f0-125">On the **Tools** menu, select **Options...** , and then expand **F# Tools** .</span></span> <span data-ttu-id="319f0-126">変更できる 2 つの設定は、F# Interactive オプションおよび 64 ビット コンピューターで F# Interactive を実行する場合にのみ関連する **64 ビット F# Interactive** 設定です。</span><span class="sxs-lookup"><span data-stu-id="319f0-126">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="319f0-127">この設定によって、32 ビットまたは 64 ビット プロセスとして実行するかどうかを決定するためにコンピューター アーキテクチャを使用する、fsi.exe または fsianycpu.exe の専用の 64 ビット バージョンを実行するかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-127">This setting determines whether you want to run the dedicated 64-bit version of fsi.exe or fsianycpu.exe, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="319f0-128">F\# によるスクリプト</span><span class="sxs-lookup"><span data-stu-id="319f0-128">Scripting with F\#</span></span>

<span data-ttu-id="319f0-129">スクリプトで使用されるファイル拡張子は **.fsx** または **.fsscript** です。</span><span class="sxs-lookup"><span data-stu-id="319f0-129">Scripts use the file extension **.fsx** or **.fsscript** .</span></span> <span data-ttu-id="319f0-130">ソース コードをコンパイルした後でそのコンパイル済みのアセンブリを実行する代わりに、 **dotnet fsi** を実行して F# ソース コードのスクリプトのファイル名を指定するだけで、F# インタラクティブによってコードを読み取り、リアルタイムで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="319f0-130">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span>

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a><span data-ttu-id="319f0-131">対話型、スクリプト、およびコンパイル型の環境の違い</span><span class="sxs-lookup"><span data-stu-id="319f0-131">Differences between the interactive, scripting, and compiled environments</span></span>

<span data-ttu-id="319f0-132">F# Interactive でのコードのコンパイル時には、対話形式で実行しているか、スクリプトを実行しているかにかかわらず、シンボル **INTERACTIVE** が定義されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-132">When you are compiling code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="319f0-133">コンパイラでのコードのコンパイル時には、シンボル **COMPILED** が定義されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-133">When you are compiling code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="319f0-134">したがって、コンパイル モードと対話モードでコードを別にする必要がある場合は、条件付きコンパイルを行うプリプロセッサ ディレクティブを使用して、どちらを有効にするかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="319f0-134">Thus, if code needs to be different in compiled and interactive modes, you can use preprocessor directives for conditional compilation to determine which to use.</span></span>

<span data-ttu-id="319f0-135">F# Interactive でスクリプトを実行するときに使用できるディレクティブの中には、コンパイラを実行するときには使用できないものがあります。</span><span class="sxs-lookup"><span data-stu-id="319f0-135">Some directives are available when you are executing scripts in F# Interactive that are not available when you are executing the compiler.</span></span> <span data-ttu-id="319f0-136">次の表に、F# Interactive で使用できるディレクティブの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="319f0-136">The following table summarizes directives that are available when you are using F# Interactive.</span></span>

|<span data-ttu-id="319f0-137">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="319f0-137">Directive</span></span>|<span data-ttu-id="319f0-138">説明</span><span class="sxs-lookup"><span data-stu-id="319f0-138">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="319f0-139">**#help**</span><span class="sxs-lookup"><span data-stu-id="319f0-139">**#help**</span></span>|<span data-ttu-id="319f0-140">使用できるディレクティブに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="319f0-140">Displays information about available directives.</span></span>|
|<span data-ttu-id="319f0-141">**#I**</span><span class="sxs-lookup"><span data-stu-id="319f0-141">**#I**</span></span>|<span data-ttu-id="319f0-142">アセンブリ検索パスを引用符で囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="319f0-142">Specifies an assembly search path in quotation marks.</span></span>|
|<span data-ttu-id="319f0-143">**#load**</span><span class="sxs-lookup"><span data-stu-id="319f0-143">**#load**</span></span>|<span data-ttu-id="319f0-144">ソース ファイルを読み取り、コンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="319f0-144">Reads a source file, compiles it, and runs it.</span></span>|
|<span data-ttu-id="319f0-145">**#quit**</span><span class="sxs-lookup"><span data-stu-id="319f0-145">**#quit**</span></span>|<span data-ttu-id="319f0-146">F# Interactive セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="319f0-146">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="319f0-147">**#r**</span><span class="sxs-lookup"><span data-stu-id="319f0-147">**#r**</span></span>|<span data-ttu-id="319f0-148">アセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="319f0-148">References an assembly.</span></span>|
|<span data-ttu-id="319f0-149">**#time ["on"&#124;"off"]**</span><span class="sxs-lookup"><span data-stu-id="319f0-149">**#time ["on"&#124;"off"]**</span></span>|<span data-ttu-id="319f0-150">**#time** 単独で、パフォーマンス情報を表示するかどうかを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="319f0-150">By itself, **#time** toggles whether to display performance information.</span></span> <span data-ttu-id="319f0-151">有効にすると、解釈および実行されるコードのセクションごとに、実時間、CPU 時間、およびガベージ コレクションの情報が F# Interactive によって計測されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-151">When it is enabled, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="319f0-152">F# Interactive でファイルまたはパスを指定するときは、リテラル文字列が想定されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-152">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="319f0-153">したがって、ファイルとパスは引用符で囲む必要があり、通常のエスケープ文字が適用されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-153">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="319f0-154">また、@ 文字を使用して、パスを含む文字列が F# Internactive で逐語的文字列として解釈されるように指示することもできます。</span><span class="sxs-lookup"><span data-stu-id="319f0-154">Also, you can use the @ character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="319f0-155">この場合、F# Interactive はエスケープ文字を無視するようになります。</span><span class="sxs-lookup"><span data-stu-id="319f0-155">This causes F# Interactive to ignore any escape characters.</span></span>

<span data-ttu-id="319f0-156">コンパイル モードと対話モードの違いの 1 つは、コマンド ライン引数にアクセスする方法です。</span><span class="sxs-lookup"><span data-stu-id="319f0-156">One of the differences between compiled and interactive mode is the way you access command line arguments.</span></span> <span data-ttu-id="319f0-157">コンパイル モードでは **System.Environment.GetCommandLineArgs** を使用します。</span><span class="sxs-lookup"><span data-stu-id="319f0-157">In compiled mode, use **System.Environment.GetCommandLineArgs** .</span></span> <span data-ttu-id="319f0-158">スクリプトでは、 **fsi.CommandLineArgs** を使用します。</span><span class="sxs-lookup"><span data-stu-id="319f0-158">In scripts, use **fsi.CommandLineArgs** .</span></span>

<span data-ttu-id="319f0-159">次のコードは、スクリプトでコマンド ライン引数を読み取る関数を作成する方法と、スクリプトから別のアセンブリを参照する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="319f0-159">The following code illustrates how to create a function that reads the command line arguments in a script and also demonstrates how to reference another assembly from a script.</span></span> <span data-ttu-id="319f0-160">最初のコード ファイル **MyAssembly.fs** は、参照先となるアセンブリのコードです。</span><span class="sxs-lookup"><span data-stu-id="319f0-160">The first code file, **MyAssembly.fs** , is the code for the assembly being referenced.</span></span> <span data-ttu-id="319f0-161">このファイルをコマンド ラインでコンパイルし ( **fsc -a MyAssembly.fs** )、2 番目のファイルをスクリプトとしてコマンド ラインで実行します ( **fsi --exec file1.fsx** test)。</span><span class="sxs-lookup"><span data-stu-id="319f0-161">Compile this file with the command line: **fsc -a MyAssembly.fs** and then execute the second file as a script with the command line: **fsi --exec file1.fsx** test</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="319f0-162">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="319f0-162">The output is as follows:</span></span>

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="package-management-in-f-interactive"></a><span data-ttu-id="319f0-163">F# インタラクティブの Package Management</span><span class="sxs-lookup"><span data-stu-id="319f0-163">Package Management in F# Interactive</span></span>

[!NOTE] <span data-ttu-id="319f0-164">Package Management は、.NET SDK バージョン `3.1.300` 以降と、.NET SDK バージョン `5.*` のすべてに付属するバージョンの `dotnet fsi` のプレビュー機能として使用できます。</span><span class="sxs-lookup"><span data-stu-id="319f0-164">Package management is available as a preview feature in versions of `dotnet fsi` shipped in the `3.1.300` and greater versions of the .NET SDK, as well as all `5.*` versions of the .NET SDK.</span></span> <span data-ttu-id="319f0-165">このプレビュー リリースで有効にするには、`--langversion:preview` 引数を指定して `dotnet fsi` を実行します。</span><span class="sxs-lookup"><span data-stu-id="319f0-165">To enable it in this preview release, run `dotnet fsi` with the `--langversion:preview` argument.</span></span>

<span data-ttu-id="319f0-166">F# インタラクティブで DLL を参照するための `#r` 構文を使用して、nuget パッケージを参照することもできます。それには次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="319f0-166">The `#r` syntax for referencing a DLL in F# Interactive can also be used to reference a nuget package via the following syntax:</span></span>

```fsharp
#r "nuget: <package name>"
```

<span data-ttu-id="319f0-167">たとえば、`FSharp.Data` パッケージを参照するには、次の `#r` 参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="319f0-167">For example, to reference the `FSharp.Data` package, use the following `#r` reference:</span></span>

```fsharp
#r "nuget: FSharp.Data"
```

<span data-ttu-id="319f0-168">この行を実行すると、最新バージョンの `FSharp.Data` パッケージが nuget キャッシュにダウンロードされ、現在の F# インタラクティブ セッションで参照されます。</span><span class="sxs-lookup"><span data-stu-id="319f0-168">After executing this line, the latest version of the `FSharp.Data` package will be downloaded to your nuget cache and referenced in the current F# Interactive session.</span></span>

<span data-ttu-id="319f0-169">パッケージ名に加えて、パッケージの特定のバージョンも次の短い構文で参照できます。</span><span class="sxs-lookup"><span data-stu-id="319f0-169">In addition to the package name, specific versions of a package can be referenced via a short syntax:</span></span>

```fsharp
#r "nuget: FSharp.Data, 3.3.2"
```

<span data-ttu-id="319f0-170">より明確な形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="319f0-170">or in a more explicit fashion:</span></span>

```fsharp
#r "nuget: FSharp.Data, Version=3.3.2"
```

## <a name="related-articles"></a><span data-ttu-id="319f0-171">関連記事</span><span class="sxs-lookup"><span data-stu-id="319f0-171">Related articles</span></span>

|<span data-ttu-id="319f0-172">Title</span><span class="sxs-lookup"><span data-stu-id="319f0-172">Title</span></span>|<span data-ttu-id="319f0-173">説明</span><span class="sxs-lookup"><span data-stu-id="319f0-173">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="319f0-174">F# Interactive オプション</span><span class="sxs-lookup"><span data-stu-id="319f0-174">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="319f0-175">F# インタラクティブ (fsi.exe) のコマンド ライン構文やオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="319f0-175">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|
