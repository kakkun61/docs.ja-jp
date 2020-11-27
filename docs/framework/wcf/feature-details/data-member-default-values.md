---
title: データ メンバーの既定値
description: .NET Framework の既定値がある場合に、シリアル化されたデータからデータメンバーを省略する方法について説明します。 WCF では、既定値をシリアル化しないことでパフォーマンスを向上させることができます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: 98b19fdabebeb8a1d43a66a192cb523b82ada618
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261996"
---
# <a name="data-member-default-values"></a><span data-ttu-id="6e417-104">データ メンバーの既定値</span><span class="sxs-lookup"><span data-stu-id="6e417-104">Data Member Default Values</span></span>

<span data-ttu-id="6e417-105">.NET Framework では、型に *既定値* の概念があります。</span><span class="sxs-lookup"><span data-stu-id="6e417-105">In the .NET Framework, types have a concept of *default values*.</span></span> <span data-ttu-id="6e417-106">たとえば、参照型の既定値は `null` で、整数型の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="6e417-106">For example, for any reference type the default value is `null`, and for an integer type it is zero.</span></span> <span data-ttu-id="6e417-107">しかし、データ メンバーが既定値に設定されている場合は、シリアル化されたデータからそのデータ メンバーを省略することが望ましいことがあります。</span><span class="sxs-lookup"><span data-stu-id="6e417-107">It is occasionally desirable to omit a data member from serialized data when it is set to its default value.</span></span> <span data-ttu-id="6e417-108">それは、メンバーが既定値に設定されているために実際の値をシリアル化する必要がなく、パフォーマンスの点で有利だからです。</span><span class="sxs-lookup"><span data-stu-id="6e417-108">Because the member has a default value, an actual value need not be serialized; this has a performance advantage.</span></span>  
  
 <span data-ttu-id="6e417-109">シリアル化されたデータからデータ メンバーを省略するには、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを `false` に設定します (既定値は `true`)。</span><span class="sxs-lookup"><span data-stu-id="6e417-109">To omit a member from serialized data, set the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to `false` (the default is `true`).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e417-110">相互運用性の維持やデータ サイズの縮小のような特別なニーズがある場合は、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> プロパティを `false` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e417-110">You should set the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property to `false` if there is a specific need to do so, such as for interoperability or data size reduction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e417-111">例</span><span class="sxs-lookup"><span data-stu-id="6e417-111">Example</span></span>  

 <span data-ttu-id="6e417-112">次のコードには、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> が `false` に設定された複数のメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e417-112">The following code has several members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> set to `false`.</span></span>  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 <span data-ttu-id="6e417-113">このクラスのインスタンスをシリアル化すると、次に示すように `employeeName` と `employeeID` がシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="6e417-113">If an instance of this class is serialized, the result is as follows: `employeeName` and `employeeID` is serialized.</span></span> <span data-ttu-id="6e417-114">`employeeName` の null 値と `employeeID` の値 0 は、シリアル化されるデータに明示的に含められます。</span><span class="sxs-lookup"><span data-stu-id="6e417-114">The null value for `employeeName` and the zero value for `employeeID` is explicitly part of the serialized data.</span></span> <span data-ttu-id="6e417-115">ただし、`position`、`salary`、および `bonus` のメンバーはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="6e417-115">However, the `position`, `salary`, and `bonus` members are not serialized.</span></span> <span data-ttu-id="6e417-116">また、`targetSalary` プロパティは <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> に設定されていますが、57800 が .NET の整数の既定値 (0) と一致しないため、`false` が通常どおりにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="6e417-116">Finally, `targetSalary` is serialized as usual, even though the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property is set to `false`, because 57800 does not match the .NET default value for an integer, which is zero.</span></span>  
  
### <a name="xml-representation"></a><span data-ttu-id="6e417-117">XML 表現</span><span class="sxs-lookup"><span data-stu-id="6e417-117">XML Representation</span></span>  

 <span data-ttu-id="6e417-118">前の例を XML にシリアル化すると、生成される XML 表現は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6e417-118">If the previous example is serialized to XML, the representation is similar to the following.</span></span>  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 <span data-ttu-id="6e417-119">`xsi:nil` 属性は W3C (World Wide Web Consortium) XML スキーマ インスタンス名前空間の特別な属性であり、null 値を明示的に表すための相互運用可能な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="6e417-119">The `xsi:nil` attribute is a special attribute in the World Wide Web Consortium (W3C) XML Schema instance namespace that provides an interoperable way to explicitly represent a null value.</span></span> <span data-ttu-id="6e417-120">この XML には、地位、給与、ボーナスの各データ メンバーに関する情報がまったく含まれていないことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="6e417-120">Note that there is no information at all in the XML about position, salary, and bonus data members.</span></span> <span data-ttu-id="6e417-121">これらのデータ メンバーは、受信エンドポイントで、それぞれ `null`、0、および `null` として解釈します。</span><span class="sxs-lookup"><span data-stu-id="6e417-121">The receiving end can interpret these as `null`, zero, and `null`, respectively.</span></span> <span data-ttu-id="6e417-122">これらをサードパーティ製のデシリアライザーで正しく解釈できる保証はないため、このパターンはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="6e417-122">There is no guarantee that a third-party deserializer can make the correct interpretation, which is why this pattern is not recommended.</span></span> <span data-ttu-id="6e417-123"><xref:System.Runtime.Serialization.DataContractSerializer> クラスを使用すると、値が指定されていない場合でも、常に正しい解釈が選択されます。</span><span class="sxs-lookup"><span data-stu-id="6e417-123">The <xref:System.Runtime.Serialization.DataContractSerializer> class always selects the correct interpretation for missing values.</span></span>  
  
