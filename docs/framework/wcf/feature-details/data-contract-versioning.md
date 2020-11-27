---
title: データ コントラクトのバージョン管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 6f8623c9d8e9e7ba1f7c762c929f986b523c2f90
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285201"
---
# <a name="data-contract-versioning"></a><span data-ttu-id="ad0d1-102">データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="ad0d1-102">Data Contract Versioning</span></span>

<span data-ttu-id="ad0d1-103">アプリケーションの進化に伴って、サービスが使用するデータ コントラクトを変更することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-103">As applications evolve, you may also have to change the data contracts the services use.</span></span> <span data-ttu-id="ad0d1-104">ここでは、データ コントラクトをバージョン管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-104">This topic explains how to version data contracts.</span></span> <span data-ttu-id="ad0d1-105">データ コントラクトのバージョン管理のメカニズムについても説明します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-105">This topic describes the data contract versioning mechanisms.</span></span> <span data-ttu-id="ad0d1-106">完全な概要と規範となるバージョン管理のガイダンスについては、「 [ベストプラクティス: データコントラクトのバージョン管理](../best-practices-data-contract-versioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-106">For a complete overview and prescriptive versioning guidance, see [Best Practices: Data Contract Versioning](../best-practices-data-contract-versioning.md).</span></span>  
  
## <a name="breaking-vs-nonbreaking-changes"></a><span data-ttu-id="ad0d1-107">互換性に影響する変更と影響しない変更</span><span class="sxs-lookup"><span data-stu-id="ad0d1-107">Breaking vs. Nonbreaking Changes</span></span>  

 <span data-ttu-id="ad0d1-108">データ コントラクトへの変更には、互換性に影響するものと影響しないものとがあります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-108">Changes to a data contract can be breaking or nonbreaking.</span></span> <span data-ttu-id="ad0d1-109">互換性に影響しない方法でデータ コントラクトを変更すると、古いバージョンのコントラクトを使用するアプリケーションは新しいバージョンを使用するアプリケーションと通信できます。また、新しいバージョンを使用するアプリケーションも古いバージョンを使用するアプリケーションと通信できます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-109">When a data contract is changed in a nonbreaking way, an application using the older version of the contract can communicate with an application using the newer version, and an application using the newer version of the contract can communicate with an application using the older version.</span></span> <span data-ttu-id="ad0d1-110">一方、互換性に影響する変更では、一方向または双方向で通信できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-110">On the other hand, a breaking change prevents communication in one or both directions.</span></span>  
  
 <span data-ttu-id="ad0d1-111">型を変更してもその送受信方法に影響しない場合は、互換性に影響しない変更と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-111">Any changes to a type that do not affect how it is transmitted and received are nonbreaking.</span></span> <span data-ttu-id="ad0d1-112">このような変更では、データ コントラクトは変更されず、基になる型のみが変更されます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-112">Such changes do not change the data contract, only the underlying type.</span></span> <span data-ttu-id="ad0d1-113">たとえば、フィールドの名前を変更した後で <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを以前のバージョン名に設定すれば、互換性に影響しません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-113">For example, you can change the name of a field in a nonbreaking way if you then set the <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to the older version name.</span></span> <span data-ttu-id="ad0d1-114">次のコードに、バージョン 1 のデータ コントラクトを示します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-114">The following code shows version 1 of a data contract.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 <span data-ttu-id="ad0d1-115">互換性に影響しない変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-115">The following code shows a nonbreaking change.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 <span data-ttu-id="ad0d1-116">変更によっては、送信されるデータを変更しても、必ずしも互換性に影響しない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-116">Some changes do modify the transmitted data, but may or may not be breaking.</span></span> <span data-ttu-id="ad0d1-117">次の変更は常に互換性に影響します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-117">The following changes are always breaking:</span></span>  
  
- <span data-ttu-id="ad0d1-118">データ コントラクトの <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 値または <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 値の変更。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-118">Changing the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> or <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> value of a data contract.</span></span>  
  
- <span data-ttu-id="ad0d1-119"><xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを使用したデータ メンバーの順序の変更。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-119">Changing the order of data members by using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute>.</span></span>  
  
- <span data-ttu-id="ad0d1-120">データ メンバーの名前の変更。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-120">Renaming a data member.</span></span>  
  
