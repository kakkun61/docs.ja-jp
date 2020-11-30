---
title: '方法 : URL からプロトコルとポート番号を抽出する'
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
ms.openlocfilehash: ba512fbe4ebc7ec35ca590541fe5bf94d07c465d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734518"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="29deb-102">方法 : URL からプロトコルとポート番号を抽出する</span><span class="sxs-lookup"><span data-stu-id="29deb-102">How to: Extract a Protocol and Port Number from a URL</span></span>

<span data-ttu-id="29deb-103">次の例では、URL からプロトコルとポート番号を抽出します。</span><span class="sxs-lookup"><span data-stu-id="29deb-103">The following example extracts a protocol and port number from a URL.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="29deb-104">例</span><span class="sxs-lookup"><span data-stu-id="29deb-104">Example</span></span>  

 <span data-ttu-id="29deb-105">例では <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドを使用して、後にコロンとポート番号が続くプロトコルを返します。</span><span class="sxs-lookup"><span data-stu-id="29deb-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="29deb-106">この正規表現パターン `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="29deb-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="29deb-107">パターン</span><span class="sxs-lookup"><span data-stu-id="29deb-107">Pattern</span></span>|<span data-ttu-id="29deb-108">[説明]</span><span class="sxs-lookup"><span data-stu-id="29deb-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="29deb-109">文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="29deb-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="29deb-110">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="29deb-110">Match one or more word characters.</span></span> <span data-ttu-id="29deb-111">このグループに `proto` と名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="29deb-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="29deb-112">後に 2 つのスラッシュ記号が続くコロンと一致します。</span><span class="sxs-lookup"><span data-stu-id="29deb-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="29deb-113">スラッシュ記号以外の任意の文字の 1 回以上の (ただし、可能な限り少ない) 出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="29deb-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="29deb-114">後に 1 桁以上の文字が続くコロンの 0 回または 1 回の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="29deb-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="29deb-115">このグループに `port` と名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="29deb-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="29deb-116">スラッシュ記号に一致します。</span><span class="sxs-lookup"><span data-stu-id="29deb-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="29deb-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドは、正規表現パターンでキャプチャされた 2 つの名前付きグループの値を連結する、`${proto}${port}` 置換シーケンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="29deb-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="29deb-118">これは、<xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> プロパティによって返されたコレクション オブジェクトから取得した文字列を明示的に連結するための便利な代替です。</span><span class="sxs-lookup"><span data-stu-id="29deb-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="29deb-119">例では、<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドを 2 つの置換 `${proto}` と `${port}` とともに使用して、キャプチャされたグループを出力文字列に含めます。</span><span class="sxs-lookup"><span data-stu-id="29deb-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="29deb-120">代わりに、次のコードに示されているように、一致の <xref:System.Text.RegularExpressions.GroupCollection> オブジェクトから、キャプチャされたグループを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="29deb-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="29deb-121">参照</span><span class="sxs-lookup"><span data-stu-id="29deb-121">See also</span></span>

- [<span data-ttu-id="29deb-122">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="29deb-122">.NET Regular Expressions</span></span>](regular-expressions.md)
