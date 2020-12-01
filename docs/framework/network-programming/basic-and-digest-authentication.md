---
title: 基本認証とダイジェスト認証
description: データを要求するために使用する WebRequest オブジェクトにアプリケーションによってユーザー名とパスワードが提供される、基本とダイジェスト認証を使用する方法について学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: e55dc58a7998824dbcfffa204008aacb815be03a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287580"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="8a5b1-103">基本認証とダイジェスト認証</span><span class="sxs-lookup"><span data-stu-id="8a5b1-103">Basic and Digest Authentication</span></span>

<span data-ttu-id="8a5b1-104">基本認証とダイジェスト認証の <xref:System.Net> 実装は、RFC2617 – HTTP 認証:基本認証とダイジェスト認証 ([World Wide Web コンソーシアム](https://www.w3.org)の Web サイトで入手可能) に従います。</span><span class="sxs-lookup"><span data-stu-id="8a5b1-104">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="8a5b1-105">基本認証とダイジェスト認証を使用するには、次の例に示すように、アプリケーションはインターネットからデータを要求するために使用される <xref:System.Net.WebRequest> オブジェクトの <xref:System.Net.WebRequest.Credentials%2A> プロパティでユーザー名とパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a5b1-105">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
> <span data-ttu-id="8a5b1-106">基本認証およびダイジェスト認証で送信されるデータは暗号化されないため、敵対者がデータを見ることができます。</span><span class="sxs-lookup"><span data-stu-id="8a5b1-106">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="8a5b1-107">また、基本認証の資格情報 (ユーザー名とパスワード) はクリア テキストで送信されるので、傍受される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a5b1-107">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a5b1-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a5b1-108">See also</span></span>

- [<span data-ttu-id="8a5b1-109">NTLM 認証および Kerberos 認証</span><span class="sxs-lookup"><span data-stu-id="8a5b1-109">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="8a5b1-110">インターネット認証</span><span class="sxs-lookup"><span data-stu-id="8a5b1-110">Internet Authentication</span></span>](internet-authentication.md)
