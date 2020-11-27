---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 6e5946dd7d107c34eafe55a62c51d089931b5b77
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252304"
---
# <a name="wshttpbinding"></a><span data-ttu-id="bd402-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bd402-102">WSHttpBinding</span></span>

<span data-ttu-id="bd402-103">このサンプルでは、Windows Communication Foundation (WCF) を使用して、一般的なサービスと一般的なクライアントを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd402-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="bd402-104">このサンプルは、クライアント コンソール プログラム (client.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリで構成されています。</span><span class="sxs-lookup"><span data-stu-id="bd402-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="bd402-105">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="bd402-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="bd402-106">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="bd402-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="bd402-107">クライアントは指定された算術演算を同期要求し、サービスは結果と共に応答します。</span><span class="sxs-lookup"><span data-stu-id="bd402-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="bd402-108">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd402-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bd402-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd402-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd402-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bd402-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bd402-111">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="bd402-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd402-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bd402-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="bd402-113">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd402-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bd402-114">このサンプルで `ICalculator` は、を使用してコントラクトを公開 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="bd402-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="bd402-115">このバインディングの構成は、次のように Web.config ファイルで展開されています。</span><span class="sxs-lookup"><span data-stu-id="bd402-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"
              transactionFlow="false"
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"
              textEncoding="utf-8"
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="bd402-116">ベース `binding` 要素で `maxReceivedMessageSize` 値を使用すると、受信メッセージの最大サイズ (バイト単位) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="bd402-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="bd402-117">`hostNameComparisonMode` 値を使用すると、メッセージの非多重化を行ってサービスに変換する際にホスト名を考慮するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="bd402-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="bd402-118">`messageEncoding` 値を使用すると、メッセージのテキスト エンコーディングまたは MTOM エンコーディングを使用するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="bd402-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="bd402-119">`textEncoding` 値を使用すると、メッセージの文字エンコーディングを構成できます。</span><span class="sxs-lookup"><span data-stu-id="bd402-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="bd402-120">`bypassProxyOnLocal` 値を使用すると、ローカル通信に HTTP プロキシを使用するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="bd402-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="bd402-121">現在のトランザクションをフローするかどうかは、`transactionFlow` 値で構成されます (操作がトランザクション フロー用に構成されている場合)。</span><span class="sxs-lookup"><span data-stu-id="bd402-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="bd402-122">要素では、 [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) 有効なブール値によって、信頼できるセッションが有効かどうかが構成されます。</span><span class="sxs-lookup"><span data-stu-id="bd402-122">On the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="bd402-123">メッセージの順序が保持されるかどうかは、`ordered` 値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="bd402-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="bd402-124">エラーになる前の、セッションのアイドル状態の期間は、`inactivityTimeout` 値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="bd402-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="bd402-125">では、 [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) 値を使用して、使用する `mode` セキュリティモードを構成します。</span><span class="sxs-lookup"><span data-stu-id="bd402-125">On the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="bd402-126">このサンプルでは、メッセージセキュリティが使用されています。これは、 [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) が内で指定されているためです [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="bd402-126">In this sample, messages security is being used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="bd402-127">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd402-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bd402-128">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bd402-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd402-129">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="bd402-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bd402-130">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bd402-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="bd402-131">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bd402-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="bd402-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bd402-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="bd402-133">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bd402-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
