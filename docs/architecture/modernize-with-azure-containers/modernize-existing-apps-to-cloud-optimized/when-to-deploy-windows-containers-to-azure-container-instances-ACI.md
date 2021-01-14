---
title: Azure Container Instances (ACI) に Windows コンテナーをデプロイするタイミング
description: Azure Cloud と Windows コンテナーで既存の .NET アプリケーションを最新化する | Azure Container Instances (ACI) に Windows コンテナーをデプロイするタイミング
ms.date: 12/21/2020
ms.openlocfilehash: 556fe7cbec7d259db9ec886b777feda9eed09116
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025134"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="0f80f-103">Azure Container Instances (ACI) に Windows コンテナーをデプロイするタイミング</span><span class="sxs-lookup"><span data-stu-id="0f80f-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="0f80f-104">Azure Container Instances の主な価値提案は、それにコンテナーをすぐにデプロイできるということ、その環境を保守管理する必要がないこと、基礎となるオペレーティング システムや VM をアップグレードしたり、パッチを適用したりする必要がないこと、すべてが透過的であり、利用者に求められることはすぐに使える環境にコンテナーをデプロイすることだけであることです。</span><span class="sxs-lookup"><span data-stu-id="0f80f-104">The main value proposition of Azure Container Instances is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="0f80f-105">ACI を使用する理由とシナリオは、Azure VM と共にコンテナーを使用する主なシナリオに似ています。そのため、基本的に、Azure Container Instances を使用する主なシナリオは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0f80f-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="0f80f-106">**Dev/Test シナリオ**</span><span class="sxs-lookup"><span data-stu-id="0f80f-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="0f80f-107">**タスクの自動化**</span><span class="sxs-lookup"><span data-stu-id="0f80f-107">**Task automation**</span></span>
- <span data-ttu-id="0f80f-108">**CI/CD エージェント**</span><span class="sxs-lookup"><span data-stu-id="0f80f-108">**CI/CD agents**</span></span>
- <span data-ttu-id="0f80f-109">**小規模/スケール バッチ処理**</span><span class="sxs-lookup"><span data-stu-id="0f80f-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="0f80f-110">**単純な Web アプリ**</span><span class="sxs-lookup"><span data-stu-id="0f80f-110">**Simple web apps**</span></span>

<span data-ttu-id="0f80f-111">単純な Web アプリ シナリオは ACI にとって妥当なシナリオではありますが、ACI では、コンテナー イメージあたりコンテナー インスタンスが 1 つに限られるため、可用性が高くなく、スケーラビリティが限られることを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="0f80f-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="0f80f-112">ただし、1 つだけコンテナー インスタンスを提供するため、ACI をインフラストラクチャとして見なすとしても、通常の Azure VM と Windows Server の組み合わせと比べ、大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="0f80f-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="0f80f-113">ACI を使用するとき、コンテナーを自己保守環境にデプロイし、そのコンテナーに対してのみ料金を支払います。</span><span class="sxs-lookup"><span data-stu-id="0f80f-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="0f80f-114">VM を管理/更新/パッチ適用する必要はありません。そのため、VM と共にコンテナーを使用するようなほとんどのシナリオで、はるかに優れたプラットフォームとなります。</span><span class="sxs-lookup"><span data-stu-id="0f80f-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="0f80f-115">ACI の使用は単純であり、コンテナーをデプロイするだけです。VM 環境を作る必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0f80f-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="0f80f-116">Azure Container Instances (ACI) の主な利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f80f-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="0f80f-117">サーバーを管理せずにコンテナーを実行する</span><span class="sxs-lookup"><span data-stu-id="0f80f-117">Run containers without managing servers</span></span>
- <span data-ttu-id="0f80f-118">オンデマンド コンテナーでアジリティが向上する</span><span class="sxs-lookup"><span data-stu-id="0f80f-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="0f80f-119">コンテナーをクラウドにデプロイする作業が 1 回の命令で終わり、前例のないくらい単純で速い</span><span class="sxs-lookup"><span data-stu-id="0f80f-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="0f80f-120">ハイパーバイザー分離というセキュリティでアプリケーションを保護する</span><span class="sxs-lookup"><span data-stu-id="0f80f-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="0f80f-121">つまり、ACI を使用すると、仮想マシンを管理したり、新しいツールを習得したりすることなく、アプリを短期間で開発できます。</span><span class="sxs-lookup"><span data-stu-id="0f80f-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="0f80f-122">自分のアプリケーションをコンテナーに入れ、クラウドで実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="0f80f-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="0f80f-123">[前へ](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [次へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="0f80f-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
