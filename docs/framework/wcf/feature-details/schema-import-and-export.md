---
title: スキーマのインポートとエクスポート
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: 52a9e1bf4c9442bd42beb55b133a185c4a42148d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288567"
---
# <a name="schema-import-and-export"></a><span data-ttu-id="eb729-102">スキーマのインポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="eb729-102">Schema Import and Export</span></span>

<span data-ttu-id="eb729-103">Windows Communication Foundation (WCF) には、新しいシリアル化エンジン、が含まれてい <xref:System.Runtime.Serialization.DataContractSerializer> ます。</span><span class="sxs-lookup"><span data-stu-id="eb729-103">Windows Communication Foundation (WCF) includes a new serialization engine, the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="eb729-104">は、 `DataContractSerializer` .NET Framework のオブジェクトと XML を双方向に変換します。</span><span class="sxs-lookup"><span data-stu-id="eb729-104">The `DataContractSerializer` translates between .NET Framework objects and XML (in both directions).</span></span> <span data-ttu-id="eb729-105">シリアライザー自体に加えて、WCF には、関連付けられたスキーマインポートおよびスキーマエクスポートメカニズムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb729-105">In addition to the serializer itself, WCF includes associated schema import and schema export mechanisms.</span></span> <span data-ttu-id="eb729-106">*スキーマ* は、シリアライザーによって生成されるか、またはデシリアライザーがアクセスできる XML の構造について、正式で正確で、コンピューターが読み取り可能な記述です。</span><span class="sxs-lookup"><span data-stu-id="eb729-106">*Schema* is a formal, precise, and machine-readable description of the shape of XML that the serializer produces or that the deserializer can access.</span></span> <span data-ttu-id="eb729-107">WCF は、World Wide Web コンソーシアム (W3C) XML スキーマ定義言語 (XSD) をスキーマ表現として使用します。これは、多数のサードパーティプラットフォームと幅広く相互運用できます。</span><span class="sxs-lookup"><span data-stu-id="eb729-107">WCF uses the World Wide Web Consortium (W3C) XML Schema definition language (XSD) as its schema representation, which is widely interoperable with numerous third-party platforms.</span></span>  
  
 <span data-ttu-id="eb729-108">スキーマインポートコンポーネントは、 <xref:System.Runtime.Serialization.XsdDataContractImporter> XSD スキーマドキュメントを受け取り、シリアル化された形式が特定のスキーマに対応するように .NET Framework クラス (通常はデータコントラクトクラス) を生成します。</span><span class="sxs-lookup"><span data-stu-id="eb729-108">The schema import component, <xref:System.Runtime.Serialization.XsdDataContractImporter>, takes an XSD schema document and generates .NET Framework classes (normally data contract classes) such that the serialized forms correspond to the given schema.</span></span>  
  
 <span data-ttu-id="eb729-109">たとえば、次のスキーマ フラグメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="eb729-109">For example, the following schema fragment:</span></span>  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 <span data-ttu-id="eb729-110">これは、読みやすいように、やや簡素化された次の型を生成します。</span><span class="sxs-lookup"><span data-stu-id="eb729-110">generates the following type (simplified slightly for better readability).</span></span>  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 <span data-ttu-id="eb729-111">生成される型は、データコントラクトのベストプラクティス (「 [ベストプラクティス: データコントラクトのバージョン管理](../best-practices-data-contract-versioning.md)」にあります) に従うことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="eb729-111">Note that the generated type follows several data contract best practices (found in [Best Practices: Data Contract Versioning](../best-practices-data-contract-versioning.md)):</span></span>  
  
