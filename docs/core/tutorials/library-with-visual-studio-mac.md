---
title: Visual Studio for Mac を使用して .NET Standard クラス ライブラリを作成する
description: Visual Studio for Mac を使用して .NET Standard クラス ライブラリを作成する方法について説明します。
ms.date: 06/08/2020
ms.openlocfilehash: a78cc68d29095e4fefcaf1d3b2158d673b8892ec
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400566"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="3f490-103">チュートリアル: Visual Studio for Mac を使用して .NET Standard ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="3f490-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="3f490-104">このチュートリアルでは、1 つの文字列処理メソッドを含むクラス ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f490-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span> <span data-ttu-id="3f490-105">それを[拡張メソッド](../../csharp/programming-guide/classes-and-structs/extension-methods.md)として実装し、<xref:System.String> クラスのメンバーと同じように呼び出すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="3f490-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="3f490-106">" *クラス ライブラリ* " は、アプリケーションから呼び出される型とメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="3f490-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="3f490-107">.NET Standard 2.1 をターゲットとするクラス ライブラリは、バージョン 2.1 の .NET Standard をサポートする任意の .NET 実装をターゲットとするアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f490-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="3f490-108">クラス ライブラリが完成したら、サードパーティ製のコンポーネントとして配布するか、1 つ以上のアプリケーションを含むバンドルされたコンポーネントとして配布することができます。</span><span class="sxs-lookup"><span data-stu-id="3f490-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="3f490-109">お客様のフィードバックは非常に貴重です。</span><span class="sxs-lookup"><span data-stu-id="3f490-109">Your feedback is highly valued.</span></span> <span data-ttu-id="3f490-110">次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信できます。</span><span class="sxs-lookup"><span data-stu-id="3f490-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="3f490-111">Visual Studio for Mac で、メニューから **[ヘルプ]**  >  **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="3f490-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="3f490-112">お客様のフィードバックは、[開発者コミュニティ](https://aka.ms/feedback/report?space=41) ポータルで追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="3f490-112">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> - <span data-ttu-id="3f490-113">提案するには、メニューから **[ヘルプ]**  >  **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、 [Visual Studio for Mac の開発者コミュニティの Web ページ](https://aka.ms/feedback/suggest?space=41)に移動します。</span><span class="sxs-lookup"><span data-stu-id="3f490-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f490-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3f490-114">Prerequisites</span></span>

