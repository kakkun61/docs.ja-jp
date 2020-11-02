---
title: .NET でのその他の文字列の解析
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 5a8afde40dddd69a9648439be5c0f232db23b37b
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889011"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="edfb7-102">.NET でのその他の文字列の解析</span><span class="sxs-lookup"><span data-stu-id="edfb7-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="edfb7-103">数値および <xref:System.DateTime> 文字列だけでなく、<xref:System.Char>、<xref:System.Boolean>、<xref:System.Enum> 型を表す文字列をデータ型に解析することもできます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="edfb7-104">Char</span><span class="sxs-lookup"><span data-stu-id="edfb7-104">Char</span></span>  
 <span data-ttu-id="edfb7-105">**Char** データ型に関連付けられている静的解析メソッドは、1 つの文字を含む文字列をUnicode 値に変換するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="edfb7-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="edfb7-106">次のコードの例では、文字列を Unicode 文字に解析します。</span><span class="sxs-lookup"><span data-stu-id="edfb7-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="edfb7-107">Boolean</span><span class="sxs-lookup"><span data-stu-id="edfb7-107">Boolean</span></span>  
 <span data-ttu-id="edfb7-108">**Boolean** データ型には、 **Parse** メソッドが含まれ、Boolean 値を示す文字列を実際の **Boolean** 型に変換するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="edfb7-109">このメソッドは大文字と小文字を区別しません。また、"True" または "False" を含む文字列を正常に解析することができます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="edfb7-110">**Boolean** 型に関連付けられる **Parse** メソッドは、空白で囲まれた文字列を解析することもできます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="edfb7-111">その他の文字列が渡された場合、<xref:System.FormatException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="edfb7-112">次のコードの例では、 **Parse** メソッドを使用して、文字列を Boolean 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="edfb7-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="edfb7-113">Enumeration</span><span class="sxs-lookup"><span data-stu-id="edfb7-113">Enumeration</span></span>  
 <span data-ttu-id="edfb7-114">静的 **Parse** メソッドを使用して、列挙型を文字列の値に初期化できます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="edfb7-115">このメソッドでは、解析している列挙型、解析する文字列、および解析が大文字小文字を区別するかどうかを示す省略可能な Boolean フラグを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="edfb7-116">解析している文字列は、コンマで区切られた複数の値を含めることができます。これは、1 つ以上の空の領域 (空白とも呼ばれます) が前後にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="edfb7-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="edfb7-117">文字列に複数の値がある場合、返されたオブジェクトの値は、ビット演算 OR 演算と組み合わされたすべての指定された値の値です。</span><span class="sxs-lookup"><span data-stu-id="edfb7-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="edfb7-118">次の例では、 **Parse** メソッドを使用して、文字列形式を列挙値に変換します。</span><span class="sxs-lookup"><span data-stu-id="edfb7-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="edfb7-119"><xref:System.DayOfWeek> 列挙体は、文字列から **Thursday** に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="edfb7-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="edfb7-120">参照</span><span class="sxs-lookup"><span data-stu-id="edfb7-120">See also</span></span>

- [<span data-ttu-id="edfb7-121">文字列の解析</span><span class="sxs-lookup"><span data-stu-id="edfb7-121">Parsing Strings</span></span>](parsing-strings.md)
- [<span data-ttu-id="edfb7-122">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="edfb7-122">Formatting Types</span></span>](formatting-types.md)
- [<span data-ttu-id="edfb7-123">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="edfb7-123">Type Conversion in the .NET</span></span>](type-conversion.md)
