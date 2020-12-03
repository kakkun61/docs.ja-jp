---
title: 'チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)'
description: このチュートリアルでは、動的オブジェクトを作成および使用する方法について説明します。 カスタム動的オブジェクトと、'IronPython' ライブラリを使用するプロジェクトを作成します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: 8da8ba964a9f0721602b10a6258a4e85341a617f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716136"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a><span data-ttu-id="57c08-104">チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57c08-104">Walkthrough: Creating and Using Dynamic Objects (C# and Visual Basic)</span></span>

<span data-ttu-id="57c08-105">動的オブジェクトは、プロパティやメソッドなどのメンバーを、コンパイル時ではなく実行時に公開します。</span><span class="sxs-lookup"><span data-stu-id="57c08-105">Dynamic objects expose members such as properties and methods at run time, instead of at compile time.</span></span> <span data-ttu-id="57c08-106">これにより、静的な型や書式に一致しない構造体と連携するオブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="57c08-106">This enables you to create objects to work with structures that do not match a static type or format.</span></span> <span data-ttu-id="57c08-107">たとえば、動的オブジェクトを使用して HTML ドキュメント オブジェクト モデル (DOM) を参照することもできます。HTML DOM には、有効な HTML マークアップ要素と属性の任意の組み合わせを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="57c08-107">For example, you can use a dynamic object to reference the HTML Document Object Model (DOM), which can contain any combination of valid HTML markup elements and attributes.</span></span> <span data-ttu-id="57c08-108">各 HTML ドキュメントは一意であるため、特定の HTML ドキュメントのメンバーは実行時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-108">Because each HTML document is unique, the members for a particular HTML document are determined at run time.</span></span> <span data-ttu-id="57c08-109">HTML 要素の属性を参照するための一般的な方法は、属性の名前を要素の `GetProperty` メソッドに渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="57c08-109">A common method to reference an attribute of an HTML element is to pass the name of the attribute to the `GetProperty` method of the element.</span></span> <span data-ttu-id="57c08-110">HTML 要素 `<div id="Div1">` の `id` 属性を参照するには、まず `<div>` 要素への参照を取得し、その後 `divElement.GetProperty("id")` を使用します。</span><span class="sxs-lookup"><span data-stu-id="57c08-110">To reference the `id` attribute of the HTML element `<div id="Div1">`, you first obtain a reference to the `<div>` element, and then use `divElement.GetProperty("id")`.</span></span> <span data-ttu-id="57c08-111">動的オブジェクトを使用する場合は、`id` 属性を `divElement.id` として参照できます。</span><span class="sxs-lookup"><span data-stu-id="57c08-111">If you use a dynamic object, you can reference the `id` attribute as `divElement.id`.</span></span>

 <span data-ttu-id="57c08-112">動的オブジェクトを使用すると、IronPython や IronRuby などの動的言語にも簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="57c08-112">Dynamic objects also provide convenient access to dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="57c08-113">動的オブジェクトを使用して、実行時に解釈される動的スクリプトを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="57c08-113">You can use a dynamic object to refer to a dynamic script that is interpreted at run time.</span></span>

 <span data-ttu-id="57c08-114">動的オブジェクトを参照するには、遅延バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="57c08-114">You reference a dynamic object by using late binding.</span></span> <span data-ttu-id="57c08-115">C# では、遅延バインディング オブジェクトの型は `dynamic` として指定します。</span><span class="sxs-lookup"><span data-stu-id="57c08-115">In C#, you specify the type of a late-bound object as `dynamic`.</span></span> <span data-ttu-id="57c08-116">Visual Basic では、遅延バインディング オブジェクトの型は `Object` として指定します。</span><span class="sxs-lookup"><span data-stu-id="57c08-116">In Visual Basic, you specify the type of a late-bound object as `Object`.</span></span> <span data-ttu-id="57c08-117">詳しくは、「[dynamic](../../language-reference/builtin-types/reference-types.md)」および「[事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="57c08-117">For more information, see [dynamic](../../language-reference/builtin-types/reference-types.md) and [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>

 <span data-ttu-id="57c08-118">カスタムの動的オブジェクトは、<xref:System.Dynamic?displayProperty=nameWithType> 名前空間内のクラスを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="57c08-118">You can create custom dynamic objects by using the classes in the <xref:System.Dynamic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="57c08-119">たとえば、<xref:System.Dynamic.ExpandoObject> を作成し、実行時にそのオブジェクトのメンバーを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="57c08-119">For example, you can create an <xref:System.Dynamic.ExpandoObject> and specify the members of that object at run time.</span></span> <span data-ttu-id="57c08-120">また、<xref:System.Dynamic.DynamicObject> クラスを継承する、独自の型を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="57c08-120">You can also create your own type that inherits the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="57c08-121">その後、<xref:System.Dynamic.DynamicObject> クラスのメンバーをオーバーライドして、実行時の動的機能を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="57c08-121">You can then override the members of the <xref:System.Dynamic.DynamicObject> class to provide run-time dynamic functionality.</span></span>

 <span data-ttu-id="57c08-122">このチュートリアルでは、次のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="57c08-122">In this walkthrough you will perform the following tasks:</span></span>

- <span data-ttu-id="57c08-123">テキスト ファイルの内容をオブジェクトのプロパティとして動的に公開する、カスタム オブジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="57c08-123">Create a custom object that dynamically exposes the contents of a text file as properties of an object.</span></span>

- <span data-ttu-id="57c08-124">`IronPython` ライブラリを使用するプロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="57c08-124">Create a project that uses an `IronPython` library.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57c08-125">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="57c08-125">Prerequisites</span></span>

<span data-ttu-id="57c08-126">このチュートリアルを実行するには、[IronPython](https://ironpython.net/) for .NET が必要です。</span><span class="sxs-lookup"><span data-stu-id="57c08-126">You need [IronPython](https://ironpython.net/) for .NET to complete this walkthrough.</span></span> <span data-ttu-id="57c08-127">最新バージョンを取得するには、[ダウンロード ページ](https://ironpython.net/download/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="57c08-127">Go to their [Download page](https://ironpython.net/download/) to obtain the latest version.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-a-custom-dynamic-object"></a><span data-ttu-id="57c08-128">カスタム動的オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="57c08-128">Creating a Custom Dynamic Object</span></span>

<span data-ttu-id="57c08-129">このチュートリアルで作成する最初のプロジェクトでは、テキスト ファイルの内容を検索するカスタムの動的オブジェクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="57c08-129">The first project that you create in this walkthrough defines a custom dynamic object that searches the contents of a text file.</span></span> <span data-ttu-id="57c08-130">検索するテキストは、動的プロパティの名前によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-130">Text to search for is specified by the name of a dynamic property.</span></span> <span data-ttu-id="57c08-131">たとえば、呼び出しコードで `dynamicFile.Sample` が指定された場合、動的クラスは "Sample" で始まるすべての行をファイルから取得し、それらを含んだ文字列のジェネリック リストを返します。</span><span class="sxs-lookup"><span data-stu-id="57c08-131">For example, if calling code specifies `dynamicFile.Sample`, the dynamic class returns a generic list of strings that contains all of the lines from the file that begin with "Sample".</span></span> <span data-ttu-id="57c08-132">検索では、大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="57c08-132">The search is case-insensitive.</span></span> <span data-ttu-id="57c08-133">動的クラスでは、2 つの省略可能な引数もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="57c08-133">The dynamic class also supports two optional arguments.</span></span> <span data-ttu-id="57c08-134">最初の引数は、検索オプションの列挙値です。この引数では、動的クラスが行の先頭、行の末尾、または行内の任意の場所から一致を検索することを指定します。</span><span class="sxs-lookup"><span data-stu-id="57c08-134">The first argument is a search option enum value that specifies that the dynamic class should search for matches at the start of the line, the end of the line, or anywhere in the line.</span></span> <span data-ttu-id="57c08-135">2 番目の引数は、動的クラスが検索の前に各行から先頭と末尾の空白をトリミングすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="57c08-135">The second argument specifies that the dynamic class should trim leading and trailing spaces from each line before searching.</span></span> <span data-ttu-id="57c08-136">たとえば、呼び出しコードで `dynamicFile.Sample(StringSearchOption.Contains)` と指定された場合、動的クラスは行内の任意の場所にある "Sample" を検索します。</span><span class="sxs-lookup"><span data-stu-id="57c08-136">For example, if calling code specifies `dynamicFile.Sample(StringSearchOption.Contains)`, the dynamic class searches for "Sample" anywhere in a line.</span></span> <span data-ttu-id="57c08-137">呼び出しコードで `dynamicFile.Sample(StringSearchOption.StartsWith, false)` と指定された場合、動的クラスは、各行の先頭にある "Sample" を検索し、先頭と末尾のスペースは削除しません。</span><span class="sxs-lookup"><span data-stu-id="57c08-137">If calling code specifies `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, the dynamic class searches for "Sample" at the start of each line, and does not remove leading and trailing spaces.</span></span> <span data-ttu-id="57c08-138">既定では、動的クラスは各行の先頭で一致を検索し、先頭と末尾のスペースを削除します。</span><span class="sxs-lookup"><span data-stu-id="57c08-138">The default behavior of the dynamic class is to search for a match at the start of each line and to remove leading and trailing spaces.</span></span>

### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="57c08-139">カスタムの動的クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="57c08-139">To create a custom dynamic class</span></span>

1. <span data-ttu-id="57c08-140">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="57c08-140">Start Visual Studio.</span></span>

2. <span data-ttu-id="57c08-141">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-141">On the **File** menu, point to **New** and then click **Project**.</span></span>

3. <span data-ttu-id="57c08-142">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="57c08-142">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="57c08-143">**[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="57c08-143">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="57c08-144">**[名前]** ボックスに `DynamicSample` と入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-144">In the **Name** box, type `DynamicSample`, and then click **OK**.</span></span> <span data-ttu-id="57c08-145">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-145">The new project is created.</span></span>

4. <span data-ttu-id="57c08-146">DynamicSample プロジェクトを右クリックし、 **[追加]** をポイントした後、 **[クラス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-146">Right-click the DynamicSample project and point to **Add**, and then click **Class**.</span></span> <span data-ttu-id="57c08-147">**[名前]** ボックスに `ReadOnlyFile` と入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-147">In the **Name** box, type `ReadOnlyFile`, and then click **OK**.</span></span> <span data-ttu-id="57c08-148">ReadOnlyFile クラスを含んだ新しいファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-148">A new file is added that contains the ReadOnlyFile class.</span></span>

5. <span data-ttu-id="57c08-149">ReadOnlyFile.cs ファイルまたは ReadOnlyFile.vb ファイルの先頭に、次のコードを追加して <xref:System.IO?displayProperty=nameWithType> および <xref:System.Dynamic?displayProperty=nameWithType> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="57c08-149">At the top of the ReadOnlyFile.cs or ReadOnlyFile.vb file, add the following code to import the <xref:System.IO?displayProperty=nameWithType> and <xref:System.Dynamic?displayProperty=nameWithType> namespaces.</span></span>

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]

6. <span data-ttu-id="57c08-150">カスタム動的オブジェクトでは、列挙型を使用して検索条件を決定します。</span><span class="sxs-lookup"><span data-stu-id="57c08-150">The custom dynamic object uses an enum to determine the search criteria.</span></span> <span data-ttu-id="57c08-151">クラス ステートメントの前に、次の列挙定義を追加します。</span><span class="sxs-lookup"><span data-stu-id="57c08-151">Before the class statement, add the following enum definition.</span></span>

    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]

7. <span data-ttu-id="57c08-152">次のコード例に示すように、クラス ステートメントを更新して `DynamicObject` クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="57c08-152">Update the class statement to inherit the `DynamicObject` class, as shown in the following code example.</span></span>

    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. <span data-ttu-id="57c08-153">`ReadOnlyFile` クラスに次のコードを追加して、 ファイル パスのプライベート フィールドと、`ReadOnlyFile` クラスのコンス トラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="57c08-153">Add the following code to the `ReadOnlyFile` class to define a private field for the file path and a constructor for the `ReadOnlyFile` class.</span></span>

    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]

9. <span data-ttu-id="57c08-154">次の `GetPropertyValue` メソッドを `ReadOnlyFile` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="57c08-154">Add the following `GetPropertyValue` method to the `ReadOnlyFile` class.</span></span> <span data-ttu-id="57c08-155">`GetPropertyValue` メソッドは検索条件を (入力として) 受け取り、テキスト ファイルから検索条件に一致する行を返します。</span><span class="sxs-lookup"><span data-stu-id="57c08-155">The `GetPropertyValue` method takes, as input, search criteria and returns the lines from a text file that match that search criteria.</span></span> <span data-ttu-id="57c08-156">`ReadOnlyFile` クラスによって提供される動的メソッドは、`GetPropertyValue` メソッドを呼び出して、それぞれの結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="57c08-156">The dynamic methods provided by the `ReadOnlyFile` class call the `GetPropertyValue` method to retrieve their respective results.</span></span>

    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]

