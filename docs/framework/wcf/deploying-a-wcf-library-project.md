---
title: WCF ライブラリ プロジェクトの配置
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: e3a90f03639a888b4528a1962a24b7adc5d43c58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260891"
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="45a75-102">WCF ライブラリ プロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="45a75-102">Deploying a WCF Library Project</span></span>

<span data-ttu-id="45a75-103">このトピックでは、Windows Communication Foundation (WCF) サービスライブラリプロジェクトを配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45a75-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="45a75-104">WCF サービス ライブラリの配置</span><span class="sxs-lookup"><span data-stu-id="45a75-104">Deploying a WCF Service Library</span></span>  

 <span data-ttu-id="45a75-105">WCF サービスライブラリは、ダイナミックリンクライブラリ (DLL) です。</span><span class="sxs-lookup"><span data-stu-id="45a75-105">A WCF service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="45a75-106">それ自体を単独で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="45a75-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="45a75-107">ホスティング環境に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45a75-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="45a75-108">このプロセスの詳細については、「 [WCF サービスのホストと](/previous-versions/dotnet/articles/bb332338(v=msdn.10))使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45a75-108">For more information about this process, see [Hosting and Consuming WCF Services](/previous-versions/dotnet/articles/bb332338(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="45a75-109">WCF サービスライブラリは、他の WCF サービスと同様にデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="45a75-109">A WCF service library can be deployed like any other WCF service.</span></span> <span data-ttu-id="45a75-110">ただし、.NET Framework は Dll の構成をサポートしていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="45a75-110">However, be aware that .NET Framework does not support configuration for DLLs.</span></span> <span data-ttu-id="45a75-111"><xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="45a75-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="45a75-112">WCF サービスライブラリプロジェクトでは、開発時にライブラリの App.config ファイルを提供することによって、この制限を軽減します。</span><span class="sxs-lookup"><span data-stu-id="45a75-112">The WCF service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="45a75-113">ただし、配置後、この App.config ファイルは認識されません。</span><span class="sxs-lookup"><span data-stu-id="45a75-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="45a75-114">構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45a75-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="45a75-115">自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="45a75-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="45a75-116">サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="45a75-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
