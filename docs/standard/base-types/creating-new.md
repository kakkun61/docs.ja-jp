---
title: .NET で新しい文字列を作成する
description: 割り当て、クラス コンストラクター、または System.String メソッドを使用して文字列を作成する方法について学習します。これにより、.NET で複数の文字列、文字列の配列、またはオブジェクトが結合されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: a8fec6c08d44212d1b7cdd5a34c9a27b0fc19746
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683876"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="4dc58-103">.NET で新しい文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="4dc58-103">Creating New Strings in .NET</span></span>

<span data-ttu-id="4dc58-104">.NET は、単純な割り当てを使用した文字列の作成をサポートしています。また、多数の異なるパラメーターを使用した文字列を作成できるよう、クラス コンストラクターをオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-104">.NET allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="4dc58-105">.NET には、<xref:System.String?displayProperty=nameWithType> クラスにいくつかの文字列、文字列の配列、またはオブジェクトを組み合わせて新しい文字列オブジェクトを作成できるメソッドもいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4dc58-105">.NET also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="4dc58-106">割り当てを使用した文字列の作成</span><span class="sxs-lookup"><span data-stu-id="4dc58-106">Creating Strings Using Assignment</span></span>  

 <span data-ttu-id="4dc58-107">新しい <xref:System.String> オブジェクトを作成する最も簡単な方法としては、単に文字列リテラルを <xref:System.String> オブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-107">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="4dc58-108">クラス コンストラクターを使用した文字列の作成</span><span class="sxs-lookup"><span data-stu-id="4dc58-108">Creating Strings Using a Class Constructor</span></span>  

 <span data-ttu-id="4dc58-109"><xref:System.String> クラス コンストラクターのオーバーロードを使用すると、文字配列から文字列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-109">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="4dc58-110">また、指定した回数だけ特定の文字を複製することで、新しい文字列を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-110">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="4dc58-111">文字列を返すメソッド</span><span class="sxs-lookup"><span data-stu-id="4dc58-111">Methods that Return Strings</span></span>  

 <span data-ttu-id="4dc58-112">次の表は、新しい文字列オブジェクトを返すいくつかの便利なメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="4dc58-112">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="4dc58-113">メソッド名</span><span class="sxs-lookup"><span data-stu-id="4dc58-113">Method name</span></span>|<span data-ttu-id="4dc58-114">使用</span><span class="sxs-lookup"><span data-stu-id="4dc58-114">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="4dc58-115">入力オブジェクトのセットから、書式設定された文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-115">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="4dc58-116">2 つ以上の文字列から文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-116">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="4dc58-117">文字列の配列を組み合わせることで、新しい文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-117">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="4dc58-118">既存の文字列の指定のインデックスに文字列を挿入することで、新しい文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-118">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="4dc58-119">文字配列内の指定の位置に、文字列内の指定の文字をコピーします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-119">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="4dc58-120">形式</span><span class="sxs-lookup"><span data-stu-id="4dc58-120">Format</span></span>  

 <span data-ttu-id="4dc58-121">**String.Format** メソッドを使用すると、書式設定された文字列を作成し、複数のオブジェクトを表す文字列を連結できます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-121">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="4dc58-122">このメソッドは、渡されたすべてのオブジェクトを文字列に自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-122">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="4dc58-123">たとえば、アプリケーションでユーザーに対して **Int32** 値と **DateTime** 値を表示する必要がある場合、**Format** メソッドを使用して、これらの値を表す文字列を簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-123">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="4dc58-124">このメソッドで使用される書式設定規則については、[複合書式指定](composite-formatting.md)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dc58-124">For information about formatting conventions used with this method, see the section on [composite formatting](composite-formatting.md).</span></span>  
  
 <span data-ttu-id="4dc58-125">次の例では、**Format** メソッドを使用して、整数型の変数を使用する文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-125">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="4dc58-126">この例では、<xref:System.DateTime.Now%2A?displayProperty=nameWithType> は、現在のスレッドに関連付けられているカルチャで指定された方法で現在の日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-126">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="4dc58-127">Concat</span><span class="sxs-lookup"><span data-stu-id="4dc58-127">Concat</span></span>  

 <span data-ttu-id="4dc58-128">**String.Concat** メソッドを使用すると、2 つ以上の既存のオブジェクトから新しい文字列オブジェクトを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-128">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="4dc58-129">言語に依存せずに文字列を連結する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-129">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="4dc58-130">このメソッドは、**System.Object** から派生したすべてのクラスを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-130">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="4dc58-131">次の例では、2 つの既存の文字列オブジェクトおよび区切り文字から文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-131">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="4dc58-132">Join</span><span class="sxs-lookup"><span data-stu-id="4dc58-132">Join</span></span>  

 <span data-ttu-id="4dc58-133">**String.Join** メソッドは、文字列の配列および区切り文字列から新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-133">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="4dc58-134">このメソッドは、複数の文字列を連結して、たとえばコンマで区切られたリストを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="4dc58-134">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="4dc58-135">次の例では、スペースを使用して文字列の配列をバインドします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-135">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="4dc58-136">挿入</span><span class="sxs-lookup"><span data-stu-id="4dc58-136">Insert</span></span>  

 <span data-ttu-id="4dc58-137">**String.Insert** メソッドは、別の文字列内の指定の位置に文字列を挿入することで、新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-137">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="4dc58-138">このメソッドは、0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-138">This method uses a zero-based index.</span></span> <span data-ttu-id="4dc58-139">次の例では、`MyString` の 5 番目のインデックス位置に文字列を挿入し、この値を持つ新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4dc58-139">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="4dc58-140">CopyTo</span><span class="sxs-lookup"><span data-stu-id="4dc58-140">CopyTo</span></span>  

 <span data-ttu-id="4dc58-141">**String.CopyTo** メソッドは、文字配列に文字列の部分をコピーします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-141">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="4dc58-142">文字列の開始インデックスと、コピーする文字数の両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="4dc58-142">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="4dc58-143">このメソッドは、ソース インデックス、文字配列、コピー先のインデックス、およびコピーする文字数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4dc58-143">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="4dc58-144">すべてのインデックスは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="4dc58-144">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="4dc58-145">次の例では、**CopyTo** メソッドを使用して、文字列オブジェクトから文字配列の最初のインデックス位置に、単語 "Hello" の文字をコピーします。</span><span class="sxs-lookup"><span data-stu-id="4dc58-145">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4dc58-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dc58-146">See also</span></span>

- [<span data-ttu-id="4dc58-147">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="4dc58-147">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="4dc58-148">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="4dc58-148">Composite Formatting</span></span>](composite-formatting.md)