10. <span data-ttu-id="57c08-157">`GetPropertyValue` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドをオーバーライドする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="57c08-157">After the `GetPropertyValue` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="57c08-158"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドは、動的クラスのメンバーが要求され、引数が指定されていない場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-158">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method is called when a member of a dynamic class is requested and no arguments are specified.</span></span> <span data-ttu-id="57c08-159">`binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="57c08-159">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="57c08-160"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="57c08-160">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>

    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]

11. <span data-ttu-id="57c08-161">`TryGetMember` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドをオーバーライドする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="57c08-161">After the `TryGetMember` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="57c08-162"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドは、動的クラスのメンバーが引数を使用して要求された場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-162">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method is called when a member of a dynamic class is requested with arguments.</span></span> <span data-ttu-id="57c08-163">`binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="57c08-163">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="57c08-164">`args` 引数には、メンバーに渡される引数の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="57c08-164">The `args` argument contains an array of the arguments that are passed to the member.</span></span> <span data-ttu-id="57c08-165"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="57c08-165">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>

    <span data-ttu-id="57c08-166">`TryInvokeMember` メソッドのカスタム バージョンは、1 つ目の引数として、前の手順で定義した `StringSearchOption` 列挙からの値を受け付けます。</span><span class="sxs-lookup"><span data-stu-id="57c08-166">The custom version of the `TryInvokeMember` method expects the first argument to be a value from the `StringSearchOption` enum that you defined in a previous step.</span></span> <span data-ttu-id="57c08-167">`TryInvokeMember` メソッドは、2 つ目の引数としてブール値を受け付けます。</span><span class="sxs-lookup"><span data-stu-id="57c08-167">The `TryInvokeMember` method expects the second argument to be a Boolean value.</span></span> <span data-ttu-id="57c08-168">引数の一方または両方が有効な値であれば、それらが `GetPropertyValue` メソッドに渡され、結果が取得されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-168">If one or both arguments are valid values, they are passed to the `GetPropertyValue` method to retrieve the results.</span></span>

    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]

