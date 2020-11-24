---
title: カルチャを認識しない文字列操作の実行
ms.date: 08/22/2018
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 868f36a1025f0b121a8765edf50bb42679736240
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829766"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="98b6b-102">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="98b6b-102">Performing culture-insensitive string operations</span></span>

<span data-ttu-id="98b6b-103">カルチャを認識する文字列操作を既定で実行するほとんどの .NET メソッドには、<xref:System.Globalization.CultureInfo> パラメーターを渡すことによって使用するカルチャを明示的に指定できるメソッド オーバーロードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="98b6b-103">Most .NET methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="98b6b-104">これらのオーバーロードによって、大文字小文字のマップおよび並べ替え規則のカルチャによる違いを排除し、カルチャを認識しない結果を確保できます。</span><span class="sxs-lookup"><span data-stu-id="98b6b-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="98b6b-105">このセクションの次の記事では、既定ではカルチャを認識する .NET のメソッドを使用し、カルチャを認識しない文字列操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98b6b-105">This section provides the following articles to demonstrate how to perform culture-insensitive string operations using .NET methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98b6b-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="98b6b-106">In this section</span></span>  
 [<span data-ttu-id="98b6b-107">カルチャを認識しない文字列比較の実行</span><span class="sxs-lookup"><span data-stu-id="98b6b-107">Performing Culture-Insensitive String Comparisons</span></span>](performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="98b6b-108"><xref:System.String.Compare%2A?displayProperty=nameWithType> メソッドと <xref:System.String.CompareTo%2A?displayProperty=nameWithType> メソッドを使用してカルチャを認識しない文字列比較を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98b6b-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="98b6b-109">カルチャを認識しない大文字と小文字の変更の実行</span><span class="sxs-lookup"><span data-stu-id="98b6b-109">Performing Culture-Insensitive Case Changes</span></span>](performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="98b6b-110"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType>、<xref:System.Char.ToLower%2A?displayProperty=nameWithType> の各メソッドを使用してカルチャを認識しない大文字と小文字の変換を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98b6b-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="98b6b-111">カルチャを認識しないコレクションの操作の実行</span><span class="sxs-lookup"><span data-stu-id="98b6b-111">Performing Culture-Insensitive String Operations in Collections</span></span>](performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="98b6b-112"><xref:System.Collections.CaseInsensitiveComparer>、<xref:System.Collections.CaseInsensitiveHashCodeProvider> クラス、<xref:System.Collections.SortedList>、<xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>、<xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> を使用して、コレクションでカルチャを認識しない操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98b6b-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="98b6b-113">カルチャを認識しない配列の操作の実行</span><span class="sxs-lookup"><span data-stu-id="98b6b-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="98b6b-114"><xref:System.Array.Sort%2A?displayProperty=nameWithType> メソッドと <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> メソッドを使用してカルチャを認識しない配列の操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98b6b-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="98b6b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="98b6b-115">Related sections</span></span>  
 [<span data-ttu-id="98b6b-116">カルチャを認識しない文字列操作</span><span class="sxs-lookup"><span data-stu-id="98b6b-116">Culture-Insensitive String Operations</span></span>](culture-insensitive-string-operations.md)  
 <span data-ttu-id="98b6b-117">文字列操作を実行する際にカルチャに注意する理由について説明し、カルチャを認識する操作を実行するときとカルチャを認識しない操作を実行するときのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="98b6b-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="98b6b-118">参照</span><span class="sxs-lookup"><span data-stu-id="98b6b-118">See also</span></span>

- [<span data-ttu-id="98b6b-119">並べ替え重みテーブル (Windows システム上の .NET 用)</span><span class="sxs-lookup"><span data-stu-id="98b6b-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="98b6b-120">デフォルト Unicode 照合基本テーブル (Linux と macOS 上の .NET Core 用)</span><span class="sxs-lookup"><span data-stu-id="98b6b-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
