---
title: '方法: ソケットを作成する'
description: ソケットを初期化してリモート デバイスと通信する方法について学習します。 Socket クラスを使用して、アドレス ファミリ、ソケットの種類、プロトコルの種類を指定します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 9746b814188a4dc92463399542a6044501d0da12
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287398"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="926c6-104">方法: ソケットを作成する</span><span class="sxs-lookup"><span data-stu-id="926c6-104">How to: Create a Socket</span></span>

<span data-ttu-id="926c6-105">ソケットを使用してリモート デバイスと通信するには、ソケットをプロトコルとネットワーク アドレスの情報を使用して事前に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="926c6-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="926c6-106"><xref:System.Net.Sockets.Socket> クラスのコンストラクターには、アドレス ファミリ、ソケットの種類、およびソケットが接続を行うために使用するプロトコルの種類を指定するパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="926c6-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="926c6-107">例</span><span class="sxs-lookup"><span data-stu-id="926c6-107">Example</span></span>  

 <span data-ttu-id="926c6-108">次の例では、インターネットなどの TCP/IP ベースのネットワーク上で通信するために使用できるソケットを作成します。</span><span class="sxs-lookup"><span data-stu-id="926c6-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="926c6-109">TCP ではなく UDP を使用するには、次の例のように、プロトコルの種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="926c6-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="926c6-110"><xref:System.Net.Sockets.AddressFamily> 列挙体では、ネットワーク アドレスを解決するために **Socket** クラスで使用される標準のアドレス ファミリを指定します (たとえば、**AddressFamily.InterNetwork** メンバーは IPv4 アドレス ファミリを指定します)。</span><span class="sxs-lookup"><span data-stu-id="926c6-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="926c6-111"><xref:System.Net.Sockets.SocketType> 列挙体ではソケットの種類を指定します (たとえば、**SocketType.Stream** メンバーは、フロー制御付きでデータを送受信するための標準のソケットを示します)。</span><span class="sxs-lookup"><span data-stu-id="926c6-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="926c6-112"><xref:System.Net.Sockets.ProtocolType> 列挙体では、**Socket** での通信時に使用するネットワーク プロトコルを指定します (たとえば、**ProtocolType.Tcp** はソケットが TCP を使用することを示し、**ProtocolType.Udp** はソケットが UDP を使用することを示します)。</span><span class="sxs-lookup"><span data-stu-id="926c6-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="926c6-113">**Socket** が作成されたら、リモート エンドポイントへの接続を開始したり、リモート デバイスから接続を受信したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="926c6-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926c6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="926c6-114">See also</span></span>

- [<span data-ttu-id="926c6-115">クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="926c6-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="926c6-116">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="926c6-116">Listening with Sockets</span></span>](listening-with-sockets.md)
