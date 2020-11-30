---
title: XSLT 処理中の外部リソースの解決
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 5d50711eda266cecdb817c778f04aa845fa4c342
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686645"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="777ce-102">XSLT 処理中の外部リソースの解決</span><span class="sxs-lookup"><span data-stu-id="777ce-102">Resolving External Resources During XSLT Processing</span></span>

<span data-ttu-id="777ce-103">XSLT 変換中には、外部リソースの解決が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="777ce-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="777ce-104">XmlResolver クラスの使い方</span><span class="sxs-lookup"><span data-stu-id="777ce-104">Using the XmlResolver Class</span></span>  

 <span data-ttu-id="777ce-105">外部リソースを解決するには、<xref:System.Xml.XmlResolver> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="777ce-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="777ce-106">XSLT 処理中に <xref:System.Xml.XmlResolver> が使用される場合を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="777ce-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="777ce-107">XSLT タスク</span><span class="sxs-lookup"><span data-stu-id="777ce-107">XSLT task</span></span>|<span data-ttu-id="777ce-108">XmlResolver が使用される場合</span><span class="sxs-lookup"><span data-stu-id="777ce-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="777ce-109">スタイル シートのコンパイル。</span><span class="sxs-lookup"><span data-stu-id="777ce-109">Compile the style sheet.</span></span>|<span data-ttu-id="777ce-110">スタイル シートの URI の解決。</span><span class="sxs-lookup"><span data-stu-id="777ce-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="777ce-111">および</span><span class="sxs-lookup"><span data-stu-id="777ce-111">-and-</span></span><br /><br /> <span data-ttu-id="777ce-112">`xsl:import` 要素または `xsl:include` 要素の URI リファレンスの解決。</span><span class="sxs-lookup"><span data-stu-id="777ce-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="777ce-113">スタイル シートの実行。</span><span class="sxs-lookup"><span data-stu-id="777ce-113">Execute the style sheet.</span></span>|<span data-ttu-id="777ce-114">コンテキスト ドキュメントの URI の解決。</span><span class="sxs-lookup"><span data-stu-id="777ce-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="777ce-115">および</span><span class="sxs-lookup"><span data-stu-id="777ce-115">-and-</span></span><br /><br /> <span data-ttu-id="777ce-116">XSLT の `document()` 関数での URI リファレンスの解決。</span><span class="sxs-lookup"><span data-stu-id="777ce-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="777ce-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドおよび <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドには、<xref:System.Xml.XmlResolver> オブジェクトを引数の 1 つとして受け取るオーバーロードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="777ce-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="777ce-118"><xref:System.Xml.XmlResolver> を指定しない場合は、資格情報を持たない既定の <xref:System.Xml.XmlUrlResolver> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="777ce-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="777ce-119"><xref:System.Xml.XmlResolver> オブジェクトを使用する場合の説明を次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="777ce-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="777ce-120">XSLT 処理で認証が必要なネットワーク リソースにアクセスする必要がある場合、必要な資格情報に対して <xref:System.Xml.XmlResolver> を使用します。</span><span class="sxs-lookup"><span data-stu-id="777ce-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="777ce-121">XSLT 処理がアクセスできるリソースを制限する場合、適切なアクセス許可セットに対して <xref:System.Xml.XmlSecureResolver> を使用します。</span><span class="sxs-lookup"><span data-stu-id="777ce-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="777ce-122">制御対象外の (信頼できない) リソースを開く場合には、<xref:System.Xml.XmlSecureResolver> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="777ce-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="777ce-123">動作をカスタマイズする場合は、独自の <xref:System.Xml.XmlResolver> クラスを実装し、これを使用してリソースを解決することができます。</span><span class="sxs-lookup"><span data-stu-id="777ce-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="777ce-124">外部リソースにアクセスできないようにする場合は、<xref:System.Xml.XmlResolver> の引数に `null` を指定します。</span><span class="sxs-lookup"><span data-stu-id="777ce-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="777ce-125">例</span><span class="sxs-lookup"><span data-stu-id="777ce-125">Example</span></span>  

 <span data-ttu-id="777ce-126">ネットワーク リソースに格納されているスタイル シートをコンパイルする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="777ce-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="777ce-127"><xref:System.Xml.XmlUrlResolver> オブジェクトには、スタイル シートにアクセスするのに必要な資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="777ce-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="777ce-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="777ce-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="777ce-129">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="777ce-129">XSLT Transformations</span></span>](xslt-transformations.md)