12. <span data-ttu-id="57c08-169">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="57c08-169">Save and close the file.</span></span>

#### <a name="to-create-a-sample-text-file"></a><span data-ttu-id="57c08-170">サンプルのテキスト ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="57c08-170">To create a sample text file</span></span>

1. <span data-ttu-id="57c08-171">DynamicSample プロジェクトを右クリックし、 **[追加]** をポイントした後、 **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-171">Right-click the DynamicSample project and point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="57c08-172">**[インストールされたテンプレート]** ペインで **[全般]** をクリックし、 **[テキスト ファイル]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="57c08-172">In the **Installed Templates** pane, select **General**, and then select the **Text File** template.</span></span> <span data-ttu-id="57c08-173">**[名前]** ボックスで、既定の名前である TextFile1.txt をそのままにし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-173">Leave the default name of TextFile1.txt in the **Name** box, and then click **Add**.</span></span> <span data-ttu-id="57c08-174">新しいテキスト ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-174">A new text file is added to the project.</span></span>

2. <span data-ttu-id="57c08-175">TextFile1.txt ファイルに次のテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="57c08-175">Copy the following text to the TextFile1.txt file.</span></span>

    ```text
    List of customers and suppliers

    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)
    Customer: Preston, Chris
    Customer: Hines, Patrick
    Customer: Cameron, Maria
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan
    Customer: Koch, Paul
    ```

