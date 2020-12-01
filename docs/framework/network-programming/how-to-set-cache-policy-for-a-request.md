---
title: '方法: 要求のキャッシュ ポリシーを設定する'
description: .NET Framework で要求のキャッシュ ポリシーを設定する方法について学習します。 このキャッシュ ポリシーによって、キャッシュからリソースを最大 1 日使用できるようになります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- request cache policies
ms.assetid: 39c15e40-586b-4ac9-9cce-146f74b7e545
ms.openlocfilehash: cbb8f2eaf618cb9faaca1375d829478a645962a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253415"
---
# <a name="how-to-set-cache-policy-for-a-request"></a><span data-ttu-id="026ab-104">方法: 要求のキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="026ab-104">How to: Set Cache Policy for a Request</span></span>

<span data-ttu-id="026ab-105">次の例では、要求のキャッシュ ポリシーの設定方法を示します。</span><span class="sxs-lookup"><span data-stu-id="026ab-105">The following example demonstrates setting a cache policy for a request.</span></span> <span data-ttu-id="026ab-106">入力の例は、`http://www.contoso.com/` などの URI です。</span><span class="sxs-lookup"><span data-stu-id="026ab-106">The example input is a URI such as `http://www.contoso.com/`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="026ab-107">例</span><span class="sxs-lookup"><span data-stu-id="026ab-107">Example</span></span>  

 <span data-ttu-id="026ab-108">次のコード例では、リソースがキャッシュ内にある時間が 1 日より短い場合に、要求されたリソースの使用を許可するキャッシュ ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="026ab-108">The following code example creates a cache policy that allows the requested resource to be used from the cache if it has not been in the cache for longer than one day.</span></span> <span data-ttu-id="026ab-109">この例では、リソースがキャッシュから使用されたかどうかを示すメッセージ ( たとえば、`"The response was retrieved from the cache : False."`) が表示され、リソースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="026ab-109">The example displays a message that indicates whether the resource was used from the cache—for example, `"The response was retrieved from the cache : False."`—and then displays the resource.</span></span> <span data-ttu-id="026ab-110">要求は、クライアントとサーバー間にある任意のキャッシュによって満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="026ab-110">A request can be fulfilled by any cache between the client and server.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Cache;  
using System.IO;  
  
namespace Examples.System.Net.Cache  
{  
    public class CacheExample  
    {
        public static void UseCacheForOneDay(Uri resource)  
        {  
            // Create a policy that allows items in the cache  
            // to be used if they have been cached one day or less.  
            HttpRequestCachePolicy requestPolicy =
                new HttpRequestCachePolicy (HttpCacheAgeControl.MaxAge,  
                TimeSpan.FromDays(1));  
  
            WebRequest request = WebRequest.Create (resource);  
            // Set the policy for this request only.  
            request.CachePolicy = requestPolicy;  
            HttpWebResponse response = (HttpWebResponse)request.GetResponse();  
            // Determine whether the response was retrieved from the cache.  
            Console.WriteLine ("The response was retrieved from the cache : {0}.",  
               response.IsFromCache);  
            Stream s = response.GetResponseStream ();  
            StreamReader reader = new StreamReader (s);  
            // Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd());  
            reader.Close ();  
            s.Close();  
            response.Close();  
        }  
        public static void Main(string[] args)  
        {  
            if (args == null || args.Length != 1)  
            {  
                Console.WriteLine ("You must specify the URI to retrieve.");  
                return;  
            }  
            UseCacheForOneDay (new Uri(args[0]));  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Cache  
Imports System.IO  
Namespace Examples.System.Net.Cache  
    Public Class CacheExample  
        Public Shared Sub UseCacheForOneDay(ByVal resource As Uri)  
            ' Create a policy that allows items in the cache  
            ' to be used if they have been cached one day or less.  
            Dim requestPolicy As New HttpRequestCachePolicy _  
                  (HttpCacheAgeControl.MaxAge, TimeSpan.FromDays(1))  
            Dim request As WebRequest = WebRequest.Create(resource)  
            ' Set the policy for this request only.  
            request.CachePolicy = requestPolicy  
            Dim response As HttpWebResponse = _  
             CType(request.GetResponse(), HttpWebResponse)  
            ' Determine whether the response was retrieved from the cache.  
            Console.WriteLine("The response was retrieved from the cache : {0}.", _  
                response.IsFromCache)  
            Dim s As Stream = response.GetResponseStream()  
            Dim reader As New StreamReader(s)  
            ' Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd())  
            reader.Close()  
            s.Close()  
            response.Close()  
        End Sub  
        Public Shared Sub Main(ByVal args() As String)  
            If args Is Nothing OrElse args.Length <> 1 Then  
                Console.WriteLine("You must specify the URI to retrieve.")  
                Return  
            End If  
            UseCacheForOneDay(New Uri(args(0)))  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="026ab-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="026ab-111">See also</span></span>

- [<span data-ttu-id="026ab-112">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="026ab-112">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="026ab-113">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="026ab-113">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="026ab-114">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="026ab-114">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="026ab-115">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="026ab-115">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="026ab-116">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="026ab-116">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
