---
title: 非同期要求を行う
description: System.Net クラスで、インターネット リソースへの非同期アクセスに .NET Framework の標準非同期プログラミング モデルを使用するしくみについて説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, asynchronous access
- Networking
- asynchronous requests, Internet resources
- Network Resources
- WebRequest class, asynchronous access
ms.assetid: 735d3fce-f80c-437f-b02c-5c47f5739674
ms.openlocfilehash: f6eba7a1f10e037f93b20c0e7016f083e3e24200
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258713"
---
# <a name="making-asynchronous-requests"></a><span data-ttu-id="4703a-103">非同期要求を行う</span><span class="sxs-lookup"><span data-stu-id="4703a-103">Making Asynchronous Requests</span></span>

<span data-ttu-id="4703a-104"><xref:System.Net> クラスは、インターネット リソースへの非同期アクセスに .NET Framework の標準非同期プログラミング モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="4703a-104">The <xref:System.Net> classes use the .NET Framework's standard asynchronous programming model for asynchronous access to Internet resources.</span></span> <span data-ttu-id="4703a-105"><xref:System.Net.WebRequest> クラスの <xref:System.Net.WebRequest.BeginGetResponse%2A> および <xref:System.Net.WebRequest.EndGetResponse%2A> メソッドは、インターネット リソースの非同期要求の開始と完了を行います。</span><span class="sxs-lookup"><span data-stu-id="4703a-105">The <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods of the <xref:System.Net.WebRequest> class start and complete asynchronous requests for an Internet resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4703a-106">非同期コールバック メソッドで同期呼び出しを使用すると、パフォーマンスが大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4703a-106">Using synchronous calls in asynchronous callback methods can result in severe performance penalties.</span></span> <span data-ttu-id="4703a-107">**WebRequest** とその子孫を使用して作成されたインターネット要求で、<xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> メソッドで返されたストリームを読み取るには、<xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4703a-107">Internet requests made with **WebRequest** and its descendants must use <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> to read the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="4703a-108">次のサンプル コードは、**WebRequest** クラスで非同期呼び出しを使用する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="4703a-108">The following sample code demonstrates how to use asynchronous calls with the **WebRequest** class.</span></span> <span data-ttu-id="4703a-109">このサンプルは、コマンド ラインから URI を取得し、その URI のリソースを要求し、インターネットから受信したデータをコンソールに出力するコンソール プログラムです。</span><span class="sxs-lookup"><span data-stu-id="4703a-109">The sample is a console program that takes a URI from the command line, requests the resource at the URI, and then prints data to the console as it is received from the Internet.</span></span>  
  
 <span data-ttu-id="4703a-110">このプログラムでは、独自の用途がある 2 つのクラスを定義しています。非同期呼び出し全体にデータを渡す **RequestState** クラスと、インターネット リソースに対する非同期要求を実装する **ClientGetAsync** クラスです。</span><span class="sxs-lookup"><span data-stu-id="4703a-110">The program defines two classes for its own use, the **RequestState** class, which passes data across asynchronous calls, and the **ClientGetAsync** class, which implements the asynchronous request to an Internet resource.</span></span>  
  
 <span data-ttu-id="4703a-111">**RequestState** クラスは、要求を処理する非同期メソッドの呼び出し全体について要求の状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="4703a-111">The **RequestState** class preserves the state of the request across calls to the asynchronous methods that service the request.</span></span> <span data-ttu-id="4703a-112">たとえば、リソースに対する現在の要求と応答で受信したストリームを含む **WebRequest** および <xref:System.IO.Stream> インスタンス、インターネット リソースから現在受信しているデータを含むバッファー、完全な応答を含む <xref:System.Text.StringBuilder> があります。</span><span class="sxs-lookup"><span data-stu-id="4703a-112">It contains **WebRequest** and <xref:System.IO.Stream> instances that contain the current request to the resource and the stream received in response, a buffer that contains the data currently received from the Internet resource, and a <xref:System.Text.StringBuilder> that contains the complete response.</span></span> <span data-ttu-id="4703a-113"><xref:System.AsyncCallback> メソッドが **WebRequest.BeginGetResponse** に登録されている場合、**RequestState** は *state* パラメーターとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="4703a-113">A **RequestState** is passed as the *state* parameter when the <xref:System.AsyncCallback> method is registered with **WebRequest.BeginGetResponse**.</span></span>  
  
 <span data-ttu-id="4703a-114">**ClientGetAsync** クラスは、インターネット リソースに対する非同期要求を実装し、結果の応答をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="4703a-114">The **ClientGetAsync** class implements an asynchronous request to an Internet resource and writes the resulting response to the console.</span></span> <span data-ttu-id="4703a-115">次の一覧で説明するメソッドとプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="4703a-115">It contains the methods and properties described in the following list.</span></span>  
  
