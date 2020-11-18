---
title: 暗号化と復号化のためのキーの生成
description: .NET で暗号化と復号化を行うための対称キーと非対称キーを作成して管理する方法について説明します。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: aa95204a90f2aee684cdd20095d1816e890a0306
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831079"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="ffcc2-103">暗号化と復号化のためのキーの生成</span><span class="sxs-lookup"><span data-stu-id="ffcc2-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="ffcc2-104">キーの作成と管理は、暗号プロセスの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="ffcc2-105">対称アルゴリズムでは、キーと初期化ベクター (IV) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="ffcc2-106">キーは、データの暗号化解除を許可しないユーザーに対しては秘密にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="ffcc2-107">IV は秘密にする必要はありませんが、セッションごとに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="ffcc2-108">非対称アルゴリズムでは、公開キーと秘密キーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="ffcc2-109">公開キーはだれに公開してもかまいせんが、秘密キーを知らせる相手は、公開キーで暗号化されたデータを復号化する人だけにします。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="ffcc2-110">このセクションでは、対称アルゴリズムと非対称アルゴリズムの両方について、キーを作成して管理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="ffcc2-111">対称キー</span><span class="sxs-lookup"><span data-stu-id="ffcc2-111">Symmetric Keys</span></span>  
 <span data-ttu-id="ffcc2-112">.NET によって提供される対称暗号化クラスでは、データを暗号化および復号化するために、キーと新しい初期化ベクター (IV) が必要です。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-112">The symmetric encryption classes supplied by .NET require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="ffcc2-113">パラメーターなしのメソッドを使用して、いずれかのマネージ対称暗号化クラスの新しいインスタンスを作成するたびに、 `Create()` 新しいキーと IV が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless `Create()` method, a new key and IV are automatically created.</span></span> <span data-ttu-id="ffcc2-114">自分のデータを復号化できるようにする相手は、自分と同じキーおよび IV を所有し、同じアルゴリズムを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="ffcc2-115">一般に、キーと IV はセッションごとに新しく作成する必要があり、キーも IV も格納して後のセッションで使用することは望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="ffcc2-116">通常、共通キーと IV を離れた場所にいる人へ送信するためには、非対称暗号化方式を使用して共通キーを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="ffcc2-117">これらの値を暗号化せずに安全でないネットワーク経由で送信することは、値を傍受した人ならだれでもデータを暗号化解除できるようになるため危険です。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span>  
  
 <span data-ttu-id="ffcc2-118">次の例は、アルゴリズムの既定の実装クラスの新しいインスタンスを作成する方法を示して <xref:System.Security.Cryptography.Aes> います。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-118">The following example shows the creation of a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 <span data-ttu-id="ffcc2-119">上記のコードを実行すると新しいキーと IV が生成され、それぞれ **Key** プロパティと **IV** プロパティに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="ffcc2-120">複数のキーを生成する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="ffcc2-121">このような状況では、対称アルゴリズムを実装するクラスの新しいインスタンスを作成し、次に **GenerateKey** および **GenerateIV** メソッドを呼び出すことによって新しいキーと IV を作成します。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="ffcc2-122">次のコード例は、対称暗号化クラスの新しいインスタンスが作成された後に、新しいキーと Iv を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 <span data-ttu-id="ffcc2-123">上記のコードを実行すると、 **Aes** の新しいインスタンスが作成されるときにキーと IV が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-123">When the preceding code is executed, a key and IV are generated when the new instance of **Aes** is made.</span></span> <span data-ttu-id="ffcc2-124">**GenerateKey** メソッドと **GenerateIV** メソッドを呼び出すと、別のキーと IV が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>
  
## <a name="asymmetric-keys"></a><span data-ttu-id="ffcc2-125">非対称キー</span><span class="sxs-lookup"><span data-stu-id="ffcc2-125">Asymmetric Keys</span></span>

 <span data-ttu-id="ffcc2-126">.NET には、 <xref:System.Security.Cryptography.RSA> 非対称暗号化用のクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-126">.NET provides the <xref:System.Security.Cryptography.RSA> class for asymmetric encryption.</span></span> <span data-ttu-id="ffcc2-127">このクラスは、パラメーターなしのメソッドを使用して新しいインスタンスを作成するときに、公開キーと秘密キーのペアを作成し `Create()` ます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-127">This class creates a public/private key pair when you use the parameterless `Create()` method to create a new instance.</span></span> <span data-ttu-id="ffcc2-128">非対称キーは、複数のセッションで使用できるように格納したり、1 つのセッション専用として生成したりできます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="ffcc2-129">公開キーは一般に公開できますが、秘密キーは厳密に保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="ffcc2-130">非対称アルゴリズム クラスの新しいインスタンスを作成すると、公開キーと秘密キーのペアが常に生成されます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="ffcc2-131">クラスの新しいインスタンスが作成された後、キー情報を <xref:System.Security.Cryptography.RSA.ExportParameters%2A> 保持する構造体を返すメソッドを使用して、キー情報を抽出でき <xref:System.Security.Cryptography.RSAParameters> ます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-131">After a new instance of the class is created, the key information can be extracted using the <xref:System.Security.Cryptography.RSA.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span> <span data-ttu-id="ffcc2-132">メソッドは、公開キー情報だけを返すか、公開キーと秘密キーの両方の情報を返すかを示すブール値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-132">The method accepts a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span>

<span data-ttu-id="ffcc2-133">また、次のような重要な情報を抽出するためのメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-133">There are also other methods that let you extract key information, such as:</span></span>

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

<span data-ttu-id="ffcc2-134">**RSA** インスタンスは、メソッドを使用して、 **RSAParameters** 構造体の値に初期化でき <xref:System.Security.Cryptography.RSA.ImportParameters%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-134">An **RSA** instance can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A> method.</span></span> <span data-ttu-id="ffcc2-135">または、メソッドを使用して新しいインスタンスを作成し <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-135">Or create a new instance by using the <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ffcc2-136">非対称秘密キーは、ローカル コンピューターにそのまま平文として保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="ffcc2-137">秘密キーを格納する必要がある場合は、キー コンテナーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="ffcc2-138">秘密キーをキーコンテナーに格納する方法の詳細については、「 [方法: キーコンテナーに非対称キーを格納](how-to-store-asymmetric-keys-in-a-key-container.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-138">For more information about how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="ffcc2-139">次のコード例では、 **RSA** クラスの新しいインスタンスを作成し、公開キーと秘密キーのペアを作成して、公開キー情報を **RSAParameters** 構造体に保存します。</span><span class="sxs-lookup"><span data-stu-id="ffcc2-139">The following code example creates a new instance of the **RSA** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffcc2-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffcc2-140">See also</span></span>

- [<span data-ttu-id="ffcc2-141">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="ffcc2-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="ffcc2-142">データの復号化</span><span class="sxs-lookup"><span data-stu-id="ffcc2-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="ffcc2-143">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="ffcc2-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="ffcc2-144">方法: キー コンテナーに非対称キーを格納する</span><span class="sxs-lookup"><span data-stu-id="ffcc2-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
- [<span data-ttu-id="ffcc2-145">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="ffcc2-145">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="ffcc2-146">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ffcc2-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
