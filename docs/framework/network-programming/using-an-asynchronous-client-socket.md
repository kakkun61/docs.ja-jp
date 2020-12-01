---
title: 非同期クライアント ソケットの使用
description: この例では、非同期クライアント ソケットを示しています。 .NET Framework 非同期プログラミングでは、接続の処理中もアプリケーションの実行を続行できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: af5379533e51e7488d673359dc24268c6329c082
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265220"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="a613a-104">非同期クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="a613a-104">Using an Asynchronous Client Socket</span></span>

<span data-ttu-id="a613a-105">ネットワーク操作が完了するまで待機している間、非同期クライアント ソケットはアプリケーションを一時停止しません。</span><span class="sxs-lookup"><span data-stu-id="a613a-105">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="a613a-106">標準の .NET Framework 非同期プログラミング モデルを使用して、1 つのスレッドでネットワーク接続を処理しながら、アプリケーションは元のスレッドで実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="a613a-106">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="a613a-107">ネットワークの使用量が多いアプリケーションや、ネットワーク操作が完了するのを待機してから完了することができないアプリケーションの場合、非同期ソケットが適しています。</span><span class="sxs-lookup"><span data-stu-id="a613a-107">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="a613a-108">非同期メソッドの場合、<xref:System.Net.Sockets.Socket> クラスは .NET Framework の名前付けパターンに従います。たとえば、同期の <xref:System.Net.Sockets.Socket.Receive%2A> メソッドは非同期の <xref:System.Net.Sockets.Socket.BeginReceive%2A> メソッドと <xref:System.Net.Sockets.Socket.EndReceive%2A> メソッドに対応します。</span><span class="sxs-lookup"><span data-stu-id="a613a-108">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="a613a-109">非同期操作には、操作の結果を返すコールバック メソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="a613a-109">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="a613a-110">結果を知る必要がないアプリケーションの場合、コールバック メソッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a613a-110">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="a613a-111">このセクションのコード例では、ネットワーク デバイスへの接続を開始するメソッドと接続を完了するコールバック メソッド、データの送信を開始するメソッドと送信を完了するコールバック メソッド、およびデータの受信を開始するメソッドとデータの受信を終了するコールバック メソッドの使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a613a-111">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="a613a-112">非同期ソケットは、システム スレッド プールの複数のスレッドを使用して、ネットワーク接続を処理します。</span><span class="sxs-lookup"><span data-stu-id="a613a-112">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="a613a-113">1 つのスレッドは、データの送信または受信の開始を担当し、他のスレッドは、ネットワーク デバイスへの接続を完了し、データを送信または受信します。</span><span class="sxs-lookup"><span data-stu-id="a613a-113">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="a613a-114">以下の例では、<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> クラスのインスタンスを使用してメイン スレッドの実行を停止し、実行を続行できるようになったらシグナルを送ります。</span><span class="sxs-lookup"><span data-stu-id="a613a-114">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="a613a-115">次の例では、非同期ソケットをネットワーク デバイスに接続するために、`Connect` メソッドで **Socket** を開始してから <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> メソッドを呼び出し、ネットワーク デバイスを表すリモート エンドポイント、connect のコールバック メソッド、および状態オブジェクト (クライアントの **Socket**) を渡します。このオブジェクトは、非同期呼び出しの間で状態を渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a613a-115">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="a613a-116">この例では、指定した **Socket** を指定したエンドポイントに接続する `Connect` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-116">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="a613a-117">`connectDone` というグローバル **ManualResetEvent** があるとします。</span><span class="sxs-lookup"><span data-stu-id="a613a-117">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 <span data-ttu-id="a613a-118">connect のコールバック メソッド `ConnectCallback` は <xref:System.AsyncCallback> デリゲートを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-118">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="a613a-119">リモート デバイスが使用できるようになるとリモート デバイスに接続してから、**ManualResetEvent** `connectDone` を設定して接続が完了したというシグナルをアプリケーションのスレッドに送ります。</span><span class="sxs-lookup"><span data-stu-id="a613a-119">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="a613a-120">次のコードでは、`ConnectCallback` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-120">The following code implements the `ConnectCallback` method.</span></span>  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="a613a-121">例のメソッド `Send` は指定した文字列データを ASCII 形式でエンコードし、指定したソケットが示すネットワーク デバイスに非同期に送信します。</span><span class="sxs-lookup"><span data-stu-id="a613a-121">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="a613a-122">次の例では、`Send` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-122">The following example implements the `Send` method.</span></span>  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 <span data-ttu-id="a613a-123">send のコールバック メソッド `SendCallback` は <xref:System.AsyncCallback> デリゲートを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-123">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="a613a-124">ネットワーク デバイスに受信する準備が整ったらデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="a613a-124">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="a613a-125">次の例では、`SendCallback` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-125">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="a613a-126">`sendDone` というグローバル **ManualResetEvent** があるとします。</span><span class="sxs-lookup"><span data-stu-id="a613a-126">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="a613a-127">クライアント ソケットからデータを読み取るには、非同期呼び出しの間で値を渡す状態オブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="a613a-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="a613a-128">次のクラスは、クライアント ソケットからデータを受信する状態オブジェクトの例です。</span><span class="sxs-lookup"><span data-stu-id="a613a-128">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="a613a-129">クライアント ソケットのフィールド、受信したデータのバッキング フィールド、受信データ文字列を保持する <xref:System.Text.StringBuilder> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a613a-129">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="a613a-130">これらのフィールドを状態オブジェクトに格納することで、複数の呼び出し間で値を保持し、クライアント ソケットからデータ読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a613a-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="a613a-131">例の `Receive` メソッドは、状態オブジェクトを設定してから、**BeginReceive** メソッドを呼び出してクライアント ソケットからデータを非同期に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a613a-131">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="a613a-132">`Receive` メソッドを実装する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a613a-132">The following example implements the `Receive` method.</span></span>  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="a613a-133">receive のコールバック メソッド `ReceiveCallback` は **AsyncCallback** デリゲートを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-133">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="a613a-134">このコールバック メソッドはネットワーク デバイスからデータを受信し、メッセージ文字列を構築します。</span><span class="sxs-lookup"><span data-stu-id="a613a-134">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="a613a-135">また、ネットワークからデータ バッファーに 1 から数バイトのデータを読み取ってから、クライアントから送信されたデータが完了するまで、**BeginReceive** メソッドを再び呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a613a-135">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="a613a-136">クライアントからすべてのデータを読み取ると、`ReceiveCallback` は **ManualResetEvent** `sendDone` を設定することで、データが完了したというシグナルをアプリケーション スレッドに送ります。</span><span class="sxs-lookup"><span data-stu-id="a613a-136">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="a613a-137">次のコード例では、`ReceiveCallback` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a613a-137">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="a613a-138">受け取った文字列を保持する `response` というグローバル文字列と、`receiveDone` というグローバル **ManualResetEvent** があります。</span><span class="sxs-lookup"><span data-stu-id="a613a-138">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="a613a-139">ネットワーク セッションを正常に終了するには、サーバーがクライアント ソケットをシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a613a-139">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a613a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a613a-140">See also</span></span>

- [<span data-ttu-id="a613a-141">同期クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="a613a-141">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="a613a-142">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="a613a-142">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="a613a-143">非同期クライアント ソケットの例</span><span class="sxs-lookup"><span data-stu-id="a613a-143">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)
