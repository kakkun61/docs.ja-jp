---
title: シリアル化のガイドライン
description: このドキュメントでは、シリアル化される API を設計する際に考慮するガイドラインと、.NET で提供される 3 つの主要なシリアル化テクノロジの概要について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: 32d71aba5d8a650293a4d8653fb2a2e383b8a800
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282371"
---
# <a name="serialization-guidelines"></a><span data-ttu-id="897de-103">シリアル化のガイドライン</span><span class="sxs-lookup"><span data-stu-id="897de-103">Serialization guidelines</span></span>

<span data-ttu-id="897de-104">この記事では、シリアル化されるように API を設計するときに考慮すべきガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="897de-104">This article lists the guidelines to consider when designing an API to be serialized.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

 <span data-ttu-id="897de-105">.NET には、さまざまなシリアル化シナリオに合わせて最適化できる 3 つの主なシリアル化テクノロジがあります。</span><span class="sxs-lookup"><span data-stu-id="897de-105">.NET offers three main serialization technologies that are optimized for various serialization scenarios.</span></span> <span data-ttu-id="897de-106">これらのテクノロジ、およびテクノロジに関連した主な .NET 型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="897de-106">The following table lists these technologies and the main .NET types related to these technologies.</span></span>

|<span data-ttu-id="897de-107">テクノロジ</span><span class="sxs-lookup"><span data-stu-id="897de-107">Technology</span></span>|<span data-ttu-id="897de-108">関連するクラス</span><span class="sxs-lookup"><span data-stu-id="897de-108">Relevant Classes</span></span>|<span data-ttu-id="897de-109">メモ</span><span class="sxs-lookup"><span data-stu-id="897de-109">Notes</span></span>|
|----------------|----------------------|-----------|
|<span data-ttu-id="897de-110">データ コントラクトのシリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-110">Data Contract Serialization</span></span>|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|<span data-ttu-id="897de-111">永続化全般</span><span class="sxs-lookup"><span data-stu-id="897de-111">General persistence</span></span><br /><br /> <span data-ttu-id="897de-112">Web サービス</span><span class="sxs-lookup"><span data-stu-id="897de-112">Web Services</span></span><br /><br /> <span data-ttu-id="897de-113">JSON</span><span class="sxs-lookup"><span data-stu-id="897de-113">JSON</span></span>|
|<span data-ttu-id="897de-114">XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-114">XML Serialization</span></span>|<xref:System.Xml.Serialization.XmlSerializer>|<span data-ttu-id="897de-115">XML 形式</span><span class="sxs-lookup"><span data-stu-id="897de-115">XML format</span></span> <br /><span data-ttu-id="897de-116">フル コントロール</span><span class="sxs-lookup"><span data-stu-id="897de-116">with full control</span></span>|
|<span data-ttu-id="897de-117">ランタイム シリアル化 (バイナリおよび SOAP)</span><span class="sxs-lookup"><span data-stu-id="897de-117">Runtime -Serialization (Binary and SOAP)</span></span>|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|<span data-ttu-id="897de-118">.NET リモート処理</span><span class="sxs-lookup"><span data-stu-id="897de-118">.NET Remoting</span></span>|

 <span data-ttu-id="897de-119">新しい型をデザインする際は、新しい型でどのテクノロジをサポートするかを決める必要があります。</span><span class="sxs-lookup"><span data-stu-id="897de-119">When you design new types, you should decide which, if any, of these technologies those types need to support.</span></span> <span data-ttu-id="897de-120">次のガイドラインでその選択方法とサポートの提供方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="897de-120">The following guidelines describe how to make that choice and how to provide such support.</span></span> <span data-ttu-id="897de-121">このガイドラインは、アプリケーションまたはライブラリの実装時に使用するシリアル化テクノロジを決定するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="897de-121">These guidelines are not meant to help you choose which serialization technology you should use in the implementation of your application or library.</span></span> <span data-ttu-id="897de-122">そのようなガイドラインは API のデザインには直接関係ないため、このトピックのスコープの範囲外となります。</span><span class="sxs-lookup"><span data-stu-id="897de-122">Such guidelines are not directly related to API design and thus are not within the scope of this topic.</span></span>

