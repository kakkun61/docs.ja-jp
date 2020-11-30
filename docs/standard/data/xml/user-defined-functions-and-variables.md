---
title: ユーザー定義の関数と変数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: c1f519dd539a266d61945ad221bccceaa1361779
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675621"
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="be211-102">ユーザー定義の関数と変数</span><span class="sxs-lookup"><span data-stu-id="be211-102">User Defined Functions and Variables</span></span>

<span data-ttu-id="be211-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> データの操作に使用されるメソッドのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="be211-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="be211-104">XPath クエリ式で使用する拡張関数および変数を実装することで、標準の XPath 関数を補完できます。</span><span class="sxs-lookup"><span data-stu-id="be211-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="be211-105"><xref:System.Xml.XPath.XPathExpression.SetContext%2A> メソッドは、<xref:System.Xml.Xsl.XsltContext> から派生した、ユーザー定義のコンテキストを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="be211-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="be211-106">ユーザー定義の関数は、カスタム コンテキストで解決されます。</span><span class="sxs-lookup"><span data-stu-id="be211-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="be211-107">拡張関数および変数は、XML インジェクション攻撃を防止するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="be211-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="be211-108">このようなシナリオでは、処理命令と連結された生の入力としてではなく、ユーザー入力がカスタム変数に割り当てられ、拡張関数で処理されます。</span><span class="sxs-lookup"><span data-stu-id="be211-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="be211-109">拡張関数および変数にユーザー入力が含まれて、設計者が意図したように、XML データに対してだけ機能します。</span><span class="sxs-lookup"><span data-stu-id="be211-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="be211-110">拡張関数および変数を使用するには、カスタム クラス <xref:System.Xml.Xsl.XsltContext> を、拡張関数および変数をサポートする <xref:System.Xml.Xsl.IXsltContextFunction> インターフェイスおよび <xref:System.Xml.Xsl.IXsltContextVariable> インターフェイスと共に実装します。</span><span class="sxs-lookup"><span data-stu-id="be211-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="be211-111"><xref:System.Xml.XPath.XPathExpression> は、ユーザー入力をその <xref:System.Xml.Xsl.XsltArgumentList> と共にカスタム <xref:System.Xml.Xsl.XsltContext> に追加します。</span><span class="sxs-lookup"><span data-stu-id="be211-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="be211-112"><xref:System.Xml.XPath.XPathExpression> は、式で識別されるノードを見つけて処理するのに <xref:System.Xml.XPath.XPathNavigator> が使用する、コンパイル済みクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="be211-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="be211-113"><xref:System.Xml.Xsl.XsltContext> から派生したカスタム コンテキスト クラスの実装を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="be211-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="be211-114">コード コメントは、クラスのメンバーと、カスタム関数でのそれらのメンバーの使用法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="be211-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="be211-115">このコードの後に、関数および変数の実装と、それらの実装を使用するサンプル アプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="be211-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="be211-116">次のコードでは <xref:System.Xml.Xsl.IXsltContextFunction> を実装します。</span><span class="sxs-lookup"><span data-stu-id="be211-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="be211-117"><xref:System.Xml.Xsl.IXsltContextFunction> を実装するクラスは、ユーザー定義の関数を解決し、実行します。</span><span class="sxs-lookup"><span data-stu-id="be211-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="be211-118">この例では、宣言 `private int CountChar(string title, char charTocount)` で識別される関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="be211-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="be211-119">コード コメントでは、クラスのメンバーを示しています。</span><span class="sxs-lookup"><span data-stu-id="be211-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="be211-120">次のコードでは <xref:System.Xml.Xsl.IXsltContextVariable> を実装します。</span><span class="sxs-lookup"><span data-stu-id="be211-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="be211-121">このクラスは、実行時に XPath クエリ式内のユーザー定義変数への参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="be211-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="be211-122">このクラスのインスタンスは、カスタム クラス <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> の、オーバーライドされた <xref:System.Xml.Xsl.XsltContext> メソッドによって作成され、返されます。</span><span class="sxs-lookup"><span data-stu-id="be211-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="be211-123">コード コメントでは、クラスのメンバーを示しています。</span><span class="sxs-lookup"><span data-stu-id="be211-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="be211-124">前のクラス定義がスコープ内にある次のコードでは、カスタム関数を使用して `Tasks.xml` ドキュメントの要素内の文字をカウントします。</span><span class="sxs-lookup"><span data-stu-id="be211-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="be211-125">コード コメントでは、カスタム関数をコンパイルし、それを `Tasks.xml` ドキュメントに対して実行するコードについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="be211-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="be211-126">この例では、次の XML データを使用しています。</span><span class="sxs-lookup"><span data-stu-id="be211-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