* <span data-ttu-id="3f490-115">[Visual Studio for Mac バージョン 8.6 以降をインストールします](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="3f490-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="3f490-116">.NET Core をインストールするオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="3f490-117">.NET Core 開発の場合、Xamarin のインストールは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3f490-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="3f490-118">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f490-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="3f490-119">[チュートリアル: Visual Studio for Mac をインストールする](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="3f490-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="3f490-120">[サポート対象の macOS のバージョン](../install/macos.md)。</span><span class="sxs-lookup"><span data-stu-id="3f490-120">[Supported macOS versions](../install/macos.md).</span></span>
  * <span data-ttu-id="3f490-121">[Visual Studio for Mac でサポートされている .NET Core のバージョン](/visualstudio/mac/net-core-support)。</span><span class="sxs-lookup"><span data-stu-id="3f490-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="3f490-122">クラス ライブラリ プロジェクトを含むソリューションの作成</span><span class="sxs-lookup"><span data-stu-id="3f490-122">Create a solution with a class library project</span></span>

<span data-ttu-id="3f490-123">1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="3f490-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="3f490-124">ソリューションと、そのソリューション内のクラス ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f490-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="3f490-125">後ほど、さらに関連するプロジェクトを同じソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3f490-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="3f490-126">Visual Studio for Mac を起動します。</span><span class="sxs-lookup"><span data-stu-id="3f490-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="3f490-127">スタート ウィンドウで、 **[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="3f490-128">**[新しいプロジェクト]** ダイアログで、 **[マルチプラットフォーム]** ノードの下にある **[ライブラリ]** を選択し、 **[.NET Standard ライブラリ]** テンプレートを選択して、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library** , then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="[新しいプロジェクト] ダイアログ":::

1. <span data-ttu-id="3f490-130">**[Configure your new .NET Standard Library]\(新しい .NET Standard ライブラリの構成\)** ダイアログで、[.NET Standard 2.1] を選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text=".NET Standard 2.1 を選択する":::

1. <span data-ttu-id="3f490-132">プロジェクトに「StringLibrary」という名前を指定し、ソリューションに「ClassLibraryProjects」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f490-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="3f490-133">**[ソリューション ディレクトリ内にプロジェクト ディレクトリを作成する]** はオンのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="3f490-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="3f490-134">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio for Mac の [新しいプロジェクト] ダイアログのオプション":::

1. <span data-ttu-id="3f490-136">メイン メニューから **[表示]**  >  **[パッド]**  >  **[ソリューション]** の順に選択し、ドッキング アイコンを選択してパッドを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="3f490-136">From the main menu, select **View** > **Pads** > **Solution** , and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="ソリューション パッドのドッキング アイコン":::

1. <span data-ttu-id="3f490-138">**[ソリューション]** パッドで、`StringLibrary` ノードを展開し、テンプレートで提供される *Class1.cs* というクラス ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="3f490-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="3f490-139"><kbd>ctrl</kbd> キーを押しながらファイルをクリックし、コンテキスト メニューから **[名前の変更]** を選択して、ファイル名を *StringLibrary.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="3f490-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="3f490-140">ファイルを開き、内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3f490-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="3f490-141"><kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd> + <kbd>S</kbd>) キーを押して、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="3f490-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="3f490-142">IDE ウィンドウの下部の余白にある **[エラー]** を選択して、 **[エラー]** パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3f490-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="3f490-143">**[ビルド出力]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="[エラー] ボタンが示された Visual Studio Mac IDE の下部余白":::

1. <span data-ttu-id="3f490-145">メニューから **[ビルド]**  >  **[すべてビルド]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="3f490-146">ソリューションがビルドされます。</span><span class="sxs-lookup"><span data-stu-id="3f490-146">The solution builds.</span></span> <span data-ttu-id="3f490-147">ビルド出力パネルに、ビルドが成功したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="3f490-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="ビルドの成功メッセージが表示された、[エラー] パネルの Visual Studio Mac のビルド出力ウィンドウ":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="3f490-149">ソリューションにコンソール アプリを追加する</span><span class="sxs-lookup"><span data-stu-id="3f490-149">Add a console app to the solution</span></span>

<span data-ttu-id="3f490-150">このクラス ライブラリを使用するコンソール アプリケーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f490-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="3f490-151">アプリによって、ユーザーに文字列の入力が求められ、文字列が大文字で始まるかどうかが報告されます。</span><span class="sxs-lookup"><span data-stu-id="3f490-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="3f490-152">**[ソリューション]** パッドで、 <kbd>ctrl</kbd> キーを押しながら `ClassLibraryProjects` ソリューションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f490-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="3f490-153">**[Web and Console]\(Web とコンソール\)**  >  **[アプリ]** テンプレートからテンプレートを選択することで、新しい **[コンソール アプリケーション]** プロジェクトを追加し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="3f490-154">**[ターゲット フレームワーク]** として **[.NET Core 3.1]** を選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="3f490-155">プロジェクトに「 **ShowCase** 」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3f490-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="3f490-156">**[作成]** を選択し、ソリューションでプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f490-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="ShowCase プロジェクトを追加する":::

1. <span data-ttu-id="3f490-158">*Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3f490-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="3f490-159">このコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3f490-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="3f490-160">プログラムは、ユーザーに文字列の入力を要求し、</span><span class="sxs-lookup"><span data-stu-id="3f490-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="3f490-161">文字列が大文字で始まるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3f490-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="3f490-162">ユーザーが文字列を入力せずに <kbd>enter</kbd> キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。</span><span class="sxs-lookup"><span data-stu-id="3f490-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="3f490-163">このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。</span><span class="sxs-lookup"><span data-stu-id="3f490-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="3f490-164">これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f490-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="3f490-165">プロジェクト参照を追加する</span><span class="sxs-lookup"><span data-stu-id="3f490-165">Add a project reference</span></span>

<span data-ttu-id="3f490-166">最初は、新しいコンソール アプリ プロジェクトにクラス ライブラリへのアクセス権はありません。</span><span class="sxs-lookup"><span data-stu-id="3f490-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="3f490-167">クラス ライブラリでメソッドを呼び出せるようにするには、クラス ライブラリ プロジェクトへのプロジェクト参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="3f490-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="3f490-168">**[ソリューション]** パッドで、 <kbd>ctrl</kbd> キーを押しながら、新しい **ShowCase** プロジェクトの **[依存関係]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f490-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="3f490-169">コンテキスト メニューから **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="3f490-170">**[参照]** ダイアログで、 **[StringLibrary]** を選択して **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="3f490-171">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="3f490-171">Run the app</span></span>

1. <span data-ttu-id="3f490-172"><kbd>ctrl</kbd> キーを押しながら ShowCase プロジェクトをクリックし、コンテキスト メニューから **[プロジェクトの実行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f490-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="3f490-173">文字列を入力して <kbd>enter</kbd> キーを押すことでプログラムを試してみます。<kbd>enter</kbd> キーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="3f490-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="アプリが実行中であることを示す Visual Studio for Mac のコンソール ウィンドウ":::

## <a name="additional-resources"></a><span data-ttu-id="3f490-175">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="3f490-175">Additional resources</span></span>

* [<span data-ttu-id="3f490-176">.NET Core CLI を使用したライブラリの開発</span><span class="sxs-lookup"><span data-stu-id="3f490-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="3f490-177">[.NET Standard のバージョンとそれらでサポートされているプラットフォーム](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="3f490-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="3f490-178">Visual Studio 2019 for Mac リリース ノート</span><span class="sxs-lookup"><span data-stu-id="3f490-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="3f490-179">次の手順</span><span class="sxs-lookup"><span data-stu-id="3f490-179">Next steps</span></span>

<span data-ttu-id="3f490-180">このチュートリアルでは、ソリューションとライブラリ プロジェクトを作成し、そのライブラリを使用するコンソール アプリ プロジェクトを追加しました。</span><span class="sxs-lookup"><span data-stu-id="3f490-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="3f490-181">次のチュートリアルでは、ソリューションに単体テスト プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f490-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f490-182">Visual Studio for Mac を使用して .NET Core で .NET Standard ライブラリをテストする</span><span class="sxs-lookup"><span data-stu-id="3f490-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