## <a name="guidelines"></a><span data-ttu-id="897de-123">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="897de-123">Guidelines</span></span>

- <span data-ttu-id="897de-124">新しい型をデザインする際にはシリアル化について考えてください。</span><span class="sxs-lookup"><span data-stu-id="897de-124">DO think about serialization when you design new types.</span></span>

  <span data-ttu-id="897de-125">シリアル化は、プログラムで型のインスタンスを永続化または変換しなければならないことがあるため、どのような型においてもデザイン上の重要な考慮事項です。</span><span class="sxs-lookup"><span data-stu-id="897de-125">Serialization is an important design consideration for any type, because programs might need to persist or transmit instances of the type.</span></span>

### <a name="choosing-the-right-serialization-technology-to-support"></a><span data-ttu-id="897de-126">サポートする適切なシリアル化テクノロジの選択</span><span class="sxs-lookup"><span data-stu-id="897de-126">Choosing the right serialization technology to support</span></span>
 <span data-ttu-id="897de-127">任意の型で 0、または 1 つ以上のシリアル化テクノロジをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="897de-127">Any given type can support none, one, or more of the serialization technologies.</span></span>

- <span data-ttu-id="897de-128">使用する型のインスタンスを Web サービスで永続化させる、または使用する必要がある場合は、 *データ コントラクトのシリアル化* をサポートすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-128">CONSIDER supporting *data contract serialization* if instances of your type might need to be persisted or used in Web Services.</span></span>

- <span data-ttu-id="897de-129">型をシリアル化したときに作成される XML 形式の制御を強化する必要がある場合は、データ コントラクトのシリアル化の代わり、またはこれに加えて *XML シリアル化* をサポートすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-129">CONSIDER supporting the *XML serialization* instead of or in addition to data contract serialization if you need more control over the XML format that is produced when the type is serialized.</span></span>

     <span data-ttu-id="897de-130">これは、データ コントラクトのシリアル化でサポートされていない XML 構築を使用して XML 属性を作成するような一部の相互運用シナリオで必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="897de-130">This may be necessary in some interoperability scenarios where you need to use an XML construct that is not supported by data contract serialization, for example, to produce XML attributes.</span></span>

- <span data-ttu-id="897de-131">使用する型のインスタンスが .NET リモート処理境界を超えて移動する必要がある場合は、 *ランタイムのシリアル化* をサポートすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-131">CONSIDER supporting *runtime serialization* if instances of your type need to travel across .NET Remoting boundaries.</span></span>

- <span data-ttu-id="897de-132">一般的な永続化のためにランタイムのシリアル化や XML のシリアル化をサポートしないでください。</span><span class="sxs-lookup"><span data-stu-id="897de-132">AVOID supporting runtime serialization or XML serialization just for general persistence reasons.</span></span> <span data-ttu-id="897de-133">データ コントラクトのシリアル化を優先的に使用してください。</span><span class="sxs-lookup"><span data-stu-id="897de-133">Prefer data contract serialization instead</span></span>

#### <a name="data-contract-serialization"></a><span data-ttu-id="897de-134">データ コントラクトのシリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-134">Data contract serialization</span></span>
 <span data-ttu-id="897de-135"><xref:System.Runtime.Serialization.DataContractAttribute> を型に適用し、<xref:System.Runtime.Serialization.DataMemberAttribute> をその型のメンバー (フィールドおよびプロパティ) に適用することによって、型でデータ コントラクトのシリアル化をサポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="897de-135">Types can support data contract serialization by applying the <xref:System.Runtime.Serialization.DataContractAttribute> to the type and the <xref:System.Runtime.Serialization.DataMemberAttribute> to the members (fields and properties) of the type.</span></span>

 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]

