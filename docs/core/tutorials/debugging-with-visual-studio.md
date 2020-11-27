---
title: Visual Studio を使用して .NET コンソール アプリケーションをデバッグする
description: Visual Studio を使用して .NET コンソール アプリをデバッグする方法について説明します。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 8a914dc6cf069c011ea5b077ada514bf8cec331d
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916198"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio"></a><span data-ttu-id="84058-103">チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="84058-103">Tutorial: Debug a .NET console application using Visual Studio</span></span>

<span data-ttu-id="84058-104">このチュートリアルでは、Visual Studio で使用できるデバッグ ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="84058-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84058-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="84058-105">Prerequisites</span></span>

- <span data-ttu-id="84058-106">このチュートリアルでは、「[Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」で作成するコンソール アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="84058-106">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="84058-107">デバッグ ビルド構成の使用</span><span class="sxs-lookup"><span data-stu-id="84058-107">Use Debug build configuration</span></span>

<span data-ttu-id="84058-108">"*デバッグ*" と "*リリース*" は、Visual Studio の組み込みビルド構成です。</span><span class="sxs-lookup"><span data-stu-id="84058-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="84058-109">デバッグ用のデバッグ ビルド構成と、最終リリース配布用のリリース構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="84058-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="84058-110">デバッグ構成では、プログラムのコンパイルにシンボリック デバッグ情報が完全に含まれ、最適化は行われません。</span><span class="sxs-lookup"><span data-stu-id="84058-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="84058-111">ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。</span><span class="sxs-lookup"><span data-stu-id="84058-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="84058-112">プログラムのリリース構成は、シンボリック デバッグ情報を含まず、完全に最適化されます。</span><span class="sxs-lookup"><span data-stu-id="84058-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="84058-113">既定では、Visual Studio ではデバッグ ビルド構成が使用されるため、デバッグの前に変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="84058-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="84058-114">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="84058-114">Start Visual Studio.</span></span>

1. <span data-ttu-id="84058-115">「[Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」で作成したプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="84058-115">Open the project that you created in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

   <span data-ttu-id="84058-116">現時点のビルド構成はツールバーに表示されています。</span><span class="sxs-lookup"><span data-stu-id="84058-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="84058-117">次のツール バーの画像では、アプリのデバッグ バージョンをコンパイルするように Visual Studio が構成されています。</span><span class="sxs-lookup"><span data-stu-id="84058-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png" alt-text="デバッグが強調表示された Visual Studio のツールバー":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="84058-119">ブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="84058-119">Set a breakpoint</span></span>

<span data-ttu-id="84058-120">"*ブレークポイント*" によって、ブレークポイントを含む行が実行される前に、アプリケーションの実行が一時的に中断されます。</span><span class="sxs-lookup"><span data-stu-id="84058-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="84058-121">名前、日付、時刻を表示する行のコード ウィンドウの左側の余白をクリックして、その行に "*ブレークポイント*" 設定します。</span><span class="sxs-lookup"><span data-stu-id="84058-121">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="84058-122">左余白は、行番号の左側にあります。</span><span class="sxs-lookup"><span data-stu-id="84058-122">The left margin is to the left of the line numbers.</span></span>  <span data-ttu-id="84058-123">ブレークポイントを設定する他の 1 つの方法は、コード行にカーソルを置き、<kbd>F9</kbd> キーを押すか、メニュー バーから **[デバッグ]** 、 **[ブレークポイントの設定/解除]** の順に選択することです。</span><span class="sxs-lookup"><span data-stu-id="84058-123">Other ways to set a breakpoint are by placing the cursor in the line of code and then pressing <kbd>F9</kbd> or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="84058-124">次の図のとおり、Visual Studio では、ブレークポイントが設定された行を強調表示し、左端の余白に赤い点を表示することで、その行を示しています。</span><span class="sxs-lookup"><span data-stu-id="84058-124">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/set-breakpoint-in-editor.png" alt-text="ブレークポイントが設定された Visual Studio のプログラム ウィンドウ":::

1. <span data-ttu-id="84058-126"><kbd>F5</kbd> キーを押して、プログラムをデバッグ モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="84058-126">Press <kbd>F5</kbd> to run the program in Debug mode.</span></span> <span data-ttu-id="84058-127">デバッグを開始するもう 1 つの方法は、メニューから **[デバッグ]**  >  **[デバッグの開始]** を選択することです。</span><span class="sxs-lookup"><span data-stu-id="84058-127">Another way to start debugging is by choosing **Debug** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="84058-128">プログラムが名前の入力を求めたら、コンソール ウィンドウに文字列を入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-128">Enter a string in the console window when the program prompts for a name, and then press <kbd>Enter</kbd>.</span></span>

1. <span data-ttu-id="84058-129">プログラムがブレークポイントに到達すると、プログラム実行は停止します。`Console.WriteLine` メソッドが実行される前にも停止します。</span><span class="sxs-lookup"><span data-stu-id="84058-129">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="84058-130">**[ローカル]** ウィンドウには、現在実行しているメソッドで定義されている変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-130">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/breakpoint-hit.png" alt-text="Visual Studio でのブレークポイントのスクリーンショット":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="84058-132">[イミディエイト] ウィンドウを使用する</span><span class="sxs-lookup"><span data-stu-id="84058-132">Use the Immediate window</span></span>

<span data-ttu-id="84058-133">**[イミディエイト]** ウィンドウでは、デバッグ中のアプリケーションと対話できます。</span><span class="sxs-lookup"><span data-stu-id="84058-133">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="84058-134">変数の値を対話的に変更して、プログラムにどのような影響があるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="84058-134">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="84058-135">**[イミディエイト]** ウィンドウが表示されない場合は、 **[デバッグ]**  >  **[Windows]**  >  **[イミディエイト]** の順に選択して表示します。</span><span class="sxs-lookup"><span data-stu-id="84058-135">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

1. <span data-ttu-id="84058-136">**[イミディエイト]** ウィンドウに「`name = "Gracie"`」と入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-136">Enter `name = "Gracie"` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

1. <span data-ttu-id="84058-137">**[イミディエイト]** ウィンドウに「`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`」と入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-137">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="84058-138">**[イミディエイト]** ウィンドウに、文字列変数の値と、<xref:System.DateTime> 値のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-138">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="84058-139">さらに、変数の値は **[ローカル]** ウィンドウで更新されます。</span><span class="sxs-lookup"><span data-stu-id="84058-139">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/locals-immediate-window.png" alt-text="Visual Studio 2019 の [ローカル] と [イミディエイト] ウィンドウ":::

1. <span data-ttu-id="84058-141"><kbd>F5</kbd> キーを押して、プログラムの実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="84058-141">Press <kbd>F5</kbd> to continue program execution.</span></span> <span data-ttu-id="84058-142">続行するもう 1 つの方法は、メニューから **[デバッグ]**  >  **[続行]** を選択することです。</span><span class="sxs-lookup"><span data-stu-id="84058-142">Another way to continue is by choosing **Debug** > **Continue** from the menu.</span></span>

   <span data-ttu-id="84058-143">コンソール ウィンドウに表示される値は、 **[イミディエイト]** ウィンドウで行った変更に対応しています。</span><span class="sxs-lookup"><span data-stu-id="84058-143">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/console-window.png" alt-text="入力した値が表示されているコンソール ウィンドウ":::

1. <span data-ttu-id="84058-145">任意のキーを押してアプリケーションを終了し、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="84058-145">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="84058-146">条件付きブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="84058-146">Set a conditional breakpoint</span></span>

<span data-ttu-id="84058-147">プログラムによって、ユーザーが入力した文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-147">The program displays the string that the user enters.</span></span> <span data-ttu-id="84058-148">ユーザーが何も入力しないとどうなるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="84058-148">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="84058-149">これは、"*条件付きブレークポイント*" と呼ばれる便利なデバッグ機能を使用してテストできます。</span><span class="sxs-lookup"><span data-stu-id="84058-149">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="84058-150">ブレークポイントを表す赤丸を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="84058-150">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="84058-151">コンテキスト メニューで **[条件]** を選んで、 **[ブレークポイント設定]** ダイアログを開きます。</span><span class="sxs-lookup"><span data-stu-id="84058-151">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="84058-152">**[条件]** のチェック ボックスをオンにします (まだオンになっていない場合)。</span><span class="sxs-lookup"><span data-stu-id="84058-152">Select the box for **Conditions** if it's not already selected.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/breakpoint-settings.png" alt-text="[ブレークポイント設定] パネルが表示されているエディター - C#":::

1. <span data-ttu-id="84058-154">**[条件式]** には、`x` が 5 かどうかをテストするコード例を示す次のコードをフィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="84058-154">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="84058-155">使用する言語が表示されていない場合は、ページの上部にある言語セレクターを変更します。</span><span class="sxs-lookup"><span data-stu-id="84058-155">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="84058-156">ブレークポイントにヒットするたびに、デバッガーは `String.IsNullOrEmpty(name)` メソッドを呼び出し、メソッド呼び出しが `true` を返す場合にのみ、この行で中断します。</span><span class="sxs-lookup"><span data-stu-id="84058-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="84058-157">条件式の代わりに、"*ヒット カウント*" を指定できます。この場合、ステートメントが指定された回数実行される前にプログラムの実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="84058-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="84058-158">もう 1 つのオプションは、"*フィルター条件*" を指定することです。これにより、スレッド識別子、プロセス名、またはスレッド名などの属性に基づいてプログラムの実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="84058-158">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="84058-159">**[閉じる]** を選択して、ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="84058-159">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="84058-160"><kbd>F5</kbd> を押して、デバッグとともにプログラムを開始します。</span><span class="sxs-lookup"><span data-stu-id="84058-160">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="84058-161">コンソール ウィンドウで、名前の入力を求められたら、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-161">In the console window, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

1. <span data-ttu-id="84058-162">指定した条件 (`name` は `null` または <xref:System.String.Empty?displayProperty=nameWithType> のどちらか) が満たされたため、ブレークポイントに到達すると、`Console.WriteLine` メソッドが実行される前に、プログラムの実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="84058-162">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="84058-163">**[ローカル]** ウィンドウを選ぶと、現在実行しているメソッドに対してローカルな変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-163">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="84058-164">この場合、`Main` は現在実行中のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="84058-164">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="84058-165">`name` 変数の値が `""` または <xref:System.String.Empty?displayProperty=nameWithType> であることを調べます。</span><span class="sxs-lookup"><span data-stu-id="84058-165">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="84058-166">**[イミディエイト]** ウィンドウに次のステートメントを入力し、<kbd>Enter</kbd> キーを押して、値が空の文字列であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84058-166">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="84058-167">結果は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="84058-167">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="84058-168">疑問符は、イミディエイト ウィンドウに、[式を評価](/visualstudio/ide/reference/immediate-window#enter-commands)するように指示します。</span><span class="sxs-lookup"><span data-stu-id="84058-168">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/immediate-window-output.png" alt-text="ステートメントが実行された後で値 true を返す [イミディエイト ウィンドウ] - C#":::

1. <span data-ttu-id="84058-170"><kbd>F5</kbd> キーを押して、プログラムの実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="84058-170">Press <kbd>F5</kbd> to continue program execution.</span></span>

1. <span data-ttu-id="84058-171">任意のキーを押してコンソール ウィンドウを閉じ、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="84058-171">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="84058-172">コード ウィンドウの左端の余白のドットをクリックして、ブレークポイントをクリアします。</span><span class="sxs-lookup"><span data-stu-id="84058-172">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="84058-173">ブレークポイントをクリアするその他の方法としては、コード行を選択した状態で <kbd>F9</kbd> キーを押すか、 **[デバッグ]、[ブレークポイントの設定/解除]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="84058-173">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="84058-174">プログラムのステップ実行</span><span class="sxs-lookup"><span data-stu-id="84058-174">Step through a program</span></span>

<span data-ttu-id="84058-175">Visual Studio では、1 行ずつプログラムをステップ実行して、実行を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="84058-175">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="84058-176">通常は、ブレークポイントを設定して、プログラム コードのごく一部を通じてプログラム フローに従います。</span><span class="sxs-lookup"><span data-stu-id="84058-176">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="84058-177">このプログラムは小さいため、次の手順に従ってプログラム全体をステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="84058-177">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="84058-178">**[デバッグ]**  >  **[ステップ イン]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="84058-178">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="84058-179">1 つのステートメントを一度にデバッグするもう 1 つの方法は、<kbd>F11</kbd> キーを押すことです。</span><span class="sxs-lookup"><span data-stu-id="84058-179">Another way to debug one statement at a time is by pressing <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="84058-180">次に実行される行が強調表示されて、横に矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-180">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="84058-181">C#</span><span class="sxs-lookup"><span data-stu-id="84058-181">C#</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/step-into-method.png" alt-text="Visual Studio のステップ イン メソッド - C#":::

   <span data-ttu-id="84058-183">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84058-183">Visual Basic</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/vb-step-into-method.png" alt-text="Visual Studio のステップ イン メソッド - Visual Basic":::

   <span data-ttu-id="84058-185">この時点で、 **[ローカル]** ウィンドウに `args` 配列が空であることが示され、`name` と `date` には既定値が設定されています。</span><span class="sxs-lookup"><span data-stu-id="84058-185">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="84058-186">さらに、空のコンソール ウィンドウが開かれています。</span><span class="sxs-lookup"><span data-stu-id="84058-186">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="84058-187"><kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-187">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="84058-188">次に実行される行が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-188">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="84058-189">**[ローカル]** ウィンドウは変更されず、コンソール ウィンドウは空白のままになります。</span><span class="sxs-lookup"><span data-stu-id="84058-189">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="84058-190">C#</span><span class="sxs-lookup"><span data-stu-id="84058-190">C#</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/step-into-source-method.png" alt-text="Visual Studio のステップ イン メソッド ソース - C#":::

   <span data-ttu-id="84058-192">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84058-192">Visual Basic</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/vb-step-into-source-method.png" alt-text="Visual Studio のステップ イン メソッド ソース - Visual Basic":::

1. <span data-ttu-id="84058-194"><kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-194">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="84058-195">`name` の変数代入を含むステートメントが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-195">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="84058-196">**[ローカル]** ウィンドウに `name` が `null` であると表示され、コンソール ウィンドウに "What is your name?" という文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-196">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="84058-197">コンソール ウィンドウに文字列を入力し、<kbd>Enter</kbd> キーを押して、このプロンプトに応答します。</span><span class="sxs-lookup"><span data-stu-id="84058-197">Respond to the prompt by entering a string in the console window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="84058-198">コンソールは応答せず、入力した文字列はコンソール ウィンドウに表示されませんが、それでも <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドにより入力が取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="84058-198">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="84058-199"><kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-199">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="84058-200">Visual Studio によって、`date` 変数代入 (Visual Basic では `currentDate`) を含むステートメントが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-200">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="84058-201">**[ローカル]** ウィンドウには、<xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドの呼び出しによって返された値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-201">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84058-202">コンソール ウィンドウには、プロンプトで入力した文字列も表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-202">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="84058-203"><kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-203">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="84058-204">**[ローカル]** ウィンドウには、<xref:System.DateTime.Now?displayProperty=nameWithType> プロパティから代入された後の `date` 変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-204">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="84058-205">コンソール ウィンドウに変更はありません。</span><span class="sxs-lookup"><span data-stu-id="84058-205">The console window is unchanged.</span></span>

1. <span data-ttu-id="84058-206"><kbd>F11</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="84058-206">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="84058-207">Visual Studio は、<xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="84058-207">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84058-208">コンソール ウィンドウには書式設定された文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84058-208">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="84058-209">**[デバッグ]**  >  **[ステップ アウト]** の順に選択します。ステップ バイ ステップの実行を停止するもう 1 つの方法は、<kbd>Shift</kbd>+<kbd>F11</kbd> キーを押すことです。</span><span class="sxs-lookup"><span data-stu-id="84058-209">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   <span data-ttu-id="84058-210">コンソール ウィンドウにメッセージが表示され、任意のキーを押すよう求められます。</span><span class="sxs-lookup"><span data-stu-id="84058-210">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="84058-211">任意のキーを押してコンソール ウィンドウを閉じ、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="84058-211">Press any key to close the console window and stop debugging.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="84058-212">リリース ビルド構成を使用する</span><span class="sxs-lookup"><span data-stu-id="84058-212">Use Release build configuration</span></span>

<span data-ttu-id="84058-213">アプリケーションのデバッグ バージョンのテストが終了したら、リリース バージョンもコンパイルしてテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="84058-213">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="84058-214">リリース バージョンには、アプリケーションの動作に悪影響を与える可能性があるコンパイラの最適化が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="84058-214">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="84058-215">たとえば、パフォーマンスを向上させるように設計されたコンパイラの最適化では、マルチスレッド アプリケーションで競合状態が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="84058-215">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="84058-216">コンソール アプリケーションのリリース バージョンをビルドしてテストするには、ツール バーのビルド構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="84058-216">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

:::image type="content" source="./media/debugging-with-visual-studio/visual-studio-toolbar-release.png" alt-text="リリースが強調表示された Visual Studio の既定のツール バー":::

<span data-ttu-id="84058-218"><kbd>F5</kbd> キーを押すか、 **[ビルド]** メニューの **[ソリューションのビルド]** を選ぶと、アプリケーションのリリース バージョンが Visual Studio でコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="84058-218">When you press <kbd>F5</kbd> or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="84058-219">それをデバッグ バージョンと同様にテストできます。</span><span class="sxs-lookup"><span data-stu-id="84058-219">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="84058-220">次の手順</span><span class="sxs-lookup"><span data-stu-id="84058-220">Next steps</span></span>

<span data-ttu-id="84058-221">このチュートリアルでは、Visual Studio のデバッグ ツールを使用しました。</span><span class="sxs-lookup"><span data-stu-id="84058-221">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="84058-222">次のチュートリアルでは、アプリの展開可能なバージョンを発行します。</span><span class="sxs-lookup"><span data-stu-id="84058-222">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84058-223">Visual Studio を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="84058-223">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
