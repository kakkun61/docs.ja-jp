---
title: Visual Studio for Mac を使用して .NET コンソール アプリケーションをデバッグする
description: Visual Studio Mac を使用して .NET コンソール アプリをデバッグする方法について説明します。
ms.date: 11/30/2020
ms.openlocfilehash: e35bbef5582b6eec00ee48669a0f5d028eb051fb
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599617"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="5f8a9-103">チュートリアル: Visual Studio for Mac を使用して .NET コンソール アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="5f8a9-103">Tutorial: Debug a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="5f8a9-104">このチュートリアルでは、Visual Studio for Mac で使用できるデバッグ ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f8a9-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5f8a9-105">Prerequisites</span></span>

- <span data-ttu-id="5f8a9-106">このチュートリアルでは、「[Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-mac.md)」で作成したコンソール アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-106">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="5f8a9-107">デバッグ ビルド構成の使用</span><span class="sxs-lookup"><span data-stu-id="5f8a9-107">Use Debug build configuration</span></span>

<span data-ttu-id="5f8a9-108">"*デバッグ*" と "*リリース*" は、Visual Studio の組み込みビルド構成です。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="5f8a9-109">デバッグ用のデバッグ ビルド構成と、最終リリース配布用のリリース構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="5f8a9-110">デバッグ構成では、プログラムのコンパイルにシンボリック デバッグ情報が完全に含まれ、最適化は行われません。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="5f8a9-111">ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="5f8a9-112">プログラムのリリース構成は、シンボリック デバッグ情報を含まず、完全に最適化されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="5f8a9-113">既定では、Visual Studio for Mac ではデバッグ ビルド構成が使用されるため、デバッグの前に変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-113">By default, Visual Studio for Mac uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="5f8a9-114">Visual Studio for Mac を起動します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="5f8a9-115">「[Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-mac.md)」で作成したプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-115">Open the project that you created in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="5f8a9-116">現時点のビルド構成はツールバーに表示されています。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="5f8a9-117">次のツール バーの画像では、アプリのデバッグ バージョンをコンパイルするように Visual Studio が構成されています。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="デバッグが強調表示された Visual Studio のツールバー":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="5f8a9-119">ブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="5f8a9-119">Set a breakpoint</span></span>

<span data-ttu-id="5f8a9-120">"*ブレークポイント*" によって、ブレークポイントを含む行が実行される前に、アプリケーションの実行が一時的に中断されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="5f8a9-121">名前、日付、および時刻を表示する行にブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="5f8a9-122">これを行うには、コード行にカーソルを置き、<kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd> + <kbd>\\</kbd>) キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="5f8a9-123">ブレークポイントを設定するもう 1 つの方法は、メニューから **[実行]**  >  **[ブレークポイントの設定/解除]** を選択することです。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="5f8a9-124">Visual Studio では、ブレークポイントが設定された行を強調表示し、左余白に赤い点を表示することで、その行が示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="ブレークポイントが設定された Visual Studio のプログラム ウィンドウ":::

1. <span data-ttu-id="5f8a9-126"><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd> + <kbd>enter</kbd>) キーを押して、デバッグ モードでプログラムを起動します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="5f8a9-127">デバッグを開始するもう 1 つの方法は、メニューから **[実行]**  >  **[デバッグの開始]** を選択することです。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="5f8a9-128">プログラムから名前の入力を求められたら、ターミナル ウィンドウに文字列を入力して、<kbd>enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="5f8a9-129">プログラムの実行は、ブレークポイントに到達するときに、`Console.WriteLine` メソッドが実行される前に停止します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio でのブレークポイントのスクリーンショット":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="5f8a9-131">[イミディエイト] ウィンドウを使用する</span><span class="sxs-lookup"><span data-stu-id="5f8a9-131">Use the Immediate window</span></span>

