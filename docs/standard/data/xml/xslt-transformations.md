---
title: XSLT 変換
ms.date: 03/30/2017
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: b87768b402f92e0e59279aab0f0062e510fda2e6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818194"
---
# <a name="xslt-transformations"></a><span data-ttu-id="344c5-102">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="344c5-102">XSLT Transformations</span></span>
<span data-ttu-id="344c5-103">XSLT (Extensible Stylesheet Language Transformation) を使用すれば、ソース XML ドキュメントの内容を、形式や構造が異なる別のドキュメントに変換できます。</span><span class="sxs-lookup"><span data-stu-id="344c5-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="344c5-104">たとえば、XSLT を使用して、XML を Web サイトで使われる HTML に変換したり、アプリケーションが必要とするフィールドだけが含まれたドキュメントに変換したりできます。</span><span class="sxs-lookup"><span data-stu-id="344c5-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="344c5-105">この変換処理の仕様は、[W3C 勧告『XSL Transformations (XSLT) Version 1.0』](https://www.w3.org/TR/xslt-10/)で規定されています。</span><span class="sxs-lookup"><span data-stu-id="344c5-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="344c5-106"><xref:System.Xml.Xsl.XslCompiledTransform> クラスは .NET の XSLT プロセッサです。</span><span class="sxs-lookup"><span data-stu-id="344c5-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="344c5-107"><xref:System.Xml.Xsl.XslCompiledTransform> クラスは、[W3C 勧告『XSLT 1.0』](https://www.w3.org/TR/xslt-10/)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="344c5-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="344c5-108">.NET Framework Version 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="344c5-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="344c5-109"><xref:System.Xml.Xsl.XslCompiledTransform> クラスが XSLT エンジンの新しい実装です。</span><span class="sxs-lookup"><span data-stu-id="344c5-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="344c5-110">このクラスは、パフォーマンスが向上しており、新しいセキュリティ機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="344c5-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="344c5-111">XSLT アプリケーションの作成には <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用することが推奨されています。</span><span class="sxs-lookup"><span data-stu-id="344c5-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="344c5-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="344c5-112">In This Section</span></span>  
 [<span data-ttu-id="344c5-113">XslCompiledTransform クラスの使用</span><span class="sxs-lookup"><span data-stu-id="344c5-113">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="344c5-114"><xref:System.Xml.Xsl.XslCompiledTransform> クラスの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="344c5-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="344c5-115">XslTransform クラスからの移行</span><span class="sxs-lookup"><span data-stu-id="344c5-115">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="344c5-116"><xref:System.Xml.Xsl.XslTransform> クラスからコードを移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="344c5-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="344c5-117">XSLT コンパイラ (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="344c5-117">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="344c5-118">XSLT コンパイラの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="344c5-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="344c5-119">XslTransform クラスを使用した XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="344c5-119">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="344c5-120"><xref:System.Xml.Xsl.XslTransform> クラスの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="344c5-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="344c5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="344c5-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="344c5-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="344c5-122">Related Sections</span></span>  
 [<span data-ttu-id="344c5-123">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="344c5-123">XML Documents and Data</span></span>](index.md)