- <span data-ttu-id="eb729-112">この型は <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="eb729-112">The type implements the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span> <span data-ttu-id="eb729-113">詳細については、「[上位互換性のあるデータ コントラクト](forward-compatible-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb729-113">For more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
- <span data-ttu-id="eb729-114">データ メンバーは、プライベート フィールドをラップするパブリック プロパティとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="eb729-114">Data members are implemented as public properties that wrap private fields.</span></span>  
  
- <span data-ttu-id="eb729-115">クラスは部分クラスであり、生成されたコードを変更せずに追加を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="eb729-115">The class is a partial class, and additions can be made without modifying generated code.</span></span>  
  
 <span data-ttu-id="eb729-116"><xref:System.Runtime.Serialization.XsdDataContractExporter> では反転を実行できます。つまり、`DataContractSerializer` によってシリアル化できる型を受け取って XSD スキーマ ドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="eb729-116">The <xref:System.Runtime.Serialization.XsdDataContractExporter> enables you to do the reverse—take types that are serializable with the `DataContractSerializer` and generate an XSD Schema document.</span></span>  
  
## <a name="fidelity-is-not-guaranteed"></a><span data-ttu-id="eb729-117">忠実性は保証されない</span><span class="sxs-lookup"><span data-stu-id="eb729-117">Fidelity Is Not Guaranteed</span></span>  

 <span data-ttu-id="eb729-118">スキーマや型のラウンド トリップでの完全な忠実性は保証されません </span><span class="sxs-lookup"><span data-stu-id="eb729-118">It is not guaranteed that schema or types make a round trip with total fidelity.</span></span> <span data-ttu-id="eb729-119">( *ラウンドトリップ* とは、スキーマをインポートして一連のクラスを作成し、その結果をエクスポートしてもう一度スキーマを作成することを意味します)。同じスキーマを返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="eb729-119">(A *round trip* means to import a schema to create a set of classes, and export the result to create a schema again.) The same schema may not be returned.</span></span> <span data-ttu-id="eb729-120">また、これとは逆のプロセスでも忠実性は保証されません </span><span class="sxs-lookup"><span data-stu-id="eb729-120">Reversing the process is also not guaranteed to preserve fidelity.</span></span> <span data-ttu-id="eb729-121">(スキーマを生成する型をエクスポートしてから、型をインポートし直す場合です。</span><span class="sxs-lookup"><span data-stu-id="eb729-121">(Export a type to generate its schema, and then import the type back.</span></span> <span data-ttu-id="eb729-122">この場合も、同じ型が返されない可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="eb729-122">It is unlikely the same type is returned.)</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="eb729-123">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="eb729-123">Supported Types</span></span>  

 <span data-ttu-id="eb729-124">データ コントラクト モデルは、WC3 スキーマの限られたサブセットしかサポートしません。</span><span class="sxs-lookup"><span data-stu-id="eb729-124">The data contract model supports only a limited subset of the WC3 schema.</span></span> <span data-ttu-id="eb729-125">このサブセットに準拠しないスキーマを使用すると、インポート プロセスで例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="eb729-125">Any schema that does not conform to this subset will cause an exception during the import process.</span></span> <span data-ttu-id="eb729-126">たとえば、データ コントラクトのデータ メンバーを XML 属性としてシリアル化するように指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="eb729-126">For example, there is no way to specify that a data member of a data contract should be serialized as an XML attribute.</span></span> <span data-ttu-id="eb729-127">したがって、XML 属性を使用する必要があるスキーマはサポートされず、適切な XML 投影を持つデータ コントラクトを生成できないため、インポート時に例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="eb729-127">Thus, schemas that require the use of XML attributes are not supported and will cause exceptions during import, because it is impossible to generate a data contract with the correct XML projection.</span></span>  
  
 <span data-ttu-id="eb729-128">たとえば、次のスキーマ フラグメントは、既定のインポート設定を使用してインポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="eb729-128">For example, the following schema fragment cannot be imported using the default import settings.</span></span>  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 <span data-ttu-id="eb729-129">詳細については、「 [データコントラクトスキーマの参照](data-contract-schema-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb729-129">For more information, see [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span> <span data-ttu-id="eb729-130">スキーマがデータ コントラクト ルールに準拠していない場合は、別のシリアル化エンジンを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb729-130">If a schema does not conform to the data contract rules, use a different serialization engine.</span></span> <span data-ttu-id="eb729-131">たとえば、<xref:System.Xml.Serialization.XmlSerializer> は、独自のスキーマ インポート機構を使用します。</span><span class="sxs-lookup"><span data-stu-id="eb729-131">For example, the <xref:System.Xml.Serialization.XmlSerializer> uses its own separate schema import mechanism.</span></span> <span data-ttu-id="eb729-132">また、サポートされるスキーマの範囲を拡張する特別なインポート モードもあります。</span><span class="sxs-lookup"><span data-stu-id="eb729-132">Also, there is a special import mode in which the range of supported schema is expanded.</span></span> <span data-ttu-id="eb729-133">詳細については、「 <xref:System.Xml.Serialization.IXmlSerializable> [クラスを生成するためのスキーマのインポート](importing-schema-to-generate-classes.md)」で型を生成する方法に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb729-133">For more information, see the section about generating <xref:System.Xml.Serialization.IXmlSerializable> types in [Importing Schema to Generate Classes](importing-schema-to-generate-classes.md).</span></span>  
  
 <span data-ttu-id="eb729-134">は `XsdDataContractExporter` 、でシリアル化できるすべての .NET Framework 型をサポートして `DataContractSerializer` います。</span><span class="sxs-lookup"><span data-stu-id="eb729-134">The `XsdDataContractExporter` supports any .NET Framework types that can be serialized with the `DataContractSerializer`.</span></span> <span data-ttu-id="eb729-135">詳細については、「 [データコントラクトシリアライザーでサポートされる型](types-supported-by-the-data-contract-serializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb729-135">For more information, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span> <span data-ttu-id="eb729-136">通常、`XsdDataContractExporter` を使用して作成されたスキーマは、`XsdDataContractImporter` を使用してカスタマイズしない限り、<xref:System.Xml.Serialization.XmlSchemaProviderAttribute> で使用できる有効なデータです。</span><span class="sxs-lookup"><span data-stu-id="eb729-136">Note that schema generated using the `XsdDataContractExporter` is normally valid data that the `XsdDataContractImporter` can use (unless the <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> is used to customize the schema).</span></span>  
  
 <span data-ttu-id="eb729-137">の使用方法の詳細については <xref:System.Runtime.Serialization.XsdDataContractImporter> 、「 [スキーマをインポートしてクラスを生成する](importing-schema-to-generate-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb729-137">For more information about using the <xref:System.Runtime.Serialization.XsdDataContractImporter>, see [Importing Schema to Generate Classes](importing-schema-to-generate-classes.md).</span></span>  
  
 <span data-ttu-id="eb729-138">の使用方法の詳細については <xref:System.Runtime.Serialization.XsdDataContractExporter> 、「 [クラスからのスキーマのエクスポート](exporting-schemas-from-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb729-138">For more information about using the <xref:System.Runtime.Serialization.XsdDataContractExporter>, see [Exporting Schemas from Classes](exporting-schemas-from-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb729-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb729-139">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [<span data-ttu-id="eb729-140">クラスを作成するためのスキーマのインポート</span><span class="sxs-lookup"><span data-stu-id="eb729-140">Importing Schema to Generate Classes</span></span>](importing-schema-to-generate-classes.md)
- [<span data-ttu-id="eb729-141">クラスからのスキーマのエクスポート</span><span class="sxs-lookup"><span data-stu-id="eb729-141">Exporting Schemas from Classes</span></span>](exporting-schemas-from-classes.md)