- <span data-ttu-id="4703a-116">`allDone` プロパティには、要求の完了を通知する <xref:System.Threading.ManualResetEvent> クラスのインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4703a-116">The `allDone` property contains an instance of the <xref:System.Threading.ManualResetEvent> class that signals the completion of the request.</span></span>  
  
- <span data-ttu-id="4703a-117">`Main()` メソッドは、コマンド ラインを読み取り、指定されたインターネット リソースの要求を開始します。</span><span class="sxs-lookup"><span data-stu-id="4703a-117">The `Main()` method reads the command line and begins the request for the specified Internet resource.</span></span> <span data-ttu-id="4703a-118">**WebRequest** `wreq` および **RequestState** `rs` を作成し、**BeginGetResponse** を呼び出して要求の処理を開始し、`allDone.WaitOne()` メソッドを呼び出して、コールバックが完了するまでアプリケーションが終了しないようにします。</span><span class="sxs-lookup"><span data-stu-id="4703a-118">It creates the **WebRequest** `wreq` and the **RequestState** `rs`, calls **BeginGetResponse** to begin processing the request, and then calls the `allDone.WaitOne()`method so that the application will not exit until the callback is complete.</span></span> <span data-ttu-id="4703a-119">インターネット リソースから応答を読み取ると、`Main()` はその応答をコンソールに出力し、アプリケーションは終了します。</span><span class="sxs-lookup"><span data-stu-id="4703a-119">After the response is read from the Internet resource, `Main()` writes it to the console and the application ends.</span></span>  
  
- <span data-ttu-id="4703a-120">`showusage()` メソッドは、コンソールにコマンド ライン例を出力します。</span><span class="sxs-lookup"><span data-stu-id="4703a-120">The `showusage()` method writes an example command line on the console.</span></span> <span data-ttu-id="4703a-121">これは、コマンド ラインに URI が指定されていない場合に `Main()` から呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4703a-121">It is called by `Main()` when no URI is provided on the command line.</span></span>  
  
- <span data-ttu-id="4703a-122">`RespCallBack()` メソッドは、インターネット要求の非同期コールバック メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="4703a-122">The `RespCallBack()` method implements the asynchronous callback method for the Internet request.</span></span> <span data-ttu-id="4703a-123">インターネット リソースからの応答を含む **WebResponse** インスタンスを作成し、応答ストリームを取得し、非同期にストリームからデータの読み取りを開始します。</span><span class="sxs-lookup"><span data-stu-id="4703a-123">It creates the **WebResponse** instance containing the response from the Internet resource, gets the response stream, and then starts reading the data from the stream asynchronously.</span></span>  
  
- <span data-ttu-id="4703a-124">`ReadCallBack()` メソッドは、応答ストリームを読み取るための非同期コールバック メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="4703a-124">The `ReadCallBack()` method implements the asynchronous callback method for reading the response stream.</span></span> <span data-ttu-id="4703a-125">インターネット リソースから受信したデータを **RequestState** インスタンスの **ResponseData** プロパティに転送し、データが返されなくなるまで、応答ストリームの非同期読み取りを再び開始します。</span><span class="sxs-lookup"><span data-stu-id="4703a-125">It transfers data received from the Internet resource into the **ResponseData** property of the **RequestState** instance, then starts another asynchronous read of the response stream until no more data is returned.</span></span> <span data-ttu-id="4703a-126">すべてのデータが読み取られたら、`ReadCallBack()` は応答ストリームを終了し、`allDone.Set()` メソッドを呼び出して、応答全体が **ResponseData** 内にあることを示します。</span><span class="sxs-lookup"><span data-stu-id="4703a-126">Once all the data has been read, `ReadCallBack()` closes the response stream and calls the `allDone.Set()` method to indicate that the entire response is present in **ResponseData**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4703a-127">すべてのネットワーク ストリームが終了していることが重要です。</span><span class="sxs-lookup"><span data-stu-id="4703a-127">It is critical that all network streams are closed.</span></span> <span data-ttu-id="4703a-128">各要求と応答ストリームが終了していない場合、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4703a-128">If you do not close each request and response stream, your application will run out of connections to the server and be unable to process additional requests.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Threading;  
using System.Text;  
using System.IO;  
  
