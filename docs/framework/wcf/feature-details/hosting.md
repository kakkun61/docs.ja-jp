---
title: Hosting2
ms.date: 03/30/2017
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
ms.openlocfilehash: a83cc0d12b1099bc77d62f108741de1dbf387686
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255989"
---
# <a name="hosting"></a><span data-ttu-id="db88f-102">Hosting</span><span class="sxs-lookup"><span data-stu-id="db88f-102">Hosting</span></span>

<span data-ttu-id="db88f-103">このセクションのトピックでは、サービス ホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="db88f-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="db88f-104">サービスは、インターネットインフォメーションサービス (IIS)、windows プロセスアクティブ化サービス (WAS)、Windows Server AppFabric、Windows サービス、またはマネージアプリケーションによってホストできます。このオプションは、多くの場合、 *自己ホスト* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="db88f-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="db88f-105">信頼されていないホストからサービスや拡張機能を実行すると、セキュリティが損なわれるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="db88f-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db88f-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="db88f-106">In This Section</span></span>  

 [<span data-ttu-id="db88f-107">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="db88f-107">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)  
 <span data-ttu-id="db88f-108">Windows Communication Foundation (WCF) サービスがインターネットインフォメーションサービスまたは [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10))でどのようにホストされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="db88f-108">Describes how a Windows Communication Foundation (WCF) service is hosted in Internet Information Services or [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)).</span></span>  
  
 [<span data-ttu-id="db88f-109">Windows プロセス アクティブ化サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="db88f-109">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="db88f-110">WCF サービスが Windows プロセスアクティブ化サービスによってどのようにホストされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="db88f-110">Describes how a WCF service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="db88f-111">Windows サービス アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="db88f-111">Hosting in a Windows Service Application</span></span>](hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="db88f-112">WCF サービスが Windows サービスによってどのようにホストされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="db88f-112">Describes how a WCF service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="db88f-113">マネージド アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="db88f-113">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)  
 <span data-ttu-id="db88f-114">マネージアプリケーションでの WCF サービスのホスト方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="db88f-114">Describes how a WCF service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="db88f-115">IIS と WAS における構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="db88f-115">Configuration-Based Activation in IIS and WAS</span></span>](configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="db88f-116">.Svc ファイルを使用せずに、IIS または WAS で WCF サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="db88f-116">Describes how a WCF service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="db88f-117">複数の IIS サイト バインディングのサポート</span><span class="sxs-lookup"><span data-stu-id="db88f-117">Supporting Multiple IIS Site Bindings</span></span>](supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="db88f-118">1 つの Web サイト上で同じ URI スキームを使用してサービスの複数のベース アドレスを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="db88f-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db88f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="db88f-119">See also</span></span>

- [<span data-ttu-id="db88f-120">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="db88f-120">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="db88f-121">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="db88f-121">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