1. <span data-ttu-id="897de-136">型を部分信頼で使用する場合は、型のデータ メンバーをパブリックにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-136">CONSIDER marking data members of your type public if the type can be used in partial trust.</span></span> <span data-ttu-id="897de-137">完全な信頼では、データ コントラクト シリアライザーでパブリックではない型とメンバーのシリアル化と逆シリアル化を行うことが可能ですが、部分信頼の場合、パブリック メンバーのみをシリアル化および逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="897de-137">In full trust, data contract serializers can serialize and deserialize nonpublic types and members, but only public members can be serialized and deserialized in partial trust.</span></span>

2. <span data-ttu-id="897de-138">Data-MemberAttribute を持つすべてのプロパティに getter と setter を実装してください。</span><span class="sxs-lookup"><span data-stu-id="897de-138">DO implement a getter and setter on all properties that have Data-MemberAttribute.</span></span> <span data-ttu-id="897de-139">データ コントラクト シリアライザーでは、この型の getter と setter の両方がシリアル化可能と見なされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="897de-139">Data contract serializers require both the getter and the setter for the type to be considered serializable.</span></span> <span data-ttu-id="897de-140">型を部分信頼で使用しない場合は、1 つまたは両方のプロパティ アクセサーを非パブリックにできます。</span><span class="sxs-lookup"><span data-stu-id="897de-140">If the type won't be used in partial trust, one or both of the property accessors can be nonpublic.</span></span>

     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]

3. <span data-ttu-id="897de-141">逆シリアル化されたインスタンスの初期化には、シリアル化コールバックを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-141">CONSIDER using the serialization callbacks for initialization of deserialized instances.</span></span>

     <span data-ttu-id="897de-142">オブジェクトの逆シリアル化時にはコンストラクターは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="897de-142">Constructors are not called when objects are deserialized.</span></span> <span data-ttu-id="897de-143">このため、通常の構築時に実行されるすべてのロジックは、 *シリアル化のコールバック* の 1 つとして実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="897de-143">Therefore, any logic that executes during normal construction needs to be implemented as one of the *serialization callbacks*.</span></span>

     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]

     <span data-ttu-id="897de-144"><xref:System.Runtime.Serialization.OnDeserializedAttribute> 属性は最もよく使用されるコールバック属性です。</span><span class="sxs-lookup"><span data-stu-id="897de-144">The <xref:System.Runtime.Serialization.OnDeserializedAttribute> attribute is the most commonly used callback attribute.</span></span> <span data-ttu-id="897de-145">ファミリのその他の属性には、<xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute>、および <xref:System.Runtime.Serialization.OnSerializedAttribute> があります。</span><span class="sxs-lookup"><span data-stu-id="897de-145">The other attributes in the family are <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, and <xref:System.Runtime.Serialization.OnSerializedAttribute>.</span></span> <span data-ttu-id="897de-146">これらを使用して、逆シリアル化前、シリアル化前、およびシリアル化後に実行されるコールバックをマークすることができます。</span><span class="sxs-lookup"><span data-stu-id="897de-146">They can be used to mark callbacks that get executed before deserialization, before serialization, and finally, after serialization, respectively.</span></span>

4. <span data-ttu-id="897de-147">複雑なオブジェクト グラフを逆シリアル化する場合は、使用する具象型を示す <xref:System.Runtime.Serialization.KnownTypeAttribute> を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-147">CONSIDER using the <xref:System.Runtime.Serialization.KnownTypeAttribute> to indicate concrete types that should be used when deserializing a complex object graph.</span></span>

     <span data-ttu-id="897de-148">たとえば、逆シリアル化されたデータ メンバーの型を抽象クラスで表す場合、シリアライザーはインスタンス化してメンバーに割り当てる具象型を判断するために、 *既知の型* の情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="897de-148">For example, if a type of a deserialized data member is represented by an abstract class, the serializer will need the *known type* information to decide what concrete type to instantiate and assign to the member.</span></span> <span data-ttu-id="897de-149">属性を使用して既知の型を指定しない場合、明示的にシリアライザーに渡す (既知の型をシリアライザーのコンストラクターに渡します) か、構成ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="897de-149">If the known type is not specified using the attribute, it will need to be passed to the serializer explicitly (you can do it by passing known types to the serializer constructor) or it will need to be specified in the configuration file.</span></span>

     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]

     <span data-ttu-id="897de-150">既知の型のリストが静的にわからない場合 ( **Person** クラスをコンパイルした場合)、 **KnownTypeAttribute** で実行時に既知の型の一覧を返すメソッドを指すこともできます。</span><span class="sxs-lookup"><span data-stu-id="897de-150">In cases where the list of known types is not known statically (when the **Person** class is compiled), the **KnownTypeAttribute** can also point to a method that returns a list of known types at run time.</span></span>

