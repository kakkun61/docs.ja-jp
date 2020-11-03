---
title: '方法: データ保護の使用'
description: .NET でデータ保護 API (DPAPI) にアクセスしてデータ保護を使用する方法について説明します。
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: d3fe7ef3ddbc6e75a248101829b11a8abcb3c15a
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282047"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="b44e5-103">方法: データ保護の使用</span><span class="sxs-lookup"><span data-stu-id="b44e5-103">How to: Use Data Protection</span></span>

> [!NOTE]
> <span data-ttu-id="b44e5-104">この記事は、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="b44e5-105">ASP.NET Core の詳細については、「 [データ保護の ASP.NET Core](/aspnet/core/security/data-protection/introduction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b44e5-105">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="b44e5-106">.NET では、データ保護 API (DPAPI) にアクセスできます。これにより、現在のユーザーアカウントまたはコンピューターの情報を使用してデータを暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-106">.NET provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="b44e5-107">DPAPI を使用すると、暗号化キーを明示的に生成および格納するという困難な問題を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-107">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
<span data-ttu-id="b44e5-108">バイト配列のコピーを暗号化するには、<xref:System.Security.Cryptography.ProtectedData> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b44e5-108">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="b44e5-109">この機能は、.NET Framework、.NET Core、.NET 5 で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-109">This functionality is available in .NET Framework, .NET Core, and .NET 5.</span></span>  <span data-ttu-id="b44e5-110">現在のユーザー アカウントによって暗号化されたデータは、同じユーザー アカウントによってのみ復号化できることを指定できます。あるいは、現在のユーザー アカウントによって暗号化されたデータは、コンピューター上の任意のアカウントによって復号化できることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-110">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="b44e5-111"><xref:System.Security.Cryptography.ProtectedData> オプションの詳しい説明については、「<xref:System.Security.Cryptography.DataProtectionScope> 列挙型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b44e5-111">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
## <a name="encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="b44e5-112">データ保護を使用してデータをファイルまたはストリームに暗号化する</span><span class="sxs-lookup"><span data-stu-id="b44e5-112">Encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="b44e5-113">ランダム エントロピを作成します。</span><span class="sxs-lookup"><span data-stu-id="b44e5-113">Create random entropy.</span></span>  
  
2. <span data-ttu-id="b44e5-114">暗号化するバイト配列、エントロピ、およびデータ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedData.Protect%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b44e5-114">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="b44e5-115">ファイルまたはストリームに暗号化されたデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-115">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="b44e5-116">データ保護を使用してファイルやストリームからデータを復号化するには</span><span class="sxs-lookup"><span data-stu-id="b44e5-116">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="b44e5-117">ファイルまたはストリームから暗号化されたデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b44e5-117">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="b44e5-118">復号化するバイト配列およびデータ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b44e5-118">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b44e5-119">例</span><span class="sxs-lookup"><span data-stu-id="b44e5-119">Example</span></span>

<span data-ttu-id="b44e5-120">次のコード例は、暗号化と復号化の 2 つの形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="b44e5-120">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="b44e5-121">最初に、コード例では、メモリ内のバイト配列を暗号化してから復号化します。</span><span class="sxs-lookup"><span data-stu-id="b44e5-121">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="b44e5-122">次に、コード例では、バイト配列のコピーを暗号化し、ファイルに保存して、そのファイルからデータを読み込み、その後データを復号化しています。</span><span class="sxs-lookup"><span data-stu-id="b44e5-122">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="b44e5-123">例では、元のデータ、暗号化されたデータ、および復号化されたデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-123">The example displays the original data, the encrypted data, and the decrypted data.</span></span>

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b44e5-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b44e5-124">Compiling the Code</span></span>  

<span data-ttu-id="b44e5-125">この例は、.NET Framework を対象とし、Windows で実行している場合にのみ、コンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="b44e5-125">This example compiles and runs only when targeting .NET Framework and running on Windows.</span></span>

- <span data-ttu-id="b44e5-126">`System.Security.dll` への参照を含めます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-126">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="b44e5-127"><xref:System>、<xref:System.IO>、<xref:System.Security.Cryptography>、および <xref:System.Text> 名前空間を含めます。</span><span class="sxs-lookup"><span data-stu-id="b44e5-127">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44e5-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b44e5-128">See also</span></span>

- [<span data-ttu-id="b44e5-129">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="b44e5-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="b44e5-130">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="b44e5-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="b44e5-131">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="b44e5-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [<span data-ttu-id="b44e5-132">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b44e5-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
