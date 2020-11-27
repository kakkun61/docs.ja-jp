---
title: ClickOnce を使用して WCF アプリケーションを展開する
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: ad4c603d07885aa16640b71d43038746d3702b05
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260858"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="082c8-102">ClickOnce を使用して WCF アプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="082c8-102">Deploying WCF Applications with ClickOnce</span></span>

<span data-ttu-id="082c8-103">Windows Communication Foundation (WCF) を使用するクライアントアプリケーションは、ClickOnce テクノロジを使用して配置できます。</span><span class="sxs-lookup"><span data-stu-id="082c8-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="082c8-104">このテクノロジを使用すると、クライアント アプリケーションが、信頼できる証明書でデジタル署名されている場合、コード アクセス セキュリティによって提供されるランタイム セキュリティ保護を受けられます。</span><span class="sxs-lookup"><span data-stu-id="082c8-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="082c8-105">ClickOnce アプリケーションの署名に使用される証明書は、信頼された発行者のストアに存在する必要があり、またそのクライアント コンピューターのローカル セキュリティ ポリシーでは、発行者の証明書で署名されたアプリケーションに対して、完全信頼のアクセス許可が構成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="082c8-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="082c8-106">ClickOnce アプリケーションと信頼された発行元の構成については、「 [Clickonce 信頼された発行元の構成](/previous-versions/dotnet/articles/ms996418(v=msdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="082c8-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082c8-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="082c8-107">See also</span></span>

- [<span data-ttu-id="082c8-108">信頼されたアプリケーションの配置の概要</span><span class="sxs-lookup"><span data-stu-id="082c8-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="082c8-109">[Windows フォームアプリケーションの ClickOnce 配置](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="082c8-109">[ClickOnce Deployment for Windows Forms Applications](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>
