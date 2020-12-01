---
title: Secure Sockets Layerの使用
description: System.Net および拡張クラスで Secure Sockets Layer を使用し、.NET Framework のいくつかのネットワーク プロトコルの接続を暗号化するしくみについて説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: 1309e9dc594869cec7bce81ef666d9f5e06f13b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265181"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="9fcfb-103">Secure Sockets Layerの使用</span><span class="sxs-lookup"><span data-stu-id="9fcfb-103">Using Secure Sockets Layer</span></span>

<span data-ttu-id="9fcfb-104"><xref:System.Net> クラスは、Secure Sockets Layer (SSL) を使用して、複数のネットワーク プロトコルの接続を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-104">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="9fcfb-105">HTTP 接続の場合、<xref:System.Net.WebRequest> クラスと <xref:System.Net.WebResponse> クラスは SSL を使用して、SSL をサポートする Web ホストと通信します。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-105">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="9fcfb-106">SSL の使用は、指定された URI に基づいて <xref:System.Net.WebRequest> クラスで決定されます。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-106">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="9fcfb-107">URI が "https:" で始まる場合は SSL が使用されます。URI が "http:" で始まる場合は、暗号化されていない接続が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-107">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="9fcfb-108">ファイル転送プロトコル (FTP) で SSL を使用するには、<xref:System.Net.FtpWebRequest.EnableSsl> プロパティを true に設定してから <xref:System.Net.FtpWebRequest.GetResponse> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-108">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="9fcfb-109">同様に、簡易メール転送プロトコル (SMTP) で SSL を使用するには、<xref:System.Net.Mail.SmtpClient.EnableSsl> プロパティを true に設定してからメールを送信します。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-109">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="9fcfb-110"><xref:System.Net.Security.SslStream> クラスは、SSL のストリームベースの抽象化を提供します。また、SSL ハンドシェイクを構成する方法が多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-110">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fcfb-111">例</span><span class="sxs-lookup"><span data-stu-id="9fcfb-111">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="9fcfb-112">コード</span><span class="sxs-lookup"><span data-stu-id="9fcfb-112">Code</span></span>  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9fcfb-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9fcfb-113">Compiling the Code</span></span>  

 <span data-ttu-id="9fcfb-114">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-114">This example requires:</span></span>  
  
- <span data-ttu-id="9fcfb-115">**System.Net** 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="9fcfb-115">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fcfb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fcfb-116">See also</span></span>

- [<span data-ttu-id="9fcfb-117">ネットワーク プログラミングにおけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="9fcfb-117">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="9fcfb-118">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="9fcfb-118">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="9fcfb-119">証明書の選択と検証</span><span class="sxs-lookup"><span data-stu-id="9fcfb-119">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
