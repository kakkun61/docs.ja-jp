---
title: HTTP
description: HttpWebRequest と HttpWebResponse クラスを使用することで .NET Framework によって提供される、HTTP の包括的なサポートについて学習します。
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: 62c4ddb7e4b904be501ed2938692bce405c7e5f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253402"
---
# <a name="http"></a><span data-ttu-id="8fe8d-103">HTTP</span><span class="sxs-lookup"><span data-stu-id="8fe8d-103">HTTP</span></span>

<span data-ttu-id="8fe8d-104">.NET Framework は、<xref:System.Net.HttpWebRequest> クラスと <xref:System.Net.HttpWebResponse> クラスを使用して、すべてのインターネット トラフィックの大部分を構成する HTTP プロトコルに対して包括的なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-104">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="8fe8d-105"><xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> から派生したこれらのクラスは、静的メソッド <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> が "http" または "https" で始まる URI に遭遇するたびに既定で返されます。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-105">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="8fe8d-106">ほとんどの場合、**WebRequest** クラスと **WebResponse** クラスは、要求を行うために必要なすべてを提供しますが、プロパティとして公開されている HTTP 固有の機能にアクセスする必要がある場合は、これらのクラスを **HttpWebRequest** または **HttpWebResponse** に型キャストすることができますです。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-106">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="8fe8d-107">**HttpWebRequest** と **HttpWebResponse** は、標準の HTTP 要求-応答のトランザクションをカプセル化し、一般的な HTTP ヘッダーへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-107">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="8fe8d-108">これらのクラスは、パイプライン処理、チャック内データの送受信、認証、事前認証、暗号化、プロキシのサポート、サーバー証明書の検証、接続の管理を含むほとんどの HTTP 1.1 の機能もサポートします。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-108">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="8fe8d-109">カスタム ヘッダー、およびプロパティを介して提供されていないヘッダーを格納し、**Headers** プロパティを介してアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-109">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="8fe8d-110">**HttpWebRequest** は、**WebRequest** によって使用される既定のクラスであり、**WebRequest.Create** メソッドに URI を渡す前に登録する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-110">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="8fe8d-111"><xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> プロパティを **true** (既定) に設定することで自動的に HTTP リダイレクトに従うアプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-111">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="8fe8d-112">アプリケーションが、要求をリダイレクトし、**HttpWebResponse** の <xref:System.Net.HttpWebResponse.ResponseUri%2A> プロパティに要求に応答した実際の Web リソースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-112">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="8fe8d-113">**AllowAutoRedirect** を **false** に設定した場合、アプリケーションは、HTTP プロトコル エラーとしてリダイレクトを処理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-113">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="8fe8d-114">アプリケーションでは、<xref:System.Net.WebException.Status%2A> を <xref:System.Net.WebExceptionStatus> に設定し、<xref:System.Net.WebException> をキャッチすることによって HTTP プロトコル エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-114">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="8fe8d-115"><xref:System.Net.WebException.Response%2A> プロパティは、サーバーによって送信された **WebResponse** を含み、実際の HTTP エラーがに発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8fe8d-115">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe8d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fe8d-116">See also</span></span>

- [<span data-ttu-id="8fe8d-117">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="8fe8d-117">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="8fe8d-118">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="8fe8d-118">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="8fe8d-119">方法: HTTP 固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="8fe8d-119">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
