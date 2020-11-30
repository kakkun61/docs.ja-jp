---
title: XSLT 拡張オブジェクト
ms.date: 03/30/2017
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 0e874bb7679854b75a07eb452e47eba0d30807a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720790"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="5714f-102">XSLT 拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5714f-102">XSLT Extension Objects</span></span>

<span data-ttu-id="5714f-103">拡張オブジェクトは、スタイル シートの機能を拡張する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5714f-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="5714f-104">拡張オブジェクトは、<xref:System.Xml.Xsl.XsltArgumentList> クラスによって維持されます。</span><span class="sxs-lookup"><span data-stu-id="5714f-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="5714f-105">埋め込みスクリプトではなく、拡張オブジェクトを使用する利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5714f-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="5714f-106">クラスをより効果的にカプセル化および再利用できます。</span><span class="sxs-lookup"><span data-stu-id="5714f-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="5714f-107">スタイル シートを小さくすることができ、管理が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="5714f-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="5714f-108">XSLT 拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトに追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="5714f-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="5714f-109">その時点で、修飾名と名前空間 URI がその拡張オブジェクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="5714f-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5714f-110"><xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを呼び出すには、FullTrust アクセス許可セットが必要です。</span><span class="sxs-lookup"><span data-stu-id="5714f-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="5714f-111">詳細については、「[コード アクセス セキュリティ](../../../framework/misc/code-access-security.md)」および「[名前付きアクセス許可セット](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5714f-111">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="5714f-112">拡張オブジェクトが返すデータ型は、4 つの基本 XPath データ型である `number`、`string`、`Boolean`、および `node set` のうちのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="5714f-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="5714f-113">現在、`params` キーワードを使用して定義されるメソッド (不特定数のパラメーターを渡すことができる) は、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="5714f-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5714f-114">`params` キーワードを使用して定義されたメソッドを使用する XSLT スタイル シートは、正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="5714f-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="5714f-115">詳細については、[params](../../../csharp/language-reference/keywords/params.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5714f-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="5714f-116">XSLT 拡張オブジェクトを使用するために必要な処理</span><span class="sxs-lookup"><span data-stu-id="5714f-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="5714f-117"><xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用して拡張オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="5714f-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="5714f-118">スタイル シートから拡張オブジェクトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5714f-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="5714f-119"><xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="5714f-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5714f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5714f-120">See also</span></span>

- [<span data-ttu-id="5714f-121">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="5714f-121">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="5714f-122">XSLT のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="5714f-122">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