- <span data-ttu-id="ad0d1-121">データ メンバーのデータ コントラクトの変更 </span><span class="sxs-lookup"><span data-stu-id="ad0d1-121">Changing the data contract of a data member.</span></span> <span data-ttu-id="ad0d1-122">(たとえば、データ メンバーの型を整数型から文字列型に変更したり、"Customer" という名前のデータ コントラクトを持つ型を "Person" という名前のデータ コントラクトを持つ型に変更したりするなど)。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-122">For example, changing the type of data member from an integer to a string, or from a type with a data contract named "Customer" to a type with a data contract named "Person".</span></span>  
  
 <span data-ttu-id="ad0d1-123">以下のような変更も考えられます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-123">The following changes are also possible.</span></span>  
  
## <a name="adding-and-removing-data-members"></a><span data-ttu-id="ad0d1-124">データ メンバーの追加と削除</span><span class="sxs-lookup"><span data-stu-id="ad0d1-124">Adding and Removing Data Members</span></span>  

 <span data-ttu-id="ad0d1-125">厳密なスキーマ検証 (古いスキーマに基づく新しいインスタンスの検証) が必要ではない限り、多くの場合、データ メンバーの追加または削除は互換性に影響する変更ではありません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-125">In most cases, adding or removing a data member is not a breaking change, unless you require strict schema validity (new instances validating against the old schema).</span></span>  
  
 <span data-ttu-id="ad0d1-126">追加のフィールドを持つ型が、そのフィールドを持たない型に逆シリアル化された場合、追加のフィールドにある情報は無視されます </span><span class="sxs-lookup"><span data-stu-id="ad0d1-126">When a type with an extra field is deserialized into a type with a missing field, the extra information is ignored.</span></span> <span data-ttu-id="ad0d1-127">(ラウンドトリップのために保存される場合もあります。詳細については、「 [上位互換性のあるデータコントラクト](forward-compatible-data-contracts.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-127">(It may also be stored for round-tripping purposes; for more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md)).</span></span>  
  
 <span data-ttu-id="ad0d1-128">一部のフィールドが足りない型が、追加のフィールドを持つ型に逆シリアル化された場合、追加のフィールドは既定値 (通常はゼロまたは `null`) のままになります </span><span class="sxs-lookup"><span data-stu-id="ad0d1-128">When a type with a missing field is deserialized into a type with an extra field, the extra field is left at its default value, usually zero or `null`.</span></span> <span data-ttu-id="ad0d1-129">(既定値は変更される可能性があります。詳細については、「 [バージョントレラントなシリアル化コールバック](version-tolerant-serialization-callbacks.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-129">(The default value may be changed; for more information, see [Version-Tolerant Serialization Callbacks](version-tolerant-serialization-callbacks.md).)</span></span>  
  
 <span data-ttu-id="ad0d1-130">たとえば、クライアントで `CarV1` クラスを使用し、サービスで `CarV2` クラスを使用することも、サービスで `CarV1` クラスを使用し、クライアントで `CarV2` クラスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-130">For example, you can use the `CarV1` class on a client and the `CarV2` class on a service, or you can use the `CarV1` class on a service and the `CarV2` class on a client.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 <span data-ttu-id="ad0d1-131">バージョン 2 のエンドポイントからバージョン 1 のエンドポイントに正常にデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-131">The version 2 endpoint can successfully send data to the version 1 endpoint.</span></span> <span data-ttu-id="ad0d1-132">`Car` データ コントラクトのバージョン 2 をシリアル化すると、次のような XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-132">Serializing version 2 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 <span data-ttu-id="ad0d1-133">バージョン 1 の逆シリアル化エンジンでは、`HorsePower` フィールドに一致するデータ メンバーを見つけられないため、データは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-133">The deserialization engine on V1 does not find a matching data member for the `HorsePower` field, and discards that data.</span></span>  
  
 <span data-ttu-id="ad0d1-134">また、バージョン 1 のエンドポイントからバージョン 2 のエンドポイントにデータを送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-134">Also, the version 1 endpoint can send data to the version 2 endpoint.</span></span> <span data-ttu-id="ad0d1-135">`Car` データ コントラクトのバージョン 1 をシリアル化すると、次のような XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-135">Serializing version 1 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 <span data-ttu-id="ad0d1-136">受信 XML に一致するデータがないため、バージョン 2 のデシリアライザーでは `HorsePower` フィールドを何に設定するのか判別できません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-136">The version 2 deserializer does not know what to set the `HorsePower` field to, because there is no matching data in the incoming XML.</span></span> <span data-ttu-id="ad0d1-137">そのため、このフィールドには既定値である 0 が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-137">Instead, the field is set to the default value of 0.</span></span>  
  
## <a name="required-data-members"></a><span data-ttu-id="ad0d1-138">必須データ メンバー</span><span class="sxs-lookup"><span data-stu-id="ad0d1-138">Required Data Members</span></span>  

 <span data-ttu-id="ad0d1-139"><xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを `true` に設定すると、データ メンバーを必須のデータ メンバーとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-139">A data member may be marked as being required by setting the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to `true`.</span></span> <span data-ttu-id="ad0d1-140">逆シリアル化中に必須データがない場合、データ メンバーは既定値に設定されず、代わりに例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-140">If required data is missing while deserializing, an exception is thrown instead of setting the data member to its default value.</span></span>  
  
 <span data-ttu-id="ad0d1-141">必須のデータ メンバーの追加は、互換性に影響する変更です。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-141">Adding a required data member is a breaking change.</span></span> <span data-ttu-id="ad0d1-142">つまり、新しい型を古い型のエンドポイントに送信することはできますが、その逆はできなくなります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-142">That is, the newer type can still be sent to endpoints with the older type, but not the other way around.</span></span> <span data-ttu-id="ad0d1-143">以前のバージョンで必須としてマークされていたデータ メンバーを削除することも、互換性に影響する変更です。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-143">Removing a data member that was marked as required in any prior version is also a breaking change.</span></span>  
  
 <span data-ttu-id="ad0d1-144"><xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティの値を `true` から `false` に変更することは互換性に影響しませんが、`false` から `true` に変更すると、これよりも以前のいずれかのバージョンの型にこのデータ メンバーが存在していない場合、互換性に影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-144">Changing the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property value from `true` to `false` is not breaking, but changing it from `false` to `true` may be breaking if any prior versions of the type do not have the data member in question.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad0d1-145"><xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティが `true` に設定されていても、受信データは NULL またはゼロの場合があるので、型ではこの可能性を処理できるようにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-145">Although the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property is set to `true`, the incoming data may be null or zero, and a type must be prepared to handle this possibility.</span></span> <span data-ttu-id="ad0d1-146">不適切な受信データに対するセキュリティ保護メカニズムとして <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-146">Do not use <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> as a security mechanism to protect against bad incoming data.</span></span>  
  
## <a name="omitted-default-values"></a><span data-ttu-id="ad0d1-147">既定値の省略</span><span class="sxs-lookup"><span data-stu-id="ad0d1-147">Omitted Default Values</span></span>  

 <span data-ttu-id="ad0d1-148">「 `EmitDefaultValue` `false` [データメンバーの既定値](data-member-default-values.md)」で説明されているように、DataMemberAttribute 属性のプロパティをに設定することもできます (推奨されません)。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-148">It is possible (although not recommended) to set the `EmitDefaultValue` property on the DataMemberAttribute attribute to `false`, as described in [Data Member Default Values](data-member-default-values.md).</span></span> <span data-ttu-id="ad0d1-149">このプロパティが `false` に設定されている場合、データ メンバーが既定値 (通常 NULL またはゼロ) に設定されていても、そのデータ メンバーは出力されません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-149">If this setting is `false`, the data member will not be emitted if it is set to its default value (usually null or zero).</span></span> <span data-ttu-id="ad0d1-150">これにより、次の 2 つの点で、異なるバージョンの必須データ メンバーの互換性が失われます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-150">This is not compatible with required data members in different versions in two ways:</span></span>  
  
- <span data-ttu-id="ad0d1-151">あるバージョンで必須になっているデータ メンバーを持つデータ コントラクトは、データ メンバーの `EmitDefaultValue` が `false` に設定されている別のバージョンから既定 (NULL またはゼロ) のデータを受信できません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-151">A data contract with a data member that is required in one version cannot receive default (null or zero) data from a different version in which the data member has `EmitDefaultValue` set to `false`.</span></span>  
  
- <span data-ttu-id="ad0d1-152">`EmitDefaultValue` が `false` に設定されている必須データ メンバーは、既定値 (NULL またはゼロ) をシリアル化で使用できませんが、逆シリアル化ではこのような値を受信できます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-152">A required data member that has `EmitDefaultValue` set to `false` cannot be used to serialize its default (null or zero) value, but can receive such a value on deserialization.</span></span> <span data-ttu-id="ad0d1-153">これによりラウンド トリップの問題が発生します (データを読み取ることはできますが、書き込むことができません)。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-153">This creates a round-tripping problem (data can be read in but the same data cannot then be written out).</span></span> <span data-ttu-id="ad0d1-154">そのため、あるバージョンにおいて `IsRequired` が `true` であり、`EmitDefaultValue` が `false` である場合、どのバージョンのデータ コントラクトにおいてもラウンド トリップを発生させる値を生成できるように、これ以外のすべてのバージョンに同じ組み合わせを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-154">Therefore, if `IsRequired` is `true` and `EmitDefaultValue` is `false` in one version, the same combination should apply to all other versions such that no version of the data contract would be able to produce a value that does not result in a round trip.</span></span>  
  
## <a name="schema-considerations"></a><span data-ttu-id="ad0d1-155">スキーマの考慮事項</span><span class="sxs-lookup"><span data-stu-id="ad0d1-155">Schema Considerations</span></span>  

 <span data-ttu-id="ad0d1-156">データコントラクト型に対して生成されるスキーマの説明については、「 [データコントラクトスキーマの参照](data-contract-schema-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-156">For an explanation of what schema is produced for data contract types, see [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span>  
  
 <span data-ttu-id="ad0d1-157">データコントラクト型に対して WCF によって生成されるスキーマは、バージョン管理のための準備を行いません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-157">The schema WCF produces for data contract types makes no provisions for versioning.</span></span> <span data-ttu-id="ad0d1-158">つまり、あるバージョンの型からエクスポートされたスキーマには、そのバージョンに存在するデータ メンバーのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-158">That is, the schema exported from a certain version of a type contains only those data members present in that version.</span></span> <span data-ttu-id="ad0d1-159"><xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装しても、型のスキーマは変更されません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-159">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface does not change the schema for a type.</span></span>  
  
 <span data-ttu-id="ad0d1-160">データ メンバーは、既定でオプション要素としてスキーマにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-160">Data members are exported to the schema as optional elements by default.</span></span> <span data-ttu-id="ad0d1-161">つまり、`minOccurs` (XML 属性) の値は 0 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-161">That is, the `minOccurs` (XML attribute) value is set to 0.</span></span> <span data-ttu-id="ad0d1-162">`minOccurs` を 1 に設定した場合、必須データ メンバーがエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-162">Required data members are exported with `minOccurs` set to 1.</span></span>  
  
 <span data-ttu-id="ad0d1-163">スキーマを厳密に遵守する必要がある場合、互換性に影響しないと思われる変更の多くが、実際には互換性に影響します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-163">Many of the changes considered to be nonbreaking are actually breaking if strict adherence to the schema is required.</span></span> <span data-ttu-id="ad0d1-164">前述の例では、`CarV1` 要素だけを持つ `Model` インスタンスは、`CarV2` スキーマ (`Model` と `Horsepower` の 2 つの要素を持ちますが、いずれも省略可能です) に対して有効です。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-164">In the preceding example, a `CarV1` instance with just the `Model` element would validate against the `CarV2` schema (which has both `Model` and `Horsepower`, but both are optional).</span></span> <span data-ttu-id="ad0d1-165">しかし、この逆は真ではありません。つまり、`CarV2` インスタンスは `CarV1` スキーマに対して検証が失敗します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-165">However, the reverse is not true: a `CarV2` instance would fail validation against the `CarV1` schema.</span></span>  
  
 <span data-ttu-id="ad0d1-166">ラウンド トリップにもいくつかの考慮事項があります。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-166">Round-tripping also entails some additional considerations.</span></span> <span data-ttu-id="ad0d1-167">詳細については、「 [上位互換性のあるデータコントラクト](forward-compatible-data-contracts.md)」の「スキーマの考慮事項」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-167">For more information, see the "Schema Considerations" section in [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
### <a name="other-permitted-changes"></a><span data-ttu-id="ad0d1-168">許可されるその他の変更</span><span class="sxs-lookup"><span data-stu-id="ad0d1-168">Other Permitted Changes</span></span>  

 <span data-ttu-id="ad0d1-169"><xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスの実装は、互換性に影響しない変更です。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-169">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface is a nonbreaking change.</span></span> <span data-ttu-id="ad0d1-170">ただし、<xref:System.Runtime.Serialization.IExtensibleDataObject> が実装されていた型のバージョンより前のバージョンでは、ラウンド トリップはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-170">However, round-tripping support does not exist for versions of the type prior to the version in which <xref:System.Runtime.Serialization.IExtensibleDataObject> was implemented.</span></span> <span data-ttu-id="ad0d1-171">詳細については、「[上位互換性のあるデータ コントラクト](forward-compatible-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-171">For more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="ad0d1-172">列挙型</span><span class="sxs-lookup"><span data-stu-id="ad0d1-172">Enumerations</span></span>  

 <span data-ttu-id="ad0d1-173">列挙体メンバーの追加や削除は、互換性に影響する変更です。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-173">Adding or removing an enumeration member is a breaking change.</span></span> <span data-ttu-id="ad0d1-174">`EnumMemberAttribute` 属性を使用して古いバージョンのコントラクト名を保持しない限り、列挙体メンバーの名前の変更は互換性に影響します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-174">Changing the name of an enumeration member is breaking, unless its contract name is kept the same as in the old version by using the `EnumMemberAttribute` attribute.</span></span> <span data-ttu-id="ad0d1-175">詳細については、「 [データコントラクトの列挙型](enumeration-types-in-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-175">For more information, see [Enumeration Types in Data Contracts](enumeration-types-in-data-contracts.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="ad0d1-176">コレクション</span><span class="sxs-lookup"><span data-stu-id="ad0d1-176">Collections</span></span>  

 <span data-ttu-id="ad0d1-177">コレクション型の大半はデータ コントラクト モデル内で交換可能であるため、多くの場合、コレクションの変更は互換性に影響しません。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-177">Most collection changes are nonbreaking because most collection types are interchangeable with each other in the data contract model.</span></span> <span data-ttu-id="ad0d1-178">ただし、カスタマイズされていないコレクションからカスタマイズされたコレクションへの変更またはその逆の変更は、互換性に影響する変更です。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-178">However, making a noncustomized collection customized or vice versa is a breaking change.</span></span> <span data-ttu-id="ad0d1-179">また、コレクションのカスタマイズ設定の変更 (データ コントラクトの名前と名前空間の変更、要素名、キー要素名、および値要素名の反復) も互換性に影響します。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-179">Also, changing the collection's customization settings is a breaking change; that is, changing its data contract name and namespace, repeating element name, key element name, and value element name.</span></span> <span data-ttu-id="ad0d1-180">コレクションのカスタマイズの詳細については、「 [データコントラクトのコレクション型](collection-types-in-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-180">For more information about collection customization, see [Collection Types in Data Contracts](collection-types-in-data-contracts.md).</span></span>  
<span data-ttu-id="ad0d1-181">また、コレクションの内容のデータ コントラクトの変更 (整数のリストから文字列のリストへの変更など) は互換性に影響する変更です。</span><span class="sxs-lookup"><span data-stu-id="ad0d1-181">Naturally, changing the data contract of contents of a collection (for example, changing from a list of integers to a list of strings) is a breaking change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0d1-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad0d1-182">See also</span></span>

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [<span data-ttu-id="ad0d1-183">バージョン トレラントなシリアル化コールバック</span><span class="sxs-lookup"><span data-stu-id="ad0d1-183">Version-Tolerant Serialization Callbacks</span></span>](version-tolerant-serialization-callbacks.md)
- [<span data-ttu-id="ad0d1-184">ベスト プラクティス:データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="ad0d1-184">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="ad0d1-185">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="ad0d1-185">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="ad0d1-186">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="ad0d1-186">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="ad0d1-187">上位互換性のあるデータ コントラクト</span><span class="sxs-lookup"><span data-stu-id="ad0d1-187">Forward-Compatible Data Contracts</span></span>](forward-compatible-data-contracts.md)
