---
title: スキーマのノード型および構造を推論するときの規則
ms.date: 03/30/2017
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
ms.openlocfilehash: 16636460c6635852bb68b4821fab5aa99b07413c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823577"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a><span data-ttu-id="f5bb1-102">スキーマのノード型および構造を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="f5bb1-102">Rules for Inferring Schema Node Types and Structure</span></span>
<span data-ttu-id="f5bb1-103">このトピックでは、スキーマ推論プロセスで、XML ドキュメント内のノード型を XML スキーマ定義言語 (XSD) 構造に変換する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-103">This topic describes how the schema inference process translates the node types in an XML document to an XML Schema definition language (XSD) structure.</span></span>  
  
## <a name="element-inference-rules"></a><span data-ttu-id="f5bb1-104">要素を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="f5bb1-104">Element Inference Rules</span></span>  
 <span data-ttu-id="f5bb1-105">このセクションでは、要素宣言を推論するときの規則を説明します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-105">This section describes the inference rules for element declarations.</span></span> <span data-ttu-id="f5bb1-106">推論される要素宣言には 8 つの構造があります。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-106">There are eight structures of element declarations that will be inferred:</span></span>  
  
1. <span data-ttu-id="f5bb1-107">単純型の要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-107">Element of simple type</span></span>  
  
2. <span data-ttu-id="f5bb1-108">空要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-108">Empty element</span></span>  
  
3. <span data-ttu-id="f5bb1-109">属性を持つ空要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-109">Empty element with attributes</span></span>  
  
4. <span data-ttu-id="f5bb1-110">属性と単純内容を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-110">Element with attributes and simple content</span></span>  
  
5. <span data-ttu-id="f5bb1-111">子要素のシーケンスを持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-111">Element with a sequence of child elements</span></span>  
  
6. <span data-ttu-id="f5bb1-112">子要素のシーケンスと属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-112">Element with a sequence of child elements and attributes</span></span>  
  
7. <span data-ttu-id="f5bb1-113">子要素のシーケンスと choice を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-113">Element with a sequence of choices of child elements</span></span>  
  
8. <span data-ttu-id="f5bb1-114">子要素のシーケンスと choice を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-114">Element with a sequence of choices of child elements and attributes</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5bb1-115">すべての `complexType` 宣言は匿名型として推論されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-115">All `complexType` declarations are inferred as anonymous types.</span></span> <span data-ttu-id="f5bb1-116">推論されるグローバル要素はルート要素だけであり、その他すべての要素はローカル要素です。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-116">The only global element inferred is the root element; all other elements are local.</span></span>  
  
 <span data-ttu-id="f5bb1-117">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-117">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
