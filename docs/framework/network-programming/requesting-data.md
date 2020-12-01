---
title: データの要求
description: プラグ可能なプロトコルを利用することで、単一のインターフェイスを使用して複数のプロトコルからデータを取得するアプリケーションを開発するしくみについて説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
ms.openlocfilehash: 87ad0144f57bdca0e0235aea30c4ab450cc890f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279299"
---
# <a name="requesting-data"></a><span data-ttu-id="50bee-103">データの要求</span><span class="sxs-lookup"><span data-stu-id="50bee-103">Requesting Data</span></span>

<span data-ttu-id="50bee-104">今日のインターネットの分散操作環境で動作するアプリケーションを開発するには、あらゆる種類のリソースからデータを取得するための効率的で使いやすい方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="50bee-104">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="50bee-105">プラグ可能なプロトコルを使うと、単一のインターフェイスを使って複数のインターネット プロトコルからデータを取得するアプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="50bee-105">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="50bee-106">インターネット サーバーへのデータのアップロードとサーバーからのダウンロード</span><span class="sxs-lookup"><span data-stu-id="50bee-106">Uploading and Downloading Data from an Internet Server</span></span>  

 <span data-ttu-id="50bee-107">単純な要求/応答トランザクションの場合、<xref:System.Net.WebClient> クラスが、インターネット サーバーとの間でデータをアップロードまたはダウンロードする最も簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="50bee-107">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="50bee-108">**WebClient** には、ファイルのアップロードとダウンロード、ストリームの送信と受信、およびサーバーへのデータ バッファーの送信と応答の受信を行うメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="50bee-108">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="50bee-109">**WebClient** は、<xref:System.Net.WebRequest> および <xref:System.Net.WebResponse> クラスを使ってインターネット リソースへの実際の接続を行うので、登録されているどのプラグ可能プロトコルでも使用可能です。</span><span class="sxs-lookup"><span data-stu-id="50bee-109">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="50bee-110">より複雑なトランザクションを行う必要があるクライアント アプリケーションは、**WebRequest** クラスとその子孫を使って、サーバーにデータを要求します。</span><span class="sxs-lookup"><span data-stu-id="50bee-110">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="50bee-111">**WebRequest** は、サーバーへの接続、要求の送信、応答の受信の詳細をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="50bee-111">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="50bee-112">**WebRequest** は、プラグ可能なプロトコルを使うすべてのアプリケーションで使うことができるプロパティとメソッドのセットを定義している抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="50bee-112">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="50bee-113">**WebRequest** の子孫 (<xref:System.Net.HttpWebRequest> など) は、**WebRequest** によって定義されているプロパティとメソッドを、基になるプロトコルと整合性があるように実装します。</span><span class="sxs-lookup"><span data-stu-id="50bee-113">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="50bee-114">**WebRequest** クラスは、<xref:System.Net.WebRequest.Create%2A> メソッドに渡された URI の値を使って、作成する特定の派生クラス インスタンスを決定することで、**WebRequest** の子孫のプロトコル固有のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="50bee-114">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="50bee-115">アプリケーションは、子孫のコンストラクターを <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> メソッドに登録することで、要求の処理に使う必要のある **WebRequest** の子孫を示します。</span><span class="sxs-lookup"><span data-stu-id="50bee-115">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="50bee-116">インターネット リソースに対する要求は、**WebRequest** の <xref:System.Net.WebRequest.GetResponse%2A> メソッドを呼び出すことによって行われます。</span><span class="sxs-lookup"><span data-stu-id="50bee-116">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="50bee-117">**GetResponse** メソッドは、**WebRequest** のプロパティからプロトコル固有の要求を作成し、サーバーに TCP または UDP ソケット接続を行って、要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="50bee-117">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="50bee-118">HTTP の **Post** 要求や FTP の **Put** 要求など、サーバーにデータを送信する要求の場合は、<xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> メソッドがデータを送信するネットワーク ストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="50bee-118">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="50bee-119">**GetResponse** メソッドは、**WebRequest** と一致するプロトコル固有の **WebResponse** を返します。</span><span class="sxs-lookup"><span data-stu-id="50bee-119">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="50bee-120">**WebResponse** クラスも、プラグ可能なプロトコルを使うすべてのアプリケーションで使うことができるプロパティとメソッドを定義している抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="50bee-120">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="50bee-121">**WebResponse** の子孫は、基になるプロトコルのこれらのプロパティとメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="50bee-121">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="50bee-122">たとえば、<xref:System.Net.HttpWebResponse> クラスは、HTTP 用の **WebResponse** クラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="50bee-122">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="50bee-123">サーバーから返されたデータは、<xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> メソッドによって返されるストリームでアプリケーションに提供されます。</span><span class="sxs-lookup"><span data-stu-id="50bee-123">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="50bee-124">次の例で示すように、他のストリームと同じようにこのストリームを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="50bee-124">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="50bee-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="50bee-125">See also</span></span>

- [<span data-ttu-id="50bee-126">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="50bee-126">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="50bee-127">方法: Web ページを要求し、ストリームとして結果を取得する</span><span class="sxs-lookup"><span data-stu-id="50bee-127">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="50bee-128">方法: WebRequest に一致するプロトコル固有の WebResponse を取得する</span><span class="sxs-lookup"><span data-stu-id="50bee-128">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
