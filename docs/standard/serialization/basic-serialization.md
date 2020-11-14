---
title: 基本的なシリアル化
description: この記事では、SerializableAttribute でクラスをシリアル化できるようにする方法について説明し、シリアル化と逆シリアル化の例を紹介します。
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: 2b75ba6875b2a4430b6776c27dead72476884fff
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282078"
---
# <a name="basic-serialization"></a><span data-ttu-id="9d224-103">基本的なシリアル化</span><span class="sxs-lookup"><span data-stu-id="9d224-103">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="9d224-104">クラスをシリアル化できるようにするための最も簡単な方法は、次に示すように <xref:System.SerializableAttribute> でマークすることです。</span><span class="sxs-lookup"><span data-stu-id="9d224-104">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="9d224-105">このクラスのインスタンスをファイルにシリアル化する方法を、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="9d224-105">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
<span data-ttu-id="9d224-106">この例では、バイナリ フォーマッタを使用してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="9d224-106">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="9d224-107">必要な作業は、使用するストリームのインスタンスとフォーマッタを作成し、フォーマッタで **Serialize** メソッドを呼び出すことだけです。</span><span class="sxs-lookup"><span data-stu-id="9d224-107">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="9d224-108">ストリームとシリアル化するオブジェクトを、この呼び出しのパラメーターとして指定します。</span><span class="sxs-lookup"><span data-stu-id="9d224-108">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="9d224-109">この例では明示的に示されていませんが、クラスのすべてのメンバー変数は、変数がプライベートとして指定されている場合でもシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="9d224-109">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="9d224-110">この点で、バイナリ シリアル化は、パブリック フィールドのみをシリアル化する <xref:System.Xml.Serialization.XmlSerializer> クラスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="9d224-110">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="9d224-111">バイナリ シリアル化からメンバー変数を除外する方法については、「[選択的シリアル化](selective-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d224-111">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="9d224-112">オブジェクトを元の状態に復元することも、同じように簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="9d224-112">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="9d224-113">最初に、読み取るストリームと <xref:System.Runtime.Serialization.Formatter> を作成してから、フォーマッタに対してオブジェクトの逆シリアル化を指示します。</span><span class="sxs-lookup"><span data-stu-id="9d224-113">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="9d224-114">この処理を行うコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9d224-114">The code example below shows how this is done.</span></span>  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<span data-ttu-id="9d224-115">前の例で使用している <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> は非常に効率的であり、コンパクトなバイト ストリームを生成します。</span><span class="sxs-lookup"><span data-stu-id="9d224-115">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="9d224-116">このフォーマッタでシリアル化されたすべてのオブジェクトは、同じフォーマッタで逆シリアル化することもできるため、これは .NET で逆シリアル化されるオブジェクトをシリアル化するための最適なツールです。</span><span class="sxs-lookup"><span data-stu-id="9d224-116">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on .NET.</span></span> <span data-ttu-id="9d224-117">オブジェクトの逆シリアル化中は、コンストラクターが呼び出されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9d224-117">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="9d224-118">パフォーマンス上の理由から、逆シリアル化に対してこの制約が設けられています。</span><span class="sxs-lookup"><span data-stu-id="9d224-118">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="9d224-119">ただし、この制約はランタイムがオブジェクト作成者と結ぶ通常の協定の一部に違反するため、開発者は、オブジェクトをシリアル化可能としてマークするときに生じる影響を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d224-119">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="9d224-120">移植性が必要な場合には、代わりに <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="9d224-120">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="9d224-121">その場合は、コード内の **BinaryFormatter** を **SoapFormatter** に置き換え、前のコードと同様に **Serialize** および **Deserialize** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9d224-121">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="9d224-122">前の例では、このフォーマッタの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9d224-122">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
<span data-ttu-id="9d224-123">[Serializable](xref:System.SerializableAttribute) 属性は継承できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9d224-123">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="9d224-124">`MyObject` から新しいクラスを派生させる場合は、その新しいクラスもこの属性でマークする必要があります。マークしないと、このクラスをシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="9d224-124">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="9d224-125">たとえば、次に示すクラスのインスタンスをシリアル化しようとすると、`MyStuff` 型がシリアル化可能としてマークされていないことを通知する <xref:System.Runtime.Serialization.SerializationException> が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d224-125">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="9d224-126">[Serializable](xref:System.SerializableAttribute) 属性を使用すると便利ですが、このような制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="9d224-126">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="9d224-127">シリアル化するクラスをマークするタイミングについては、「[シリアル化のガイドライン](serialization-guidelines.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d224-127">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="9d224-128">クラスをコンパイルした後でシリアル化を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="9d224-128">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d224-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d224-129">See also</span></span>

- [<span data-ttu-id="9d224-130">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="9d224-130">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="9d224-131">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="9d224-131">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