3. <span data-ttu-id="57c08-176">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="57c08-176">Save and close the file.</span></span>

#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a><span data-ttu-id="57c08-177">カスタム動的オブジェクトを使用するサンプル アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="57c08-177">To create a sample application that uses the custom dynamic object</span></span>

1. <span data-ttu-id="57c08-178">**ソリューション エクスプローラー** で、Visual Basic を使用している場合は Module1.vb ファイルを、Visual C# を使用している場合は Program.cs ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-178">In **Solution Explorer**, double-click the Module1.vb file if you are using Visual Basic or the Program.cs file if you are using Visual C#.</span></span>

2. <span data-ttu-id="57c08-179">Main プロシージャに次のコードを追加して、TextFile1.txt ファイルの `ReadOnlyFile` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="57c08-179">Add the following code to the Main procedure to create an instance of the `ReadOnlyFile` class for the TextFile1.txt file.</span></span> <span data-ttu-id="57c08-180">このコードは、遅延バインディングを使用して動的メンバーを呼び出し、"Customer" という文字列を含んだテキスト行を取得します。</span><span class="sxs-lookup"><span data-stu-id="57c08-180">The code uses late binding to call dynamic members and retrieve lines of text that contain the string "Customer".</span></span>

     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]

3. <span data-ttu-id="57c08-181">ファイルを保存し、Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="57c08-181">Save the file and press CTRL+F5 to build and run the application.</span></span>

