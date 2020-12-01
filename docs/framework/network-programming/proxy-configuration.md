---
title: プロキシの構成
description: アダプティブおよび静的プロキシ サーバーを構成する方法について説明します。 プロキシ構成によって、リソースに対するクライアント要求をプロキシ サーバーで処理する動作が制御されます。
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 5094a066fe6689a1c0cda227b284accaac49ad54
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263166"
---
# <a name="proxy-configuration"></a><span data-ttu-id="d664c-104">プロキシの構成</span><span class="sxs-lookup"><span data-stu-id="d664c-104">Proxy Configuration</span></span>

<span data-ttu-id="d664c-105">プロキシ サーバーは、リソースに対するクライアント要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="d664c-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="d664c-106">プロキシは、要求されたリソースをキャッシュから返したり、リソースが存在するサーバーに要求を転送したりできます。</span><span class="sxs-lookup"><span data-stu-id="d664c-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="d664c-107">プロキシは、リモート サーバーに送信された要求の数を減らすことで、ネットワークのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="d664c-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="d664c-108">プロキシを使用して、リソースへのアクセスを制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="d664c-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="d664c-109">アダプティブ プロキシ</span><span class="sxs-lookup"><span data-stu-id="d664c-109">Adaptive Proxies</span></span>  

 <span data-ttu-id="d664c-110">.NET Framework には、アダプティブと静的という 2 種類のプロキシがあります。</span><span class="sxs-lookup"><span data-stu-id="d664c-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="d664c-111">アダプティブ プロキシは、ネットワーク構成を変更するときに、その設定を調整します。</span><span class="sxs-lookup"><span data-stu-id="d664c-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="d664c-112">たとえば、ラップトップ ユーザーがダイヤルアップ ネットワーク接続を起動する場合、アダプティブ プロキシはこの変更を認識し、新しい構成スクリプトを検出して実行し、その設定を適切に調整します。</span><span class="sxs-lookup"><span data-stu-id="d664c-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="d664c-113">アダプティブ プロキシは、構成スクリプトによって構成されます (「[自動プロキシ検出](automatic-proxy-detection.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="d664c-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="d664c-114">スクリプトは、一連のアプリケーション プロトコルと、各プロトコル用のプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="d664c-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="d664c-115">ネットワーク環境での変更により、システムで新しい一連のプロキシを使用することが必要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d664c-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="d664c-116">ネットワーク接続がダウンしたか、新しいネットワーク接続が開始された場合、システムは新しい環境で構成スクリプトの適切なソースを検出し、新しいスクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d664c-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="d664c-117">構成ファイル内の [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) 要素の `usesystemdefault` 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d664c-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="d664c-118">`usesystemdefault` 属性は、静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="d664c-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="d664c-119">この値を `true` に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d664c-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="d664c-120">この値が `false` であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d664c-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="d664c-121">アダプティブ プロキシを有効にする場合も、この値を `false` に設定するか、または設定しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d664c-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="d664c-122">一般的なアダプティブ プロキシの構成例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d664c-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="d664c-123">静的プロキシ</span><span class="sxs-lookup"><span data-stu-id="d664c-123">Static Proxies</span></span>  

 <span data-ttu-id="d664c-124">静的プロキシは、通常、アプリケーションによって明示的に構成されるか、アプリケーションまたはシステムによって構成ファイルが呼び出されたときに構成されます。</span><span class="sxs-lookup"><span data-stu-id="d664c-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="d664c-125">静的プロキシは、企業ネットワークに接続されているデスクトップ コンピューターなど、トポロジがあまり変更されないネットワークで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d664c-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="d664c-126">いくつかのオプションで静的プロキシの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="d664c-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="d664c-127">以下を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d664c-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="d664c-128">プロキシのアドレス。</span><span class="sxs-lookup"><span data-stu-id="d664c-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="d664c-129">ローカル アドレスに対してプロキシをバイパスするかかどうか。</span><span class="sxs-lookup"><span data-stu-id="d664c-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="d664c-130">一連のアドレスに対してプロキシをバイパスするかかどうか。</span><span class="sxs-lookup"><span data-stu-id="d664c-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="d664c-131">次の表に、静的プロキシの構成オプションを示します。</span><span class="sxs-lookup"><span data-stu-id="d664c-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="d664c-132">属性、プロパティ、または構成ファイルの設定</span><span class="sxs-lookup"><span data-stu-id="d664c-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="d664c-133">説明</span><span class="sxs-lookup"><span data-stu-id="d664c-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="d664c-134">`proxyaddress` または <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="d664c-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="d664c-135">使用するプロキシのアドレス。</span><span class="sxs-lookup"><span data-stu-id="d664c-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="d664c-136">`bypassonlocal` または <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="d664c-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="d664c-137">ローカル アドレスに対してプロキシをバイパスするかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="d664c-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="d664c-138">`bypasslist` または <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="d664c-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="d664c-139">正規表現を使用して、プロキシをバイパスするアドレスのセットを記述します。</span><span class="sxs-lookup"><span data-stu-id="d664c-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="d664c-140">静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="d664c-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="d664c-141">この値を `true` に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d664c-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="d664c-142">.NET Framework 2.0 でこの値を `true` に設定した場合、Internet Explorer のプロキシ設定は構成ファイル内の他のプロキシ設定でオーバーライドされません。</span><span class="sxs-lookup"><span data-stu-id="d664c-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="d664c-143">.NET Framework 1.1 では、構成ファイル内の他のプロキシ設定で Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d664c-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="d664c-144">この値が `false` であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d664c-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="d664c-145">アダプティブ プロキシを有効にする場合も、この値を `false` に設定するか、または設定しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d664c-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="d664c-146">一般的な静的プロキシの構成例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d664c-146">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="True"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d664c-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d664c-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="d664c-148">自動プロキシ検出</span><span class="sxs-lookup"><span data-stu-id="d664c-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
