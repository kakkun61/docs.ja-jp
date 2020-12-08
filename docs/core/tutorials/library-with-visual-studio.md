---
title: Visual Studio を使用して .NET クラス ライブラリを作成する
description: Visual Studio を使用して .NET クラス ライブラリを作成する方法について学習します。
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 6a3f61525ca86afc9ee71d56cbc9450862760ba4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599513"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a><span data-ttu-id="46bc3-103">チュートリアル: Visual Studio を使用して .NET クラス ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="46bc3-103">Tutorial: Create a .NET class library using Visual Studio</span></span>

<span data-ttu-id="46bc3-104">このチュートリアルでは、1 つの文字列処理メソッドを含むシンプルなクラス ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="46bc3-105">"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="46bc3-106">ライブラリのターゲットが .NET Standard 2.0 である場合は、.NET Standard 2.0 をサポートする任意の .NET 実装 (.NET Framework を含む) で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="46bc3-107">ライブラリのターゲットが .NET 5 である場合は、.NET 5 をターゲットとする任意のアプリケーションで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="46bc3-108">このチュートリアルでは、.NET 5 をターゲットとする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-108">This tutorial shows how to target .NET 5.</span></span>

<span data-ttu-id="46bc3-109">クラス ライブラリを作成するときに、NuGet パッケージとして、またはそれを使用するアプリケーションにバンドルされているコンポーネントとして配布できます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-109">When you create a class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46bc3-110">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="46bc3-110">Prerequisites</span></span>