## <a name="calling-a-dynamic-language-library"></a><span data-ttu-id="57c08-182">動的言語ライブラリの呼び出し</span><span class="sxs-lookup"><span data-stu-id="57c08-182">Calling a Dynamic Language Library</span></span>

<span data-ttu-id="57c08-183">このチュートリアルで作成する次のプロジェクトでは、動的言語 IronPython で記述されたライブラリにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="57c08-183">The next project that you create in this walkthrough accesses a library that is written in the dynamic language IronPython.</span></span>

### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="57c08-184">カスタムの動的クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="57c08-184">To create a custom dynamic class</span></span>

1. <span data-ttu-id="57c08-185">Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-185">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="57c08-186">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="57c08-186">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="57c08-187">**[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="57c08-187">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="57c08-188">**[名前]** ボックスに `DynamicIronPythonSample` と入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-188">In the **Name** box, type `DynamicIronPythonSample`, and then click **OK**.</span></span> <span data-ttu-id="57c08-189">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="57c08-189">The new project is created.</span></span>

3. <span data-ttu-id="57c08-190">Visual Basic を使用している場合は、DynamicIronPythonSample プロジェクトを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-190">If you are using Visual Basic, right-click the DynamicIronPythonSample project and then click **Properties**.</span></span> <span data-ttu-id="57c08-191">**[参照]** タブをクリックします。 **[追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-191">Click the **References** tab. Click the **Add** button.</span></span> <span data-ttu-id="57c08-192">Visual C# を使用している場合は、**ソリューション エクスプローラー** で **[参照]** フォルダーを右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-192">If you are using Visual C#, in **Solution Explorer**, right-click the **References** folder and then click **Add Reference**.</span></span>

