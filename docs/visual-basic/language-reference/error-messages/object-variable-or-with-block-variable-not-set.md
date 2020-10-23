---
title: オブジェクト変数または With ブロック変数が設定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 5eff7622ce2a35cf2846c5141cede98ea033d708
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159886"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="75a81-102">オブジェクト変数または With ブロック変数が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="75a81-102">Object variable or With block variable not set</span></span>

<span data-ttu-id="75a81-103">無効なオブジェクト変数が参照されています。</span><span class="sxs-lookup"><span data-stu-id="75a81-103">An invalid object variable is being referenced.</span></span> <span data-ttu-id="75a81-104">このエラーが発生する原因は複数あります。</span><span class="sxs-lookup"><span data-stu-id="75a81-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="75a81-105">型を指定せずに変数が宣言されました。</span><span class="sxs-lookup"><span data-stu-id="75a81-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="75a81-106">型を指定せずに変数が宣言されている場合、既定で `Object` 型になります。</span><span class="sxs-lookup"><span data-stu-id="75a81-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="75a81-107">たとえば、`Dim x` で宣言された変数は、`Object;` 型になり、`Dim x As String` で宣言された変数は、`String` 型になります。</span><span class="sxs-lookup"><span data-stu-id="75a81-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="75a81-108">`Option Strict` ステートメントでは、結果が `Object` 型となる暗黙の型指定が許可されません。</span><span class="sxs-lookup"><span data-stu-id="75a81-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="75a81-109">型を省略すると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="75a81-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="75a81-110">「[Option Strict ステートメント](../statements/option-strict-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75a81-110">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="75a81-111">`Nothing` に設定されているオブジェクトを参照しようとしています。</span><span class="sxs-lookup"><span data-stu-id="75a81-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="75a81-112">正しく宣言されていない配列変数の要素にアクセスしようとしています。</span><span class="sxs-lookup"><span data-stu-id="75a81-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="75a81-113">たとえば、`products() As String` として宣言された配列では、配列 `products(3) = "Widget"` の要素を参照しようとした場合に、エラーがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="75a81-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="75a81-114">配列には要素がなく、オブジェクトとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="75a81-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="75a81-115">ブロックが初期化される前に、`With...End With` ブロック内のコードにアクセスしようとしています。</span><span class="sxs-lookup"><span data-stu-id="75a81-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="75a81-116">`With` ステートメントのエントリ ポイントを実行して、`With...End With` ブロックを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75a81-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="75a81-117">Visual Basic または VBA の以前のバージョンでは、このエラーは、`Set` キーワードを使用せずに変数に値を代入する (`Set x = "name"` ではなく `x = "name"`) ことによってもトリガーされていました。</span><span class="sxs-lookup"><span data-stu-id="75a81-117">In earlier versions of Visual Basic or VBA, this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="75a81-118">`Set` キーワードは、Visual Basic .Net では無効になりました。</span><span class="sxs-lookup"><span data-stu-id="75a81-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="75a81-119">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="75a81-119">To correct this error</span></span>

1. <span data-ttu-id="75a81-120">ファイルの先頭に次のコードを追加して、`Option Strict` を `On` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75a81-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="75a81-121">プロジェクトを実行すると、**エラー一覧**に、型を使用せずに指定された任意の変数についてのコンパイラ エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75a81-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="75a81-122">`Option Strict` を有効にしない場合、コードで、型を使用せずに指定されたすべての変数 (`Dim x As String` ではなく `Dim x`) を検索し、目的の型を宣言に追加します。</span><span class="sxs-lookup"><span data-stu-id="75a81-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="75a81-123">`Nothing` に設定されているオブジェクト変数を参照していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="75a81-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="75a81-124">コードでキーワード `Nothing` を検索し、オブジェクトを参照した後までオブジェクトが `Nothing` に設定されないように、コードを修正します。</span><span class="sxs-lookup"><span data-stu-id="75a81-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="75a81-125">配列変数にアクセスする前に、それらの次元が設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="75a81-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="75a81-126">最初に配列を作成するときに次元を割り当てる (`Dim x() As String` ではなく `Dim x(5) As String`) か、または配列に最初にアクセスする前に、`ReDim` キーワードを使用して、その次元を設定できます。</span><span class="sxs-lookup"><span data-stu-id="75a81-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="75a81-127">`With` ステートメントのエントリ ポイントを実行して、`With` ブロックが初期化されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="75a81-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="75a81-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="75a81-128">See also</span></span>

- [<span data-ttu-id="75a81-129">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="75a81-129">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="75a81-130">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="75a81-130">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="75a81-131">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="75a81-131">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