5. <span data-ttu-id="897de-151">シリアル化可能な型を作成または変更する場合は、上位互換性と下位互換性を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="897de-151">DO consider backward and forward compatibility when creating or changing serializable types.</span></span>

     <span data-ttu-id="897de-152">シリアル化した型の将来のバージョンは、現在のバージョンの型に逆シリアル化でき、その逆も可能であることを念頭に置いてください。</span><span class="sxs-lookup"><span data-stu-id="897de-152">Keep in mind that serialized streams of future versions of your type can be deserialized into the current version of the type, and vice versa.</span></span> <span data-ttu-id="897de-153">明示的なパラメーターを使用してデータ コントラクト属性にコントラクトを保存する特別な措置を取らない限り、データ メンバーはプライベートで内部データであっても、型の将来のバージョンで名前、型、順序を変更することはできないことを理解しておいてください。シリアル化可能な型に変更を加えるときは、シリアル化の互換性をテストしてください。</span><span class="sxs-lookup"><span data-stu-id="897de-153">Make sure you understand that data members, even private and internal, cannot change their names, types, or even their order in future versions of the type unless special care is taken to preserve the contract using explicit parameters to the data contract attributes.Test compatibility of serialization when making changes to serializable types.</span></span> <span data-ttu-id="897de-154">新しいバージョンを古いバージョンに逆シリアル化したり、その逆も試してみてください。</span><span class="sxs-lookup"><span data-stu-id="897de-154">Try deserializing the new version into an old version, and vice versa.</span></span>