4. <span data-ttu-id="57c08-193">**[参照]** タブで、IronPython ライブラリがインストールされているフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="57c08-193">On the **Browse** tab, browse to the folder where the IronPython libraries are installed.</span></span> <span data-ttu-id="57c08-194">たとえば、C:\Program Files\IronPython 2.6 for .NET Framework 4.0 です。</span><span class="sxs-lookup"><span data-stu-id="57c08-194">For example, C:\Program Files\IronPython 2.6 for .NET Framework 4.0.</span></span> <span data-ttu-id="57c08-195">**IronPython.dll**、**IronPython.Modules.dll**、**Microsoft.Scripting.dll**、および **Microsoft.Dynamic.dll** ライブラリを選択します。</span><span class="sxs-lookup"><span data-stu-id="57c08-195">Select the **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, and **Microsoft.Dynamic.dll** libraries.</span></span> <span data-ttu-id="57c08-196">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57c08-196">Click **OK**.</span></span>

5. <span data-ttu-id="57c08-197">Visual Basic を使用している場合は、Module1.vb ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="57c08-197">If you are using Visual Basic, edit the Module1.vb file.</span></span> <span data-ttu-id="57c08-198">Visual C# を使用している場合は、Program.cs ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="57c08-198">If you are using Visual C#, edit the Program.cs file.</span></span>

6. <span data-ttu-id="57c08-199">ファイルの先頭に、IronPython ライブラリから `Microsoft.Scripting.Hosting` および `IronPython.Hosting` 名前空間をインポートするための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="57c08-199">At the top of the file, add the following code to import the `Microsoft.Scripting.Hosting` and `IronPython.Hosting` namespaces from the IronPython libraries.</span></span>

    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]

7. <span data-ttu-id="57c08-200">Main メソッドで、IronPython ライブラリをホストする新しい `Microsoft.Scripting.Hosting.ScriptRuntime` オブジェクトを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="57c08-200">In the Main method, add the following code to create a new `Microsoft.Scripting.Hosting.ScriptRuntime` object to host the IronPython libraries.</span></span> <span data-ttu-id="57c08-201">`ScriptRuntime` オブジェクトは、IronPython ライブラリ モジュール random.py を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="57c08-201">The `ScriptRuntime` object loads the IronPython library module random.py.</span></span>

     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]

8. <span data-ttu-id="57c08-202">Random.py モジュールを読み込むコードの後に、整数の配列を作成する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="57c08-202">After the code to load the random.py module, add the following code to create an array of integers.</span></span> <span data-ttu-id="57c08-203">配列は random.py モジュールの `shuffle` メソッドに渡されます。このメソッドは、配列内の値をランダムに並べ替えします。</span><span class="sxs-lookup"><span data-stu-id="57c08-203">The array is passed to the `shuffle` method of the random.py module, which randomly sorts the values in the array.</span></span>

     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]

9. <span data-ttu-id="57c08-204">ファイルを保存し、Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="57c08-204">Save the file and press CTRL+F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="57c08-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="57c08-205">See also</span></span>

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="57c08-206">dynamic 型の使用</span><span class="sxs-lookup"><span data-stu-id="57c08-206">Using Type dynamic</span></span>](./using-type-dynamic.md)
- [<span data-ttu-id="57c08-207">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="57c08-207">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="57c08-208">dynamic</span><span class="sxs-lookup"><span data-stu-id="57c08-208">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="57c08-209">動的なインターフェイスの実装 (Microsoft TechNet からダウンロードできる PDF)</span><span class="sxs-lookup"><span data-stu-id="57c08-209">Implementing Dynamic Interfaces (downloadable PDF from Microsoft TechNet)</span></span>](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