<span data-ttu-id="5f8a9-132">**[イミディエイト]** ウィンドウでは、デバッグ中のアプリケーションと対話できます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="5f8a9-133">変数の値を対話的に変更して、プログラムにどのような影響があるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="5f8a9-134">**[イミディエイト]** ウィンドウが表示されない場合は、 **[表示]**  >  **[Debug Pads]\(デバッグ パッド\)**  >  **[イミディエイト]** の順に選択して表示します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="5f8a9-135">**[イミディエイト]** ウィンドウに「`name = "Gracie"`」と入力し、<kbd>enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="5f8a9-136">**[イミディエイト]** ウィンドウに「`date = date.AddDays(1)`」と入力し、<kbd>enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="5f8a9-137">**[イミディエイト]** ウィンドウに、文字列変数の新しい値と、<xref:System.DateTime> 値のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio の [イミディエイト] ウィンドウ":::

   <span data-ttu-id="5f8a9-139">**[ローカル]** ウィンドウには、現在実行しているメソッドで定義されている変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="5f8a9-140">変更したばかりの変数の値は **[ローカル]** ウィンドウで更新されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio の [ローカル] ウィンドウ":::

1. <span data-ttu-id="5f8a9-142"><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) キーを押してデバッグを続行します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="5f8a9-143">ターミナルに表示される値は、 **[イミディエイト]** ウィンドウで行った変更に対応しています。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="5f8a9-144">ターミナルが表示されない場合は、下部のナビゲーション バーで **[Terminal - HelloWorld]\(ターミナル - HelloWorld\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="下部のナビゲーション バーの [Terminal - HelloWorld]\(ターミナル - HelloWorld\)":::

1. <span data-ttu-id="5f8a9-146">任意のキーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="5f8a9-147">ターミナル ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="5f8a9-148">条件付きブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="5f8a9-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="5f8a9-149">プログラムによって、ユーザーが入力する文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="5f8a9-150">ユーザーが何も入力しないとどうなるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="5f8a9-151">これは、"*条件付きブレークポイント*" と呼ばれる便利なデバッグ機能を使用してテストできます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="5f8a9-152"><kbd>ctrl</kbd> キーを押しながら、ブレークポイントを表す赤い点をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="5f8a9-153">コンテキスト メニューで **[ブレークポイントの編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="5f8a9-154">**[ブレークポイントの編集]** ダイアログで、 **[さらに次の条件が真の場合]** の後に続くフィールドに次のコードを入力して、 **[適用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="ブレークポイントの設定パネルが表示されているエディター":::

   <span data-ttu-id="5f8a9-156">ブレークポイントにヒットするたびに、デバッガーは `String.IsNullOrEmpty(name)` メソッドを呼び出し、メソッド呼び出しが `true` を返す場合にのみ、この行で中断します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="5f8a9-157">条件式の代わりに、"*ヒット カウント*" を指定できます。この場合、ステートメントが指定された回数実行される前にプログラムの実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="5f8a9-158"><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) キーを押してデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="5f8a9-159">ターミナル ウィンドウで、名前の入力を求められたら、<kbd>enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="5f8a9-160">指定した条件 (`name` が `null` または <xref:System.String.Empty?displayProperty=nameWithType>) が満たされたため、ブレークポイントに到達すると、プログラムの実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="5f8a9-161">**[ローカル]** ウィンドウを選ぶと、現在実行しているメソッドに対してローカルな変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="5f8a9-162">この場合、`Main` は現在実行中のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="5f8a9-163">`name` 変数の値が `""` (つまり、<xref:System.String.Empty?displayProperty=nameWithType>) であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="5f8a9-164">値が空の文字列であることは、 **[イミディエイト]** ウィンドウに `name` という変数名を入力して <kbd>enter</kbd> キーを押すことでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="name が空の文字列であることを示す [イミディエイト] ウィンドウ":::

1. <span data-ttu-id="5f8a9-166"><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) キーを押してデバッグを続行します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="5f8a9-167">ターミナル ウィンドウで、任意のキーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="5f8a9-168">ターミナル ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-168">Close the terminal window.</span></span>

1. <span data-ttu-id="5f8a9-169">コード ウィンドウの左余白の赤い点をクリックして、ブレークポイントをクリアします。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="5f8a9-170">ブレークポイントをクリアするもう 1 つの方法は、コード行を選択した状態で **[実行] > [ブレークポイントの設定/解除]** を選択することです。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="5f8a9-171">プログラムのステップ実行</span><span class="sxs-lookup"><span data-stu-id="5f8a9-171">Step through a program</span></span>

