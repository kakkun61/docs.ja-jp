---
title: リッスン (ソケットで)
description: サーバー ソケットでネットワーク上のポートを開き、クライアントがそのポートに接続するのを待つリモート サービスを作成する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: 4249948579384ec0159ba61072126944596c8f56
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242215"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="44b31-103">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="44b31-103">Listening with Sockets</span></span>

<span data-ttu-id="44b31-104">リスナーまたはサーバー ソケットは、ネットワーク上のポートを開き、クライアントがそのポートに接続するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="44b31-104">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="44b31-105">他のネットワーク アドレス ファミリとプロトコルもありますが、この例では、TCP/IP ネットワーク用のリモート サービスを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="44b31-105">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="44b31-106">TCP/IP サービスの一意のアドレスは、ホストの IP アドレスとサービスのポート番号を組み合わせて、そのサービスのエンドポイントを作成することで定義します。</span><span class="sxs-lookup"><span data-stu-id="44b31-106">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="44b31-107"><xref:System.Net.Dns> クラスには、ローカル ネットワーク デバイスでサポートされているネットワーク アドレスに関する情報を返すメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="44b31-107">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="44b31-108">ローカル ネットワーク デバイスに複数のネットワーク アドレスがある場合、またはローカル システムが複数のネットワーク デバイスをサポートしている場合、**Dns** クラスは、すべてのネットワーク アドレスに関する情報を返します。また、アプリケーションはそのサービスに適切なアドレスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44b31-108">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="44b31-109">Internet Assigned Numbers Authority (IANA) では、一般的なサービスのポート番号が定義されています (詳細については、「[サービス名および転送プロトコル ポート番号レジストリ) を参照してください](https://www.iana.org/assignments/port-numbers)」 。</span><span class="sxs-lookup"><span data-stu-id="44b31-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="44b31-110">他のサービスが、1,024 から 65,535 の範囲内でポート番号を登録している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44b31-110">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="44b31-111">次の例では、ホスト コンピューターの **Dns** から返される最初の IP アドレスと、登録されているポート番号範囲から選択されたポート番号を組み合わせて、サーバーの <xref:System.Net.IPEndPoint> を作成しています。</span><span class="sxs-lookup"><span data-stu-id="44b31-111">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="44b31-112">ローカル エンドポイントを決定した後、<xref:System.Net.Sockets.Socket.Bind%2A> メソッドを使用して <xref:System.Net.Sockets.Socket> をそのエンドポイントと関連付け、<xref:System.Net.Sockets.Socket.Listen%2A> メソッドを使用してエンドポイントをリッスンするように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44b31-112">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="44b31-113">特定のアドレスとポートの組み合わせが既に使用されている場合、**Bind** は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="44b31-113">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="44b31-114">**Socket** と **IPEndPoint** を関連付ける例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="44b31-114">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp)
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="44b31-115">**Listen** メソッドには、**Socket** に対する保留中の接続数の上限を指定する 1 つのパラメーターがあります。この上限を超えると、サーバー ビジー エラーが接続クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="44b31-115">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="44b31-116">この例では、接続キューに格納できるクライアント数の上限は 100 個で、クライアント番号 101 にはサーバー ビジー応答が返されます。</span><span class="sxs-lookup"><span data-stu-id="44b31-116">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b31-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="44b31-117">See also</span></span>

- [<span data-ttu-id="44b31-118">同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="44b31-118">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="44b31-119">非同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="44b31-119">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="44b31-120">クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="44b31-120">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="44b31-121">方法: ソケットを作成する</span><span class="sxs-lookup"><span data-stu-id="44b31-121">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="44b31-122">ソケット</span><span class="sxs-lookup"><span data-stu-id="44b31-122">Sockets</span></span>](sockets.md)