6. <span data-ttu-id="897de-155">異なるバージョンの型の間でラウンドトリッピングができるように、<xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-155">CONSIDER implementing <xref:System.Runtime.Serialization.IExtensibleDataObject> interface to allow round-tripping between different versions of the type.</span></span>

     <span data-ttu-id="897de-156">インターフェイスを使用すると、ラウンドトリッピングの間にデータが失われないようにシリアライザーで確認することができます。</span><span class="sxs-lookup"><span data-stu-id="897de-156">The interface allows the serializer to ensure that no data is lost during round-tripping.</span></span> <span data-ttu-id="897de-157"><xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> プロパティにより、現在のバージョンでは未知の、将来使用される型の任意のデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="897de-157">The <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property stores any data from the future version of the type that is unknown to the current version.</span></span> <span data-ttu-id="897de-158">現在のバージョンを後で将来のバージョンにシリアル化または逆シリアル化するときに、 **ExtensionData** プロパティ値を通じて、シリアル化されたストリーム内で追加データを使用できます。</span><span class="sxs-lookup"><span data-stu-id="897de-158">When the current version is subsequently serialized and deserialized into a future version, the additional data will be available in the serialized stream through the **ExtensionData** property value.</span></span>

     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]

     <span data-ttu-id="897de-159">詳細については、「[上位互換性のあるデータ コントラクト](../../framework/wcf/feature-details/forward-compatible-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="897de-159">For more information, see [Forward-Compatible Data Contracts](../../framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>

#### <a name="xml-serialization"></a><span data-ttu-id="897de-160">XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-160">XML serialization</span></span>
 <span data-ttu-id="897de-161">データ コントラクトのシリアル化は .NET Framework の主な (既定の) シリアル化テクノロジですが、データ コントラクトのシリアル化ではサポートされないシリアル化シナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="897de-161">Data contract serialization is the main (default) serialization technology in .NET Framework, but there are serialization scenarios that data contract serialization does not support.</span></span> <span data-ttu-id="897de-162">たとえば、シリアライザーによって作成または使用された XML の形状は完全に制御できません。</span><span class="sxs-lookup"><span data-stu-id="897de-162">For example, it does not give you full control over the shape of XML produced or consumed by the serializer.</span></span> <span data-ttu-id="897de-163">そのような微調整が必要な場合は、 *XML シリアル化* を使用する必要があり、このシリアル化テクノロジをサポートする型を自分でデザインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="897de-163">If such fine control is required, *XML serialization* has to be used, and you need to design your types to support this serialization technology.</span></span>

1. <span data-ttu-id="897de-164">作成された XML の形状を制御しなければならない強力な理由がない限り、XML シリアル化のために特別に型をデザインすることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="897de-164">AVOID designing your types specifically for XML Serialization, unless you have a very strong reason to control the shape of the XML produced.</span></span> <span data-ttu-id="897de-165">このシリアル化テクノロジは、前のセクションで説明したデータ コントラクトのシリアル化よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="897de-165">This serialization technology has been superseded by the Data Contract Serialization discussed in the previous section.</span></span>

     <span data-ttu-id="897de-166">言い換えれば、XML シリアル化で使用する型であることがわかっている場合を除き、<xref:System.Xml.Serialization> 名前空間の属性を新しい型に適用しないでください。</span><span class="sxs-lookup"><span data-stu-id="897de-166">In other words, don't apply attributes from the <xref:System.Xml.Serialization> namespace to new types, unless you know that the type will be used with XML Serialization.</span></span> <span data-ttu-id="897de-167">**System.Xml.Serialization** を使用して、作成された XML の形状を制御する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="897de-167">The following example shows how **System.Xml.Serialization** can be used to control the shape of the XML -produced.</span></span>

     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]

2. <span data-ttu-id="897de-168">XML シリアル化属性を適用することで提供される、シリアル化された XML の形状をより細かく制御する場合は、<xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-168">CONSIDER implementing the <xref:System.Xml.Serialization.IXmlSerializable> interface if you want even more control over the shape of the serialized XML than what's offered by applying the XML Serialization attributes.</span></span> <span data-ttu-id="897de-169">2 つのインターフェイスのメソッド、<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> と <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> を使用することで、シリアル化された XML ストリームを完全制御できます。</span><span class="sxs-lookup"><span data-stu-id="897de-169">Two methods of the interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, allow you to fully control the serialized XML stream.</span></span> <span data-ttu-id="897de-170">また、<xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 属性を適用することで、その型用に生成される XML スキーマを制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="897de-170">You can also control the XML schema that gets generated for the type by applying the <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute.</span></span>

#### <a name="runtime-serialization"></a><span data-ttu-id="897de-171">ランタイム シリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-171">Runtime serialization</span></span>
 <span data-ttu-id="897de-172">*ランタイム シリアル化* は .NET リモート処理で使用されるテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="897de-172">*Runtime serialization* is a technology used by .NET Remoting.</span></span> <span data-ttu-id="897de-173">.NET リモート処理を使用して型を変換する場合、ランタイム シリアル化がサポートされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="897de-173">If you think your types will be transported using .NET Remoting, make sure they support runtime serialization.</span></span>

 <span data-ttu-id="897de-174">*ランタイム シリアル化* の基本的なサポートは <xref:System.SerializableAttribute> 属性を適用して提供できますが、より高度なシナリオでは単純な *ランタイム シリアル化可能パターン* の実装 (-<xref:System.Runtime.Serialization.ISerializable> を実装してシリアル化コンストラクターを指定) が必要になります。</span><span class="sxs-lookup"><span data-stu-id="897de-174">The basic support for *runtime serialization* can be provided by applying the <xref:System.SerializableAttribute> attribute, and more advanced scenarios involve implementing a simple *runtime serializable pattern* (implement -<xref:System.Runtime.Serialization.ISerializable> and provide a serialization constructor).</span></span>

1. <span data-ttu-id="897de-175">使用する型で .NET リモート処理を使用する場合は、ランタイムのシリアル化をサポートすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-175">CONSIDER supporting runtime serialization if your types will be used with .NET Remoting.</span></span> <span data-ttu-id="897de-176">たとえば、<xref:System.AddIn> 名前空間は .NET リモート処理を使用するため、 **System.AddIn** アドイン間で交換されるすべての型でランタイム シリアル化をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="897de-176">For example, the <xref:System.AddIn> namespace uses .NET Remoting, and so all types exchanged between **System.AddIn** add-ins need to support runtime serialization.</span></span>

     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]