<span data-ttu-id="5f8a9-172">Visual Studio では、1 行ずつプログラムをステップ実行して、実行を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="5f8a9-173">通常は、ブレークポイントを設定して、プログラム コードのごく一部を通じてプログラム フローに従います。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="5f8a9-174">このプログラムは小さいため、次の手順に従ってプログラム全体をステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="5f8a9-175">`Main` メソッドの開始を示す中かっこにブレークポイントを設定します (<kbd>command</kbd> + <kbd>\\</kbd> キーを押す)。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="5f8a9-176"><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) キーを押してデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="5f8a9-177">ブレークポイントがある行で Visual Studio が停止します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="5f8a9-178"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd> + <kbd>command</kbd> + <kbd>I</kbd>) キーを押すか、 **[実行]**  >  **[ステップ イン]** を選択して、1 行進めます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="5f8a9-179">次に実行される行が強調表示されて、横に矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio のステップ イン メソッド":::

   <span data-ttu-id="5f8a9-181">この時点で、 **[ローカル]** ウィンドウに `args` 配列が空であることが示され、`name` と `date` には既定値が設定されています。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="5f8a9-182">さらに、Visual Studio によって空のターミナルが開かれています。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="5f8a9-183"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd> + <kbd>command</kbd> + <kbd>I</kbd>) キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="5f8a9-184">`name` の変数代入を含むステートメントが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="5f8a9-185">**[ローカル]** ウィンドウに `name` が `null` であると表示され、ターミナルに "What is your name?" という文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="5f8a9-186">コンソール ウィンドウに文字列を入力して <kbd>enter</kbd> キーを押すことで、このプロンプトに応答します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="5f8a9-187"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd> + <kbd>command</kbd> + <kbd>I</kbd>) キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="5f8a9-188">`date` の変数代入を含むステートメントが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="5f8a9-189">**[ローカル]** ウィンドウには、<xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドの呼び出しによって返された値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5f8a9-190">ターミナルには、プロンプトで入力した文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="5f8a9-191"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd> + <kbd>command</kbd> + <kbd>I</kbd>) キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="5f8a9-192">**[ローカル]** ウィンドウには、<xref:System.DateTime.Now?displayProperty=nameWithType> プロパティから代入された後の `date` 変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5f8a9-193">ターミナルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="5f8a9-194"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd> + <kbd>command</kbd> + <kbd>I</kbd>) キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="5f8a9-195">Visual Studio は、<xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5f8a9-196">ターミナルには、書式設定された文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="5f8a9-197"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd> + <kbd>command</kbd> + <kbd>U</kbd>) キーを押すか、 **[実行]**  >  **[ステップ アウト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="5f8a9-198">ターミナルにメッセージが表示され、任意のキーを押すよう求められます。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="5f8a9-199">任意のキーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="5f8a9-200">リリース ビルド構成を使用する</span><span class="sxs-lookup"><span data-stu-id="5f8a9-200">Use Release build configuration</span></span>

<span data-ttu-id="5f8a9-201">アプリケーションのデバッグ バージョンのテストが終了したら、リリース バージョンもコンパイルしてテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="5f8a9-202">リリース バージョンには、アプリケーションの動作に悪影響を与える可能性があるコンパイラの最適化が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="5f8a9-203">たとえば、パフォーマンスを向上させるように設計されたコンパイラの最適化では、マルチスレッド アプリケーションで競合状態が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="5f8a9-204">コンソール アプリケーションのリリース バージョンをビルドしてテストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="5f8a9-205">ツール バーのビルド構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="デバッグが強調表示された Visual Studio の既定のツール バー":::

1. <span data-ttu-id="5f8a9-207"><kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>command</kbd> + <kbd>enter</kbd>) キーを押して、デバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5f8a9-208">次の手順</span><span class="sxs-lookup"><span data-stu-id="5f8a9-208">Next steps</span></span>

<span data-ttu-id="5f8a9-209">このチュートリアルでは、Visual Studio のデバッグ ツールを使用しました。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="5f8a9-210">次のチュートリアルでは、アプリの展開可能なバージョンを発行します。</span><span class="sxs-lookup"><span data-stu-id="5f8a9-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5f8a9-211">Visual Studio for Mac を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="5f8a9-211">Publish a .NET console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
