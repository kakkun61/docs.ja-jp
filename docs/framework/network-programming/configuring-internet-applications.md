---
title: 構成 (インターネット アプリケーションを)
description: .NET Framework で <system.Net> 要素を使用して、インターネット アプリケーションを構成する方法について学習します。 この記事にはコード例が含まれます。
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: 796752ebf6e3cc5c3dac2a20213934f35d31b392
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287463"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="47f11-104">構成 (インターネット アプリケーションを)</span><span class="sxs-lookup"><span data-stu-id="47f11-104">Configuring Internet Applications</span></span>

<span data-ttu-id="47f11-105">[\<system.Net> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/system-net-element-network-settings.md) 構成要素には、アプリケーションのネットワーク構成情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="47f11-105">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="47f11-106">[\<system.Net> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/system-net-element-network-settings.md) 要素を使用すると、プロキシ サーバーを設定し、接続管理パラメーターを設定し、カスタム認証および要求モジュールをアプリケーションに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="47f11-106">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="47f11-107">[\<defaultProxy> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) 要素は、`GlobalProxySelection` クラスによって返されるプロキシ サーバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="47f11-107">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="47f11-108">独自の <xref:System.Net.HttpWebRequest.Proxy%2A> プロパティが特定の値に設定されていない <xref:System.Net.HttpWebRequest> はすべて、既定のプロキシを使用します。</span><span class="sxs-lookup"><span data-stu-id="47f11-108">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="47f11-109">プロキシ アドレスを設定するだけでなく、プロキシを使用しないサーバー アドレスの一覧を作成し、ローカル アドレスにプロキシを使用しないように指定できます。</span><span class="sxs-lookup"><span data-stu-id="47f11-109">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="47f11-110">Microsoft Internet Explorer の設定は構成の設定と組み合わせて使用され、構成の設定が優先されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="47f11-110">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="47f11-111">次の例では、既定のプロキシ サーバー アドレスを `http://proxyserver` に設定し、ローカル アドレスにプロキシを使用しないようにし、contoso.com ドメインにあるサーバーへのすべての要求でプロキシをバイパスするように指定しています。</span><span class="sxs-lookup"><span data-stu-id="47f11-111">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="47f11-112">特定のサーバーまたは他のすべてのサーバーに対して行うことができる持続接続の数を構成するには、[\<connectionManagement> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="47f11-112">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="47f11-113">次の例では、サーバー `www.contoso.com` への 2 つの持続接続、IP アドレス 192.168.1.2 を持つサーバーへの 4 つの持続接続、および他のすべてのサーバーへの 1 つの持続接続が使用されるようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="47f11-113">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="47f11-114">カスタム認証モジュールは、[\<authenticationModules> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="47f11-114">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="47f11-115">カスタム認証モジュールは <xref:System.Net.IAuthenticationModule> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47f11-115">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="47f11-116">次の例では、カスタム認証モジュールを構成します。</span><span class="sxs-lookup"><span data-stu-id="47f11-116">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="47f11-117">[\<webRequestModules> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) 要素を使用し、カスタム プロトコル固有のモジュールを使用してインターネット リソースから情報を要求するように、アプリケーションを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="47f11-117">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="47f11-118">指定されたモジュールは <xref:System.Net.IWebRequestCreate> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47f11-118">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="47f11-119">既定の HTTP、HTTPS、およびファイル要求モジュールは、次の例のように、構成ファイルでカスタム モジュールを指定してオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="47f11-119">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47f11-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="47f11-120">See also</span></span>

- [<span data-ttu-id="47f11-121">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="47f11-121">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="47f11-122">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="47f11-122">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="47f11-123">\<system.Net> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="47f11-123">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
