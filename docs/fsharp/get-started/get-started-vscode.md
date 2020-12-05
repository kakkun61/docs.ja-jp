---
title: Visual Studio Code での F# の概要
description: 'Visual Studio Code と Ionide plugin suite で F # を使用する方法について説明します。'
ms.date: 12/23/2018
ms.openlocfilehash: 11fb0d443fb7c2b3f270d45bfeaa91102ba28efd
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739803"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="211f6-103">Visual Studio Code での F# の概要</span><span class="sxs-lookup"><span data-stu-id="211f6-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="211f6-104">[Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)を使用して[Visual Studio Code](https://code.visualstudio.com)に F # を記述すると、IntelliSense とコードリファクタリングを使用して、優れたクロスプラットフォームで軽量の統合開発環境 (IDE) エクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="211f6-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="211f6-105">プラグインの詳細については、 [Ionide.io](https://ionide.io) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="211f6-105">Visit [Ionide.io](https://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="211f6-106">開始するには、 [F # と Ionide プラグインが正しくインストールさ](install-fsharp.md#install-f-with-visual-studio-code)れていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="211f6-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="211f6-107">Ionide を使用して最初のプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="211f6-107">Create your first project with Ionide</span></span>

<span data-ttu-id="211f6-108">新しい F # プロジェクトを作成するには、コマンドラインを開き、.NET Core CLI を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="211f6-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

<span data-ttu-id="211f6-109">完了したら、ディレクトリをプロジェクトに変更し、Visual Studio Code を開きます。</span><span class="sxs-lookup"><span data-stu-id="211f6-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="211f6-110">Visual Studio Code にプロジェクトが読み込まれると、ウィンドウの左側に [F # ソリューションエクスプローラー] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="211f6-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="211f6-111">これは、Ionide によって作成したプロジェクトが正常に読み込まれたことを意味します。</span><span class="sxs-lookup"><span data-stu-id="211f6-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="211f6-112">この時点より前に、エディターでコードを記述できますが、これが発生すると、すべての読み込みが完了します。</span><span class="sxs-lookup"><span data-stu-id="211f6-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="211f6-113">F # interactive の構成</span><span class="sxs-lookup"><span data-stu-id="211f6-113">Configure F# interactive</span></span>

<span data-ttu-id="211f6-114">最初に、.NET Core スクリプトが既定のスクリプト環境であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="211f6-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="211f6-115">Visual Studio Code 設定 ([**コード**  >  **設定]**  >  **設定**) を開きます。</span><span class="sxs-lookup"><span data-stu-id="211f6-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="211f6-116">「 **F # スクリプト**」という用語を検索します。</span><span class="sxs-lookup"><span data-stu-id="211f6-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="211f6-117">**「Fsharp.core: USE SDK scripts**」というチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="211f6-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="211f6-118">これは現在、.NET Core スクリプトでは動作しない .NET Framework ベースのスクリプトのいくつかのレガシ動作のために必要です。また、Ionide は現在、旧バージョンとの互換性を維持するために努力しています。</span><span class="sxs-lookup"><span data-stu-id="211f6-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="211f6-119">今後、.NET Core スクリプトが既定値になります。</span><span class="sxs-lookup"><span data-stu-id="211f6-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="211f6-120">最初のスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="211f6-120">Write your first script</span></span>

<span data-ttu-id="211f6-121">.NET Core スクリプトを使用するように Visual Studio Code を構成したら、Visual Studio Code の [エクスプローラー] ビューに移動し、新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="211f6-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="211f6-122">名前を *MyFirstScript script.fsx* にします。</span><span class="sxs-lookup"><span data-stu-id="211f6-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="211f6-123">ここで、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="211f6-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="211f6-124">この関数は、単語を [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="211f6-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="211f6-125">次の手順では、F# インタラクティブ (FSI.EXE) を使用して評価します。</span><span class="sxs-lookup"><span data-stu-id="211f6-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="211f6-126">関数全体を強調表示します (11 行の長さである必要があります)。</span><span class="sxs-lookup"><span data-stu-id="211f6-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="211f6-127">強調表示されたら、 **Alt** キーを押しながら **Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="211f6-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="211f6-128">画面の下部にターミナルウィンドウがポップアップ表示され、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="211f6-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Ionide を使用した F# インタラクティブ出力の例](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="211f6-130">これは次の3つの処理を行いました。</span><span class="sxs-lookup"><span data-stu-id="211f6-130">This did three things:</span></span>

1. <span data-ttu-id="211f6-131">FSI.EXE プロセスを開始しました。</span><span class="sxs-lookup"><span data-stu-id="211f6-131">It started the FSI process.</span></span>
2. <span data-ttu-id="211f6-132">FSI.EXE プロセスで強調表示したコードが送信されました。</span><span class="sxs-lookup"><span data-stu-id="211f6-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="211f6-133">FSI.EXE プロセスは、送信したコードを評価しました。</span><span class="sxs-lookup"><span data-stu-id="211f6-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="211f6-134">送信したのは [関数](../language-reference/functions/index.md)だったので、fsi.exe! を使用してその関数を呼び出すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="211f6-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="211f6-135">対話型ウィンドウで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="211f6-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="211f6-136">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="211f6-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="211f6-137">では、最初の文字として母音を試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="211f6-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="211f6-138">次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="211f6-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="211f6-139">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="211f6-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="211f6-140">関数が想定どおりに動作しているようです。</span><span class="sxs-lookup"><span data-stu-id="211f6-140">The function appears to be working as expected.</span></span> <span data-ttu-id="211f6-141">これで、最初の F # 関数を Visual Studio Code に記述し、FSI.EXE を使用して評価しました。</span><span class="sxs-lookup"><span data-stu-id="211f6-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="211f6-142">ご存知かもしれませんが、FSI.EXE の行はで終了 `;;` します。</span><span class="sxs-lookup"><span data-stu-id="211f6-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="211f6-143">これは、FSI.EXE で複数の行を入力できるためです。</span><span class="sxs-lookup"><span data-stu-id="211f6-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="211f6-144">`;;`最後のは、コードが終了したことを fsi.exe に通知します。</span><span class="sxs-lookup"><span data-stu-id="211f6-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="211f6-145">コードの説明</span><span class="sxs-lookup"><span data-stu-id="211f6-145">Explaining the code</span></span>

<span data-ttu-id="211f6-146">実際にコードが何をしているかわからない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="211f6-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="211f6-147">ご覧のように、 `toPigLatin` は単語を入力として受け取り、その単語の Pig-Latin 表現に変換する関数です。</span><span class="sxs-lookup"><span data-stu-id="211f6-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="211f6-148">この規則は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="211f6-148">The rules for this are as follows:</span></span>

<span data-ttu-id="211f6-149">単語の最初の文字が母音で始まる場合は、単語の末尾に "yay" を追加します。</span><span class="sxs-lookup"><span data-stu-id="211f6-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="211f6-150">母音で始まらない場合は、その最初の文字を単語の末尾に移動し、それに "ay" を追加します。</span><span class="sxs-lookup"><span data-stu-id="211f6-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="211f6-151">FSI.EXE では、次のことにご気になるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="211f6-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="211f6-152">これ `toPigLatin` は、を `string` 入力として受け取り (と呼びます)、別のを返す関数であることを示し `word` `string` ます。</span><span class="sxs-lookup"><span data-stu-id="211f6-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="211f6-153">これは、f # コードを理解するうえで重要な F # の基本的な部分である [関数の型シグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="211f6-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="211f6-154">Visual Studio Code で関数をポイントすると、この点にも注意してください。</span><span class="sxs-lookup"><span data-stu-id="211f6-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="211f6-155">関数の本体には、次の2つの異なる部分があります。</span><span class="sxs-lookup"><span data-stu-id="211f6-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="211f6-156">指定した `isVowel` 文字 () が、指定された `c` パターンのいずれかと一致 [するか](../language-reference/pattern-matching.md)どうかをチェックすることによって、特定の文字 () が母音であるかどうかを判断する内部関数。</span><span class="sxs-lookup"><span data-stu-id="211f6-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="211f6-157">[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)最初の文字が母音であるかどうかを確認し、最初の文字が母音であるかどうかに基づいて、入力文字から戻り値を構築する式。</span><span class="sxs-lookup"><span data-stu-id="211f6-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="211f6-158">そのため、のフロー `toPigLatin` は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="211f6-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="211f6-159">入力単語の最初の文字が母音であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="211f6-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="211f6-160">の場合は、単語の末尾に "yay" を付加します。</span><span class="sxs-lookup"><span data-stu-id="211f6-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="211f6-161">それ以外の場合は、最初の文字を単語の末尾に移動し、それに "ay" を追加します。</span><span class="sxs-lookup"><span data-stu-id="211f6-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="211f6-162">この点については最後に説明します。 F # では、関数から戻る明示的な命令がありません。</span><span class="sxs-lookup"><span data-stu-id="211f6-162">There's one final thing to notice about this: in F#, there's no explicit instruction to return from the function.</span></span> <span data-ttu-id="211f6-163">これは、F # が式ベースであり、関数の本体で評価された最後の式によってその関数の戻り値が決定されるためです。</span><span class="sxs-lookup"><span data-stu-id="211f6-163">This is because F# is expression-based, and the last expression evaluated in the body of a function determines the return value of that function.</span></span> <span data-ttu-id="211f6-164">`if..then..else`はそれ自体が式であるため、ブロックの本体 `then` またはブロックの本体の評価に `else` よって、関数によって返される値が決まり `toPigLatin` ます。</span><span class="sxs-lookup"><span data-stu-id="211f6-164">Because `if..then..else` is itself an expression, evaluation of the body of the `then` block or the body of the `else` block determines the value returned by the `toPigLatin` function.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="211f6-165">コンソールアプリを Pig Latin ジェネレーターにする</span><span class="sxs-lookup"><span data-stu-id="211f6-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="211f6-166">この記事の前のセクションでは、F # コードを記述するための一般的な最初の手順を示しています。初期関数を記述し、FSI.EXE を使用して対話形式で実行します。</span><span class="sxs-lookup"><span data-stu-id="211f6-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="211f6-167">これは REPL ドリブン開発と呼ばれます。 [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) は "Read Evaluate-Print Loop" を表します。</span><span class="sxs-lookup"><span data-stu-id="211f6-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="211f6-168">機能を使用するには、機能を試してみることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="211f6-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="211f6-169">REPL 駆動型開発の次の手順では、作業コードを F # 実装ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="211f6-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="211f6-170">その後、これを F # コンパイラでコンパイルして、実行可能なアセンブリにすることができます。</span><span class="sxs-lookup"><span data-stu-id="211f6-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="211f6-171">まず、.NET Core CLI で作成した *プログラム* のファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="211f6-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="211f6-172">いくつかのコードが既に存在していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="211f6-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="211f6-173">次に、という新しいを作成 [`module`](../language-reference/modules.md) `PigLatin` し、 `toPigLatin` 先ほど作成した関数を次のようにコピーします。</span><span class="sxs-lookup"><span data-stu-id="211f6-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

<span data-ttu-id="211f6-174">このモジュールは、関数の上と宣言の下に配置する必要があり `main` `open System` ます。</span><span class="sxs-lookup"><span data-stu-id="211f6-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="211f6-175">F # では宣言の順序が重要であるため、関数をファイルで呼び出す前に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="211f6-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="211f6-176">次に、関数で、 `main` 引数に対して Pig Latin generator 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="211f6-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn %"{name} in Pig Latin is: {newName}"

    0
```

<span data-ttu-id="211f6-177">これで、コマンドラインからコンソールアプリを実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="211f6-177">Now you can run your console app from the command line:</span></span>

```dotnetcli
dotnet run apple banana
```

<span data-ttu-id="211f6-178">スクリプトファイルと同じ結果が出力されますが、今回は実行中のプログラムとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="211f6-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="211f6-179">Ionide のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="211f6-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="211f6-180">発生する可能性がある特定の問題をトラブルシューティングするには、次のいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="211f6-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="211f6-181">Ionide のコード編集機能を利用するには、F # ファイルをディスクに保存し、[Visual Studio Code] ワークスペースで開いているフォルダー内に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="211f6-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="211f6-182">システムに変更を加えた場合、または Visual Studio Code を開いた状態でインストールされた Ionide の前提条件を確認した場合は、Visual Studio Code を再起動します。</span><span class="sxs-lookup"><span data-stu-id="211f6-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="211f6-183">プロジェクトディレクトリに無効な文字が含まれていると、Ionide が機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="211f6-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="211f6-184">この場合は、プロジェクトディレクトリの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="211f6-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="211f6-185">Ionide コマンドがいずれも動作していない場合は、 [Visual Studio Code キーバインド](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) を調べて、誤って上書きしているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="211f6-185">If none of the Ionide commands are working, check your [Visual Studio Code Key Bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="211f6-186">Ionide がコンピューター上で破損していて、上記のいずれも問題を解決していない場合は、 `ionide-fsharp` コンピューター上のディレクトリを削除し、プラグインスイートを再インストールしてみてください。</span><span class="sxs-lookup"><span data-stu-id="211f6-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="211f6-187">プロジェクトの読み込みに失敗した場合 (F # ソリューションエクスプローラーによって表示されます)、そのプロジェクトを右クリックし、[ **詳細の表示** ] をクリックして診断情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="211f6-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="211f6-188">Ionide は、F # コミュニティのメンバーによって構築および管理されるオープンソースプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="211f6-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="211f6-189">問題を報告して、 [ionide-vscode-Fsharp.core GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)に投稿してください。</span><span class="sxs-lookup"><span data-stu-id="211f6-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="211f6-190">[Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)の Ionide 開発者や F # コミュニティから、さらに支援を求めることもできます。</span><span class="sxs-lookup"><span data-stu-id="211f6-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="211f6-191">次のステップ</span><span class="sxs-lookup"><span data-stu-id="211f6-191">Next steps</span></span>

<span data-ttu-id="211f6-192">F # とその言語の機能の詳細については、「 [f # のツアー](../tour.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="211f6-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
