---
title: '方法: XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する'
description: XML スキーマ定義ツールを使用して、クラスを説明する XML スキーマを生成したり、XML スキーマで定義されるクラスを生成したりする方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 9d94ed7c2558b1d60efb8b3cdbaac1ea1f0087b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676661"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="c0664-103">方法: XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する</span><span class="sxs-lookup"><span data-stu-id="c0664-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>

<span data-ttu-id="c0664-104">XML スキーマ定義ツール (Xsd.exe) を使用して、クラスを説明する XML スキーマを生成したり、XML スキーマで定義されるクラスを生成したりできます。</span><span class="sxs-lookup"><span data-stu-id="c0664-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="c0664-105">次の手順では、これらの操作の実行方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c0664-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="c0664-106">通常、XML スキーマ定義ツール (Xsd.exe) は、次のパスにあります。</span><span class="sxs-lookup"><span data-stu-id="c0664-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:\</span></span>
<span data-ttu-id="c0664-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="c0664-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="c0664-108">特定のスキーマに準拠するクラスを生成するには</span><span class="sxs-lookup"><span data-stu-id="c0664-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="c0664-109">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c0664-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="c0664-110">XML スキーマ定義ツールに XML スキーマを引数として渡します。XML スキーマ定義ツールは、次のように XML スキーマに正確に一致するクラスのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="c0664-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="c0664-111">ツールは、2001 年 3 月 16 日付けの World Wide Web Consortium XML 仕様を参照するスキーマのみを処理できます。</span><span class="sxs-lookup"><span data-stu-id="c0664-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="c0664-112">つまり、XML スキーマ名前空間は、次の例に示すように "http://www.w3.org/2001/XMLSchema" になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0664-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="c0664-113">必要に応じて、クラスのメソッド、プロパティ、またはフィールドを変更します。</span><span class="sxs-lookup"><span data-stu-id="c0664-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="c0664-114">属性によるクラスの変更の詳細については、「[属性を使用した XML シリアル化の制御](controlling-xml-serialization-using-attributes.md)」と「[エンコード済み SOAP シリアル化を制御する属性](attributes-that-control-encoded-soap-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0664-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="c0664-115">クラスのインスタンスがシリアル化されるときに生成される XML ストリームのスキーマを調べることは、さまざまな場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c0664-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="c0664-116">たとえば、他のユーザーが使用できるようにスキーマを公開したり、準拠しようとしているスキーマと自分のスキーマを比較したりできます。</span><span class="sxs-lookup"><span data-stu-id="c0664-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="c0664-117">クラスのセットから XML スキーマ ドキュメントを生成するには</span><span class="sxs-lookup"><span data-stu-id="c0664-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="c0664-118">クラスを DLL にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c0664-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="c0664-119">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c0664-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="c0664-120">次の例に示すように、DLL を引数として Xsd.exe に渡します。</span><span class="sxs-lookup"><span data-stu-id="c0664-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="c0664-121">スキーマが、"schema0.xsd" という名前から順に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="c0664-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0664-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0664-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="c0664-123">XML スキーマ定義ツールと XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="c0664-123">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="c0664-124">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="c0664-124">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="c0664-125">XML スキーマ定義ツール (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="c0664-125">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="c0664-126">方法: オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="c0664-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="c0664-127">方法: オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="c0664-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
