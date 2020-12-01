---
title: クライアント ソケットの使用
description: この例では、.NET Framework のソケットを使用し、リモート サービスへの TCP/IP 接続を作成する方法を示しています。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: 6982d09c20cd0d7e9d27fc63880b39e0982c86ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265194"
---
# <a name="using-client-sockets"></a><span data-ttu-id="b4c6b-103">クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="b4c6b-103">Using Client Sockets</span></span>

<span data-ttu-id="b4c6b-104"><xref:System.Net.Sockets.Socket> を使用して会話を開始するには、まずアプリケーションとリモート デバイス間にデータ パイプを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-104">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="b4c6b-105">他のネットワーク アドレス ファミリとプロトコルもありますが、この例では、リモート サービスとの TCP/IP 接続を作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-105">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="b4c6b-106">TCP/IP はネットワーク アドレスとサービス ポート番号を使用して、サービスを一意に識別しています。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-106">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="b4c6b-107">ネットワーク アドレスは、ネットワーク上の特定のデバイスを識別します。ポート番号は、そのデバイス上の特定のサービスの接続先を識別します。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-107">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="b4c6b-108">ネットワーク アドレスとサービス ポートの組み合わせはエンドポイントと呼ばれます。 .NET Framework では、エンドポイントは <xref:System.Net.EndPoint> クラスで表されます。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-108">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="b4c6b-109">**EndPoint** の子孫は、サポートされるアドレス ファミリごとに定義されます。IP アドレス ファミリの場合、クラスは <xref:System.Net.IPEndPoint> です。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-109">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="b4c6b-110"><xref:System.Net.Dns> クラスは、TCP/IP インターネット サービスを使用するアプリケーションにドメインネーム サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-110">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="b4c6b-111"><xref:System.Net.Dns.Resolve%2A> メソッドは、ユーザー フレンドリなドメイン名 ("host.contoso.com" など) を数値のインターネット アドレス (192.168.1.1 など) にマップするクエリを DNS サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-111">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="b4c6b-112">**Resolve** は、要求した名前のアドレスとエイリアスの一覧を含む <xref:System.Net.IPHostEntry> を返します。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-112">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="b4c6b-113">ほとんどの場合、<xref:System.Net.IPHostEntry.AddressList%2A> 配列で返された最初のアドレスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-113">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="b4c6b-114">次のコードでは、サーバー host.contoso.com の IP アドレスを含む <xref:System.Net.IPAddress> を取得します。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-114">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="b4c6b-115">Internet Assigned Numbers Authority (IANA) では、一般的なサービスのポート番号が定義されています (詳細については、「[Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)」 (サービス名および転送プロトコル ポート番号レジストリ) を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-115">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="b4c6b-116">他のサービスが、1,024 から 65,535 の範囲内でポート番号を登録している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-116">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="b4c6b-117">次のコードでは、host.contoso.com の IP アドレスとポート番号を組み合わせて、接続のリモート エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-117">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="b4c6b-118">リモート デバイスのアドレスを決定し、接続に使用するポートを選択すると、アプリケーションはそのリモート デバイスと接続の確立を試行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-118">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="b4c6b-119">次の例では、既存の **IPEndPoint** を使用してリモート デバイスに接続し、スローされるすべての例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="b4c6b-119">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4c6b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4c6b-120">See also</span></span>

- [<span data-ttu-id="b4c6b-121">同期クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="b4c6b-121">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="b4c6b-122">非同期クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="b4c6b-122">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="b4c6b-123">方法: ソケットを作成する</span><span class="sxs-lookup"><span data-stu-id="b4c6b-123">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="b4c6b-124">ソケット</span><span class="sxs-lookup"><span data-stu-id="b4c6b-124">Sockets</span></span>](sockets.md)
