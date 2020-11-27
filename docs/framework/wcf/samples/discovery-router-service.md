---
title: 探索ルーター サービス
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: f3ea32d10e27eceb3edcee8b6aeacbf9c5ebc6f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292650"
---
# <a name="discovery-router-service"></a><span data-ttu-id="a8d4b-102">探索ルーター サービス</span><span class="sxs-lookup"><span data-stu-id="a8d4b-102">Discovery Router Service</span></span>

<span data-ttu-id="a8d4b-103">このサンプルでは、探索メッセージを別のエンドポイントに転送する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a8d4b-104">対象</span><span class="sxs-lookup"><span data-stu-id="a8d4b-104">Demonstrates</span></span>  

 <span data-ttu-id="a8d4b-105">探索ルーティング</span><span class="sxs-lookup"><span data-stu-id="a8d4b-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a8d4b-106">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="a8d4b-106">Discussion</span></span>  

 <span data-ttu-id="a8d4b-107">探索ルーティングは、プロキシがサービスを認識しないが、別のプロキシのことは認識する場合に、クライアントがプロキシを使用してそのようなサービスを検索するシナリオで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="a8d4b-108">このプロキシは、探索パケットをこのクライアントから 2 番目のプロキシに転送できます。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="a8d4b-109">2 番目のプロキシはサービスを検索し、応答を元のクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="a8d4b-110">このサンプルでは、クライアントはメッセージを探索ルーティング コンポーネントに送信します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="a8d4b-111">このメッセージは、探索ルーター上の特定のエンドポイントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="a8d4b-112">その後、このルーターはメッセージを UDP マルチキャスト エンドポイントに転送します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="a8d4b-113">プローブ メッセージはマルチキャスト エンドポイントに送信され、UDP マルチキャスト アドレスをリッスンするサービスは、その探索ルーターに応答します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="a8d4b-114">探索ルーターは応答を収集し、クライアントにその応答を返します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8d4b-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a8d4b-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a8d4b-116">サンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="a8d4b-117">DiscoveryRouter 実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="a8d4b-118">ビルド ディレクトリからサービス実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="a8d4b-119">クライアント実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-119">Run the client executable.</span></span> <span data-ttu-id="a8d4b-120">クライアントでサービスが検索されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8d4b-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8d4b-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a8d4b-123">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8d4b-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a8d4b-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
