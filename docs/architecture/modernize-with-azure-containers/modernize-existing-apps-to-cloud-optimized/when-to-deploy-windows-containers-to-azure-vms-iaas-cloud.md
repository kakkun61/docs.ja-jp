---
title: Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
description: Azure Cloud と Windows コンテナーで既存の .NET アプリケーションを最新化する | Azure VM (IaaS クラウド) に Windows コンテナーをデプロイするタイミング
ms.date: 12/21/2020
ms.openlocfilehash: 64ba53fa56227266ee0e61a128d18373a2dbbc93
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025095"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="8433b-103">Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング</span><span class="sxs-lookup"><span data-stu-id="8433b-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="8433b-104">組織で Azure VM を利用している場合、Windows コンテナーも使用しているとしても、IaaS を引き続き扱っています。</span><span class="sxs-lookup"><span data-stu-id="8433b-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="8433b-105">つまり、負荷分散型のインフラストラクチャで複数の VM にデプロイする必要があるとき、高度にスケーラブルなアプリケーションを実現するには、インフラストラクチャ運用、VM OS パッチ、複雑なインフラストラクチャを扱うことになります。</span><span class="sxs-lookup"><span data-stu-id="8433b-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load-balanced infrastructure.</span></span> <span data-ttu-id="8433b-106">Azure VM で Windows コンテナーを使用する主なシナリオは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8433b-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

- <span data-ttu-id="8433b-107">**Dev/test 環境**:クラウド内の VM は、クラウドでの開発とテストに最適です。</span><span class="sxs-lookup"><span data-stu-id="8433b-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="8433b-108">ニーズに合わせて環境を短時間で構築したり、停止したりできます。</span><span class="sxs-lookup"><span data-stu-id="8433b-108">You can rapidly create or stop the environment depending on your needs.</span></span>

- <span data-ttu-id="8433b-109">**小規模/中規模のスケーラビリティ ニーズ**:運用環境に必要な VM が 2 つか 3 つのシナリオでは、オーケストレーターなどのさらに高度な PaaS 環境に移行できるまで、少数の VM を管理すれば安上がりになります。</span><span class="sxs-lookup"><span data-stu-id="8433b-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a few VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

- <span data-ttu-id="8433b-110">**既存のデプロイ ツールを使用した運用環境**:VM またはベアメタル サーバー (Puppet や同様のツールなど) に複雑なデプロイを行う目的で、ツールに投資しているオンプレミス環境から移行することがあります。</span><span class="sxs-lookup"><span data-stu-id="8433b-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="8433b-111">運用環境のデプロイ プロシージャの変更を最小限に留めてクラウドに移行するために、そのツールを引き続き使用し、Azure VM にデプロイするかもしれません。</span><span class="sxs-lookup"><span data-stu-id="8433b-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="8433b-112">しかしながら、開発単位として Windows コンテナーを使用すれば、より良いデプロイが可能になります。</span><span class="sxs-lookup"><span data-stu-id="8433b-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8433b-113">[前へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[次へ](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="8433b-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>
