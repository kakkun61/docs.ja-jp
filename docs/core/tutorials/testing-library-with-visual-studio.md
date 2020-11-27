---
title: Visual Studio を使用して .NET クラス ライブラリをテストする
description: Visual Studio を使用して、.NET クラス ライブラリの単体テスト プロジェクトを作成および実行する方法について学習します。
ms.date: 11/18/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3d56627b937fa0ad5f8002f396ce617e09ce9d2c
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916127"
---
# <a name="tutorial-test-a-net-class-library-with-net-using-visual-studio"></a><span data-ttu-id="6c717-103">チュートリアル: Visual Studio を使用して .NET で .NET クラス ライブラリをテストする</span><span class="sxs-lookup"><span data-stu-id="6c717-103">Tutorial: Test a .NET class library with .NET using Visual Studio</span></span>

<span data-ttu-id="6c717-104">このチュートリアルでは、テスト プロジェクトをソリューションに追加して、単体テストを自動化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c717-104">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c717-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6c717-105">Prerequisites</span></span>

- <span data-ttu-id="6c717-106">このチュートリアルでは、「[Visual Studio を使用して .NET クラス ライブラリを作成する](library-with-visual-studio.md)」で作成するソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6c717-106">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="6c717-107">単体テスト プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="6c717-107">Create a unit test project</span></span>

