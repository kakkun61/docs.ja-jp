---
title: Microsoft ツールを使用した Docker アプリケーション DevOps ワークフロー
description: Microsoft プラットフォームでのコンテナー化された Docker アプリケーションのライフサイクルと Microsoft ツールでの Tools DevOps ワークフロー
ms.date: 01/06/2021
ms.openlocfilehash: 7f2d380dec046804772ea7d13e764ab6f3224c12
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970155"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a><span data-ttu-id="a3050-103">Microsoft ツールを使用した Docker アプリケーション DevOps ワークフロー</span><span class="sxs-lookup"><span data-stu-id="a3050-103">Docker application DevOps workflow with Microsoft tools</span></span>

<span data-ttu-id="a3050-104">*Microsoft Visual Studio、Azure DevOps Services、Team Foundation Server、Azure Monitor は、開発および IT 操作の包括的なエコシステムを提供します。これにより、チームでは、プロジェクトを管理し、コンテナー化アプリケーションを迅速にビルド、テスト、展開することができます。*</span><span class="sxs-lookup"><span data-stu-id="a3050-104">*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server, and Azure Monitor provide a comprehensive ecosystem for development and IT operations that give your team the tools to manage projects and rapidly build, test, and deploy containerized applications.*</span></span>

<span data-ttu-id="a3050-105">クラウドの Visual Studio と Azure DevOps Services と、オンプレミスの Team Foundation Server により、開発チームは、Windows または Linux を対象にするコンテナー化アプリケーションを生産的に直接ビルド、テスト、リリースできます。</span><span class="sxs-lookup"><span data-stu-id="a3050-105">With Visual Studio and Azure DevOps Services in the cloud, along with Team Foundation Server on-premises, development teams can productively build, test, and release containerized applications that target either Windows or Linux.</span></span>

<span data-ttu-id="a3050-106">Microsoft ツールは、Docker、.NET、または他のプラットフォームとのあらゆる組み合わせのコンテナー化アプリケーションの特定の実装の、グローバル ビルド、継続的インテグレーション (CI)、Azure DevOps Services または Team Foundation Server でのテストから、Docker 環境 (開発、ステージング、実稼働) への継続的デプロイ (CD) と Azure Monitor を介した開発チームへのサービスに関する分析情報の転送のパイプラインを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="a3050-106">Microsoft tools can automate the pipeline for specific implementations of containerized applications—Docker, .NET, or any combination with other platforms—from global builds and Continuous Integration (CI) and tests with Azure DevOps Services or Team Foundation Server, to Continuous Deployment (CD) to Docker environments (Development, Staging, Production), and to transmit analytics information about the services to the development team through Azure Monitor.</span></span> <span data-ttu-id="a3050-107">すべてのコードのコミットでビルド (CI) を開始して、特定のコンテナー化された環境 (CD) に自動的にサービスを展開できます。</span><span class="sxs-lookup"><span data-stu-id="a3050-107">Every code commit can initiate a build (CI) and automatically deploy the services to specific containerized environments (CD).</span></span>

<span data-ttu-id="a3050-108">開発者およびテスト担当者は、Microsoft Azure のテンプレートを使用して、Docker に基づく運用環境のような開発とテストの環境を、簡単かつ迅速にプロビジョニングできます。</span><span class="sxs-lookup"><span data-stu-id="a3050-108">Developers and testers can easily and quickly provision production-like development and test environments based on Docker by using templates in Microsoft Azure.</span></span>

<span data-ttu-id="a3050-109">コンテナー化アプリケーションの開発は、ビジネスが複雑であり、拡張のニーズがあればあるほど、着実に複雑になります。</span><span class="sxs-lookup"><span data-stu-id="a3050-109">The complexity of containerized application development increases steadily depending on the business complexity and scalability needs.</span></span> <span data-ttu-id="a3050-110">この複雑性の良い例は、マイクロサービス アーキテクチャに基づいたアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="a3050-110">A good example of this complexity are applications based on microservices architectures.</span></span> <span data-ttu-id="a3050-111">このような環境で成功するには、プロジェクトのライフ サイクル全体が自動化される必要があります。ビルドや展開のみでなく、製品利用統計情報のコレクションと共に、バージョンも管理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3050-111">To succeed in such an environment, your project must automate the entire life cycle—not only the build and deployment, but it also must manage versions along with the collection of telemetry.</span></span> <span data-ttu-id="a3050-112">Azure DevOps Services と Azure には、次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="a3050-112">Azure DevOps Services and Azure offer the following capabilities:</span></span>

- <span data-ttu-id="a3050-113">(Git または Team Foundation バージョン管理に基づく) Azure DevOps Services と Team Foundation Server のソース コード管理、(アジャイル、スクラム、CMMI がサポートされている) アジャイル計画、CI、リリース管理、アジャイル チーム用の他のツール。</span><span class="sxs-lookup"><span data-stu-id="a3050-113">Azure DevOps Services/Team Foundation Server source code management (based on Git or Team Foundation Version Control), Agile planning (Agile, Scrum, and CMMI are supported), CI, release management, and other tools for Agile teams.</span></span>

- <span data-ttu-id="a3050-114">Azure DevOps Services と Team Foundation Server にはファースト パーティおよびサード パーティの高性能な拡張機能からなるエコシステムが含まれ、そのエコシステムは増加を続けています。このような拡張機能を使用すると、マイクロサービス用に、CI、ビルド、テスト、出荷、リリース管理パイプラインを容易に構成できます。</span><span class="sxs-lookup"><span data-stu-id="a3050-114">Azure DevOps Services and Team Foundation Server include a powerful and growing ecosystem of first and third-party extensions with which you easily can construct a CI, build, test, delivery, and release management pipeline for microservices.</span></span>

- <span data-ttu-id="a3050-115">Azure DevOps Services でビルド パイプラインの一部として、自動テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3050-115">Run automated tests as part of your build pipeline in Azure DevOps Services.</span></span>

- <span data-ttu-id="a3050-116">Azure DevOps Services では、実稼働環境用のみでなく、A/B 実験、[カナリヤ リリース](https://martinfowler.com/bliki/CanaryRelease.html)など、テスト用を含む複数の環境への配信により、DevOps のライフ サイクルを強化できます。</span><span class="sxs-lookup"><span data-stu-id="a3050-116">Azure DevOps Services can tighten the DevOps life cycle with delivery to multiple environments, not just for production environments, but also for testing, including A/B experimentation, [canary releases](https://martinfowler.com/bliki/CanaryRelease.html), and so on.</span></span>

- <span data-ttu-id="a3050-117">組織は、Azure Container Registry に格納されたプライベート イメージから Docker コンテナーを、Azure Resource Manager テンプレートと既に使い慣れているツールを使用して、(Data、PaaS などの) Azure コンポーネントの任意の依存関係と共に簡単にプロビジョニングできます。</span><span class="sxs-lookup"><span data-stu-id="a3050-117">Organizations easily can provision Docker containers from private images stored in Azure Container Registry along with any dependency on Azure components (Data, PaaS, etc.) using Azure Resource Manager templates with tools they're already comfortable with.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a3050-118">[前へ](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[次へ](docker-application-outer-loop-devops-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a3050-118">[Previous](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
[Next](docker-application-outer-loop-devops-workflow.md)</span></span>
