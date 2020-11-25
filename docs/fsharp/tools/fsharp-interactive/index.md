---
title: F# インタラクティブ (dotnet) リファレンス
description: F# インタラクティブ (dotnet fsi) を使用して、コンソールで F# コードを対話形式で実行したり、F# スクリプトを実行したりする方法について説明します。
ms.date: 10/31/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: b535cb03d76909043ca192ed5a9d2078f9343795
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099484"
---
# <a name="interactive-programming-with-f"></a><span data-ttu-id="1f974-103">F\# による対話型プログラミング</span><span class="sxs-lookup"><span data-stu-id="1f974-103">Interactive programming with F\#</span></span>

<span data-ttu-id="1f974-104">F# インタラクティブ (dotnet fsi) は、コンソールで F# コードを対話形式で実行したり、F# スクリプトを実行したりするために使用します。</span><span class="sxs-lookup"><span data-stu-id="1f974-104">F# Interactive (dotnet fsi) is used to run F# code interactively at the console, or to execute F# scripts.</span></span> <span data-ttu-id="1f974-105">つまり、F# Interactive は、F# 言語の REPL (Read、Evaluate、Print Loop) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f974-105">In other words, F# interactive executes a REPL (Read, Evaluate, Print Loop) for the F# language.</span></span>

<span data-ttu-id="1f974-106">コンソールから F# インタラクティブを実行するには、`dotnet fsi` を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f974-106">To run F# Interactive from the console, run `dotnet fsi`.</span></span> <span data-ttu-id="1f974-107">`dotnet fsi` はすべての .NET SDK に備わっています。</span><span class="sxs-lookup"><span data-stu-id="1f974-107">You will find `dotnet fsi` in any .NET SDK.</span></span>

