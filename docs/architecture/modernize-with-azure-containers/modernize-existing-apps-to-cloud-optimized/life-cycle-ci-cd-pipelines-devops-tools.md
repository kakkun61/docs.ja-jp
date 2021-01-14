---
title: クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する
description: Azure クラウドおよび Windows コンテナーを使用して既存の .NET アプリケーションを最新化する | クラウドの CI/CD パイプラインと DevOps ツールを使用してアプリのライフサイクルを最新化する
ms.date: 12/21/2018
ms.openlocfilehash: e7ad76edb659fbacfc85cb398ec0c9fe9e3c66c9
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025252"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="877a9-103">クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する</span><span class="sxs-lookup"><span data-stu-id="877a9-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="877a9-104">今日の企業は、市場での競争力を高めるために、迅速にイノベーションを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="877a9-104">Today's businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="877a9-105">高品質で最新のアプリケーションを提供するには DevOps ツールおよびプロセスが必要で、この繰り返されるイノベーション サイクルの実装に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="877a9-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="877a9-106">適切な DevOps ツールを使用すると、開発者は継続的デプロイを効率化し、革新的なアプリケーションをより迅速にユーザーに届けることができます。</span><span class="sxs-lookup"><span data-stu-id="877a9-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="877a9-107">継続的インテグレーションとデプロイの方法は確立されていますが、コンテナーを導入することにより、複数コンテナー アプリケーションを使用している場合は特に、新たな考慮事項が生じます。</span><span class="sxs-lookup"><span data-stu-id="877a9-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="877a9-108">Azure DevOps Services では、Azure DevOps Services の公式のデプロイ タスクにより、さまざまな環境への複数コンテナー アプリケーションの継続的インテグレーションとデプロイがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="877a9-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to various environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="877a9-109">Azure Web App for Containers にデプロイする</span><span class="sxs-lookup"><span data-stu-id="877a9-109">Deploy to an Azure Web App for Containers</span></span>](/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="877a9-110">Azure Kubernetes Service にデプロイする</span><span class="sxs-lookup"><span data-stu-id="877a9-110">Deploy to Azure Kubernetes Service</span></span>](/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="877a9-111">ただし、Azure DevOps Services スクリプトベースのタスクを使用して、[Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) または DC/OS にデプロイすることもできます。</span><span class="sxs-lookup"><span data-stu-id="877a9-111">But you can also deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="877a9-112">デプロイのアジリティを促進し続けるために、これらのツールにより、開発および CI/CD ソリューションを選択して、コンテナーのワークロードに対して、開発からテスト、運用までの優れたデプロイ エクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="877a9-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="877a9-113">図 4-12 は、Azure Container Service で Kubernetes クラスターにデプロイする継続的デプロイ パイプラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="877a9-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Kubernetes クラスターにデプロイする Azure DevOps Services のスクリーンショット。](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="877a9-115">**図 4-12**</span><span class="sxs-lookup"><span data-stu-id="877a9-115">**Figure 4-12.**</span></span> <span data-ttu-id="877a9-116">Kubernetes クラスターにデプロイする、Azure DevOps Services の継続的デプロイ パイプライン</span><span class="sxs-lookup"><span data-stu-id="877a9-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="877a9-117">[前へ](modernize-your-apps-with-monitoring-and-telemetry.md)
>[次へ](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="877a9-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
