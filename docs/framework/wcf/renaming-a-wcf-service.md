---
title: WCF サービス名の変更
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 25f9201253f02f368ccf95ddf1f7a7d78d2e1b2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249723"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="199aa-102">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="199aa-102">Renaming a WCF Service</span></span>

<span data-ttu-id="199aa-103">このトピックでは、Windows Communication Foundation (WCF) サービスの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="199aa-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="199aa-104">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="199aa-104">Renaming a WCF Service</span></span>  

 <span data-ttu-id="199aa-105">Windows Communication Foundation (WCF) テンプレートでサービスの名前を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="199aa-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="199aa-106">サービスを実装するクラスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="199aa-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="199aa-107">次の例に示すように、このサービスの構成ファイルで、サービスの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="199aa-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="199aa-108">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="199aa-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="199aa-109">サービスが web でホストされている場合は、 *\* .svc* ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="199aa-109">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="199aa-110">この svc ファイルを開き、次の例に示すように、サービスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="199aa-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="199aa-111">自己ホスト アプリケーションには svc ファイルがないので、この手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="199aa-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="199aa-112">WCF サービス コントラクト名の変更</span><span class="sxs-lookup"><span data-stu-id="199aa-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="199aa-113">サービス コントラクトの名前を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="199aa-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="199aa-114">サービス コントラクトの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="199aa-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="199aa-115">次の例に示すように、このサービスの構成ファイルで、サービス コントラクトの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="199aa-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="199aa-116">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="199aa-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
