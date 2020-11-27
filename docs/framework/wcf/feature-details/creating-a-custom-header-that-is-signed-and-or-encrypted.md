---
title: 署名または暗号化、あるいはその両方が行われたカスタム ヘッダーの作成
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: daa594950c25ea4a5c2012183c47231b4688719e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286722"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="2248f-102">署名または暗号化、あるいはその両方が行われたカスタム ヘッダーの作成</span><span class="sxs-lookup"><span data-stu-id="2248f-102">Creating a custom header that is signed and-or encrypted</span></span>

<span data-ttu-id="2248f-103">WCF クライアントを使用して WCF 以外のサービスを呼び出す場合、状況によっては、カスタム SOAP ヘッダーが必要です。</span><span class="sxs-lookup"><span data-stu-id="2248f-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="2248f-104">WCF には正規化のバグがあり、署名および暗号化されたカスタム ヘッダーは、WCF 以外のサービスで使用できません。</span><span class="sxs-lookup"><span data-stu-id="2248f-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="2248f-105">この問題は、既定の XML 名前空間に対する正規化の誤りが原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="2248f-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="2248f-106">この問題が生じるのは、署名または暗号化、あるいはその両方が行われたカスタム ヘッダーを持つ、WCF 以外のサービスを呼び出す場合のみです。</span><span class="sxs-lookup"><span data-stu-id="2248f-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="2248f-107">サービスは、受信したメッセージに署名または暗号化、あるいはその両方が行われたカスタム ヘッダーが含まれている場合、署名を検証できません。</span><span class="sxs-lookup"><span data-stu-id="2248f-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="2248f-108">この回避策では正規化のバグを回避し、WCF 以外のサービスとの相互運用が可能になりますが、WCF サービスとの相互運用性は妨げられません。</span><span class="sxs-lookup"><span data-stu-id="2248f-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="2248f-109">カスタム ヘッダーの定義</span><span class="sxs-lookup"><span data-stu-id="2248f-109">Defining the custom header</span></span>  

 <span data-ttu-id="2248f-110">カスタム ヘッダーは、メッセージ コントラクトを定義し、ヘッダーとして送信するメンバーを <xref:System.ServiceModel.MessageHeaderAttribute> 属性を使用してマークすることで定義されます。</span><span class="sxs-lookup"><span data-stu-id="2248f-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="2248f-111">正規化のバグを回避するには、XML シリアライザーが既定の名前空間の宣言ではなくプレフィックスによってカスタム ヘッダーの名前空間を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2248f-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="2248f-112">次のコードは、メッセージ ヘッダーとして使用されるデータ型を正しい名前空間宣言で定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2248f-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
```csharp
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2248f-113">このコードでは、XML シリアライザーによってシリアル化される `msgHeaderElement` という新しい型を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="2248f-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="2248f-114">この型のインスタンスがシリアル化されると、名前空間が "h" プレフィックスで定義されるため、正規化のバグが回避されます。</span><span class="sxs-lookup"><span data-stu-id="2248f-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="2248f-115">この後、次の例に示すように、メッセージ コントラクトによって `msgHeaderElement` のインスタンスを定義し、<xref:System.ServiceModel.MessageHeaderAttribute> 属性でそのインスタンスをマークします。</span><span class="sxs-lookup"><span data-stu-id="2248f-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
```csharp
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2248f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2248f-116">See also</span></span>

- [<span data-ttu-id="2248f-117">既定のメッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="2248f-117">Default Message Contract</span></span>](../samples/default-message-contract.md)
- [<span data-ttu-id="2248f-118">メッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="2248f-118">Message Contracts</span></span>](../samples/message-contracts.md)
- [<span data-ttu-id="2248f-119">メッセージ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="2248f-119">Using Message Contracts</span></span>](using-message-contracts.md)
