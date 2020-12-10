---
title: Visual Studio for Mac を使用して .NET クラス ライブラリをテストする
description: .NET クラス ライブラリ用の単体テスト プロジェクトを作成します。 .NET クラス ライブラリが単体テストで正しく動作することを確認します。
ms.date: 11/18/2020
ms.openlocfilehash: 02d5aa74258ec15c5447b23246a3c7e9c61a6760
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599527"
---
# <a name="test-a-net-class-library-using-visual-studio"></a><span data-ttu-id="893d8-104">Visual Studio を使用して .NET クラス ライブラリをテストする</span><span class="sxs-lookup"><span data-stu-id="893d8-104">Test a .NET class library using Visual Studio</span></span>

<span data-ttu-id="893d8-105">このチュートリアルでは、テスト プロジェクトをソリューションに追加して、単体テストを自動化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="893d8-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="893d8-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="893d8-106">Prerequisites</span></span>

- <span data-ttu-id="893d8-107">このチュートリアルでは、「[Visual Studio for Mac を使用して .NET クラス ライブラリを作成する](library-with-visual-studio-mac.md)」で作成するソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="893d8-107">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="893d8-108">単体テスト プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="893d8-108">Create a unit test project</span></span>

<span data-ttu-id="893d8-109">単体テストでは、開発および公開時に自動化されたソフトウェア テストが提供されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="893d8-110">[MSTest](https://github.com/Microsoft/testfx-docs) は、選択できる 3 つのテスト フレームワークのうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="893d8-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="893d8-111">これ以外は、[xUnit](https://xunit.net/) と [nUnit](https://nunit.org/) です。</span><span class="sxs-lookup"><span data-stu-id="893d8-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="893d8-112">Visual Studio for Mac を起動します。</span><span class="sxs-lookup"><span data-stu-id="893d8-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="893d8-113">「[Visual Studio for Mac を使用して .NET クラス ライブラリを作成する](library-with-visual-studio-mac.md)」で作成した `ClassLibraryProjects` ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="893d8-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="893d8-114">**[ソリューション]** パッドで、<kbd>ctrl</kbd> キーを押しながら `ClassLibraryProjects` ソリューションをクリックし、 **[追加]**  >  **[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="893d8-115">**[新しいプロジェクト]** ダイアログで、 **[Web and Console]\(Web とコンソール\)** ノードから **[テスト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="893d8-116">**[MSTest プロジェクト]** を選択してから **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="テスト プロジェクトを作成する Visual Studio Mac の [新しいプロジェクト] ダイアログ":::

1. <span data-ttu-id="893d8-118">**[ターゲット フレームワーク]** として **[.NET 5.0]** を選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-118">Select **.NET 5.0** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="893d8-119">新しいプロジェクトに "StringLibraryTest" という名前を付けて、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="プロジェクト名を指定する Visual Studio Mac の [新しいプロジェクト] ダイアログ":::

   <span data-ttu-id="893d8-121">Visual Studio によって、次のコードを含むクラス ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-121">Visual Studio creates a class file with the following code:</span></span>

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

   <span data-ttu-id="893d8-122">単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="893d8-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="893d8-123">単体テストで使用される型が含まれた <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="893d8-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="893d8-124"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性が `UnitTest1` クラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="893d8-125"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性が `TestMethod1` に適用されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="893d8-126">[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)でタグ付けされたテスト クラスの [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) でタグ付けされた各テスト メソッドが、単体テスト実行時に自動実行されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="893d8-127">プロジェクト参照を追加する</span><span class="sxs-lookup"><span data-stu-id="893d8-127">Add a project reference</span></span>

<span data-ttu-id="893d8-128">テスト プロジェクトが `StringLibrary` クラスと連動するように、`StringLibrary` プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="893d8-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="893d8-129">**[ソリューション]** パッドで、**StringLibraryTest** の下にある **[依存関係]** を <kbd>ctrl</kbd> キーを押しながらクリックします。</span><span class="sxs-lookup"><span data-stu-id="893d8-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="893d8-130">コンテキスト メニューから **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="893d8-131">**[参照]** ダイアログで、 **[StringLibrary]** プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="893d8-132">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Visual Studio Mac の [参照の編集] ダイアログ":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="893d8-134">単体テスト メソッドの追加と実行</span><span class="sxs-lookup"><span data-stu-id="893d8-134">Add and run unit test methods</span></span>

<span data-ttu-id="893d8-135">Visual Studio で単体テストを実行すると、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性でマークされたクラス内で、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性でマークされた各メソッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="893d8-136">テスト メソッドは、最初の失敗が検出されたとき、またはそのメソッドに含まれているすべてのテストが成功したときに終了します。</span><span class="sxs-lookup"><span data-stu-id="893d8-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="893d8-137">一般的なテストでは、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> クラスのメンバーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="893d8-138">多くのアサート メソッドは最低 2 つのパラメーターを含んでいます。1 つは予期されるテスト結果、もう 1 つは実際のテスト結果です。</span><span class="sxs-lookup"><span data-stu-id="893d8-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="893d8-139">次の表に、`Assert` クラスの頻繁に呼び出されるメソッドをいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="893d8-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="893d8-140">Assert メソッド</span><span class="sxs-lookup"><span data-stu-id="893d8-140">Assert methods</span></span>     | <span data-ttu-id="893d8-141">関数</span><span class="sxs-lookup"><span data-stu-id="893d8-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="893d8-142">2 つの値または 2 つのオブジェクトが等しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="893d8-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="893d8-143">値またはオブジェクトが等しくない場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="893d8-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="893d8-144">2 つのオブジェクト変数が同じオブジェクトを参照していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="893d8-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="893d8-145">変数が別々のオブジェクトを参照している場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="893d8-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="893d8-146">条件が `false` であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="893d8-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="893d8-147">条件が `true` の場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="893d8-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="893d8-148">オブジェクトが `null` でないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="893d8-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="893d8-149">オブジェクトが `null` である場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="893d8-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="893d8-150">また、テスト メソッドで <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> メソッドを使用して、スローすることが期待される例外の種類を示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="893d8-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="893d8-151">指定した例外がスローされない場合、テストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="893d8-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="893d8-152">`StringLibrary.StartsWithUpper` メソッドのテストでは、大文字で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="893d8-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="893d8-153">これらの場合ではメソッドが `true` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="893d8-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="893d8-154">同様に、大文字以外で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="893d8-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="893d8-155">これらの場合ではメソッドが `false` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="893d8-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="893d8-156">ライブラリ メソッドは文字列を処理するため、[空の文字列 (`String.Empty`) ](xref:System.String.Empty) (文字がなく <xref:System.String.Length> が 0 である有効な文字列)、および初期化されていない `null` 文字列を正しく処理することも確認します。</span><span class="sxs-lookup"><span data-stu-id="893d8-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="893d8-157">しかし、`StartsWithUpper` を静的メソッドとして直接呼び出して、単一の <xref:System.String> 引数を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="893d8-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="893d8-158">または、`null` に割り当てられた `string` 変数の拡張メソッドとして `StartsWithUpper` を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="893d8-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="893d8-159">メソッドを 3 つ定義します。これらのメソッドでは、文字列配列の各要素に対して <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="893d8-160">メソッドのオーバーロードを呼び出します。これにより、テストが失敗した場合に表示されるエラー メッセージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="893d8-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="893d8-161">このメッセージによって、エラーの原因となった文字列が識別されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="893d8-162">テスト メソッドを作成するには</span><span class="sxs-lookup"><span data-stu-id="893d8-162">To create the test methods:</span></span>

1. <span data-ttu-id="893d8-163">*UnitTest1.cs* ファイルを開き、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="893d8-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="893d8-164">`TestStartsWithUpper` メソッドの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="893d8-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="893d8-165">`TestDoesNotStartWithUpper` メソッドの小文字のテストには、ギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="893d8-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="893d8-166">メニュー バーから、 **[ファイル]**  >  **[名前を付けて保存]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="893d8-167">ダイアログで、 **[エンコード]** が **[Unicode (UTF-8)]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="893d8-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio の [名前を付けてファイルを保存] ダイアログ":::

1. <span data-ttu-id="893d8-169">既存のファイルを置き換えるかどうかを確認するメッセージが表示されたら、 **[置換]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="893d8-170">UTF8 でエンコードされたファイルにソース コードを保存できなかった場合、ASCII ファイルとして保存される場合があります。</span><span class="sxs-lookup"><span data-stu-id="893d8-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="893d8-171">その場合は、ランタイムで ASCII 範囲外の UTF8 文字が正確にデコードされず、テスト結果が正確でなくなります。</span><span class="sxs-lookup"><span data-stu-id="893d8-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="893d8-172">画面の右側の **[単体テスト]** パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="893d8-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="893d8-173">メニューから **[表示]**  >  **[テスト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="893d8-174">**[ドッキング]** アイコンをクリックして、パネルを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="893d8-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Visual Studio for Mac の [単体テスト] パネルの [ドッキング] アイコン":::

1. <span data-ttu-id="893d8-176">**[すべて実行]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="893d8-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="893d8-177">すべてのテストに成功します。</span><span class="sxs-lookup"><span data-stu-id="893d8-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio for Mac の予測されるテスト成功":::

## <a name="handle-test-failures"></a><span data-ttu-id="893d8-179">テストの失敗の処理</span><span class="sxs-lookup"><span data-stu-id="893d8-179">Handle test failures</span></span>

<span data-ttu-id="893d8-180">テスト駆動開発 (TDD) を行っている場合、最初にテストを作成すると、1 回目のテスト実行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="893d8-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="893d8-181">その後、テストを成功させるコードをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="893d8-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="893d8-182">このチュートリアルでは、検証するアプリ コードを記述した後にテストを作成したため、テストが失敗することはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="893d8-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="893d8-183">テストの失敗が予想されるときにテストが失敗することを検証するには、テスト入力に無効な値を追加します。</span><span class="sxs-lookup"><span data-stu-id="893d8-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="893d8-184">`TestDoesNotStartWithUpper` メソッドの `words` 配列を変更し、文字列 "Error" を含めます。</span><span class="sxs-lookup"><span data-stu-id="893d8-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="893d8-185">ソリューションをビルドし、テストを実行するときに、Visual Studio では、自動的に開いているファイルが保存されるため、ファイルは保存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="893d8-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="893d8-186">テストをもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="893d8-186">Run the tests again.</span></span>

   <span data-ttu-id="893d8-187">今回は、 **[テスト エクスプローラー]** ウィンドウに、2 つのテストが成功し、1 つが失敗したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="[テスト エクスプローラー] ウィンドウと失敗したテスト":::

1. <span data-ttu-id="893d8-189"><kbd>ctrl</kbd> キーを押しながら、失敗したテスト、`TestDoesNotStartWithUpper` の順にクリックして、コンテキスト メニューから **[結果パッドを表示する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="893d8-190">**[結果]** パッドに、アサートによって生成されたメッセージが表示されます。"Assert.IsFalse failed.</span><span class="sxs-lookup"><span data-stu-id="893d8-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="893d8-191">Expected for 'Error': false; actual:True" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="893d8-192">エラーのため、配列内の "Error" の後ろの文字列はテストされませんでした。</span><span class="sxs-lookup"><span data-stu-id="893d8-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="IsFalse アサーションの失敗を示す [テスト エクスプローラー] ウィンドウ":::

1. <span data-ttu-id="893d8-194">手順 1 で追加した文字列 "Error" を削除します。</span><span class="sxs-lookup"><span data-stu-id="893d8-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="893d8-195">テストを再実行すると、テストは成功します。</span><span class="sxs-lookup"><span data-stu-id="893d8-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="893d8-196">ライブラリのリリース バージョンのテスト</span><span class="sxs-lookup"><span data-stu-id="893d8-196">Test the Release version of the library</span></span>

<span data-ttu-id="893d8-197">これで、ライブラリのデバッグ ビルドを実行したときにすべてのテストが成功したので、さらにライブラリのリリース ビルドに対してテストを行います。</span><span class="sxs-lookup"><span data-stu-id="893d8-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="893d8-198">コンパイラの最適化などのさまざまな要因により、デバッグ ビルドとリリース ビルドとでは動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="893d8-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="893d8-199">リリース ビルドをテストするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="893d8-199">To test the Release build:</span></span>

1. <span data-ttu-id="893d8-200">Visual Studio のツールバーで、ビルド構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="893d8-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="リリース ビルドが強調表示された Visual Studio のツールバー":::

1. <span data-ttu-id="893d8-202">**[ソリューション]** パッドで、<kbd>ctrl</kbd> キーを押しながら **StringLibrary** プロジェクトをクリックし、コンテキスト メニューから **[ビルド]** を選択してライブラリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="893d8-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="StringLibrary のコンテキスト メニューとビルド コマンド":::

1. <span data-ttu-id="893d8-204">単体テストをもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="893d8-204">Run the unit tests again.</span></span>

   <span data-ttu-id="893d8-205">テストが成功します。</span><span class="sxs-lookup"><span data-stu-id="893d8-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="893d8-206">テストのデバッグ</span><span class="sxs-lookup"><span data-stu-id="893d8-206">Debug tests</span></span>

<span data-ttu-id="893d8-207">IDE として Visual Studio for Mac を使用する場合は、「[チュートリアル:Visual Studio for Mac を使用して .NET コンソール アプリケーションをデバッグする](debugging-with-visual-studio-mac.md)」に記載されているのと同じプロセスに従って、単体テスト プロジェクトを使用してコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="893d8-207">If you're using Visual Studio for Mac as your IDE, you can use the same process shown in [Tutorial: Debug a .NET console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="893d8-208">*ShowCase* アプリ プロジェクトを開始する代わりに、<kbd>ctrl</kbd> キーを押しながら **StringLibraryTests** プロジェクトをクリックし、コンテキスト メニューから **[プロジェクトのデバッグを開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="893d8-208">Instead of starting the *ShowCase* app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span>

<span data-ttu-id="893d8-209">Visual Studio により、デバッガーがアタッチされた状態でテスト プロジェクトが開始されます。</span><span class="sxs-lookup"><span data-stu-id="893d8-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="893d8-210">実行は、テスト プロジェクトまたは基になるライブラリ コードに追加したブレークポイントで停止します。</span><span class="sxs-lookup"><span data-stu-id="893d8-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="893d8-211">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="893d8-211">Additional resources</span></span>

* [<span data-ttu-id="893d8-212">.NET での単体テスト</span><span class="sxs-lookup"><span data-stu-id="893d8-212">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="893d8-213">次の手順</span><span class="sxs-lookup"><span data-stu-id="893d8-213">Next steps</span></span>

<span data-ttu-id="893d8-214">このチュートリアルでは、クラス ライブラリの単体テストを行いました。</span><span class="sxs-lookup"><span data-stu-id="893d8-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="893d8-215">ライブラリをパッケージとして [NuGet](https://nuget.org) に発行した場合、他のユーザーもそれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="893d8-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="893d8-216">方法については、次の NuGet のチュートリアルに従ってください。</span><span class="sxs-lookup"><span data-stu-id="893d8-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="893d8-217">パッケージの作成と公開 (dotnet CLI)</span><span class="sxs-lookup"><span data-stu-id="893d8-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="893d8-218">ライブラリを NuGet パッケージとして発行した場合、他のユーザーもそれをインストールして使用できます。</span><span class="sxs-lookup"><span data-stu-id="893d8-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="893d8-219">方法については、次の NuGet のチュートリアルに従ってください。</span><span class="sxs-lookup"><span data-stu-id="893d8-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="893d8-220">Visual Studio for Mac にパッケージをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="893d8-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="893d8-221">ライブラリはパッケージとして配布する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="893d8-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="893d8-222">それが使用されるコンソール アプリにバンドルすることができます。</span><span class="sxs-lookup"><span data-stu-id="893d8-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="893d8-223">コンソール アプリを発行する方法については、このシリーズの前のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="893d8-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="893d8-224">Visual Studio for Mac を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="893d8-224">Publish a .NET console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
