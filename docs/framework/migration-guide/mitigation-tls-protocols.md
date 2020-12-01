---
title: '軽減策: TLS プロトコル'
description: .NET Framework 4.6 以降の TLS プロトコル変更による影響と軽減策について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 492315d43043c83d17eab330e8d589d1cffe7ad2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273868"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="bb2e7-103">軽減策:TLS プロトコル</span><span class="sxs-lookup"><span data-stu-id="bb2e7-103">Mitigation: TLS Protocols</span></span>

<span data-ttu-id="bb2e7-104">.NET Framework 4.6 から、<xref:System.Net.ServicePointManager?displayProperty=nameWithType> および <xref:System.Net.Security.SslStream?displayProperty=nameWithType> クラスで Tls1.0、Tls1.1、または Tls 1.2 の 3 つのプロトコルのいずれかを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-104">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="bb2e7-105">SSL3.0 プロトコルと RC4 の暗号化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-105">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="bb2e7-106">影響</span><span class="sxs-lookup"><span data-stu-id="bb2e7-106">Impact</span></span>  

 <span data-ttu-id="bb2e7-107">この変更は、以下のものに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-107">This change affects:</span></span>  
  
- <span data-ttu-id="bb2e7-108">SSL を使用して <xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient>、<xref:System.Net.Security.SslStream> のいずれかのタイプで HTTPS サーバーまたはソケット サーバーと対話するすべてのアプリ。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-108">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="bb2e7-109">Tls1.0、Tls1.1、または Tls 1.2 をサポートするためにアップグレードできない、すべてのサーバー サイド アプリ。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-109">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="bb2e7-110">軽減策</span><span class="sxs-lookup"><span data-stu-id="bb2e7-110">Mitigation</span></span>  

 <span data-ttu-id="bb2e7-111">推奨される軽減策はサーバー側のアプリを Tls1.0、Tls1.1、または Tls 1.2 にアップグレードすることです。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-111">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="bb2e7-112">これが現実的でない場合、またはクライアント アプリが破損している場合は、次の 2 つの方法のいずれかにより、<xref:System.AppContext> クラスを使用してこの機能を除外できます。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-112">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="bb2e7-113">プログラム的に。次のようにコード スニペットを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-113">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="bb2e7-114"><xref:System.Net.ServicePointManager> オブジェクトの初期化が行われるのは 1 回だけなので、アプリケーションはこれらの互換性設定の定義を最初に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-114">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="bb2e7-115">app.config ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加する:</span><span class="sxs-lookup"><span data-stu-id="bb2e7-115">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="bb2e7-116">ただし、既定の動作を除外することは、アプリケーションの安全性を低下させるので推奨されません。</span><span class="sxs-lookup"><span data-stu-id="bb2e7-116">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2e7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb2e7-117">See also</span></span>

- [<span data-ttu-id="bb2e7-118">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="bb2e7-118">Application compatibility</span></span>](application-compatibility.md)
