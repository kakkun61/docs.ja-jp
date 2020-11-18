---
title: '方法: X.509 証明書で XML 要素を暗号化する'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: 5007404c1e6e872c169ce7ce71425f14d20d3a25
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820190"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="4ee1b-102">方法: X.509 証明書で XML 要素を暗号化する</span><span class="sxs-lookup"><span data-stu-id="4ee1b-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="4ee1b-103"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="4ee1b-104">XML 暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="4ee1b-105">XML 暗号化標準の詳細については、「」にある XML 暗号化の World Wide Web コンソーシアム (W3C) の仕様を参照してください <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="4ee1b-106">XML の暗号化を使用すると、任意の XML 要素またはドキュメントを、暗号化された XML データを含む <`EncryptedData`> 要素があるドキュメントに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="4ee1b-107"><`EncryptedData`> 要素には、暗号化時に使用されたキーとプロセスに関する情報が含まれているサブ要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="4ee1b-108">XML の暗号化を使用すると、ドキュメントに複数の暗号化された要素を含められるだけでなく、要素を複数回暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="4ee1b-109">この手順のコード例は、<`EncryptedData`> 要素の作成方法と共に、後の復号化時に使用するいくつかのその他のサブ要素の作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
<span data-ttu-id="4ee1b-110">この例では、2 つのキーを使用して XML 要素を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="4ee1b-111">この例では、証明書をプログラムによって取得し、それを使用して、メソッドを使用して XML 要素を暗号化し <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-111">The example programmatically retrieves a certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="4ee1b-112">内部的には、<xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> メソッドは別のセッション キーを作成し、これを使用して XML ドキュメントを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-112">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="4ee1b-113">このメソッドでは、セッション キーを暗号化し、新しい <`EncryptedData`> 要素内に暗号化された XML と共に保存します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-113">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  

<span data-ttu-id="4ee1b-114">XML 要素の暗号化を解除するには、メソッドを呼び出します <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 。これにより、ストアから x.509 証明書が自動的に取得され、必要な復号化が実行されます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-114">To decrypt the XML element, call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="4ee1b-115">この手順を使用して暗号化された XML 要素を復号化する方法の詳細については、「[方法: X.509 証明書で XML 要素を復号化する](how-to-decrypt-xml-elements-with-x-509-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-115">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
<span data-ttu-id="4ee1b-116">この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況や、1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-116">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="4ee1b-117">X.509 証明書で XML 要素を暗号化するには</span><span class="sxs-lookup"><span data-stu-id="4ee1b-117">To encrypt an XML element with an X.509 certificate</span></span>  

<span data-ttu-id="4ee1b-118">この例を実行するには、テスト証明書を作成して証明書ストアに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-118">To run this example, you need to create a test certificate and save it in a certificate store.</span></span> <span data-ttu-id="4ee1b-119">このタスクの手順は、Windows [証明書作成ツール (Makecert.exe)](/windows/desktop/SecCrypto/makecert)に対してのみ提供されています。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-119">Instructions for that task are provided only for the Windows [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span></span>

1. <span data-ttu-id="4ee1b-120">[Makecert.exe](/windows/desktop/SecCrypto/makecert)を使用してテストの x.509 証明書を生成し、ローカルユーザーストアに配置します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-120">Use [Makecert.exe](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="4ee1b-121">交換キーを生成する必要があり、このキーをエクスポート可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-121">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="4ee1b-122">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-122">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="4ee1b-123"><xref:System.Security.Cryptography.X509Certificates.X509Store> オブジェクトを作成し、このオブジェクトを現在のユーザー ストアを開くように初期化します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-123">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="4ee1b-124">ストアを読み取り専用モードで開きます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-124">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="4ee1b-125"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> を、ストア内のすべての証明書で初期化します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-125">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="4ee1b-126">ストア内の証明書を列挙し、適切な名前を持つ証明書を検索します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-126">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="4ee1b-127">この例では、証明書の名前は `"CN=XML_ENC_TEST_CERT"` です。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-127">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="4ee1b-128">証明書が見つかったら、ストアを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-128">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="4ee1b-129">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-129">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="4ee1b-130"><xref:System.Xml.XmlDocument> オブジェクトには、暗号化する XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-130">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="4ee1b-131"><xref:System.Xml.XmlDocument> オブジェクトで指定された要素を検索し、暗号化する要素を表す新しい <xref:System.Xml.XmlElement> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-131">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="4ee1b-132">この例では、`"creditcard"` 要素が暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-132">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="4ee1b-133"><xref:System.Security.Cryptography.Xml.EncryptedXml> クラスのインスタンスを新規作成し、これを使用して、X.509 証明書によって指定された要素を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-133">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="4ee1b-134"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> メソッドは、暗号化された要素を、<xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトとして返します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-134">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="4ee1b-135">元の <xref:System.Xml.XmlDocument> オブジェクトの要素を <xref:System.Security.Cryptography.Xml.EncryptedData> 要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-135">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="4ee1b-136"><xref:System.Xml.XmlDocument> オブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-136">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="4ee1b-137">例</span><span class="sxs-lookup"><span data-stu-id="4ee1b-137">Example</span></span>  
 <span data-ttu-id="4ee1b-138">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-138">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="4ee1b-139">また、`"test.xml"` には `"creditcard"` 要素が含まれることも前提としています。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-139">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="4ee1b-140">次の XML を `test.xml` というファイルに配置し、この例で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-140">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ee1b-141">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="4ee1b-141">Compiling the Code</span></span>  
  
- <span data-ttu-id="4ee1b-142">.NET Framework を対象とするプロジェクトでは、への参照を含め `System.Security.dll` ます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-142">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="4ee1b-143">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-143">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="4ee1b-144">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-144">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="4ee1b-145">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4ee1b-145">.NET Security</span></span>
  
<span data-ttu-id="4ee1b-146">この例で使用される X.509 証明書は、テスト専用です。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-146">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="4ee1b-147">アプリケーションでは、信頼された証明機関によって生成された x.509 証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ee1b-147">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee1b-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ee1b-148">See also</span></span>

- [<span data-ttu-id="4ee1b-149">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="4ee1b-149">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="4ee1b-150">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="4ee1b-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="4ee1b-151">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="4ee1b-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="4ee1b-152">方法: X.509 証明書で XML 要素を復号化する</span><span class="sxs-lookup"><span data-stu-id="4ee1b-152">How to: Decrypt XML Elements with X.509 Certificates</span></span>](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="4ee1b-153">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4ee1b-153">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
