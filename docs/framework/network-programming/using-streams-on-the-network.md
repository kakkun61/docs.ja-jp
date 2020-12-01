---
title: ネットワーク上でストリームを使用する
description: .NET Framework では、ネットワーク リソースはストリームとして表されます。 NetworkStream クラスでは、ネットワーク リソースを使用するために Stream クラスが実装されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: c59e4aa2edad7b28203cfce5f568f8ccb8558dbb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263114"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="04e55-104">ネットワーク上でストリームを使用する</span><span class="sxs-lookup"><span data-stu-id="04e55-104">Using Streams on the Network</span></span>

<span data-ttu-id="04e55-105">.NET Framework では、ネットワーク リソースはストリームとして表されます。</span><span class="sxs-lookup"><span data-stu-id="04e55-105">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="04e55-106">.NET Framework は、ストリームを汎用的に扱うことで、次の機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="04e55-106">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="04e55-107">Web データを送受信する一般的な方法。</span><span class="sxs-lookup"><span data-stu-id="04e55-107">A common way to send and receive Web data.</span></span> <span data-ttu-id="04e55-108">ファイルの実際のコンテンツ (HTML、XML など) にかかわらず、アプリケーションは <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> と <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> を使用してデータを送受信します。</span><span class="sxs-lookup"><span data-stu-id="04e55-108">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="04e55-109">.NET Framework 全体のストリームとの互換性。</span><span class="sxs-lookup"><span data-stu-id="04e55-109">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="04e55-110">ストリームは、.NET Framework 全体で使用されます。 .NET Framework には、ストリームを処理する高機能なインフラストラクチャがあります。</span><span class="sxs-lookup"><span data-stu-id="04e55-110">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="04e55-111">たとえば、ストリームを初期化するコードの数行を変更するだけで、<xref:System.IO.FileStream> から XML データを読み取るアプリケーションを、<xref:System.Net.Sockets.NetworkStream> からデータを読み取るように変更することができます。</span><span class="sxs-lookup"><span data-stu-id="04e55-111">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="04e55-112">**NetworkStream** クラスと他のストリームの主な違いは、**NetworkStream** はシーク不可能であり、<xref:System.Net.Sockets.NetworkStream.CanSeek%2A> プロパティは常に **false** を返し、<xref:System.Net.Sockets.NetworkStream.Seek%2A> メソッドと <xref:System.Net.Sockets.NetworkStream.Position%2A> メソッドは <xref:System.NotSupportedException> をスローする点です。</span><span class="sxs-lookup"><span data-stu-id="04e55-112">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="04e55-113">データ受信時のデータの処理。</span><span class="sxs-lookup"><span data-stu-id="04e55-113">Processing of data as it arrives.</span></span> <span data-ttu-id="04e55-114">ストリームは、アプリケーションに対して、ダウンロード対象として設定されたデータ全体を強制的に待機させるのではなく、ネットワークからデータを受信したときにデータへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="04e55-114">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="04e55-115"><xref:System.Net.Sockets> 名前空間には、特にネットワーク リソースに使用される <xref:System.IO.Stream> クラスを実装する **NetworkStream** クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="04e55-115">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="04e55-116"><xref:System.Net.Sockets> 名前空間のクラスは、**NetworkStream** クラスを使用してストリームを表します。</span><span class="sxs-lookup"><span data-stu-id="04e55-116">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="04e55-117">返されたストリームを使用してネットワークにデータを送信するには、<xref:System.Net.WebRequest> で <xref:System.Net.WebRequest.GetRequestStream%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="04e55-117">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="04e55-118">**WebRequest** は要求のヘッダーをサーバーに送信します。その後は、返されるストリームで <xref:System.IO.Stream.BeginWrite%2A>、<xref:System.IO.Stream.EndWrite%2A>、または <xref:System.IO.Stream.Write%2A> メソッドを呼び出して、ネットワーク リソースにデータを送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="04e55-118">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="04e55-119">HTTP など、一部のプロトコルでは、データを送信する前にプロトコル固有のプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04e55-119">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="04e55-120">データを送信するために、HTTP 固有のプロパティを設定する方法を示すコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="04e55-120">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="04e55-121">変数 `sendData` には送信するデータが含まれ、変数 `sendLength` は送信するデータのバイト数を示しているとします。</span><span class="sxs-lookup"><span data-stu-id="04e55-121">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
```csharp  
HttpWebRequest request =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 <span data-ttu-id="04e55-122">ネットワークからデータを受信するには、<xref:System.Net.WebResponse> で <xref:System.Net.WebResponse.GetResponseStream%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="04e55-122">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="04e55-123">その後は、返されるストリームで <xref:System.IO.Stream.BeginRead%2A>、<xref:System.IO.Stream.EndRead%2A>、または <xref:System.IO.Stream.Read%2A> メソッドを呼び出すことで、ネットワーク リソースからデータを読み取ることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="04e55-123">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="04e55-124">ネットワーク リソースからストリームを使用する場合は、次の点に留意してください。</span><span class="sxs-lookup"><span data-stu-id="04e55-124">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="04e55-125">**CanSeek** プロパティは常に **false** を返します。これは、**NetworkStream** クラスがストリーム内の位置を変更できないためです。</span><span class="sxs-lookup"><span data-stu-id="04e55-125">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="04e55-126">**Seek** メソッドと **Position** メソッドは **NotSupportedException** をスローします。</span><span class="sxs-lookup"><span data-stu-id="04e55-126">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="04e55-127">**WebRequest** と **WebResponse** を使用すると、**GetResponseStream** を呼び出して作成されるストリーム インスタンスは読み取り専用に、**GetRequestStream** を呼び出して作成されるストリーム インスタンスは書き込み専用になります。</span><span class="sxs-lookup"><span data-stu-id="04e55-127">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="04e55-128"><xref:System.IO.StreamReader> クラスを使用すると、エンコードが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="04e55-128">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="04e55-129">次のコード例では、**StreamReader** を使用して ASCII エンコードされたストリームを **WebResponse** から読み取ります (この例では要求の作成を示していません)。</span><span class="sxs-lookup"><span data-stu-id="04e55-129">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="04e55-130">ネットワーク リソースを使用できない場合、**GetResponse** の呼び出しがブロックされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04e55-130">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="04e55-131"><xref:System.Net.WebRequest.BeginGetResponse%2A> メソッドと <xref:System.Net.WebRequest.EndGetResponse%2A> メソッドによる非同期要求を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="04e55-131">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="04e55-132">サーバーへの接続を作成するときに、**GetRequestStream** の呼び出しがブロックされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04e55-132">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="04e55-133"><xref:System.Net.WebRequest.BeginGetRequestStream%2A> メソッドと <xref:System.Net.WebRequest.EndGetRequestStream%2A> メソッドによるストリームの非同期要求を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="04e55-133">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="04e55-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="04e55-134">See also</span></span>

- [<span data-ttu-id="04e55-135">方法: WebRequest クラスを使用してデータを要求する</span><span class="sxs-lookup"><span data-stu-id="04e55-135">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="04e55-136">データの要求</span><span class="sxs-lookup"><span data-stu-id="04e55-136">Requesting Data</span></span>](requesting-data.md)
