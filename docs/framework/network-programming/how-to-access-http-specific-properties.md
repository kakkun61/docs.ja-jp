---
title: '方法: HTTP 固有のプロパティにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: ea709bba17d4e2f00b760c8713f9e8100496f0bf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250516"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="a8755-102">方法: HTTP 固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="a8755-102">How to: Access HTTP-Specific Properties</span></span>

<span data-ttu-id="a8755-103">このサンプルでは、HTTP の **Keep-alive** 動作を無効にして、Web サーバーからプロトコル バージョン番号を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8755-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8755-104">例</span><span class="sxs-lookup"><span data-stu-id="a8755-104">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8755-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a8755-105">Compiling the Code</span></span>  

 <span data-ttu-id="a8755-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a8755-106">This example requires:</span></span>  
  
- <span data-ttu-id="a8755-107">**System.Net** 名前空間の参照。</span><span class="sxs-lookup"><span data-stu-id="a8755-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8755-108">参照</span><span class="sxs-lookup"><span data-stu-id="a8755-108">See also</span></span>

- [<span data-ttu-id="a8755-109">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a8755-109">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="a8755-110">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="a8755-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="a8755-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="a8755-111">HTTP</span></span>](http.md)
