---
title: Visual Studio Code を使用して .NET コンソール アプリケーションをデバッグする
description: Visual Studio Code を使用して .NET コンソール アプリをデバッグする方法について説明します。
ms.date: 05/26/2020
ms.openlocfilehash: 85095a9e70ee3ff846716ef91239b240d8c42410
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916230"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio-code"></a><span data-ttu-id="2758d-103">チュートリアル: Visual Studio Code を使用して .NET コンソール アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="2758d-103">Tutorial: Debug a .NET console application using Visual Studio Code</span></span>

<span data-ttu-id="2758d-104">このチュートリアルでは、.NET アプリを操作するために Visual Studio Code で使用できるデバッグ ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2758d-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2758d-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2758d-105">Prerequisites</span></span>

- <span data-ttu-id="2758d-106">このチュートリアルでは、「[Visual Studio Code を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-code.md)」で作成するコンソール アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="2758d-106">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="2758d-107">デバッグ ビルド構成の使用</span><span class="sxs-lookup"><span data-stu-id="2758d-107">Use Debug build configuration</span></span>

<span data-ttu-id="2758d-108">"*デバッグ*" と "*リリース*" は、.NET Core の組み込みビルド構成です。</span><span class="sxs-lookup"><span data-stu-id="2758d-108">*Debug* and *Release* are .NET Core's built-in build configurations.</span></span> <span data-ttu-id="2758d-109">デバッグ用のデバッグ ビルド構成と、最終リリース配布用のリリース構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="2758d-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="2758d-110">デバッグ構成では、プログラムのコンパイルにシンボリック デバッグ情報が完全に含まれ、最適化は行われません。</span><span class="sxs-lookup"><span data-stu-id="2758d-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="2758d-111">ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。</span><span class="sxs-lookup"><span data-stu-id="2758d-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="2758d-112">プログラムのリリース構成は、シンボリック デバッグ情報を含まず、完全に最適化されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="2758d-113">既定では、Visual Studio Code の起動設定ではデバッグ ビルド構成が使用されるため、デバッグの前に変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2758d-113">By default, Visual Studio Code launch settings use the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="2758d-114">Visual Studio Code を開始します。</span><span class="sxs-lookup"><span data-stu-id="2758d-114">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="2758d-115">「[Visual Studio Code を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-code.md)」で作成したプロジェクトのフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="2758d-115">Open the folder of the project that you created in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="2758d-116">ブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="2758d-116">Set a breakpoint</span></span>

<span data-ttu-id="2758d-117">"*ブレークポイント*" によって、ブレークポイントを含む行が実行される前に、アプリケーションの実行が一時的に中断されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-117">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="2758d-118">*Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2758d-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="2758d-119">コード ウィンドウの左側の余白をクリックして、名前、日付、時刻を表示する行に "*ブレークポイント*" を設定します。</span><span class="sxs-lookup"><span data-stu-id="2758d-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="2758d-120">左余白は、行番号の左側にあります。</span><span class="sxs-lookup"><span data-stu-id="2758d-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="2758d-121">ブレークポイントを設定するその他の方法としては、コード行を選択した状態で <kbd>F9</kbd> キーを押すか、メニューから **[実行]**  >  **[ブレークポイントの設定/解除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2758d-121">Other ways to set a breakpoint are by pressing <kbd>F9</kbd> or choosing **Run** > **Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

   <span data-ttu-id="2758d-122">Visual Studio Code では、左余白に赤い点を表示することで、ブレークポイントが設定されている行が示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-122">Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="ブレークポイントの設定":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="2758d-124">ターミナル入力用の設定</span><span class="sxs-lookup"><span data-stu-id="2758d-124">Set up for terminal input</span></span>

