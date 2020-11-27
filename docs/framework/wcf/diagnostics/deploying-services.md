---
title: サービスの配置
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 07bd2a3938f238336dc00fa2e0826a28a9363a4a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294808"
---
# <a name="deploying-services"></a><span data-ttu-id="ad469-102">サービスの配置</span><span class="sxs-lookup"><span data-stu-id="ad469-102">Deploying Services</span></span>

<span data-ttu-id="ad469-103">このトピックでは、Windows Communication Foundation (WCF) アプリケーションを実行時環境に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad469-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="ad469-104">アプリケーションのホスト環境の選択</span><span class="sxs-lookup"><span data-stu-id="ad469-104">Choosing the Hosting Environment for Your Application</span></span>  

 <span data-ttu-id="ad469-105">WCF サービスは、マネージコードをサポートする任意の Windows プロセスで実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="ad469-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="ad469-106">アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad469-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="ad469-107">ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス (IIS) のようなサーバー環境、あるいは Windows アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行にまで及びます。</span><span class="sxs-lookup"><span data-stu-id="ad469-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="ad469-108">WCF アプリケーションのさまざまなホスティングオプションを確認するには、「 [ホスティングサービス](../hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad469-108">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad469-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad469-109">See also</span></span>

- [<span data-ttu-id="ad469-110">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ad469-110">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="ad469-111">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="ad469-111">Hosting Services</span></span>](../hosting-services.md)
