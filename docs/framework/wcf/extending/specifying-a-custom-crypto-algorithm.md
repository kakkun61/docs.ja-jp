---
title: カスタム暗号アルゴリズムの指定
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: bdb7d45752be94c4c81e27161f57f765d64bd94a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294002"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="145c0-102">カスタム暗号アルゴリズムの指定</span><span class="sxs-lookup"><span data-stu-id="145c0-102">Specifying a Custom Crypto Algorithm</span></span>

<span data-ttu-id="145c0-103">WCF では、データの暗号化やデジタル署名の計算を行う際に使用するカスタム暗号アルゴリズムを指定できます。</span><span class="sxs-lookup"><span data-stu-id="145c0-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="145c0-104">そのためには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="145c0-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="145c0-105"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> の派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="145c0-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="145c0-106">アルゴリズムを登録します。</span><span class="sxs-lookup"><span data-stu-id="145c0-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="145c0-107"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> の派生クラスを使用してバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="145c0-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="145c0-108">SecurityAlgorithmSuite の派生クラスの作成</span><span class="sxs-lookup"><span data-stu-id="145c0-108">Derive a class from SecurityAlgorithmSuite</span></span>  

 <span data-ttu-id="145c0-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> は、セキュリティ関連のさまざまな操作を実行する際に使用するアルゴリズムを指定できるようにする抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="145c0-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="145c0-110">たとえば、デジタル署名のハッシュ計算やメッセージの暗号化などの操作です。</span><span class="sxs-lookup"><span data-stu-id="145c0-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="145c0-111">次のコードは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> から派生クラスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="145c0-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="145c0-112">カスタム アルゴリズムの登録</span><span class="sxs-lookup"><span data-stu-id="145c0-112">Register the Custom Algorithm</span></span>  

 <span data-ttu-id="145c0-113">登録は、構成ファイルまたは命令型コードで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="145c0-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="145c0-114">カスタム アルゴリズムを登録するには、暗号サービス プロバイダーを実装するクラスとエイリアスの間のマッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="145c0-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="145c0-115">その後、WCF サービスのバインディングでアルゴリズムを指定する際に使用する URI にエイリアスをマップします。</span><span class="sxs-lookup"><span data-stu-id="145c0-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="145c0-116">次の構成スニペットは、config でカスタム アルゴリズムを登録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="145c0-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://contoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="145c0-117"><> 要素の下のセクションで、 `cryptoClasses` SHA256CryptoServiceProvider とエイリアス "SHA256CSP" の間のマッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="145c0-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="145c0-118"><`nameEntry`> 要素は、"SHA256CSP" エイリアスと指定した URL の間のマッピングを作成し `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm` ます。</span><span class="sxs-lookup"><span data-stu-id="145c0-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="145c0-119">コードでカスタム アルゴリズムを登録するには、<xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="145c0-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="145c0-120">このメソッドによって、両方のマッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="145c0-120">This method creates both mappings.</span></span> <span data-ttu-id="145c0-121">次の例は、このメソッドを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="145c0-121">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://contoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="145c0-122">バインディングの構成</span><span class="sxs-lookup"><span data-stu-id="145c0-122">Configure the Binding</span></span>  

 <span data-ttu-id="145c0-123">バインディングを構成するには、次のコード スニペットに示すように、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> のカスタム派生クラスをバインディング設定で指定します。</span><span class="sxs-lookup"><span data-stu-id="145c0-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="145c0-124">完全なコード例については、「 [WCF セキュリティサンプルでの暗号化の俊敏性](../samples/cryptographic-agility-in-wcf-security.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="145c0-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="145c0-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="145c0-125">See also</span></span>

- [<span data-ttu-id="145c0-126">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="145c0-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="145c0-127">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="145c0-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="145c0-128">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="145c0-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="145c0-129">セキュリティの概念</span><span class="sxs-lookup"><span data-stu-id="145c0-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