2. <span data-ttu-id="897de-177">シリアル化プロセスを完全制御する場合は、 *ランタイム シリアル化可能パターン* を実装することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="897de-177">CONSIDER implementing the *runtime serializable pattern* if you want complete control over the serialization process.</span></span> <span data-ttu-id="897de-178">たとえば、シリアル化または逆シリアル化されたデータを変換したいとします。</span><span class="sxs-lookup"><span data-stu-id="897de-178">For example, if you want to transform data as it gets serialized or deserialized.</span></span>

     <span data-ttu-id="897de-179">パターンは単純です。</span><span class="sxs-lookup"><span data-stu-id="897de-179">The pattern is very simple.</span></span> <span data-ttu-id="897de-180">必要な作業は、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装し、オブジェクトを逆シリアル化するときに使用する特別なコンストラクターを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="897de-180">All you need to do is implement the <xref:System.Runtime.Serialization.ISerializable> interface and provide a special constructor that is used when the object is deserialized.</span></span>

     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]

3. <span data-ttu-id="897de-181">このサンプルに示すように、シリアル化コンストラクターを保護し、型と名前を指定した 2 つのパラメーターを用意してください。</span><span class="sxs-lookup"><span data-stu-id="897de-181">DO make the serialization constructor protected and provide two parameters typed and named exactly as shown in the sample here.</span></span>

     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]

4. <span data-ttu-id="897de-182">ISerializable メンバーを明示的に実装してください。</span><span class="sxs-lookup"><span data-stu-id="897de-182">DO implement the ISerializable members explicitly.</span></span>

     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]

5. <span data-ttu-id="897de-183">**ISerializable.GetObjectData** の実装にはリンク確認要求を適用してください。</span><span class="sxs-lookup"><span data-stu-id="897de-183">DO apply a link demand to **ISerializable.GetObjectData** implementation.</span></span> <span data-ttu-id="897de-184">こうすることで、完全に信頼できるコア、およびランタイムのシリアライザーだけがメンバーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="897de-184">This ensures that only fully trusted core and the runtime serializer have access to the member.</span></span>

     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]

## <a name="see-also"></a><span data-ttu-id="897de-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="897de-185">See also</span></span>

- [<span data-ttu-id="897de-186">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="897de-186">Using Data Contracts</span></span>](../../framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="897de-187">データ コントラクト シリアライザー</span><span class="sxs-lookup"><span data-stu-id="897de-187">Data Contract Serializer</span></span>](../../framework/wcf/feature-details/data-contract-serializer.md)
- [<span data-ttu-id="897de-188">データ コントラクト シリアライザーでサポートされる型</span><span class="sxs-lookup"><span data-stu-id="897de-188">Types Supported by the Data Contract Serializer</span></span>](../../framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [<span data-ttu-id="897de-189">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-189">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="897de-190">[.NET リモート処理](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="897de-190">[.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>
- [<span data-ttu-id="897de-191">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-191">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="897de-192">セキュリティとシリアル化</span><span class="sxs-lookup"><span data-stu-id="897de-192">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
