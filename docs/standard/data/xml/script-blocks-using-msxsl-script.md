---
title: msxsl:script を使用したスクリプト ブロック
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: 3cb65142243d1f910ffd0fb85750ba62786d79f0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824701"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="c76e8-102">msxsl:script を使用したスクリプト ブロック</span><span class="sxs-lookup"><span data-stu-id="c76e8-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="c76e8-103"><xref:System.Xml.Xsl.XslCompiledTransform> クラスは、`msxsl:script` 要素を使用した埋め込みスクリプトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c76e8-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="c76e8-104">スタイル シートが読み込まれると、定義されているすべての関数は Code Document Object Model (CodeDOM) によって Microsoft intermediate language (MSIL) にコンパイルされ、実行時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="c76e8-105">埋め込みのスクリプト ブロックから生成されたアセンブリは、スタイル シートに対して生成されるアセンブリとは区別されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="c76e8-106">XSLT スクリプトの有効化</span><span class="sxs-lookup"><span data-stu-id="c76e8-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="c76e8-107">埋め込みスクリプトのサポートは、<xref:System.Xml.Xsl.XslCompiledTransform> クラスではオプションの XSLT 設定です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c76e8-108">スクリプトのサポートは既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="c76e8-108">Script support is disabled by default.</span></span> <span data-ttu-id="c76e8-109">スクリプトのサポートを有効にするには、<xref:System.Xml.Xsl.XsltSettings> プロパティを <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> に設定して `true` オブジェクトを作成し、そのオブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c76e8-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c76e8-110">XSLT スクリプトは、スクリプトのサポートが必要であり、完全に信頼された環境で作業している場合のみ有効にします。</span><span class="sxs-lookup"><span data-stu-id="c76e8-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="c76e8-111">msxsl:script 要素の定義</span><span class="sxs-lookup"><span data-stu-id="c76e8-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="c76e8-112">`msxsl:script` 要素は XSLT 1.0 勧告に対するマイクロソフトの拡張機能であり、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="c76e8-113">`msxsl` プレフィックスは `urn:schemas-microsoft-com:xslt` 名前空間 URI に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="c76e8-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="c76e8-114">スタイル シートには `xmlns:msxsl=urn:schemas-microsoft-com:xslt` という名前空間の宣言が必要です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="c76e8-115">`language` 属性は省略できます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-115">The `language` attribute is optional.</span></span> <span data-ttu-id="c76e8-116">その値は、埋め込みコード ブロックのコード言語です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="c76e8-117">言語は <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> メソッドを使用して、適切な CodeDOM コンパイラに対応付けられます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c76e8-118"><xref:System.Xml.Xsl.XslCompiledTransform> クラスは、適切なプロバイダーがコンピューターにインストールされ、machine.config ファイルの system.codedom セクションに登録されている限り、任意の Microsoft .NET 言語をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="c76e8-119">`language` 属性を指定しない場合、既定の言語は JScript です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="c76e8-120">言語名では大文字小文字が区別されないため、"JavaScript" と "javascript" は同じと見なされます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="c76e8-121">`implements-prefix` 属性は必須です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="c76e8-122">この属性は、名前空間を宣言し、それをスクリプト ブロックに関連付けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="c76e8-123">この属性の値は、名前空間を表すプレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="c76e8-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="c76e8-124">このプレフィックスは、スタイル シート内の任意の場所で定義できます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c76e8-125">`msxsl:script` 要素を使用するときは、どの言語でも、スクリプトを CDATA セクション内に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c76e8-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="c76e8-126">スクリプトは、その言語で使用する演算子、識別子、または区切り記号を含むことがあり、CDATA セクション内に配置しないと、誤って XML として解釈される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c76e8-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="c76e8-127">次の XML は、コードを配置できる CDATA セクションのテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="c76e8-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="c76e8-128">スクリプト関数</span><span class="sxs-lookup"><span data-stu-id="c76e8-128">Script Functions</span></span>  
 <span data-ttu-id="c76e8-129">関数は、`msxsl:script` 要素内で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="c76e8-130">関数が宣言されると、その関数はスクリプト ブロックに含まれます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="c76e8-131">スタイル シートには、相互に独立して機能する複数のスクリプト ブロックを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="c76e8-132">このため、1 つのスクリプト ブロック内で実行しているときに、別のスクリプト ブロックで定義した関数を呼び出すことはできません。ただし、そのブロックが同じ名前空間とスクリプト言語を持つように宣言されている場合は例外です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="c76e8-133">各スクリプト ブロックは独自の言語で記述でき、ブロックはその言語に対応するパーサーの文法規則に従って解析されるため、使われている言語の正しい構文を使用することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="c76e8-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="c76e8-134">たとえば、Microsoft C# スクリプト内では C# のコメント構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c76e8-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="c76e8-135">関数に渡される引数と戻り値の型は任意です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="c76e8-136">W3C XPath 型は共通言語ランタイム (CLR) 型のサブセットなので、XPath 型とは考えられない型については型変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="c76e8-137">W3C 型と等価な CLR 型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c76e8-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="c76e8-138">W3C 型</span><span class="sxs-lookup"><span data-stu-id="c76e8-138">W3C type</span></span>|<span data-ttu-id="c76e8-139">CLR 型</span><span class="sxs-lookup"><span data-stu-id="c76e8-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="c76e8-140">CLR 数値型は <xref:System.Double> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="c76e8-141"><xref:System.DateTime> 型は <xref:System.String> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="c76e8-142"><xref:System.Xml.XPath.IXPathNavigable> 型は <xref:System.Xml.XPath.XPathNavigator> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="c76e8-143">**XPathNavigator[]** は <xref:System.Xml.XPath.XPathNodeIterator> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="c76e8-144">その他の型はエラーになります。</span><span class="sxs-lookup"><span data-stu-id="c76e8-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="c76e8-145">名前空間とアセンブリのインポート</span><span class="sxs-lookup"><span data-stu-id="c76e8-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="c76e8-146"><xref:System.Xml.Xsl.XslCompiledTransform> クラスには、既定で `msxsl:script` 要素がサポートする一連のアセンブリと名前空間が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="c76e8-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="c76e8-147">しかし、アセンブリと名前空間を `msxsl:script` ブロックにインポートすることにより、事前定義の一覧にない 1 つの名前空間に属するクラスとメンバーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="c76e8-148">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="c76e8-148">Assemblies</span></span>  
 <span data-ttu-id="c76e8-149">次の 2 つのアセンブリは既定で参照されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-149">The following two assemblies are referenced by default:</span></span>  
  