<span data-ttu-id="2758d-125">ブレークポイントは、`Console.ReadLine` メソッドの呼び出しの後に配置されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="2758d-126">**デバッグ コンソール** は、実行中のプログラムのターミナル入力を受け入れません。</span><span class="sxs-lookup"><span data-stu-id="2758d-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="2758d-127">デバッグ中にターミナル入力を処理するには、統合ターミナル (Visual Studio Code ウィンドウの 1 つ) または外部ターミナルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2758d-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="2758d-128">このチュートリアルでは、統合ターミナルを使用します。</span><span class="sxs-lookup"><span data-stu-id="2758d-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="2758d-129">*.vscode/launch.json* を開きます。</span><span class="sxs-lookup"><span data-stu-id="2758d-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="2758d-130">`console` 設定を `integratedTerminal` に変更します。</span><span class="sxs-lookup"><span data-stu-id="2758d-130">Change the `console` setting to `integratedTerminal`.</span></span>

   <span data-ttu-id="2758d-131">差出人:</span><span class="sxs-lookup"><span data-stu-id="2758d-131">From:</span></span>

   ```json
   "console": "internalConsole",
   ```

   <span data-ttu-id="2758d-132">移動先:</span><span class="sxs-lookup"><span data-stu-id="2758d-132">To:</span></span>

   ```json
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="2758d-133">変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="2758d-133">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="2758d-134">[デバッグ開始]</span><span class="sxs-lookup"><span data-stu-id="2758d-134">Start debugging</span></span>

1. <span data-ttu-id="2758d-135">左側のメニューにある [デバッグ] アイコンを選択して、デバッグ ビューを開きます。</span><span class="sxs-lookup"><span data-stu-id="2758d-135">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Visual Studio Code で [デバッグ] タブを開く":::

1. <span data-ttu-id="2758d-137">ペインの上部にある **[.NET Core Launch (console)]\(.NET Core の起動 (コンソール)\)** の横の緑色の矢印を選択します。</span><span class="sxs-lookup"><span data-stu-id="2758d-137">Select the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span> <span data-ttu-id="2758d-138">デバッグ モードでプログラムを起動するその他の方法は、<kbd>F5</kbd> キーを押すか、メニューから **[実行]**  >  **[デバッグの開始]** を選択することです。</span><span class="sxs-lookup"><span data-stu-id="2758d-138">Other ways to start the program in debugging mode are by pressing <kbd>F5</kbd> or choosing **Run** > **Start Debugging** from the menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="デバッグの開始":::

1. <span data-ttu-id="2758d-140">**[ターミナル]** タブを選択すると、"What is your name?" (あなたのお名前は?) の</span><span class="sxs-lookup"><span data-stu-id="2758d-140">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="2758d-141">プロンプトが表示されます。これは応答を待機する前にプログラムによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-141">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="[ターミナル] タブを選択":::

1. <span data-ttu-id="2758d-143">名前のプロンプトに応答する文字列を **[ターミナル]** ウィンドウに入力し、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-143">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="2758d-144">プログラムがブレークポイントに到達すると、プログラム実行は停止します。`Console.WriteLine` メソッドが実行される前にも停止します。</span><span class="sxs-lookup"><span data-stu-id="2758d-144">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="2758d-145">**[変数]** ウィンドウの **[ローカル]** セクションには、現在実行しているメソッドで定義されている変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-145">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="ブレークポイントのヒット、ローカルの表示":::

## <a name="use-the-debug-console"></a><span data-ttu-id="2758d-147">デバッグ コンソールを使用する</span><span class="sxs-lookup"><span data-stu-id="2758d-147">Use the Debug Console</span></span>

<span data-ttu-id="2758d-148">**[デバッグ コンソール]** ウィンドウでは、デバッグ中のアプリケーションと対話できます。</span><span class="sxs-lookup"><span data-stu-id="2758d-148">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="2758d-149">変数の値を変更して、プログラムにどのような影響があるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2758d-149">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="2758d-150">**[デバッグ コンソール]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2758d-150">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="2758d-151">**[デバッグ コンソール]** ウィンドウの下部にあるプロンプトで `name = "Gracie"` を入力し、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-151">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="変数の値の変更":::

1. <span data-ttu-id="2758d-153">**[デバッグ コンソール]** ウィンドウの下部に `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` を入力し、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-153">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="2758d-154">**[変数]** ウィンドウには、`name` 変数と `date` 変数の新しい値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-154">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="2758d-155">ツール バーの **[続行]** ボタンを選択して、プログラムの実行を続けます。</span><span class="sxs-lookup"><span data-stu-id="2758d-155">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="2758d-156">続行するもう 1 つの方法は、<kbd>F5</kbd> キーを押すことです。</span><span class="sxs-lookup"><span data-stu-id="2758d-156">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="デバッグの続行":::

1. <span data-ttu-id="2758d-158">もう一度 **[ターミナル]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2758d-158">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="2758d-159">コンソール ウィンドウに表示される値は、 **[デバッグ コンソール]** で行った変更に対応しています。</span><span class="sxs-lookup"><span data-stu-id="2758d-159">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="入力した値を示すターミナル":::

1. <span data-ttu-id="2758d-161">任意のキーを押してアプリケーションを終了し、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="2758d-161">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="2758d-162">条件付きブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="2758d-162">Set a conditional breakpoint</span></span>

<span data-ttu-id="2758d-163">プログラムによって、ユーザーが入力した文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-163">The program displays the string that the user enters.</span></span> <span data-ttu-id="2758d-164">ユーザーが何も入力しないとどうなるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2758d-164">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="2758d-165">これは、"*条件付きブレークポイント*" と呼ばれる便利なデバッグ機能を使用してテストできます。</span><span class="sxs-lookup"><span data-stu-id="2758d-165">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="2758d-166">ブレークポイントを表す赤い点を右クリック (macOS では <kbd>Ctrl</kbd> キーを押しながらクリック) します。</span><span class="sxs-lookup"><span data-stu-id="2758d-166">Right-click (<kbd>Ctrl</kbd>-click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="2758d-167">コンテキスト メニューで **[ブレークポイントの編集]** を選択して、条件式を入力するためのダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="2758d-167">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="ブレークポイント コンテキスト メニュー":::

1. <span data-ttu-id="2758d-169">ドロップダウン リストで [`Expression`] を選択し、次の条件式を入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-169">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="条件式の入力":::

   <span data-ttu-id="2758d-171">ブレークポイントにヒットするたびに、デバッガーは `String.IsNullOrEmpty(name)` メソッドを呼び出し、メソッド呼び出しが `true` を返す場合にのみ、この行で中断します。</span><span class="sxs-lookup"><span data-stu-id="2758d-171">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="2758d-172">条件式の代わりに、"*ヒット カウント*" を指定できます。この場合、ステートメントが指定された回数実行される前にプログラムの実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-172">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="2758d-173">もう 1 つのオプションは、"*フィルター条件*" を指定することです。これにより、スレッド識別子、プロセス名、またはスレッド名などの属性に基づいてプログラムの実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-173">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="2758d-174"><kbd>F5</kbd> を押して、デバッグとともにプログラムを開始します。</span><span class="sxs-lookup"><span data-stu-id="2758d-174">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="2758d-175">**[ターミナル]** タブで、自分の名前を入力するように求められたら、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-175">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="2758d-176">指定した条件 (`name` は `null` または <xref:System.String.Empty?displayProperty=nameWithType> のどちらか) が満たされたため、ブレークポイントに到達すると、`Console.WriteLine` メソッドが実行される前に、プログラムの実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="2758d-176">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="2758d-177">**[変数]** ウィンドウには、`name` 変数の値が `""` または <xref:System.String.Empty?displayProperty=nameWithType> であることが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-177">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="2758d-178">**デバッグ コンソール** プロンプトで次のステートメントを入力し、<kbd>Enter</kbd> キーを押して、値が空の文字列であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2758d-178">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="2758d-179">結果は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="2758d-179">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="ステートメントの実行後に true の値を返すデバッグ コンソール":::

1. <span data-ttu-id="2758d-181">ツール バーの **[続行]** を選んで、プログラムの実行を続けます。</span><span class="sxs-lookup"><span data-stu-id="2758d-181">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="2758d-182">**[ターミナル]** タブを選択し、任意のキーを押してプログラムを終了し、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="2758d-182">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="2758d-183">コード ウィンドウの左余白のドットをクリックして、ブレークポイントをクリアします。</span><span class="sxs-lookup"><span data-stu-id="2758d-183">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="2758d-184">ブレークポイントをクリアするその他の方法としては、コード行を選択した状態で <kbd>F9</kbd> キーを押すか、メニューから **[実行] > [ブレークポイントの設定/解除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2758d-184">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Run > Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

1. <span data-ttu-id="2758d-185">ブレークポイントの条件が失われることを示す警告が表示された場合は、 **[ブレークポイントの削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2758d-185">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="2758d-186">プログラムのステップ実行</span><span class="sxs-lookup"><span data-stu-id="2758d-186">Step through a program</span></span>

<span data-ttu-id="2758d-187">Visual Studio Code では、1 行ずつプログラムをステップ実行して、実行を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="2758d-187">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="2758d-188">通常は、ブレークポイントを設定して、プログラム コードのごく一部を通じてプログラム フローに従います。</span><span class="sxs-lookup"><span data-stu-id="2758d-188">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="2758d-189">このプログラムは小さいため、次の手順に従ってプログラム全体をステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="2758d-189">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="2758d-190">`Main` メソッドの左中かっこにブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="2758d-190">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="2758d-191"><kbd>F5</kbd> キーを押してデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="2758d-191">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="2758d-192">Visual Studio Code では、ブレークポイント行が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-192">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="2758d-193">この時点で、 **[変数]** ウィンドウに `args` 配列が空であることが示され、`name` と `date` には既定値が設定されています。</span><span class="sxs-lookup"><span data-stu-id="2758d-193">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="2758d-194">**[実行]**  >  **[ステップ イン]** を選択するか、<kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-194">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="[ステップイン] ボタン":::

   <span data-ttu-id="2758d-196">Visual Studio Code では次の行が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-196">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="2758d-197">**[実行]**  >  **[ステップ イン]** を選択するか、<kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-197">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="2758d-198">Visual Studio Code では、名前プロンプトの `Console.WriteLine` が実行され、次に実行される行が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-198">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="2758d-199">次の行は、`name` の `Console.ReadLine` です。</span><span class="sxs-lookup"><span data-stu-id="2758d-199">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="2758d-200">**[変数]** ウィンドウは変更されず、 **[ターミナル]** タブに "What is your name?"</span><span class="sxs-lookup"><span data-stu-id="2758d-200">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="2758d-201">プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-201">prompt.</span></span>

1. <span data-ttu-id="2758d-202">**[実行]**  >  **[ステップ イン]** を選択するか、<kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-202">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="2758d-203">Visual Studio によって、`name` 変数代入が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-203">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="2758d-204">**[変数]** ウィンドウに、`name` がまだ `null` であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-204">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="2758d-205">[ターミナル] タブに文字列を入力し、<kbd>Enter</kbd> キーを押して、このプロンプトに応答します。</span><span class="sxs-lookup"><span data-stu-id="2758d-205">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="2758d-206">**[ターミナル]** タブには、入力時に入力した文字列が表示されない場合がありますが、<xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドによって入力がキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="2758d-206">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="2758d-207">**[実行]**  >  **[ステップ イン]** を選択するか、<kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-207">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="2758d-208">Visual Studio Code によって、`date` 変数代入が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-208">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="2758d-209">**[変数]** ウィンドウには、<xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドの呼び出しによって返された値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-209">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2758d-210">**[ターミナル]** タブには、プロンプトで入力した文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-210">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="2758d-211">**[実行]**  >  **[ステップ イン]** を選択するか、<kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-211">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="2758d-212">**[変数]** ウィンドウには、<xref:System.DateTime.Now?displayProperty=nameWithType> プロパティから代入された後の `date` 変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-212">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="2758d-213">**[実行]**  >  **[ステップ イン]** を選択するか、<kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-213">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="2758d-214">Visual Studio Code によって <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-214">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2758d-215">コンソール ウィンドウには書式設定された文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-215">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="2758d-216">**[実行]**  >  **[ステップ アウト]** の順に選択するか、<kbd>Shift</kbd> + <kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2758d-216">Select **Run** > **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="[ステップアウト] ボタン":::

1. <span data-ttu-id="2758d-218">**[ターミナル]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2758d-218">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="2758d-219">ターミナルに、"Press any key to exit..." (終了するには何かキーを押してください...) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2758d-219">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="2758d-220">任意のキーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="2758d-220">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="2758d-221">リリース ビルド構成を使用する</span><span class="sxs-lookup"><span data-stu-id="2758d-221">Use Release build configuration</span></span>

<span data-ttu-id="2758d-222">アプリケーションのデバッグ バージョンのテストが終了したら、リリース バージョンもコンパイルしてテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2758d-222">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="2758d-223">リリース バージョンには、アプリケーションの動作に影響を与える可能性があるコンパイラの最適化が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="2758d-223">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="2758d-224">たとえば、パフォーマンスを向上させるように設計されたコンパイラの最適化では、マルチスレッド アプリケーションで競合状態が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2758d-224">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="2758d-225">コンソール アプリケーションのリリース バージョンをビルドしてテストするには、**ターミナル** を開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2758d-225">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="2758d-226">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="2758d-226">Additional resources</span></span>

* [<span data-ttu-id="2758d-227">Visual Studio Code でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="2758d-227">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="2758d-228">次の手順</span><span class="sxs-lookup"><span data-stu-id="2758d-228">Next steps</span></span>

<span data-ttu-id="2758d-229">このチュートリアルでは、Visual Studio Code のデバッグ ツールを使用しました。</span><span class="sxs-lookup"><span data-stu-id="2758d-229">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="2758d-230">次のチュートリアルでは、アプリの展開可能なバージョンを発行します。</span><span class="sxs-lookup"><span data-stu-id="2758d-230">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2758d-231">Visual Studio Code を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="2758d-231">Publish a .NET console application using Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