<span data-ttu-id="1f974-108">使用できるコマンド ライン オプションについては、「[F# Interactive オプション](../../language-reference/fsharp-interactive-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f974-108">For information about available command-line options, see [F# Interactive Options](../../language-reference/fsharp-interactive-options.md).</span></span>

## <a name="executing-code-directly-in-f-interactive"></a><span data-ttu-id="1f974-109">F# インタラクティブでコードを直接実行する</span><span class="sxs-lookup"><span data-stu-id="1f974-109">Executing code directly in F# Interactive</span></span>

<span data-ttu-id="1f974-110">F# インタラクティブは REPL (read–eval–print loop) であるため、コードを対話形式で実行できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-110">Because F# Interactive is a REPL (read-eval-print loop), you can execute code interactively in it.</span></span> <span data-ttu-id="1f974-111">コマンド ラインから `dotnet fsi` を実行した後の対話型セッションの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1f974-111">Here is an example of an interactive session after executing `dotnet fsi` from the command line:</span></span>

```console
Microsoft (R) F# Interactive version 11.0.0.0 for F# 5.0
Copyright (c) Microsoft Corporation. All Rights Reserved.

For help type #help;;

> let square x = x *  x;;
val square : x:int -> int

> square 12;;
val it : int = 144

> printfn "Hello, FSI!"
- ;;
Hello, FSI!
val it : unit = ()
```

<span data-ttu-id="1f974-112">次の 2 つの主要な点がわかります。</span><span class="sxs-lookup"><span data-stu-id="1f974-112">You'll notice two main things:</span></span>

1. <span data-ttu-id="1f974-113">すべてのコードは、評価するために 2 つのセミコロン (`;;`) で終了する必要があります</span><span class="sxs-lookup"><span data-stu-id="1f974-113">All code must be terminated with a double semicolon (`;;`) to be evaluated</span></span>
2. <span data-ttu-id="1f974-114">コードは評価され、`it` 値に格納されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-114">Code is evaluated and stored in an `it` value.</span></span> <span data-ttu-id="1f974-115">`it` は対話的に参照できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-115">You can reference `it` interactively.</span></span>

<span data-ttu-id="1f974-116">F# インタラクティブでは、複数行の入力もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1f974-116">F# Interactive also supports multi-line input.</span></span> <span data-ttu-id="1f974-117">2 つのセミコロン (`;;`) を使用して、入力を終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f974-117">You just need to terminate your submission with a double semicolon (`;;`).</span></span> <span data-ttu-id="1f974-118">F# インタラクティブに対して貼り付けられ、評価された、次のスニペットを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="1f974-118">Consider the following snippet that has been pasted into and evaluated by F# Interactive:</span></span>

```console
> let getOddSquares xs =
-     xs
-     |> List.filter (fun x -> x % 2 <> 0)
-     |> List.map (fun x -> x * x)
-
- printfn "%A" (getOddSquares [1..10]);;
[1; 9; 25; 49; 81]
val getOddSquares : xs:int list -> int list
val it : unit = ()

>
```

<span data-ttu-id="1f974-119">コードの書式設定は保持されており、入力を終了する 2 つのセミコロン (`;;`) があります。</span><span class="sxs-lookup"><span data-stu-id="1f974-119">The code's formatting is preserved, and there is a double semicolon (`;;`) terminating the input.</span></span> <span data-ttu-id="1f974-120">その後 F# インタラクティブによってコードが評価され、結果が出力されています。</span><span class="sxs-lookup"><span data-stu-id="1f974-120">F# Interactive then evaluated the code and printed the results!</span></span>

## <a name="scripting-with-f"></a><span data-ttu-id="1f974-121">F\# によるスクリプト</span><span class="sxs-lookup"><span data-stu-id="1f974-121">Scripting with F\#</span></span>

<span data-ttu-id="1f974-122">F# インタラクティブでの対話的なコードの評価は学習ツールとしては優れていますが、通常のエディターでコードを記述するほど生産的ではないことがすぐにわかります。</span><span class="sxs-lookup"><span data-stu-id="1f974-122">Evaluating code interactively in F# Interactive can be a great learning tool, but you'll quickly find that it's not as productive as writing code in a normal editor.</span></span> <span data-ttu-id="1f974-123">通常のコード編集をサポートするために、F# スクリプトを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="1f974-123">To support normal code editing, you can write F# scripts.</span></span>

<span data-ttu-id="1f974-124">スクリプトで使用されるファイル拡張子は **.fsx** です。</span><span class="sxs-lookup"><span data-stu-id="1f974-124">Scripts use the file extension **.fsx**.</span></span> <span data-ttu-id="1f974-125">ソース コードをコンパイルした後でそのコンパイル済みのアセンブリを実行する代わりに、**dotnet fsi** を実行して F# ソース コードのスクリプトのファイル名を指定するだけで、F# インタラクティブによってコードを読み取り、リアルタイムで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1f974-125">Instead of compiling source code and then later running the compiled assembly, you can just run **dotnet fsi** and specify the filename of the script of F# source code, and F# interactive reads the code and executes it in real time.</span></span> <span data-ttu-id="1f974-126">たとえば、`Script.fsx` という名前の次のスクリプトを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="1f974-126">For example, consider the following script called `Script.fsx`:</span></span>

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

printfn "%A" (getOddSquares [1..10])
```

<span data-ttu-id="1f974-127">このファイルをコンピューター上に作成したら、`dotnet fsi` を使用して実行し、ターミナル ウィンドウで直接出力を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="1f974-127">When this file is created in your machine, you can run it with `dotnet fsi` and see the output directly in your terminal window:</span></span>

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

<span data-ttu-id="1f974-128">F# スクリプトは [Visual Studio](../../get-started/get-started-visual-studio.md)、[Visual Studio Code](../../get-started/get-started-vscode.md)、[Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md) でネイティブにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1f974-128">F# scripting is natively supported in [Visual Studio](../../get-started/get-started-visual-studio.md), [Visual Studio Code](../../get-started/get-started-vscode.md), and [Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md).</span></span>

## <a name="referencing-packages-in-f-interactive"></a><span data-ttu-id="1f974-129">F# インタラクティブでのパッケージの参照</span><span class="sxs-lookup"><span data-stu-id="1f974-129">Referencing packages in F# Interactive</span></span>

<span data-ttu-id="1f974-130">F# インタラクティブでは、`#r "nuget:"` 構文と省略可能なバージョンを使用した、NuGet パッケージの参照がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1f974-130">F# Interactive supports referencing NuGet packages with the `#r "nuget:"` syntax and an optional version:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

<span data-ttu-id="1f974-131">バージョンを指定しない場合は、使用可能な最上位のプレビュー版でないパッケージが取得されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-131">If a version is not specified, the highest available non-preview package is taken.</span></span> <span data-ttu-id="1f974-132">特定のバージョンを参照するには、コンマを使用してバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f974-132">To reference a specific version, introduce the version via a comma.</span></span> <span data-ttu-id="1f974-133">これは、パッケージのプレビュー バージョンを参照するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="1f974-133">This can be handy when referencing a preview version of a package.</span></span> <span data-ttu-id="1f974-134">たとえば、プレビュー バージョンの [DiffSharp](https://diffsharp.github.io/) を使用する次のスクリプトを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="1f974-134">For example, consider this script using a preview version of [DiffSharp](https://diffsharp.github.io/):</span></span>

```fsharp
#r "nuget: DiffSharp-lite, 1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn "%A" (f (dsharp.tensor 1.2))
```

<span data-ttu-id="1f974-135">スクリプト内では、必要な数だけパッケージ参照を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-135">You can specify as many package references as you like in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="1f974-136">現在、フレームワーク参照 (`Microsoft.NET.Sdk.Web` や `Microsoft.NET.Sdk.WindowsDesktop` など) を使用するスクリプトには制限があります。</span><span class="sxs-lookup"><span data-stu-id="1f974-136">There's currently a limitation for scripts that use framework references (e.g.`Microsoft.NET.Sdk.Web` or  `Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="1f974-137">Saturn、Giraffe、WinForms などのパッケージは使用できません。</span><span class="sxs-lookup"><span data-stu-id="1f974-137">Packages like Saturn, Giraffe, WinForms are not available.</span></span> <span data-ttu-id="1f974-138">これは、イシュー [#9417](https://github.com/dotnet/fsharp/issues/9417) で追跡されています。</span><span class="sxs-lookup"><span data-stu-id="1f974-138">This is being tracked in issue [#9417](https://github.com/dotnet/fsharp/issues/9417).</span></span>

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a><span data-ttu-id="1f974-139">F# インタラクティブでディスク上のアセンブリを参照する</span><span class="sxs-lookup"><span data-stu-id="1f974-139">Referencing assemblies on disk with F# interactive</span></span>

<span data-ttu-id="1f974-140">また、ディスク上にアセンブリがあり、それをスクリプト内で参照したい場合は、`#r` 構文を使用してアセンブリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-140">Alternatively, if you have an assembly on disk and wish to reference that in a script, you can use the `#r` syntax to specify an assembly.</span></span> <span data-ttu-id="1f974-141">`MyAssembly.dll` にコンパイルされるプロジェクト内の次のコードについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="1f974-141">Consider the following code in a project compiled into `MyAssembly.dll`:</span></span>

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

<span data-ttu-id="1f974-142">コンパイルしたら、`Script.fsx` という名前のファイル内で次のように参照できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-142">One compiled, you can reference it in a file called `Script.fsx` like so:</span></span>

```fsharp
#r "path/to/MyAssembly.dll"

printfn "%A" (MyAssembly.myFunction 10 40)
```

<span data-ttu-id="1f974-143">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1f974-143">The output is as follows:</span></span>

```console
dotnet fsi Script.fsx
90
```

<span data-ttu-id="1f974-144">スクリプト内では、必要な数だけアセンブリ参照を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-144">You can specify as many assembly references as you like in a script.</span></span>

## <a name="loading-other-scripts"></a><span data-ttu-id="1f974-145">他のスクリプトの読み込み</span><span class="sxs-lookup"><span data-stu-id="1f974-145">Loading other scripts</span></span>

<span data-ttu-id="1f974-146">スクリプトを作成する際は、異なるスクリプトを異なるタスク用に使用すると便利なことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="1f974-146">When scripting, it can often be helpful to use different scripts for different tasks.</span></span> <span data-ttu-id="1f974-147">場合によっては、あるスクリプトのコードを別のスクリプトで再利用することが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="1f974-147">Sometimes you may want to reuse code from on script in another.</span></span> <span data-ttu-id="1f974-148">その内容をコピーしてファイルに貼り付ける代わりに、`#load` を使用して簡単に読み込んで評価することができます。</span><span class="sxs-lookup"><span data-stu-id="1f974-148">Rather than copy-pasting its contents into your file, you can simple load and evaluate it with `#load`.</span></span>

<span data-ttu-id="1f974-149">次の `Script1.fsx` を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="1f974-149">Consider the following `Script1.fsx`:</span></span>

```fsharp
let square x = x * x
```

<span data-ttu-id="1f974-150">また、これを使用するファイル `Script2.fsx` があります。</span><span class="sxs-lookup"><span data-stu-id="1f974-150">And the consuming file, `Script2.fsx`:</span></span>

```fsharp
#load "Script1.fsx"
open Script1

printfn "%d" (square 12)
```

<span data-ttu-id="1f974-151">`open Script1` 宣言が必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1f974-151">Note that the `open Script1` declaration is required.</span></span> <span data-ttu-id="1f974-152">これは、F# スクリプト内のコンストラクトが、それを含むスクリプト ファイルの名前である最上位レベルのモジュールにコンパイルされるためです。</span><span class="sxs-lookup"><span data-stu-id="1f974-152">This is because constructs in an F# script are compiled into a top-level module that is the name of the script file it is in.</span></span>

<span data-ttu-id="1f974-153">次のように `Script2.fsx` を評価できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-153">You can evaluate `Script2.fsx` like so:</span></span>

```console
dotnet fsi Script2.fsx
144
```

<span data-ttu-id="1f974-154">スクリプト内では、必要な数だけ `#load` ディレクティブを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-154">You can specify as many `#load` directives as you like in a script.</span></span>

## <a name="using-the-fsi-object-in-f-code"></a><span data-ttu-id="1f974-155">F# コードでの `fsi` オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="1f974-155">Using the `fsi` object in F# code</span></span>

<span data-ttu-id="1f974-156">F# スクリプトでは、F# インタラクティブ セッションを表すカスタム `fsi` オブジェクトにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="1f974-156">F# scripts have access to a custom `fsi` object that represents the F# Interactive session.</span></span> <span data-ttu-id="1f974-157">これにより、出力の書式設定などをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="1f974-157">It allows you to customize things like output formatting.</span></span> <span data-ttu-id="1f974-158">これはコマンド ライン引数にアクセスする方法でもあります。</span><span class="sxs-lookup"><span data-stu-id="1f974-158">It is also how you can access command-line arguments.</span></span>

<span data-ttu-id="1f974-159">次の例は、コマンド ライン引数を取得して使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1f974-159">The following example shows how to get and use command-line arguments:</span></span>

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn "%s" arg
```

<span data-ttu-id="1f974-160">これを評価すると、すべての引数が出力されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-160">When evaluated, it prints all arguments.</span></span> <span data-ttu-id="1f974-161">最初の引数は、常に評価されるスクリプトの名前になります。</span><span class="sxs-lookup"><span data-stu-id="1f974-161">The first argument is always the name of the script that is evaluated:</span></span>

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

<span data-ttu-id="1f974-162">同じ引数にアクセスするために `System.Environment.GetCommandLineArgs()` を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1f974-162">You can also use `System.Environment.GetCommandLineArgs()` to access the same arguments.</span></span>

## <a name="f-interactive-directive-reference"></a><span data-ttu-id="1f974-163">F# インタラクティブのディレクティブのリファレンス</span><span class="sxs-lookup"><span data-stu-id="1f974-163">F# Interactive directive reference</span></span>

<span data-ttu-id="1f974-164">前述の `#r` および `#load` ディレクティブは、F# インタラクティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-164">The `#r` and `#load` directives seen previously are only available in F# Interactive.</span></span> <span data-ttu-id="1f974-165">F# インタラクティブでのみ使用できるディレクティブがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="1f974-165">There are several directives only available in F# Interactive:</span></span>

|<span data-ttu-id="1f974-166">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1f974-166">Directive</span></span>|<span data-ttu-id="1f974-167">説明</span><span class="sxs-lookup"><span data-stu-id="1f974-167">Description</span></span>|
|---------|-----------|
|`#r "nuget:..."`|<span data-ttu-id="1f974-168">NuGet からパッケージを参照します</span><span class="sxs-lookup"><span data-stu-id="1f974-168">References a package from NuGet</span></span>|
|`#r "assembly-name.dll"`|<span data-ttu-id="1f974-169">ディスク上のアセンブリを参照します</span><span class="sxs-lookup"><span data-stu-id="1f974-169">References an assembly on disk</span></span>|
|`#load "file-name.fsx"`|<span data-ttu-id="1f974-170">ソース ファイルを読み取り、コンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="1f974-170">Reads a source file, compiles it, and runs it.</span></span>|
|`#help`|<span data-ttu-id="1f974-171">使用できるディレクティブに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="1f974-171">Displays information about available directives.</span></span>|
|`#I`|<span data-ttu-id="1f974-172">アセンブリ検索パスを引用符で囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="1f974-172">Specifies an assembly search path in quotation marks.</span></span>|
|`#quit`|<span data-ttu-id="1f974-173">F# Interactive セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="1f974-173">Terminates an F# Interactive session.</span></span>|
|<span data-ttu-id="1f974-174">`#time "on"` または `#time "off"`</span><span class="sxs-lookup"><span data-stu-id="1f974-174">`#time "on"` or `#time "off"`</span></span>|<span data-ttu-id="1f974-175">`#time` 単独で、パフォーマンス情報を表示するかどうかを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="1f974-175">By itself, `#time` toggles whether to display performance information.</span></span> <span data-ttu-id="1f974-176">`"on"` の場合、解釈および実行されるコードのセクションごとに、実時間、CPU 時間、およびガベージ コレクションの情報が F# インタラクティブによって計測されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-176">When it is `"on"`, F# Interactive measures real time, CPU time, and garbage collection information for each section of code that is interpreted and executed.</span></span>|

<span data-ttu-id="1f974-177">F# Interactive でファイルまたはパスを指定するときは、リテラル文字列が想定されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-177">When you specify files or paths in F# Interactive, a string literal is expected.</span></span> <span data-ttu-id="1f974-178">したがって、ファイルとパスは引用符で囲む必要があり、通常のエスケープ文字が適用されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-178">Therefore, files and paths must be in quotation marks, and the usual escape characters apply.</span></span> <span data-ttu-id="1f974-179">`@` 文字を使用して、パスを含む文字列が F# インタラクティブで逐語的文字列として解釈されるように指示することもできます。</span><span class="sxs-lookup"><span data-stu-id="1f974-179">You can use the `@` character to cause F# Interactive to interpret a string that contains a path as a verbatim string.</span></span> <span data-ttu-id="1f974-180">この場合、F# Interactive はエスケープ文字を無視するようになります。</span><span class="sxs-lookup"><span data-stu-id="1f974-180">This causes F# Interactive to ignore any escape characters.</span></span>

## <a name="interactive-and-compiled-preprocessor-directives"></a><span data-ttu-id="1f974-181">対話型およびコンパイル済みのプリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1f974-181">Interactive and compiled preprocessor directives</span></span>

<span data-ttu-id="1f974-182">F# インタラクティブでコードをコンパイルすると、対話形式で実行しているかスクリプトを実行しているかにかかわらず、シンボル **INTERACTIVE** が定義されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-182">When you compile code in F# Interactive, whether you are running interactively or running a script, the symbol **INTERACTIVE** is defined.</span></span> <span data-ttu-id="1f974-183">コンパイラでコードをコンパイルすると、シンボル **COMPILED** が定義されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-183">When you compile code in the compiler, the symbol **COMPILED** is defined.</span></span> <span data-ttu-id="1f974-184">したがって、コンパイル モードと対話型モードでコードを別にする必要がある場合は、条件付きコンパイルに対する次のプリプロセッサ ディレクティブを使用して、どちらを使用するか決定することができます。</span><span class="sxs-lookup"><span data-stu-id="1f974-184">Thus, if code needs to be different in compiled and interactive modes, you can use these preprocessor directives for conditional compilation to determine which to use.</span></span> <span data-ttu-id="1f974-185">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1f974-185">For example:</span></span>

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a><span data-ttu-id="1f974-186">Visual Studio での F# インタラクティブの使用</span><span class="sxs-lookup"><span data-stu-id="1f974-186">Using F# Interactive in Visual Studio</span></span>

<span data-ttu-id="1f974-187">Visual Studio で F# Interactive を実行するには、ツール バーの **[F# Interactive]** というボタンをクリックするか、**Ctrl + Alt + F** キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f974-187">To run F# Interactive through Visual Studio, you can click the appropriate toolbar button labeled **F# Interactive**, or use the keys **Ctrl+Alt+F**.</span></span> <span data-ttu-id="1f974-188">この操作により、対話形式のウィンドウが開きます。このウィンドウは、F# Interactive セッションを実行するツール ウィンドウです</span><span class="sxs-lookup"><span data-stu-id="1f974-188">Doing this will open the interactive window, a tool window running an F# Interactive session.</span></span> <span data-ttu-id="1f974-189">対話形式のウィンドウで実行するコードを選択し、**Alt + Enter** キーの組み合わせを押す方法もあります。</span><span class="sxs-lookup"><span data-stu-id="1f974-189">You can also select some code that you want to run in the interactive window and hit the key combination **Alt+Enter**.</span></span> <span data-ttu-id="1f974-190">F# インタラクティブが **[F# Interactive]** というツール ウィンドウで開始されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-190">F# Interactive starts in a tool window labeled **F# Interactive**.</span></span> <span data-ttu-id="1f974-191">このショートカット キーを使用するときは、エディター ウィンドウにフォーカスがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f974-191">When you use this key combination, make sure that the editor window has the focus.</span></span>

<span data-ttu-id="1f974-192">コンソールと Visual Studio のどちらを使用している場合でも、コマンド プロンプトが表示され、入力待ちの状態になります。</span><span class="sxs-lookup"><span data-stu-id="1f974-192">Whether you are using the console or Visual Studio, a command prompt appears and the interpreter awaits your input.</span></span> <span data-ttu-id="1f974-193">コード ファイルと同じようにコードを入力できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-193">You can enter code just as you would in a code file.</span></span> <span data-ttu-id="1f974-194">コードをコンパイルして実行するには、2 つのセミコロン (**;;**) を入力して、入力行を終了します。</span><span class="sxs-lookup"><span data-stu-id="1f974-194">To compile and execute the code, enter two semicolons (**;;**) to terminate a line or several lines of input.</span></span>

<span data-ttu-id="1f974-195">F# Interactive によってコードがコンパイルされ、成功すると、コードが実行され、コンパイルされた型のシグネチャと値が出力されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-195">F# Interactive attempts to compile the code and, if successful, it executes the code and prints the signature of the types and values that it compiled.</span></span> <span data-ttu-id="1f974-196">エラーが発生した場合は、エラー メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="1f974-196">If errors occur, the interpreter prints the error messages.</span></span>

<span data-ttu-id="1f974-197">同じセッションで入力したコードからは、前に入力したどの構成要素にもアクセスできるため、プログラムの構築が可能です。</span><span class="sxs-lookup"><span data-stu-id="1f974-197">Code entered in the same session has access to any constructs entered previously, so you can build up programs.</span></span> <span data-ttu-id="1f974-198">ツール ウィンドウには十分なバッファーが用意されており、必要に応じてコードをファイルにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="1f974-198">An extensive buffer in the tool window allows you to copy the code into a file if needed.</span></span>

<span data-ttu-id="1f974-199">Visual Studio で実行する場合、F# Interactive はプロジェクトとは独立して動作します。このため、たとえば、プロジェクトで定義された構成要素を F# Interactive で使用することはできません。使用するには、関数のコードを対話形式のウィンドウにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f974-199">When run in Visual Studio, F# Interactive runs independently of your project, so, for example, you cannot use constructs defined in your project in F# Interactive unless you copy the code for the function into the interactive window.</span></span>

<span data-ttu-id="1f974-200">設定を調整することで、F# インタラクティブのコマンド ライン引数 (省略可能) を制御できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-200">You can control the F# Interactive command-line arguments (options) by adjusting the settings.</span></span> <span data-ttu-id="1f974-201">**[ツール]** メニューの **[オプション]** をクリックし、**[F# ツール]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="1f974-201">On the **Tools** menu, select **Options...**, and then expand **F# Tools**.</span></span> <span data-ttu-id="1f974-202">変更できる 2 つの設定は、F# Interactive オプションおよび 64 ビット コンピューターで F# Interactive を実行する場合にのみ関連する **64 ビット F# Interactive** 設定です。</span><span class="sxs-lookup"><span data-stu-id="1f974-202">The two settings that you can change are the F# Interactive options and the **64-bit F# Interactive** setting, which is relevant only if you are running F# Interactive on a 64-bit machine.</span></span> <span data-ttu-id="1f974-203">この設定によって、専用 64 ビット バージョンの **fsi.exe** を実行するか、コンピューター アーキテクチャを使用して 32 ビットまたは 64 ビットどちらのプロセスで実行するかを判断する **fsianycpu.exe** を実行するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="1f974-203">This setting determines whether you want to run the dedicated 64-bit version of **fsi.exe** or **fsianycpu.exe**, which uses the machine architecture to determine whether to run as a 32-bit or 64-bit process.</span></span>

## <a name="related-articles"></a><span data-ttu-id="1f974-204">関連記事</span><span class="sxs-lookup"><span data-stu-id="1f974-204">Related articles</span></span>

|<span data-ttu-id="1f974-205">Title</span><span class="sxs-lookup"><span data-stu-id="1f974-205">Title</span></span>|<span data-ttu-id="1f974-206">説明</span><span class="sxs-lookup"><span data-stu-id="1f974-206">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="1f974-207">F# Interactive オプション</span><span class="sxs-lookup"><span data-stu-id="1f974-207">F# Interactive Options</span></span>](../../language-reference/fsharp-interactive-options.md)|<span data-ttu-id="1f974-208">F# インタラクティブ (fsi.exe) のコマンド ライン構文やオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1f974-208">Describes command-line syntax and options for the F# Interactive, fsi.exe.</span></span>|