### <a name="simple-typed-element"></a><span data-ttu-id="f5bb1-118">単純型要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-118">Simple Typed Element</span></span>  
 <span data-ttu-id="f5bb1-119"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-119">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-120">太字になっている要素は、単純型要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-120">The bolded element shows the schema inferred for the simple type element.</span></span>  
  
 <span data-ttu-id="f5bb1-121">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-121">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-122">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-122">XML</span></span>|<span data-ttu-id="f5bb1-123">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-123">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a><span data-ttu-id="f5bb1-124">空の要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-124">Empty Element</span></span>  
 <span data-ttu-id="f5bb1-125"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-125">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-126">太字になっている要素は、空要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-126">The bolded element shows the schema inferred for the empty element.</span></span>  
  
 <span data-ttu-id="f5bb1-127">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-127">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-128">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-128">XML</span></span>|<span data-ttu-id="f5bb1-129">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-129">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a><span data-ttu-id="f5bb1-130">属性を持つ空要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-130">Empty Element with Attributes</span></span>  
 <span data-ttu-id="f5bb1-131"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-131">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-132">太字になっている要素は、属性を持つ空要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-132">The bolded elements show the schema inferred for the empty element with attributes.</span></span>  
  
 <span data-ttu-id="f5bb1-133">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-133">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-134">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-134">XML</span></span>|<span data-ttu-id="f5bb1-135">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-135">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a><span data-ttu-id="f5bb1-136">属性と単純内容を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-136">Element with Attributes and Simple Content</span></span>  
 <span data-ttu-id="f5bb1-137"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-137">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-138">太字になっている要素は、属性と単純内容を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-138">The bolded elements show the schema inferred for an element with attributes and simple content.</span></span>  
  
 <span data-ttu-id="f5bb1-139">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-139">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-140">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-140">XML</span></span>|<span data-ttu-id="f5bb1-141">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-141">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a><span data-ttu-id="f5bb1-142">子要素のシーケンスを持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-142">Element with a Sequence of Child Elements</span></span>  
 <span data-ttu-id="f5bb1-143"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-143">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-144">太字になっている要素は、子要素のシーケンスを持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-144">The bolded elements show the schema inferred for an element with a sequence of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5bb1-145">要素が子要素を 1 つしか持っていない場合でも、子要素はシーケンスとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-145">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="f5bb1-146">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-146">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-147">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-147">XML</span></span>|<span data-ttu-id="f5bb1-148">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-148">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a><span data-ttu-id="f5bb1-149">子要素のシーケンスと属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-149">Element with a Sequence of Child Elements and Attributes</span></span>  
 <span data-ttu-id="f5bb1-150"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-150">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-151">太字になっている要素は、子要素のシーケンスと属性を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-151">The bolded elements show the schema inferred for an element with a sequence of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5bb1-152">要素が子要素を 1 つしか持っていない場合でも、子要素はシーケンスとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-152">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="f5bb1-153">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-153">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-154">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-154">XML</span></span>|<span data-ttu-id="f5bb1-155">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-155">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a><span data-ttu-id="f5bb1-156">子要素のシーケンスと choice を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-156">Element with a Sequence and Choices of Child Elements</span></span>  
 <span data-ttu-id="f5bb1-157"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-157">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-158">太字になっているスキーマは、子要素のシーケンスと choice を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-158">The bolded elements show the schema inferred for an element with a sequence and choice of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5bb1-159">`maxOccurs` 要素の `xs:choice` 属性は、推論されるスキーマでは `"unbounded"` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-159">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="f5bb1-160">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-160">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-161">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-161">XML</span></span>|<span data-ttu-id="f5bb1-162">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-162">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a><span data-ttu-id="f5bb1-163">子要素のシーケンスと choice および属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="f5bb1-163">Element with a Sequence and Choice of Child Elements and Attributes</span></span>  
 <span data-ttu-id="f5bb1-164"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-164">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="f5bb1-165">太字になっている要素は、子要素のシーケンスと choice および属性を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-165">The bolded elements show the schema inferred for an element with a sequence and choice of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5bb1-166">`maxOccurs` 要素の `xs:choice` 属性は、推論されるスキーマでは `"unbounded"` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-166">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="f5bb1-167">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-167">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="f5bb1-168">XML</span><span class="sxs-lookup"><span data-stu-id="f5bb1-168">XML</span></span>|<span data-ttu-id="f5bb1-169">Schema</span><span class="sxs-lookup"><span data-stu-id="f5bb1-169">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a><span data-ttu-id="f5bb1-170">属性の処理</span><span class="sxs-lookup"><span data-stu-id="f5bb1-170">Attribute Processing</span></span>  
 <span data-ttu-id="f5bb1-171">ノード内で新しい属性が検出されるたびに、その属性は推論されるノードの定義に `use="required"` として追加されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-171">Whenever a new attribute is encountered within a node, it is added to the inferred definition of the node with `use="required"`.</span></span> <span data-ttu-id="f5bb1-172">そのインスタンスで同じノードが再び検出されると、推論プロセスでは、現在のインスタンスの属性と、既に推論されている属性を比較します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-172">The next time the same node is found in the instance, the inference process will compare attributes of the current instance with the ones already inferred.</span></span> <span data-ttu-id="f5bb1-173">既に推論されている属性の一部がインスタンスにない場合は、属性の定義に `use="optional"` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-173">If some of the already inferred ones are missing in the instance, `use="optional"` is added to the attribute definition.</span></span> <span data-ttu-id="f5bb1-174">新しい属性は、既存の宣言に `use="optional"` として追加されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-174">New attributes are added to existing declarations with `use="optional"`.</span></span>  
  
### <a name="occurrence-constraints"></a><span data-ttu-id="f5bb1-175">出現回数に関する制約</span><span class="sxs-lookup"><span data-stu-id="f5bb1-175">Occurrence Constraints</span></span>  
 <span data-ttu-id="f5bb1-176">スキーマ推論プロセスでは、推論されるスキーマのコンポーネントに対して、値が `minOccurs` または `maxOccurs` の `"0"` 属性と、値が `"1"` または `"1"` の `"unbounded"` 属性が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-176">During the schema inference process, the `minOccurs` and `maxOccurs` attributes are generated, for inferred components of a schema, with the values `"0"` or `"1"` and `"1"` or `"unbounded"`.</span></span> <span data-ttu-id="f5bb1-177">値 `"1"` および `"unbounded"` は、値 `"0"` および `"1"` では XML ドキュメントを検証できない場合にのみ使われます (たとえば、`MinOccurs="0"` では要素を正確に記述できない場合は、`minOccurs="1"` が使われます)。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-177">The values `"1"` and `"unbounded"` are used only when the values `"0"` and `"1"` cannot validate the XML document (for example, if `MinOccurs="0"` does not accurately describe an element, `minOccurs="1"` is used).</span></span>  
  
