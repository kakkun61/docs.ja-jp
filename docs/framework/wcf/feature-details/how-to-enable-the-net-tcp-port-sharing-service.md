---
title: '方法: Net.TCP ポート共有サービスを有効にする'
description: Net.tcp を有効にするために、MMC を使用して Net TCP ポート共有サービスを構成する方法について説明します。 Net.tcp は、既定で無効になっています。
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 7200d82e4a45ce9e36b2a4cec3d0c08e1a5f00ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265467"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="80e11-103">方法: Net.TCP ポート共有サービスを有効にする</span><span class="sxs-lookup"><span data-stu-id="80e11-103">How to: Enable the Net.TCP Port Sharing Service</span></span>

<span data-ttu-id="80e11-104">Windows Communication Foundation (WCF) は、Net.tcp ポート共有サービスと呼ばれる Windows サービスを使用して、複数のプロセスで TCP ポートを共有しやすくします。</span><span class="sxs-lookup"><span data-stu-id="80e11-104">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="80e11-105">このサービスは WCF の一部としてインストールされますが、セキュリティ上の理由から、既定ではサービスが有効になっていないため、最初に使用する前に手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80e11-105">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="80e11-106">このトピックでは、Microsoft 管理コンソール (MMC) スナップインを使用して、Net TCP ポート共有サービスを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e11-106">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="80e11-107">Net.tcp ポート共有サービスを有効にし、手動で開始したら、「 [方法: ポート共有を使用するように WCF サービスを構成](how-to-configure-a-wcf-service-to-use-port-sharing.md) する」を参照して、このサービスを使用するようにサービスを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80e11-107">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="80e11-108">Net.tcp://ポート共有を使用するサンプルについては、 [Net.tcp ポート共有のサンプル](../samples/net-tcp-port-sharing-sample.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80e11-108">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="80e11-109">MMC を使用して Net.TCP ポート共有サービスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="80e11-109">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="80e11-110">[スタート] メニューから、[サービス] 管理コンソールを開きます。そのためには、コマンドプロンプトウィンドウを開き、「」と入力 `services.msc` するか、[実行] を開き、[開く] ボックスに「」と入力し `services.msc` ます。</span><span class="sxs-lookup"><span data-stu-id="80e11-110">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="80e11-111">サービスの一覧の [ **名前** ] 列で、 **Net.tcp ポート共有サービス** を右クリックし、メニューから [ **プロパティ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="80e11-111">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="80e11-112">サービスの手動起動を有効にするには、[ **プロパティ** ] ウィンドウで [ **全般** ] タブを選択し、[ **スタートアップの種類** ] ボックスで [手動] を選択して、[ **適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80e11-112">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="80e11-113">サービスを開始するには、[サービスの状態] 領域で [ **開始** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="80e11-113">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="80e11-114">これで、サービスの状態には "開始" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="80e11-114">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="80e11-115">サービスの一覧に戻るには、[ **OK]** をクリックして、MMC コンソールを終了します。</span><span class="sxs-lookup"><span data-stu-id="80e11-115">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e11-116">例</span><span class="sxs-lookup"><span data-stu-id="80e11-116">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e11-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="80e11-117">See also</span></span>

- [<span data-ttu-id="80e11-118">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="80e11-118">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="80e11-119">Net.TCP ポート共有サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="80e11-119">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
