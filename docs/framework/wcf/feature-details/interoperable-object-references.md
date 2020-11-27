---
title: 相互運用可能なオブジェクト参照
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: bf395c187c46e88406bfb81798c7e359b48255e3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263231"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="b15e4-102">相互運用可能なオブジェクト参照</span><span class="sxs-lookup"><span data-stu-id="b15e4-102">Interoperable object references</span></span>

<span data-ttu-id="b15e4-103">既定では、は <xref:System.Runtime.Serialization.DataContractSerializer> 値によってオブジェクトをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="b15e4-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="b15e4-104">プロパティを使用すると、オブジェクトをシリアル化する <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> ときにオブジェクト参照を保持するようにデータコントラクトシリアライザーに指示できます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="b15e4-105">生成される XML</span><span class="sxs-lookup"><span data-stu-id="b15e4-105">Generated XML</span></span>  

 <span data-ttu-id="b15e4-106">例として、次のオブジェクトを考えます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-106">As an example, consider the following object:</span></span>  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass
{  
}  
```  
  
 <span data-ttu-id="b15e4-107"><xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `false` (既定値) に設定すると、次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="b15e4-108"><xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `true` に設定すると、次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="b15e4-109">ただし、では、 <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` `ref` `preserveObjectReferences` プロパティがに設定されている場合でも、スキーマの属性と属性が記述されていません `true` 。</span><span class="sxs-lookup"><span data-stu-id="b15e4-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="b15e4-110">IsReference の使用</span><span class="sxs-lookup"><span data-stu-id="b15e4-110">Using IsReference</span></span>  

 <span data-ttu-id="b15e4-111">記述されたスキーマに従って有効なオブジェクト参照情報を生成するには、 <xref:System.Runtime.Serialization.DataContractAttribute> 属性を型に適用し、 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> フラグをに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="b15e4-112">次の例では、 `X` 前の例でを追加してクラスを変更し `IsReference` ます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
```csharp
[DataContract(IsReference=true)]
public class X
{  
     SomeClass someInstance = new SomeClass();
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember]
     public SomeClass B = someInstance;
}
  
public class SomeClass
{
}  
````

 <span data-ttu-id="b15e4-113">次のような XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="b15e4-114">`IsReference` を使用すると、メッセージのラウンド トリップに対応できます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="b15e4-115">このメソッドを使用しない場合、スキーマから型が生成されるときに、その型の XML 出力は、最初に想定したスキーマと必ずしも互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="b15e4-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="b15e4-116">つまり、`id` 属性と `ref` 属性がシリアル化されたとしても、元のスキーマによってこれらの属性 (またはすべての属性) が拒否される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b15e4-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="b15e4-117">`IsReference`データメンバーに適用されると、ラウンドトリップ時にメンバーは引き続き *参照可能* として認識されます。</span><span class="sxs-lookup"><span data-stu-id="b15e4-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15e4-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b15e4-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
