---
title: .NET の文字列からの文字のトリムと削除
description: .NET で、文字列の先頭または末尾から空白スペースを削除する方法、または文字列内の指定した位置から任意の数のスペースまたは文字を削除する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: 8bc2980aa887dc652485e135058b9f6f718e7b45
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831274"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="8eaa7-103">.NET の文字列からの文字のトリムと削除</span><span class="sxs-lookup"><span data-stu-id="8eaa7-103">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="8eaa7-104">文章を個々の単語に分割すると、単語の先頭または末尾に空白が残る場合があります。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-104">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="8eaa7-105">そのような場合は、**System.String** クラスのトリム メソッドのいずれかを使用して、文字列内の指定した位置から任意の数の空白またはその他の文字を削除できます。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-105">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="8eaa7-106">使用できるトリム メソッドとその説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-106">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="8eaa7-107">メソッド名</span><span class="sxs-lookup"><span data-stu-id="8eaa7-107">Method name</span></span>|<span data-ttu-id="8eaa7-108">使用</span><span class="sxs-lookup"><span data-stu-id="8eaa7-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="8eaa7-109">文字列の先頭と末尾から、空白または文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-109">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="8eaa7-110">文字列の末尾から、文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-110">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="8eaa7-111">文字列の先頭から、文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-111">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="8eaa7-112">文字列内の指定したインデックス位置から、指定した数の文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-112">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="8eaa7-113">Trim</span><span class="sxs-lookup"><span data-stu-id="8eaa7-113">Trim</span></span>

 <span data-ttu-id="8eaa7-114"><xref:System.String.Trim%2A?displayProperty=nameWithType> メソッドを使用すると、文字列の両端から空白を簡単に削除できます。メソッドの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-114">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="8eaa7-115">文字列の先頭と末尾から、文字配列で指定した文字を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-115">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="8eaa7-116">次に、空白文字、ピリオド、およびアスタリスクを削除する例を示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-116">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="8eaa7-117">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="8eaa7-117">TrimEnd</span></span>

 <span data-ttu-id="8eaa7-118">**String.TrimEnd** メソッドは、文字列の末尾から文字を削除して新しい文字列オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-118">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="8eaa7-119">このメソッドには、削除する文字を指定する文字配列が渡されます。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-119">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="8eaa7-120">文字配列内での要素の順序は、トリム操作に影響しません。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-120">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="8eaa7-121">トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-121">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="8eaa7-122">**TrimEnd** メソッドを使用して文字列の末尾の数文字を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-122">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="8eaa7-123">この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'r'` という文字と `'W'` という文字の順序を逆にしてあります。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-123">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="8eaa7-124">このコードは、`MyString` の最後の単語だけでなく、最初の単語の一部も削除します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-124">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="8eaa7-125">このコードは、コンソールに `He` と出力します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-125">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="8eaa7-126">**TrimEnd** メソッドを使用して、文字列の最後の単語を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-126">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="8eaa7-127">このコードでは、`Hello` という単語の後にコンマがありますが、削除する文字の配列にコンマは指定されていないため、コンマの位置でトリムが停止します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-127">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="8eaa7-128">このコードは、コンソールに `Hello,` と出力します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-128">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="8eaa7-129">TrimStart</span><span class="sxs-lookup"><span data-stu-id="8eaa7-129">TrimStart</span></span>

 <span data-ttu-id="8eaa7-130">**String.TrimStart** メソッドは **String.TrimEnd** メソッドと似ていますが、既存の文字列オブジェクトの先頭から文字を削除して新しい文字列を作成する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-130">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="8eaa7-131">**TrimStart** メソッドには、削除する文字を指定する文字配列が渡されます。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-131">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="8eaa7-132">**TrimEnd** メソッドの場合と同様に、文字配列内での要素の順序はトリム操作に影響しません。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-132">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="8eaa7-133">トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-133">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="8eaa7-134">文字列の最初の単語を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-134">The following example removes the first word of a string.</span></span> <span data-ttu-id="8eaa7-135">この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'l'` という文字と `'H'` という文字の順序を逆にしてあります。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-135">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="8eaa7-136">このコードは、コンソールに `World!` と出力します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-136">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="8eaa7-137">削除</span><span class="sxs-lookup"><span data-stu-id="8eaa7-137">Remove</span></span>

 <span data-ttu-id="8eaa7-138"><xref:System.String.Remove%2A?displayProperty=nameWithType> メソッドは、既存の文字列内の指定した位置を開始位置として、指定した数の文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-138">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="8eaa7-139">このメソッドは、インデックスが 0 から始まっていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-139">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="8eaa7-140">文字列の 0 から始まる 5 番目のインデックスを開始位置として、10 文字を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-140">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="8eaa7-141">Replace</span><span class="sxs-lookup"><span data-stu-id="8eaa7-141">Replace</span></span>

 <span data-ttu-id="8eaa7-142">また、<xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> メソッドを呼び出し、置換対象として空の文字列 (<xref:System.String.Empty?displayProperty=nameWithType>) を指定することで、文字列から指定した文字または部分文字列を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-142">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="8eaa7-143">文字列からすべてのコンマを削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8eaa7-143">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="8eaa7-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="8eaa7-144">See also</span></span>

- [<span data-ttu-id="8eaa7-145">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="8eaa7-145">Basic String Operations</span></span>](basic-string-operations.md)