// The RequestState class passes data across async calls.  
public class RequestState  
{  
   const int BufferSize = 1024;  
   public StringBuilder RequestData;  
   public byte[] BufferRead;  
   public WebRequest Request;  
   public Stream ResponseStream;  
   // Create Decoder for appropriate enconding type.  
   public Decoder StreamDecode = Encoding.UTF8.GetDecoder();  
  
   public RequestState()  
   {  
      BufferRead = new byte[BufferSize];  
      RequestData = new StringBuilder(String.Empty);  
      Request = null;  
      ResponseStream = null;  
   }
}  
  
// ClientGetAsync issues the async request.  
class ClientGetAsync
{  
   public static ManualResetEvent allDone = new ManualResetEvent(false);  
   const int BUFFER_SIZE = 1024;  
  
   public static void Main(string[] args)
   {  
      if (args.Length < 1)
      {  
         showusage();  
         return;  
      }  
  
      // Get the URI from the command line.  
      Uri httpSite = new Uri(args[0]);  
  
      // Create the request object.  
      WebRequest wreq = WebRequest.Create(httpSite);  
  
      // Create the state object.  
      RequestState rs = new RequestState();  
  
      // Put the request into the state object so it can be passed around.  
      rs.Request = wreq;  
  
      // Issue the async request.  
      IAsyncResult r = (IAsyncResult) wreq.BeginGetResponse(  
         new AsyncCallback(RespCallback), rs);  
  
      // Wait until the ManualResetEvent is set so that the application
      // does not exit until after the callback is called.  
      allDone.WaitOne();  
  
      Console.WriteLine(rs.RequestData.ToString());  
   }  
  
   public static void showusage() {  
      Console.WriteLine("Attempts to GET a URL");  
      Console.WriteLine("\r\nUsage:");  
      Console.WriteLine("   ClientGetAsync URL");  
      Console.WriteLine("   Example:");  
      Console.WriteLine("      ClientGetAsync http://www.contoso.com/");  
   }  
  
   private static void RespCallback(IAsyncResult ar)  
   {  
      // Get the RequestState object from the async result.  
      RequestState rs = (RequestState) ar.AsyncState;  
  
      // Get the WebRequest from RequestState.  
      WebRequest req = rs.Request;  
  
      // Call EndGetResponse, which produces the WebResponse object  
      //  that came from the request issued above.  
      WebResponse resp = req.EndGetResponse(ar);
  
      //  Start reading data from the response stream.  
      Stream ResponseStream = resp.GetResponseStream();  
  
      // Store the response stream in RequestState to read
      // the stream asynchronously.  
      rs.ResponseStream = ResponseStream;  
  
      //  Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead  
      IAsyncResult iarRead = ResponseStream.BeginRead(rs.BufferRead, 0,
         BUFFER_SIZE, new AsyncCallback(ReadCallBack), rs);
   }  
  
   private static void ReadCallBack(IAsyncResult asyncResult)  
   {  
      // Get the RequestState object from AsyncResult.  
      RequestState rs = (RequestState)asyncResult.AsyncState;  
  
      // Retrieve the ResponseStream that was set in RespCallback.
      Stream responseStream = rs.ResponseStream;  
  
      // Read rs.BufferRead to verify that it contains data.
      int read = responseStream.EndRead( asyncResult );  
      if (read > 0)  
      {  
         // Prepare a Char array buffer for converting to Unicode.  
         Char[] charBuffer = new Char[BUFFER_SIZE];  
  
         // Convert byte stream to Char array and then to String.  
         // len contains the number of characters converted to Unicode.  
      int len =
         rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0);  
  
         String str = new String(charBuffer, 0, len);  
  
         // Append the recently read data to the RequestData stringbuilder  
         // object contained in RequestState.  
         rs.RequestData.Append(  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read));
  
         // Continue reading data until
         // responseStream.EndRead returns –1.  
         IAsyncResult ar = responseStream.BeginRead(
            rs.BufferRead, 0, BUFFER_SIZE,
            new AsyncCallback(ReadCallBack), rs);  
      }  
      else  
      {  
         if(rs.RequestData.Length>0)  
         {  
            //  Display data to the console.  
            string strContent;
            strContent = rs.RequestData.ToString();  
         }  
         // Close down the response stream.  
         responseStream.Close();
         // Set the ManualResetEvent so the main thread can exit.  
         allDone.Set();
      }  
      return;  
   }
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Threading  
Imports System.Text  
Imports System.IO  
  
' The RequestState class passes data across async calls.  
Public Class RequestState  
  
      Public RequestData As New StringBuilder("")  
      Public BufferRead(1024) As Byte  
      Public Request As HttpWebRequest  
      Public ResponseStream As Stream  
      ' Create Decoder for appropriate encoding type.  
      Public StreamDecode As Decoder = Encoding.UTF8.GetDecoder()  
  
      Public Sub New  
         Request = Nothing  
         ResponseStream = Nothing  
      End Sub  