- <span data-ttu-id="c76e8-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="c76e8-150">System.dll</span></span>  
  
- <span data-ttu-id="c76e8-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="c76e8-151">System.Xml.dll</span></span>  
  
- <span data-ttu-id="c76e8-152">Microsoft.VisualBasic.dll (スクリプト言語が VB の場合)</span><span class="sxs-lookup"><span data-stu-id="c76e8-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="c76e8-153">`msxsl:assembly` 要素を使用して、追加のアセンブリをインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="c76e8-154">これには、スタイル シートがコンパイルされたときのアセンブリも含まれます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="c76e8-155">`msxsl:assembly` 要素は、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="c76e8-156">`name` 属性にはアセンブリの名前が含まれ、`href` 属性にはアセンブリへのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="c76e8-157">アセンブリの名前は "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" などの完全な名前でも、"System.Web" などの短い名前でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="c76e8-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="c76e8-158">名前空間</span><span class="sxs-lookup"><span data-stu-id="c76e8-158">Namespaces</span></span>  
 <span data-ttu-id="c76e8-159">次の名前空間は既定で含まれます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-159">The following namespaces are included by default:</span></span>  
  
- <span data-ttu-id="c76e8-160">システム</span><span class="sxs-lookup"><span data-stu-id="c76e8-160">System</span></span>  
  
- <span data-ttu-id="c76e8-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="c76e8-161">System.Collection</span></span>  
  
- <span data-ttu-id="c76e8-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="c76e8-162">System.Text</span></span>  
  
- <span data-ttu-id="c76e8-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="c76e8-163">System.Text.RegularExpressions</span></span>  
  
- <span data-ttu-id="c76e8-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="c76e8-164">System.Xml</span></span>  
  
- <span data-ttu-id="c76e8-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="c76e8-165">System.Xml.Xsl</span></span>  
  
- <span data-ttu-id="c76e8-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="c76e8-166">System.Xml.XPath</span></span>  
  
- <span data-ttu-id="c76e8-167">Microsoft.VisualBasic (スクリプト言語が VB の場合)</span><span class="sxs-lookup"><span data-stu-id="c76e8-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="c76e8-168">`namespace` 属性を使用して、追加の名前空間のサポートを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="c76e8-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="c76e8-169">属性値は名前空間の名前です。</span><span class="sxs-lookup"><span data-stu-id="c76e8-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="c76e8-170">例</span><span class="sxs-lookup"><span data-stu-id="c76e8-170">Example</span></span>  
 <span data-ttu-id="c76e8-171">埋め込みスクリプトを使用して、半径が指定された円の円周を算出する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c76e8-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="c76e8-172">number.xml</span><span class="sxs-lookup"><span data-stu-id="c76e8-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="c76e8-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="c76e8-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="c76e8-174">出力</span><span class="sxs-lookup"><span data-stu-id="c76e8-174">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c76e8-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="c76e8-175">See also</span></span>

- [<span data-ttu-id="c76e8-176">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="c76e8-176">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="c76e8-177">動的なソース コードの生成とコンパイル</span><span class="sxs-lookup"><span data-stu-id="c76e8-177">Dynamic Source Code Generation and Compilation</span></span>](../../../framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
