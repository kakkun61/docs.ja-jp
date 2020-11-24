---
title: スタイル シート パラメーターと拡張オブジェクト用の XsltArgumentList
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: 6f0be433abcebed7f9da70225563a04170426314
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818207"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="f2f94-102">スタイル シート パラメーターと拡張オブジェクト用の XsltArgumentList</span><span class="sxs-lookup"><span data-stu-id="f2f94-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="f2f94-103"><xref:System.Xml.Xsl.XsltArgumentList> クラスには、XSLT (Extensible Stylesheet Language for Transformations) パラメーターと XSLT 拡張オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2f94-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="f2f94-104">これらのパラメーターと拡張オブジェクトは、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡すことで、スタイル シートから呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="f2f94-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2f94-105">.NET Framework 2.0 では、<xref:System.Xml.Xsl.XslTransform> クラスと <xref:System.Xml.Xsl.XsltArgumentList> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="f2f94-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="f2f94-106"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f2f94-107">詳しくは、「[XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](migrating-from-the-xsltransform-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f2f94-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f2f94-108"><xref:System.Xml.Xsl.XsltArgumentList> クラスには、XSLT パラメーターと XSLT 拡張オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2f94-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="f2f94-109">これらのパラメーターと拡張オブジェクトは、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡すことで、スタイル シートから呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="f2f94-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="f2f94-110">埋め込みスクリプトを使用するのではなく、オブジェクトを渡す利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
- <span data-ttu-id="f2f94-111">クラスをより効果的にカプセル化および再利用できます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-111">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="f2f94-112">スタイル シートを小さくすることができ、管理が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="f2f94-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
- <span data-ttu-id="f2f94-113">サポートされている <xref:System> 名前空間のセット内で定義されているもの以外の名前空間に属しているクラスのメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
- <span data-ttu-id="f2f94-114"><xref:System.Xml.XPath.XPathNodeIterator> を使用して結果ツリー フラグメントをスタイル シートに渡す操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="f2f94-115">XSLT スタイル シートのパラメーター</span><span class="sxs-lookup"><span data-stu-id="f2f94-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="f2f94-116">XSLT パラメーターを <xref:System.Xml.Xsl.XsltArgumentList> に追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="f2f94-117">パラメーターが追加された時点で、修飾名と名前空間 URI (Uniform Resource Identifier) がそのパラメーター オブジェクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="f2f94-118">パラメーター オブジェクトは、W3C (World Wide Web Consortium) 型に対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2f94-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="f2f94-119">対応する W3C 型、それと同等の .NET Framework のクラス (型)、および W3C 型が XPath (XML Path Language) 型または XSLT 型のどちらであるかを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-119">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="f2f94-120">W3C 型</span><span class="sxs-lookup"><span data-stu-id="f2f94-120">W3C Type</span></span>|<span data-ttu-id="f2f94-121">対応する .NET Framework クラス (型)</span><span class="sxs-lookup"><span data-stu-id="f2f94-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="f2f94-122">XPath 型または XSLT 型</span><span class="sxs-lookup"><span data-stu-id="f2f94-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="f2f94-123">String</span><span class="sxs-lookup"><span data-stu-id="f2f94-123">String</span></span>|<span data-ttu-id="f2f94-124">System.String</span><span class="sxs-lookup"><span data-stu-id="f2f94-124">System.String</span></span>|<span data-ttu-id="f2f94-125">XPath</span><span class="sxs-lookup"><span data-stu-id="f2f94-125">XPath</span></span>|  
|<span data-ttu-id="f2f94-126">ブール型</span><span class="sxs-lookup"><span data-stu-id="f2f94-126">Boolean</span></span>|<span data-ttu-id="f2f94-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="f2f94-127">System.Boolean</span></span>|<span data-ttu-id="f2f94-128">XPath</span><span class="sxs-lookup"><span data-stu-id="f2f94-128">XPath</span></span>|  
|<span data-ttu-id="f2f94-129">数値</span><span class="sxs-lookup"><span data-stu-id="f2f94-129">Number</span></span>|<span data-ttu-id="f2f94-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="f2f94-130">System.Double</span></span>|<span data-ttu-id="f2f94-131">XPath</span><span class="sxs-lookup"><span data-stu-id="f2f94-131">XPath</span></span>|  
|<span data-ttu-id="f2f94-132">Result Tree Fragment</span><span class="sxs-lookup"><span data-stu-id="f2f94-132">Result Tree Fragment</span></span>|<span data-ttu-id="f2f94-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f2f94-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="f2f94-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="f2f94-134">XSLT</span></span>|  
|<span data-ttu-id="f2f94-135">Node Set</span><span class="sxs-lookup"><span data-stu-id="f2f94-135">Node Set</span></span>|<span data-ttu-id="f2f94-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="f2f94-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="f2f94-137">XPath</span><span class="sxs-lookup"><span data-stu-id="f2f94-137">XPath</span></span>|  
  
 <span data-ttu-id="f2f94-138">パラメーター オブジェクトが上に示したクラスでない場合は、クラスの種類に応じて、Double または String に強制的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="f2f94-139">Int16、UInt16、Int32、UInt32、Int64、UInt64、Single、Decimal の各型は、強制的に Double に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="f2f94-140">その他すべての型は、`ToString` メソッドを使用して強制的に文字列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="f2f94-141">XSLT パラメーターを使用するために必要な処理</span><span class="sxs-lookup"><span data-stu-id="f2f94-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="f2f94-142"><xref:System.Xml.Xsl.XsltArgumentList> を作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> を使用してオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="f2f94-143">スタイル シートからパラメーターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="f2f94-144"><xref:System.Xml.Xsl.XsltArgumentList> を <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f2f94-145">例</span><span class="sxs-lookup"><span data-stu-id="f2f94-145">Example</span></span>  
 <span data-ttu-id="f2f94-146">算出された割引日を保持するパラメーターを <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> メソッドを使用して作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="f2f94-147">割引日は、発注日から 20 日後として算出されます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="f2f94-148">入力</span><span class="sxs-lookup"><span data-stu-id="f2f94-148">Input</span></span>  
 <span data-ttu-id="f2f94-149">order.xml</span><span class="sxs-lookup"><span data-stu-id="f2f94-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="f2f94-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="f2f94-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="f2f94-151">Output</span><span class="sxs-lookup"><span data-stu-id="f2f94-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>
   15% discount if paid by: 5/6/2001 5:01:15 PM
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="f2f94-152">XSLT 拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="f2f94-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="f2f94-153">XSLT 拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> に追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="f2f94-154">その時点で、修飾名と名前空間 URI がその拡張オブジェクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="f2f94-155">オブジェクトを追加する場合、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> の呼び出し元は、セキュリティ ポリシーで完全に信頼されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2f94-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="f2f94-156">呼び出し元の信頼性が低いと、処理は失敗します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="f2f94-157">オブジェクトは正常に追加されますが、正常に実行されるかどうかは保証されません。</span><span class="sxs-lookup"><span data-stu-id="f2f94-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="f2f94-158"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを呼び出すと、<xref:System.Xml.Xsl.XslTransform.Load%2A> の実行時に指定された証拠に基づいてアクセス許可が計算され、そのアクセス許可セットが変換処理全体に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="f2f94-159">拡張オブジェクトが、アクセス許可セットにないアクセス許可を必要とする処理を実行しようとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f2f94-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="f2f94-160">拡張オブジェクトが返すデータ型は、4 つの基本 XPath 型である数値、文字列、ブール、ノード セットのうちのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="f2f94-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="f2f94-161">XSLT 拡張オブジェクトを使用するために必要な処理</span><span class="sxs-lookup"><span data-stu-id="f2f94-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="f2f94-162"><xref:System.Xml.Xsl.XsltArgumentList> を作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> を使用して拡張オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="f2f94-163">スタイル シートから拡張オブジェクトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="f2f94-164"><xref:System.Xml.Xsl.XsltArgumentList> を <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f2f94-165">例</span><span class="sxs-lookup"><span data-stu-id="f2f94-165">Example</span></span>  
 <span data-ttu-id="f2f94-166">半径が指定された円の円周を算出する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f2f94-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="f2f94-167">入力</span><span class="sxs-lookup"><span data-stu-id="f2f94-167">Input</span></span>  
 <span data-ttu-id="f2f94-168">number.xml</span><span class="sxs-lookup"><span data-stu-id="f2f94-168">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>
```  
  
 <span data-ttu-id="f2f94-169">circle.xsl</span><span class="sxs-lookup"><span data-stu-id="f2f94-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="f2f94-170">Output</span><span class="sxs-lookup"><span data-stu-id="f2f94-170">Output</span></span>  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="f2f94-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2f94-171">See also</span></span>

- [<span data-ttu-id="f2f94-172">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="f2f94-172">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
