---
title: Visual Studio for Mac を使用して .NET クラス ライブラリを作成する
description: Visual Studio for Mac を使用して .NET クラス ライブラリを作成する方法について学習します。
ms.date: 11/30/2020
ms.openlocfilehash: 1b6b26de06d18d505fa6dde3ff9779a3dab3f1e6
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599306"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-for-mac"></a><span data-ttu-id="f3c84-103">チュートリアル: Visual Studio for Mac を使用して .NET クラス ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="f3c84-103">Tutorial: Create a .NET class library using Visual Studio for Mac</span></span>

<span data-ttu-id="f3c84-104">このチュートリアルでは、1 つの文字列処理メソッドを含むクラス ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span>

<span data-ttu-id="f3c84-105">"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="f3c84-106">ライブラリのターゲットが .NET Standard 2.0 である場合は、.NET Standard 2.0 をサポートする任意の .NET 実装 (.NET Framework を含む) で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="f3c84-107">ライブラリのターゲットが .NET 5 である場合は、.NET 5 をターゲットとする任意のアプリケーションで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="f3c84-108">このチュートリアルでは、.NET 5 をターゲットとする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-108">This tutorial shows how to target .NET 5.</span></span>

> [!NOTE]
> <span data-ttu-id="f3c84-109">お客様のフィードバックは非常に貴重です。</span><span class="sxs-lookup"><span data-stu-id="f3c84-109">Your feedback is highly valued.</span></span> <span data-ttu-id="f3c84-110">次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信できます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="f3c84-111">Visual Studio for Mac で、メニューから **[ヘルプ]**  >  **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="f3c84-112">お客様のフィードバックは、[開発者コミュニティ](https://aka.ms/feedback/report?space=41) ポータルで追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-112">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> - <span data-ttu-id="f3c84-113">提案するには、メニューから **[ヘルプ]**  >  **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、[Visual Studio for Mac の開発者コミュニティの Web ページ](https://aka.ms/feedback/suggest?space=41)に移動します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3c84-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f3c84-114">Prerequisites</span></span>

* <span data-ttu-id="f3c84-115">[Visual Studio for Mac バージョン 8.8 以降をインストールします](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="f3c84-115">[Install Visual Studio for Mac version 8.8 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="f3c84-116">.NET Core をインストールするオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="f3c84-117">.NET 開発の場合、Xamarin のインストールは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f3c84-117">Installing Xamarin is optional for .NET development.</span></span> <span data-ttu-id="f3c84-118">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3c84-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="f3c84-119">[チュートリアル: Visual Studio for Mac をインストールする](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="f3c84-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="f3c84-120">[サポート対象の macOS のバージョン](../install/macos.md)。</span><span class="sxs-lookup"><span data-stu-id="f3c84-120">[Supported macOS versions](../install/macos.md).</span></span>
  * <span data-ttu-id="f3c84-121">[Visual Studio for Mac でサポートされている .NET のバージョン](/visualstudio/mac/net-core-support)。</span><span class="sxs-lookup"><span data-stu-id="f3c84-121">[.NET versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="f3c84-122">クラス ライブラリ プロジェクトを含むソリューションの作成</span><span class="sxs-lookup"><span data-stu-id="f3c84-122">Create a solution with a class library project</span></span>

<span data-ttu-id="f3c84-123">1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="f3c84-124">ソリューションと、そのソリューション内のクラス ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="f3c84-125">後ほど、さらに関連するプロジェクトを同じソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="f3c84-126">Visual Studio for Mac を起動します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="f3c84-127">スタート ウィンドウで、 **[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="f3c84-128">**[新しいプロジェクト用のテンプレートを選びます]** ダイアログで、 **[Web and Console]\(Web とコンソール\)**  >  **[ライブラリ]**  >  **[クラス ライブラリ]** の順に選択した後、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-128">In the **Choose a template for your new project** dialog select **Web and Console** > **Library** > **Class Library**, and then select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="[新しいプロジェクト] ダイアログ":::

1. <span data-ttu-id="f3c84-130">**[Configure your new Class Library]\(新しいクラス ライブラリの構成\)** ダイアログで、 **[.NET 5.0]** を選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-130">In the **Configure your new Class Library** dialog, choose **.NET 5.0**, and select **Next**.</span></span>

1. <span data-ttu-id="f3c84-131">プロジェクトに「StringLibrary」という名前を指定し、ソリューションに「ClassLibraryProjects」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-131">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="f3c84-132">**[ソリューション ディレクトリ内にプロジェクト ディレクトリを作成する]** はオンのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-132">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="f3c84-133">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-133">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio for Mac の [新しいプロジェクト] ダイアログのオプション":::

1. <span data-ttu-id="f3c84-135">メイン メニューから **[表示]**  >  **[ソリューション]** の順に選択し、ドッキング アイコンを選択してパッドを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="f3c84-135">From the main menu, select **View** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="ソリューション パッドのドッキング アイコン":::

1. <span data-ttu-id="f3c84-137">**[ソリューション]** パッドで、`StringLibrary` ノードを展開し、テンプレートで提供される *Class1.cs* というクラス ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-137">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="f3c84-138"><kbd>ctrl</kbd> キーを押しながらファイルをクリックし、コンテキスト メニューから **[名前の変更]** を選択して、ファイル名を *StringLibrary.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-138"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="f3c84-139">ファイルを開き、内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-139">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="f3c84-140"><kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd> + <kbd>S</kbd>) キーを押して、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-140">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="f3c84-141">IDE ウィンドウの下部の余白にある **[エラー]** を選択して、 **[エラー]** パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-141">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="f3c84-142">**[ビルド出力]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-142">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="[エラー] ボタンが示された Visual Studio Mac IDE の下部余白":::

1. <span data-ttu-id="f3c84-144">メニューから **[ビルド]**  >  **[すべてビルド]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-144">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="f3c84-145">ソリューションがビルドされます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-145">The solution builds.</span></span> <span data-ttu-id="f3c84-146">ビルド出力パネルに、ビルドが成功したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-146">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="ビルドの成功メッセージが表示された、[エラー] パネルの Visual Studio Mac のビルド出力ウィンドウ":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="f3c84-148">ソリューションにコンソール アプリを追加する</span><span class="sxs-lookup"><span data-stu-id="f3c84-148">Add a console app to the solution</span></span>

<span data-ttu-id="f3c84-149">このクラス ライブラリを使用するコンソール アプリケーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="f3c84-150">アプリによって、ユーザーに文字列の入力が求められ、文字列が大文字で始まるかどうかが報告されます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="f3c84-151">**[ソリューション]** パッドで、<kbd>ctrl</kbd> キーを押しながら `ClassLibraryProjects` ソリューションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3c84-151">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="f3c84-152">**[Web and Console]\(Web とコンソール\)**  >  **[アプリ]** テンプレートからテンプレートを選択することで、新しい **[コンソール アプリケーション]** プロジェクトを追加し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-152">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="f3c84-153">**[ターゲット フレームワーク]** として **[.NET 5.0]** を選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-153">Select **.NET 5.0** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="f3c84-154">プロジェクトに「**ShowCase**」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-154">Name the project **ShowCase**.</span></span> <span data-ttu-id="f3c84-155">**[作成]** を選択し、ソリューションでプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-155">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="ShowCase プロジェクトを追加する":::

1. <span data-ttu-id="f3c84-157">*Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-157">Open the *Program.cs* file.</span></span> <span data-ttu-id="f3c84-158">このコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-158">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="f3c84-159">プログラムは、ユーザーに文字列の入力を要求し、</span><span class="sxs-lookup"><span data-stu-id="f3c84-159">The program prompts the user to enter a string.</span></span> <span data-ttu-id="f3c84-160">文字列が大文字で始まるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-160">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="f3c84-161">ユーザーが文字列を入力せずに <kbd>enter</kbd> キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-161">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="f3c84-162">このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-162">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="f3c84-163">これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3c84-163">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="f3c84-164">プロジェクト参照を追加する</span><span class="sxs-lookup"><span data-stu-id="f3c84-164">Add a project reference</span></span>

<span data-ttu-id="f3c84-165">最初は、新しいコンソール アプリ プロジェクトにクラス ライブラリへのアクセス権はありません。</span><span class="sxs-lookup"><span data-stu-id="f3c84-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="f3c84-166">クラス ライブラリでメソッドを呼び出せるようにするには、クラス ライブラリ プロジェクトへのプロジェクト参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="f3c84-167">**[ソリューション]** パッドで、<kbd>ctrl</kbd> キーを押しながら、新しい **ShowCase** プロジェクトの **[依存関係]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3c84-167">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="f3c84-168">コンテキスト メニューから **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-168">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="f3c84-169">**[参照]** ダイアログで、 **[StringLibrary]** を選択して **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-169">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="f3c84-170">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="f3c84-170">Run the app</span></span>

1. <span data-ttu-id="f3c84-171"><kbd>ctrl</kbd> キーを押しながら **ShowCase** プロジェクトをクリックし、コンテキスト メニューから **[プロジェクトの実行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-171"><kbd>ctrl</kbd>-click the **ShowCase** project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="f3c84-172">文字列を入力して <kbd>enter</kbd> キーを押すことでプログラムを試してみます。<kbd>enter</kbd> キーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-172">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="アプリが実行中であることを示す Visual Studio for Mac のコンソール ウィンドウ":::

## <a name="additional-resources"></a><span data-ttu-id="f3c84-174">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="f3c84-174">Additional resources</span></span>

* [<span data-ttu-id="f3c84-175">.NET CLI を使用してライブラリを開発する</span><span class="sxs-lookup"><span data-stu-id="f3c84-175">Develop libraries with the .NET CLI</span></span>](libraries.md)
* [<span data-ttu-id="f3c84-176">Visual Studio 2019 for Mac リリース ノート</span><span class="sxs-lookup"><span data-stu-id="f3c84-176">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)
* <span data-ttu-id="f3c84-177">[.NET Standard のバージョンとそれらでサポートされているプラットフォーム](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="f3c84-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f3c84-178">次の手順</span><span class="sxs-lookup"><span data-stu-id="f3c84-178">Next steps</span></span>

<span data-ttu-id="f3c84-179">このチュートリアルでは、ソリューションとライブラリ プロジェクトを作成し、そのライブラリを使用するコンソール アプリ プロジェクトを追加しました。</span><span class="sxs-lookup"><span data-stu-id="f3c84-179">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="f3c84-180">次のチュートリアルでは、ソリューションに単体テスト プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3c84-180">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3c84-181">Visual Studio for Mac を使用して .NET クラス ライブラリをテストする</span><span class="sxs-lookup"><span data-stu-id="f3c84-181">Test a .NET class library using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