End Class  
  
' ClientGetAsync issues the async request.  
Class ClientGetAsync  
   Shared allDone As New ManualResetEvent(False)  
      Const BUFFER_SIZE As Integer = 1024  
  
    Shared Sub Main()  
        Dim Args As String() = Environment.GetCommandLineArgs()  
  
        If Args.Length < 2 Then  
            ShowUsage()  
            Return  
        End If  
  
      ' Get the URI from the command line.  
        Dim HttpSite As Uri = New Uri(Args(1))  
  
      ' Create the request object.  
        Dim wreq As HttpWebRequest = _  
           CType(WebRequest.Create(HttpSite), HttpWebRequest)  
  
      ' Create the state object.  
      Dim rs As RequestState = New RequestState()  
  
      ' Put the request into the state so it can be passed around.  
      rs.Request = wreq  
  
      ' Issue the async request.  
        Dim r As IAsyncResult = _  
           CType(wreq.BeginGetResponse( _  
           New AsyncCallback(AddressOf RespCallback), rs), IAsyncResult)  
  
      ' Wait until the ManualResetEvent is set so that the application  
      ' does not exit until after the callback is called.  
        allDone.WaitOne()  
    End Sub  
  
    Shared Sub ShowUsage()  
        Console.WriteLine("Attempts to GET a URI")  
        Console.WriteLine()  
        Console.WriteLine("Usage:")  
        Console.WriteLine("ClientGetAsync URI")  
        Console.WriteLine("Examples:")  
        Console.WriteLine("ClientGetAsync http://www.contoso.com/")  
    End Sub  
  
    Shared Sub RespCallback(ar As IAsyncResult)  
       ' Get the RequestState object from the async result.  
       Dim rs As RequestState = CType(ar.AsyncState, RequestState)  
  
       ' Get the HttpWebRequest from RequestState.  
       Dim req As HttpWebRequest= rs.Request  
  
       ' Call EndGetResponse, which returns the HttpWebResponse object  
       ' that came from the request issued above.  
       Dim resp As HttpWebResponse = _  
           CType(req.EndGetResponse(ar), HttpWebResponse)  
  
       ' Start reading data from the response stream.  
       Dim ResponseStream As Stream = resp.GetResponseStream()  
  
       ' Store the reponse stream in RequestState to read  
       ' the stream asynchronously.  
       rs.ResponseStream = ResponseStream  
  
       ' Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead.  
       Dim iarRead As IAsyncResult = _  
          ResponseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
          New AsyncCallback(AddressOf ReadCallBack), rs)  
    End Sub  
  
   Shared Sub ReadCallBack(asyncResult As IAsyncResult)  
      ' Get the RequestState object from the AsyncResult.  
      Dim rs As RequestState = CType(asyncResult.AsyncState, RequestState)  
  
      ' Retrieve the ResponseStream that was set in RespCallback.  
      Dim responseStream As Stream = rs.ResponseStream  
  
      ' Read rs.BufferRead to verify that it contains data.  
      Dim read As Integer = responseStream.EndRead( asyncResult )  
      If read > 0 Then  
         ' Prepare a Char array buffer for converting to Unicode.  
         Dim charBuffer(1024) As Char  
  
         ' Convert byte stream to Char array and then String.  
         ' len contains the number of characters converted to Unicode.  
         Dim len As Integer = _  
           rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0)  
         Dim str As String = new String(charBuffer, 0, len)
  
         ' Append the recently read data to the RequestData stringbuilder
         ' object contained in RequestState.  
         rs.RequestData.Append( _  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read))  
  
         ' Continue reading data until responseStream.EndRead  
         ' returns –1.  
         Dim ar As IAsyncResult = _  
            responseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
            New AsyncCallback(AddressOf ReadCallBack), rs)  
      Else  
          If rs.RequestData.Length > 1 Then  
            ' Display data to the console.  
            Dim strContent As String  
            strContent = rs.RequestData.ToString()  
            Console.WriteLine(strContent)  
         End If  
  
         ' Close down the response stream.  
         responseStream.Close()  
  
         ' Set the ManualResetEvent so the main thread can exit.  
         allDone.Set()  
      End If  
  
      Return  
   End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="4703a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4703a-129">See also</span></span>

- [<span data-ttu-id="4703a-130">データの要求</span><span class="sxs-lookup"><span data-stu-id="4703a-130">Requesting Data</span></span>](requesting-data.md)