<span data-ttu-id="6c717-108">単体テストでは、開発および公開時に自動化されたソフトウェア テストが提供されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-108">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="6c717-109">[MSTest](https://github.com/Microsoft/testfx-docs) は、選択できる 3 つのテスト フレームワークのうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6c717-109">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="6c717-110">これ以外は、[xUnit](https://xunit.net/) と [nUnit](https://nunit.org/) です。</span><span class="sxs-lookup"><span data-stu-id="6c717-110">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="6c717-111">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="6c717-111">Start Visual Studio.</span></span>

1. <span data-ttu-id="6c717-112">「[Visual Studio を使用して .NET クラス ライブラリを作成する](library-with-visual-studio.md)」で作成した `ClassLibraryProjects` ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="6c717-112">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="6c717-113">「StringLibraryTest」 という名前の新しい単体テスト プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="6c717-113">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="6c717-114">**ソリューション エクスプローラー** で、ソリューションを右クリックし、 **[追加]**  >  **[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-114">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="6c717-115">**[新しいプロジェクトの追加]** ページで、検索ボックスに「**mstest**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="6c717-115">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="6c717-116">言語の一覧から **[C#]** または **[Visual Basic]** を選択し、次に、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-116">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="6c717-117">**[単体テスト プロジェクト]** テンプレートを選んでから、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-117">Choose the **Unit Test Project** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="6c717-118">**[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「**StringLibraryTest**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="6c717-118">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="6c717-119">**[次へ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="6c717-119">Then choose **Next**.</span></span>

   1. <span data-ttu-id="6c717-120">**[追加情報]** ページで、 **[ターゲット フレームワーク]** ボックスの **[.NET 5.0 (Current)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-120">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="6c717-121">次に、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-121">Then choose **Create**.</span></span>

1. <span data-ttu-id="6c717-122">Visual Studio によってプロジェクトが作成され、クラス ファイルが次のコードでコード ウィンドウに開かれます。</span><span class="sxs-lookup"><span data-stu-id="6c717-122">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="6c717-123">使用する言語で表示されていない場合は、ページの上部にある言語セレクターを変更します。</span><span class="sxs-lookup"><span data-stu-id="6c717-123">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="6c717-124">単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="6c717-124">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="6c717-125">単体テストで使用される型が含まれた <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="6c717-125">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="6c717-126"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性が `UnitTest1` クラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="6c717-127"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性を適用して、C# では `TestMethod1` を、また Visual Basic では `TestSub` が定義されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-127">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="6c717-128">[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)でタグ付けされたテスト クラスの [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) でタグ付けされた各テスト メソッドが、単体テスト実行時に自動実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-128">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="6c717-129">プロジェクト参照を追加する</span><span class="sxs-lookup"><span data-stu-id="6c717-129">Add a project reference</span></span>

<span data-ttu-id="6c717-130">テスト プロジェクトが `StringLibrary` クラスと連動するように、**StringLibraryTest** プロジェクトに `StringLibrary` プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="6c717-130">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="6c717-131">**ソリューション エクスプローラー** で **[StringLibraryTest]** プロジェクトの **[依存関係]** ノードを右クリックし、コンテキスト メニューの **[プロジェクト参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-131">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="6c717-132">**[参照マネージャー]** ダイアログで、 **[プロジェクト]** ノードを展開し、 **[StringLibrary]** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6c717-132">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="6c717-133">`StringLibrary` アセンブリに参照を追加すると、コンパイラが **StringLibraryTest** プロジェクトをコンパイル中に、**StringLibrary** メソッドを見つけることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="6c717-133">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="6c717-134">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-134">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="6c717-135">単体テスト メソッドの追加と実行</span><span class="sxs-lookup"><span data-stu-id="6c717-135">Add and run unit test methods</span></span>

<span data-ttu-id="6c717-136">Visual Studio で単体テストを実行すると、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性でマークされたクラス内で、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性でマークされた各メソッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-136">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="6c717-137">テスト メソッドは、最初の失敗が検出されたとき、またはそのメソッドに含まれているすべてのテストが成功したときに終了します。</span><span class="sxs-lookup"><span data-stu-id="6c717-137">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="6c717-138">一般的なテストでは、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> クラスのメンバーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-138">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="6c717-139">多くのアサート メソッドは最低 2 つのパラメーターを含んでいます。1 つは予期されるテスト結果、もう 1 つは実際のテスト結果です。</span><span class="sxs-lookup"><span data-stu-id="6c717-139">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="6c717-140">次の表に、`Assert` クラスの頻繁に呼び出されるメソッドをいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="6c717-140">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="6c717-141">Assert メソッド</span><span class="sxs-lookup"><span data-stu-id="6c717-141">Assert methods</span></span>     | <span data-ttu-id="6c717-142">関数</span><span class="sxs-lookup"><span data-stu-id="6c717-142">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="6c717-143">2 つの値または 2 つのオブジェクトが等しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="6c717-143">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="6c717-144">値またはオブジェクトが等しくない場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="6c717-144">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="6c717-145">2 つのオブジェクト変数が同じオブジェクトを参照していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6c717-145">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="6c717-146">変数が別々のオブジェクトを参照している場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="6c717-146">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="6c717-147">条件が `false` であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6c717-147">Verifies that a condition is `false`.</span></span> <span data-ttu-id="6c717-148">条件が `true` の場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="6c717-148">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="6c717-149">オブジェクトが `null` でないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="6c717-149">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="6c717-150">オブジェクトが `null` である場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="6c717-150">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="6c717-151">また、テスト メソッドで <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> メソッドを使用して、スローすることが期待される例外の種類を示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="6c717-151">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="6c717-152">指定した例外がスローされない場合、テストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="6c717-152">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="6c717-153">`StringLibrary.StartsWithUpper` メソッドのテストでは、大文字で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="6c717-153">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="6c717-154">これらの場合ではメソッドが `true` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6c717-154">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6c717-155">同様に、大文字以外で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="6c717-155">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="6c717-156">これらの場合ではメソッドが `false` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6c717-156">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6c717-157">ライブラリ メソッドは文字列を処理するため、[空の文字列 (`String.Empty`) ](xref:System.String.Empty) (文字がなく <xref:System.String.Length> が 0 である有効な文字列)、および初期化されていない `null` 文字列を正しく処理することも確認します。</span><span class="sxs-lookup"><span data-stu-id="6c717-157">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="6c717-158">しかし、`StartsWithUpper` を静的メソッドとして直接呼び出して、単一の <xref:System.String> 引数を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="6c717-158">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="6c717-159">または、`null` に割り当てられた `string` 変数の拡張メソッドとして `StartsWithUpper` を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="6c717-159">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="6c717-160">メソッドを 3 つ定義します。これらのメソッドでは、文字列配列の各要素に対して <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-160">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="6c717-161">メソッドのオーバーロードを呼び出します。これにより、テストが失敗した場合に表示されるエラー メッセージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6c717-161">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="6c717-162">このメッセージによって、エラーの原因となった文字列が識別されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-162">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="6c717-163">テスト メソッドを作成するには</span><span class="sxs-lookup"><span data-stu-id="6c717-163">To create the test methods:</span></span>

1. <span data-ttu-id="6c717-164">*UnitTest1.cs* または *UnitTest1.vb* コード ウィンドウで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6c717-164">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="6c717-165">`TestStartsWithUpper` メソッドの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6c717-165">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="6c717-166">`TestDoesNotStartWithUpper` メソッドの小文字のテストには、ギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6c717-166">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="6c717-167">メニュー バーで、 **[ファイル]**  >  **[名前を付けて UnitTest1.cs を保存]** または **[ファイル]**  >  **[名前を付けて UnitTest1.vb を保存]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-167">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="6c717-168">**[名前を付けてファイルを保存]** ダイアログで、 **[保存]** ボタンの横にある矢印を選択して、 **[エンコード付きで保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-168">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/save-file-as-dialog.png" alt-text="Visual Studio の [名前を付けてファイルを保存] ダイアログ":::

1. <span data-ttu-id="6c717-170">**[保存の確認]** ダイアログで **[はい]** ボタンを選択してファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="6c717-170">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="6c717-171">**[保存オプションの詳細設定]** ダイアログの **[エンコード]** ドロップダウン リストから **[Unicode (UTF-8 シグネチャ付き) - コードページ 65001]** を選択し、 **[OK]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-171">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/advanced-save-options.png" alt-text="Visual Studio の [保存オプションの詳細設定] ダイアログ":::

   <span data-ttu-id="6c717-173">UTF8 でエンコードされたファイルにソース コードを保存できなかった場合、ASCII ファイルとして保存される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6c717-173">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="6c717-174">その場合は、ランタイムで ASCII 範囲外の UTF8 文字が正確にデコードされず、テスト結果が正確でなくなります。</span><span class="sxs-lookup"><span data-stu-id="6c717-174">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="6c717-175">メニュー バーで **[テスト]**  >  **[すべてのテストを実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-175">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="6c717-176">**テスト エクスプローラー** ウィンドウが開かない場合は、 **[テスト]**  >  **[テスト エクスプローラー]** を選択して開きます。</span><span class="sxs-lookup"><span data-stu-id="6c717-176">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="6c717-177">3 つのテストが **[成功したテスト]** セクションに表示され、 **[概要]** セクションにはテストの実行結果が表示されています。</span><span class="sxs-lookup"><span data-stu-id="6c717-177">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/test-explorer-window.png" alt-text="[テスト エクスプローラー] ウィンドウと成功したテスト":::

## <a name="handle-test-failures"></a><span data-ttu-id="6c717-179">テストの失敗の処理</span><span class="sxs-lookup"><span data-stu-id="6c717-179">Handle test failures</span></span>

<span data-ttu-id="6c717-180">テスト駆動開発 (TDD) を行っている場合、最初にテストを作成すると、1 回目のテスト実行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="6c717-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="6c717-181">その後、テストを成功させるコードをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="6c717-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="6c717-182">このチュートリアルでは、検証するアプリ コードを記述した後にテストを作成したため、テストが失敗することはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="6c717-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="6c717-183">テストの失敗が予想されるときにテストが失敗することを検証するには、テスト入力に無効な値を追加します。</span><span class="sxs-lookup"><span data-stu-id="6c717-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="6c717-184">`TestDoesNotStartWithUpper` メソッドの `words` 配列を変更し、文字列 "Error" を含めます。</span><span class="sxs-lookup"><span data-stu-id="6c717-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="6c717-185">ソリューションをビルドし、テストを実行するときに、Visual Studio では、自動的に開いているファイルが保存されるため、ファイルは保存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6c717-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="6c717-186">メニュー バーから **[テスト]**  >  **[すべてのテストを実行]** を選択してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c717-186">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="6c717-187">**[テスト エクスプローラー]** ウィンドウに、テストが 2 つ成功し、1 つ失敗したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-187">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-window.png" alt-text="[テスト エクスプローラー] ウィンドウと失敗したテスト":::

1. <span data-ttu-id="6c717-189">失敗したテスト `TestDoesNotStartWith` を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-189">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="6c717-190">**[テスト エクスプローラー]** ウィンドウに、アサートによって生成されたメッセージ"Assert.IsFalse failed.</span><span class="sxs-lookup"><span data-stu-id="6c717-190">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="6c717-191">Expected for 'Error': false; actual:True" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="6c717-192">エラーのため、配列内の "Error" の後ろの文字列はテストされませんでした。</span><span class="sxs-lookup"><span data-stu-id="6c717-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-detail.png" alt-text="IsFalse アサーションの失敗を示す [テスト エクスプローラー] ウィンドウ":::

1. <span data-ttu-id="6c717-194">手順 1 で追加した文字列 "Error" を削除します。</span><span class="sxs-lookup"><span data-stu-id="6c717-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="6c717-195">テストを再実行すると、テストは成功します。</span><span class="sxs-lookup"><span data-stu-id="6c717-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="6c717-196">ライブラリのリリース バージョンのテスト</span><span class="sxs-lookup"><span data-stu-id="6c717-196">Test the Release version of the library</span></span>

<span data-ttu-id="6c717-197">これで、ライブラリのデバッグ ビルドを実行したときにすべてのテストが成功したので、さらにライブラリのリリース ビルドに対してテストを行います。</span><span class="sxs-lookup"><span data-stu-id="6c717-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="6c717-198">コンパイラの最適化などのさまざまな要因により、デバッグ ビルドとリリース ビルドとでは動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6c717-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="6c717-199">リリース ビルドをテストするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6c717-199">To test the Release build:</span></span>

1. <span data-ttu-id="6c717-200">Visual Studio のツールバーで、ビルド構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="6c717-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png" alt-text="リリース ビルドが強調表示された Visual Studio のツールバー":::

1. <span data-ttu-id="6c717-202">**ソリューション エクスプローラー** で **[StringLibrary]** プロジェクトを右クリックし、コンテキスト メニューの **[ビルド]** を選択し、ライブラリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="6c717-202">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/build-library-context-menu.png" alt-text="StringLibrary のコンテキスト メニューとビルド コマンド":::

1. <span data-ttu-id="6c717-204">**[テストの実行]**  >  **[すべてのテスト]** をメニュー バーから選択して単体テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c717-204">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="6c717-205">テストが成功します。</span><span class="sxs-lookup"><span data-stu-id="6c717-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="6c717-206">テストのデバッグ</span><span class="sxs-lookup"><span data-stu-id="6c717-206">Debug tests</span></span>

<span data-ttu-id="6c717-207">IDE として Visual Studio を使用する場合は、「[チュートリアル:Visual Studio を使用して .NET コンソール アプリケーションをデバッグする](debugging-with-visual-studio.md)」に示されているのと同じプロセスを使用し、単体テスト プロジェクトを使ってコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="6c717-207">If you're using Visual Studio as your IDE, you can use the same process shown in [Tutorial: Debug a .NET console application using Visual Studio](debugging-with-visual-studio.md) to debug code using your unit test project.</span></span> <span data-ttu-id="6c717-208">*ShowCase* アプリ プロジェクトを開始する代わりに、**StringLibraryTests** プロジェクトを右クリックし、コンテキスト メニューから **[テストのデバッグ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c717-208">Instead of starting the *ShowCase* app project, right-click the **StringLibraryTests** project, and select **Debug Tests** from the context menu.</span></span>

<span data-ttu-id="6c717-209">Visual Studio により、デバッガーがアタッチされた状態でテスト プロジェクトが開始されます。</span><span class="sxs-lookup"><span data-stu-id="6c717-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="6c717-210">実行は、テスト プロジェクトまたは基になるライブラリ コードに追加したブレークポイントで停止します。</span><span class="sxs-lookup"><span data-stu-id="6c717-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6c717-211">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="6c717-211">Additional resources</span></span>

* [<span data-ttu-id="6c717-212">Visual Studio - 単体テストの基本</span><span class="sxs-lookup"><span data-stu-id="6c717-212">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="6c717-213">.NET での単体テスト</span><span class="sxs-lookup"><span data-stu-id="6c717-213">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="6c717-214">次の手順</span><span class="sxs-lookup"><span data-stu-id="6c717-214">Next steps</span></span>

<span data-ttu-id="6c717-215">このチュートリアルでは、クラス ライブラリの単体テストを行いました。</span><span class="sxs-lookup"><span data-stu-id="6c717-215">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="6c717-216">ライブラリをパッケージとして [NuGet](https://nuget.org) に発行した場合、他のユーザーもそれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c717-216">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="6c717-217">方法については、次の NuGet のチュートリアルに従ってください。</span><span class="sxs-lookup"><span data-stu-id="6c717-217">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6c717-218">Visual Studio を使用した NuGet パッケージの作成と公開</span><span class="sxs-lookup"><span data-stu-id="6c717-218">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="6c717-219">ライブラリを NuGet パッケージとして発行した場合、他のユーザーもそれをインストールして使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c717-219">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="6c717-220">方法については、次の NuGet のチュートリアルに従ってください。</span><span class="sxs-lookup"><span data-stu-id="6c717-220">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6c717-221">Visual Studio でパッケージをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="6c717-221">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="6c717-222">ライブラリはパッケージとして配布する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6c717-222">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="6c717-223">それが使用されるコンソール アプリにバンドルすることができます。</span><span class="sxs-lookup"><span data-stu-id="6c717-223">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="6c717-224">コンソール アプリを発行する方法については、このシリーズの前のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c717-224">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6c717-225">Visual Studio を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="6c717-225">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