### <a name="interaction-with-isrequired"></a><span data-ttu-id="6e417-124">IsRequired との対話</span><span class="sxs-lookup"><span data-stu-id="6e417-124">Interaction with IsRequired</span></span>  

 <span data-ttu-id="6e417-125">「 [データコントラクトのバージョン管理](data-contract-versioning.md)」で説明されているように、属性には <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティがあり <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ます (既定値は `false` )。</span><span class="sxs-lookup"><span data-stu-id="6e417-125">As discussed in [Data Contract Versioning](data-contract-versioning.md), the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property (the default is `false`).</span></span> <span data-ttu-id="6e417-126">このプロパティは、シリアル化されたデータを逆シリアル化する際に、指定されたデータ メンバーが存在する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="6e417-126">The property indicates whether a given data member must be present in the serialized data when it is being deserialized.</span></span> <span data-ttu-id="6e417-127">`IsRequired` が `true` (値が存在する必要がある) に設定され、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> が `false` (既定値に設定されている場合は、値が存在する必要がない) に設定されている場合は、結果が矛盾するため、このデータ メンバーの既定値をシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="6e417-127">If `IsRequired` is set to `true`, (which indicates that a value must be present) and <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> is set to `false` (indicating that the value must not be present if it is set to its default value), default values for this data member cannot be serialized because the results would be contradictory.</span></span> <span data-ttu-id="6e417-128">このようなデータ メンバーを既定値 (通常は `null` または 0) に設定してシリアル化を実行すると、<xref:System.Runtime.Serialization.SerializationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6e417-128">If such a data member is set to its default value (usually `null` or zero) and a serialization is attempted, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
### <a name="schema-representation"></a><span data-ttu-id="6e417-129">スキーマ表現</span><span class="sxs-lookup"><span data-stu-id="6e417-129">Schema Representation</span></span>  

 <span data-ttu-id="6e417-130">プロパティがに設定されている場合のデータメンバーの XML スキーマ定義言語 (XSD) スキーマ表現の詳細については、「 `EmitDefaultValue` `false` [データコントラクトスキーマのリファレンス](data-contract-schema-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e417-130">The details of the XML Schema definition language (XSD) schema representation of data members when the `EmitDefaultValue` property is set to `false` are discussed in [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span> <span data-ttu-id="6e417-131">以下に、その概要を簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="6e417-131">However, the following is a brief overview:</span></span>  
  
- <span data-ttu-id="6e417-132"><xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>がに設定されている場合 `false` 、スキーマでは、WINDOWS COMMUNICATION FOUNDATION (WCF) に固有の注釈として表されます。</span><span class="sxs-lookup"><span data-stu-id="6e417-132">When the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> is set to `false`, it is represented in the schema as an annotation specific to Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6e417-133">この情報を表すための相互運用可能な方法はありません。</span><span class="sxs-lookup"><span data-stu-id="6e417-133">There is no interoperable way to represent this information.</span></span> <span data-ttu-id="6e417-134">特に、スキーマにおける "default" 属性はこの目的では使用されません。また、`minOccurs` 属性は <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 設定だけに影響され、`nillable` 属性はデータ メンバーの型だけに影響されます。</span><span class="sxs-lookup"><span data-stu-id="6e417-134">In particular, the "default" attribute in the schema is not used for this purpose, the `minOccurs` attribute is affected only by the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> setting, and the `nillable` attribute is affected only by the type of the data member.</span></span>  
  
- <span data-ttu-id="6e417-135">使用される実際の既定値は、スキーマには存在しません。</span><span class="sxs-lookup"><span data-stu-id="6e417-135">The actual default value to use is not present in the schema.</span></span> <span data-ttu-id="6e417-136">指定されていない要素が適切に解釈されるかどうかは、受信エンドポイントに依存します。</span><span class="sxs-lookup"><span data-stu-id="6e417-136">It is up to the receiving endpoint to appropriately interpret a missing element.</span></span>  
  
 <span data-ttu-id="6e417-137">スキーマのインポートでは、前に説明した <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> `false` WCF 固有の注釈が検出されるたびに、プロパティは自動的にに設定されます。</span><span class="sxs-lookup"><span data-stu-id="6e417-137">On schema import, the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property is automatically set to `false` whenever the WCF-specific annotation mentioned previously is detected.</span></span> <span data-ttu-id="6e417-138">また、 `false` `nillable` `false` ASP.NET Web サービスを使用するときによく発生する特定の相互運用性シナリオをサポートするために、プロパティがに設定されている参照型に対しても設定されます。</span><span class="sxs-lookup"><span data-stu-id="6e417-138">It is also set to `false` for reference types that have the `nillable` property set to `false` to support specific interoperability scenarios that commonly occur when consuming ASP.NET Web services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e417-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e417-139">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