### <a name="mixed-content"></a><span data-ttu-id="f5bb1-178">混合コンテンツ</span><span class="sxs-lookup"><span data-stu-id="f5bb1-178">Mixed Content</span></span>  
 <span data-ttu-id="f5bb1-179">テキストに要素が混じっているなど、要素に混合コンテンツが含まれている場合は、推論される複合型の定義に対して `mixed="true"` 属性が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-179">If an element contains mixed content (for example text interspersed with elements), the `mixed="true"` attribute is generated for the inferred complex type definition.</span></span>  
  
## <a name="other-node-type-inference-rules"></a><span data-ttu-id="f5bb1-180">その他のノードの型推論規則</span><span class="sxs-lookup"><span data-stu-id="f5bb1-180">Other Node Type Inference Rules</span></span>  
 <span data-ttu-id="f5bb1-181">処理命令、コメント、エンティティ参照、CDATA、ドキュメント型、名前空間の各ノード型に関する推論の規則を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-181">The following table describes the inference rules for processing instruction, comment, entity reference, CDATA, document type, and namespace nodes.</span></span>  
  
|<span data-ttu-id="f5bb1-182">ノード型</span><span class="sxs-lookup"><span data-stu-id="f5bb1-182">Node Type</span></span>|<span data-ttu-id="f5bb1-183">変換</span><span class="sxs-lookup"><span data-stu-id="f5bb1-183">Translation</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5bb1-184">処理命令</span><span class="sxs-lookup"><span data-stu-id="f5bb1-184">Processing instruction</span></span>|<span data-ttu-id="f5bb1-185">無視されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-185">Ignored.</span></span>|  
|<span data-ttu-id="f5bb1-186">コメント</span><span class="sxs-lookup"><span data-stu-id="f5bb1-186">Comment</span></span>|<span data-ttu-id="f5bb1-187">無視されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-187">Ignored.</span></span>|  
|<span data-ttu-id="f5bb1-188">エンティティ参照</span><span class="sxs-lookup"><span data-stu-id="f5bb1-188">Entity reference</span></span>|<span data-ttu-id="f5bb1-189"><xref:System.Xml.Schema.XmlSchemaInference> クラスではエンティティ参照を処理しません。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-189">The <xref:System.Xml.Schema.XmlSchemaInference> class does not handle entity references.</span></span> <span data-ttu-id="f5bb1-190">XML ドキュメントにエンティティ参照が含まれている場合は、エンティティを展開するリーダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-190">If an XML document contains entity references, you need to use a reader that expands the entities.</span></span> <span data-ttu-id="f5bb1-191">たとえば、<xref:System.Xml.XmlTextReader> プロパティを <xref:System.Xml.XmlTextReader.EntityHandling%2A> に設定した <xref:System.Xml.EntityHandling.ExpandEntities> をパラメーターとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-191">For example, you can pass an <xref:System.Xml.XmlTextReader> with the <xref:System.Xml.XmlTextReader.EntityHandling%2A> property set to <xref:System.Xml.EntityHandling.ExpandEntities> as a parameter.</span></span> <span data-ttu-id="f5bb1-192">エンティティ参照が検出されたにもかかわらず、リーダーがエンティティを展開しない場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-192">If entity references are encountered and the reader does not expand entities, an exception is throw.</span></span>|  
|<span data-ttu-id="f5bb1-193">CDATA</span><span class="sxs-lookup"><span data-stu-id="f5bb1-193">CDATA</span></span>|<span data-ttu-id="f5bb1-194">XML ドキュメント内のすべての `<![CDATA[ … ]]` セクションが `xs:string` として推論されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-194">Any `<![CDATA[ … ]]` sections in an XML document will be inferred as `xs:string`.</span></span>|  
|<span data-ttu-id="f5bb1-195">ドキュメント型</span><span class="sxs-lookup"><span data-stu-id="f5bb1-195">Document type</span></span>|<span data-ttu-id="f5bb1-196">無視されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-196">Ignored.</span></span>|  
|<span data-ttu-id="f5bb1-197">名前空間</span><span class="sxs-lookup"><span data-stu-id="f5bb1-197">Namespaces</span></span>|<span data-ttu-id="f5bb1-198">無視されます。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-198">Ignored.</span></span>|  
  
 <span data-ttu-id="f5bb1-199">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5bb1-199">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bb1-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5bb1-200">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="f5bb1-201">XML スキーマ オブジェクト モデル (SOM)</span><span class="sxs-lookup"><span data-stu-id="f5bb1-201">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="f5bb1-202">XML スキーマの推論</span><span class="sxs-lookup"><span data-stu-id="f5bb1-202">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="f5bb1-203">XML ドキュメントからのスキーマの推論</span><span class="sxs-lookup"><span data-stu-id="f5bb1-203">Inferring Schemas from XML Documents</span></span>](inferring-schemas-from-xml-documents.md)
- [<span data-ttu-id="f5bb1-204">単純型を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="f5bb1-204">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