- <span data-ttu-id="46bc3-111">**.NET Core クロスプラットフォーム開発** ワークロードがインストールされている [Visual Studio 2019 バージョン 16.8 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="46bc3-111">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="46bc3-112">このワークロードを選択すると、.NET 5.0 SDK が自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-112">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span> <span data-ttu-id="46bc3-113">このチュートリアルでは、 **[[新しいプロジェクト] にすべての .NET Core テンプレートを表示する]** が有効になっていることを前提とします。これについては、「[チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46bc3-113">This tutorial assumes you have enabled **Show all .NET Core templates in the New project**, as shown in [Tutorial: Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="46bc3-114">ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="46bc3-114">Create a solution</span></span>

<span data-ttu-id="46bc3-115">まず、クラス ライブラリ プロジェクトを配置する空のソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="46bc3-116">1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="46bc3-117">さらに関連するプロジェクトを同じソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="46bc3-118">空のソリューションを作成するには:</span><span class="sxs-lookup"><span data-stu-id="46bc3-118">To create the blank solution:</span></span>

1. <span data-ttu-id="46bc3-119">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-119">Start Visual Studio.</span></span>

2. <span data-ttu-id="46bc3-120">スタート ウィンドウで、 **[新しいプロジェクトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="46bc3-121">**[新しいプロジェクトの作成]** ページで、検索ボックスに「**ソリューション**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="46bc3-122">**[空のソリューション]** テンプレートを選択して、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Visual Studio での空のソリューション テンプレート":::

4. <span data-ttu-id="46bc3-124">**[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**ClassLibraryProjects**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="46bc3-125">次に、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="46bc3-126">クラス ライブラリ プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="46bc3-126">Create a class library project</span></span>

1. <span data-ttu-id="46bc3-127">"StringLibrary" という名前の新しい .NET クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-127">Add a new .NET class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="46bc3-128">**ソリューション エクスプローラー** でソリューションを右クリックし、 **[追加]**  >  **[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="46bc3-129">**[新しいプロジェクトの追加]** ページで、検索ボックスに「**ライブラリ**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="46bc3-130">言語の一覧から **[C#]** または **[Visual Basic]** を選択し、次に、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="46bc3-131">**[クラス ライブラリ]** テンプレートを選んでから、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-131">Choose the **Class Library** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="46bc3-132">**[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**StringLibrary**」と入力してから、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box, and then choose **Next**.</span></span>

   1. <span data-ttu-id="46bc3-133">**[追加情報]** ページで、 **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-133">On the **Additional information** page, select **.NET 5.0 (Current)**, and then choose **Create**.</span></span>

1. <span data-ttu-id="46bc3-134">確実にライブラリのターゲットが正しいバージョンの .NET になっていることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-134">Check to make sure that the library targets the correct version of .NET.</span></span> <span data-ttu-id="46bc3-135">**ソリューション エクスプローラー** でライブラリ プロジェクトを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="46bc3-136">**[ターゲット フレームワーク]** テキスト ボックスに、.NET 5.0 がプロジェクトのターゲットになっていることが示されています。</span><span class="sxs-lookup"><span data-stu-id="46bc3-136">The **Target Framework** text box shows that the project targets .NET 5.0.</span></span>

1. <span data-ttu-id="46bc3-137">Visual Basic を使用している場合は、 **[ルート名前空間]** テキスト ボックス内のテキストをクリアします。</span><span class="sxs-lookup"><span data-stu-id="46bc3-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="クラス ライブラリのプロジェクト プロパティ":::

   <span data-ttu-id="46bc3-139">プロジェクトごとに、そのプロジェクト名に対応する名前空間が Visual Basic によって自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="46bc3-140">このチュートリアルでは、コード ファイルで [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) キーワードを使用して、最上位の名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="46bc3-141">*Class1.cs* または *Class1.vb* のコード ウィンドウ内のコードを次のコードに置き換えて、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="46bc3-142">使用する言語が表示されていない場合は、ページの上部にある言語セレクターを変更します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="46bc3-143">クラス ライブラリ `UtilityLibraries.StringLibrary` には、`StartsWithUpper` という名前のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="46bc3-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="46bc3-144">このメソッドによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す <xref:System.Boolean> 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="46bc3-145">Unicode 規格では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="46bc3-146"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> メソッドは文字が大文字の場合に `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="46bc3-147">`StartsWithUpper` は、<xref:System.String> クラスのメンバーであるかのように呼び出すことができる[拡張メソッド](../../csharp/programming-guide/classes-and-structs/extension-methods.md)として実装されます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-147">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="46bc3-148">メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** を選択するか、<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>B</kbd> キーを押して、プロジェクトがエラーなくコンパイルされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-148">On the menu bar, select **Build** > **Build Solution** or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="46bc3-149">ソリューションにコンソール アプリを追加する</span><span class="sxs-lookup"><span data-stu-id="46bc3-149">Add a console app to the solution</span></span>

<span data-ttu-id="46bc3-150">このクラス ライブラリを使用するコンソール アプリケーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="46bc3-151">アプリによって、ユーザーに文字列の入力が求められ、文字列が大文字で始まるかどうかが報告されます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="46bc3-152">"ShowCase" という名前の新しい .NET コンソール アプリケーションをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-152">Add a new .NET console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="46bc3-153">**ソリューション エクスプローラー** で、ソリューションを右クリックし、 **[追加]**  >  **[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-153">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="46bc3-154">**[新しいプロジェクトの追加]** ページで、検索ボックスに「**コンソール**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-154">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="46bc3-155">言語の一覧から **[C#]** または **[Visual Basic]** を選択し、次に、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-155">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="46bc3-156">**[コンソール アプリケーション]** テンプレートを選んでから、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-156">Choose the **Console Application** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="46bc3-157">**[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**ShowCase**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-157">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="46bc3-158">**[次へ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-158">Then choose **Next**.</span></span>

   1. <span data-ttu-id="46bc3-159">**[追加情報]** ページで、 **[ターゲット フレームワーク]** ボックスの **[.NET 5.0 (Current)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-159">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="46bc3-160">次に、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-160">Then choose **Create**.</span></span>

1. <span data-ttu-id="46bc3-161">*Program.cs* または *Program.vb* ファイルのコード ウィンドウで、すべてのコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-161">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="46bc3-162">このコードでは、`row` 変数を使って、コンソール ウィンドウに書き込まれるデータの行数のカウントを維持します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-162">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="46bc3-163">これが 25 以上になると、コードによってコンソール ウィンドウがクリアされ、ユーザーにメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-163">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="46bc3-164">プログラムは、ユーザーに文字列の入力を要求し、</span><span class="sxs-lookup"><span data-stu-id="46bc3-164">The program prompts the user to enter a string.</span></span> <span data-ttu-id="46bc3-165">文字列が大文字で始まるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-165">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="46bc3-166">ユーザーが文字列を入力せずに <kbd>Enter</kbd> キーを押すと、アプリケーションが終了し、コンソール ウィンドウが閉じます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-166">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="46bc3-167">プロジェクト参照を追加する</span><span class="sxs-lookup"><span data-stu-id="46bc3-167">Add a project reference</span></span>

<span data-ttu-id="46bc3-168">最初は、新しいコンソール アプリ プロジェクトにクラス ライブラリへのアクセス権はありません。</span><span class="sxs-lookup"><span data-stu-id="46bc3-168">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="46bc3-169">クラス ライブラリでメソッドを呼び出せるようにするには、クラス ライブラリ プロジェクトへのプロジェクト参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-169">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="46bc3-170">**ソリューション エクスプローラー** で、`ShowCase` プロジェクトの **[依存関係]** ノードを右クリックして、 **[プロジェクト参照の追加]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-170">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="Visual Studio の [参照の追加] コンテキスト メニュー":::

1. <span data-ttu-id="46bc3-172">**[参照マネージャー]** ダイアログ ボックスで、 **[StringLibrary]** プロジェクトを選び、 **[OK]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-172">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="StringLibrary が選択された [参照マネージャー] ダイアログ":::

## <a name="run-the-app"></a><span data-ttu-id="46bc3-174">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="46bc3-174">Run the app</span></span>

1. <span data-ttu-id="46bc3-175">**ソリューション エクスプローラー** で、**ShowCase** プロジェクトを右クリックして、コンテキスト メニューで **[スタートアップ プロジェクトに設定]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-175">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="スタートアップ プロジェクトを設定する Visual Studio プロジェクトのコンテキスト メニュー":::

1. <span data-ttu-id="46bc3-177"><kbd>Ctrl</kbd>+<kbd>F5</kbd> キーを押して、デバッグなしでプログラムをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-177">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="[デバッグ] ボタンを示している Visual Studio プロジェクトのツールバー":::

1. <span data-ttu-id="46bc3-179">文字列を入力して <kbd>Enter</kbd> キーを押してプログラムを実行し、<kbd>Enter</kbd> キーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-179">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="ShowCase が実行されているコンソール ウィンドウ":::

## <a name="additional-resources"></a><span data-ttu-id="46bc3-181">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="46bc3-181">Additional resources</span></span>

* [<span data-ttu-id="46bc3-182">.NET CLI を使用してライブラリを開発する</span><span class="sxs-lookup"><span data-stu-id="46bc3-182">Develop libraries with the .NET CLI</span></span>](libraries.md)
* <span data-ttu-id="46bc3-183">[.NET Standard のバージョンとそれらでサポートされているプラットフォーム](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="46bc3-183">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="46bc3-184">次の手順</span><span class="sxs-lookup"><span data-stu-id="46bc3-184">Next steps</span></span>

<span data-ttu-id="46bc3-185">このチュートリアルでは、クラス ライブラリを作成しました。</span><span class="sxs-lookup"><span data-stu-id="46bc3-185">In this tutorial, you created a class library.</span></span> <span data-ttu-id="46bc3-186">次のチュートリアルでは、そのクラス ライブラリを単体テストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="46bc3-186">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46bc3-187">Visual Studio を使用して .NET クラス ライブラリを単体テストする</span><span class="sxs-lookup"><span data-stu-id="46bc3-187">Unit test a .NET class library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="46bc3-188">または、自動化された単体テストをスキップし、NuGet パッケージを作成してそのライブラリを共有する方法を学習することもできます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-188">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46bc3-189">Visual Studio を使用した、パッケージの作成と公開</span><span class="sxs-lookup"><span data-stu-id="46bc3-189">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="46bc3-190">または、コンソール アプリを公開する方法を学習することもできます。</span><span class="sxs-lookup"><span data-stu-id="46bc3-190">Or learn how to publish a console app.</span></span> <span data-ttu-id="46bc3-191">このチュートリアルで作成したソリューションからそのコンソール アプリを発行すると、それに付属するクラス ライブラリは *.dll* ファイルとなります。</span><span class="sxs-lookup"><span data-stu-id="46bc3-191">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46bc3-192">Visual Studio を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="46bc3-192">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
