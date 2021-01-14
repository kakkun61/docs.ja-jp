---
title: ハイブリッド クラウド シナリオへの移行
description: Azure クラウドおよび Windows コンテナーを使用して既存の .NET アプリケーションを最新化する | ハイブリッド クラウド シナリオへの移行
ms.date: 12/21/2020
ms.openlocfilehash: d5bf7f08381f3718061742b37c73604d8e57f1e2
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025226"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="3f3d4-103">ハイブリッド クラウド シナリオへの移行</span><span class="sxs-lookup"><span data-stu-id="3f3d4-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="3f3d4-104">一部の組織や企業では、規制や独自のポリシーが理由で、アプリケーションの一部を Microsoft Azure を始めとするパブリック クラウドに移行することができません。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="3f3d4-105">しかしながら、どの組織でも、一部のアプリケーションをパブリック クラウドに、その他のアプリケーションをオンプレミスに配置することでメリットが得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="3f3d4-106">ところが、パブリック クラウドとオンプレミス環境では使用されるプラットフォームとテクノロジが異なるため、環境が混在することにより、過度に複雑化する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="3f3d4-107">Microsoft は最適なハイブリッド クラウド ソリューションを提供しています。そこでは、オンプレミスとパブリック クラウドの既存の資産を最適化しながら、Azure ハイブリッド クラウドの一貫性を確保できます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="3f3d4-108">Azure Stack (オンプレミス) と Azure (パブリック クラウド) のおかげで、既存のスキルを最大限活用し、クラウドまたはオンプレミスで実行できるアプリを構築するための柔軟で統合されたアプローチが得られます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="3f3d4-109">セキュリティに関しては、ハイブリッド クラウド全体で管理とセキュリティを一元化できます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="3f3d4-110">オンプレミスとクラウドのアプリにシングル サインオンを提供することで、データセンターからクラウドまで、すべての資産を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="3f3d4-111">この機能を実現するには、Active Directory をハイブリッド クラウドに拡張し、ID 管理を使用します。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-111">You accomplish this functionality by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="3f3d4-112">最後に、データのソースには関係なく、データをシームレスに分散して分析し、クラウドとオンプレミスの資産に同じクエリ言語を使用し、Azure で分析とディープ ラーニングを適用してデータを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="3f3d4-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="3f3d4-113">Azure Stack</span></span>

<span data-ttu-id="3f3d4-114">Azure Stack は、組織のデータセンターから Azure サービスを提供できるようにするハイブリッド クラウド プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="3f3d4-115">Azure Stack は、エッジ環境や非接続環境など、主要なシナリオで最新アプリケーション向けの新しいオプションをサポートし、セキュリティとコンプライアンスの特定の要件に対応できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="3f3d4-116">図 4-13 は、Microsoft が提供する真のハイブリッド クラウド プラットフォームの概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Azure Stack と Azure を使用した Microsoft ハイブリッド クラウド プラットフォームの図。](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="3f3d4-118">**図 4-13**</span><span class="sxs-lookup"><span data-stu-id="3f3d4-118">**Figure 4-13.**</span></span> <span data-ttu-id="3f3d4-119">Azure Stack と Azure を使用した Microsoft ハイブリッド クラウド プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="3f3d4-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="3f3d4-120">Azure Stack には、お客様のニーズに合わせて次の 2 つのデプロイ オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="3f3d4-121">Azure Stack 統合システム</span><span class="sxs-lookup"><span data-stu-id="3f3d4-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="3f3d4-122">Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="3f3d4-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="3f3d4-123">Azure Stack 統合システム</span><span class="sxs-lookup"><span data-stu-id="3f3d4-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="3f3d4-124">Azure Stack 統合システムは、Microsoft とハードウェア パートナーのパートナーシップを通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="3f3d4-125">このパートナーシップでは、管理の簡略化とのバランスが取れたクラウドベースのイノベーションを提供するソリューションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="3f3d4-126">Azure Stack はハードウェアとソフトウェアの統合システムとして提供されるため、クラウドからのイノベーションを引き続き採用しながら、適度な柔軟性と制御性を得られます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="3f3d4-127">Azure Stack 統合システムは、4 ノードから 12 ノードまでのサイズがあり、ハードウェア パートナーと Microsoft によって共同でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="3f3d4-128">Azure Stack 統合システムを使用して、運用ワークロード向けに新しいシナリオを実装します。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="3f3d4-129">Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="3f3d4-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="3f3d4-130">Microsoft Azure Stack Development Kit は、Azure Stack の評価と学習に使用できる Azure Stack の単一ノード デプロイです。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="3f3d4-131">Azure Stack Development Kit は開発環境としても使用でき、Azure と一貫性のある API とツールを使用して開発できます。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="3f3d4-132">Azure Stack Development Kit は、運用環境での使用を想定していません。</span><span class="sxs-lookup"><span data-stu-id="3f3d4-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3f3d4-133">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="3f3d4-133">Additional resources</span></span>

- <span data-ttu-id="3f3d4-134">**Azure ハイブリッド クラウド**</span><span class="sxs-lookup"><span data-stu-id="3f3d4-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="3f3d4-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="3f3d4-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="3f3d4-136">**Windows コンテナー用の Active Directory サービス アカウント**</span><span class="sxs-lookup"><span data-stu-id="3f3d4-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="3f3d4-137">**Active Directory サポートを含むコンテナーの作成**</span><span class="sxs-lookup"><span data-stu-id="3f3d4-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="3f3d4-138">**Azure ハイブリッド特典のライセンス**</span><span class="sxs-lookup"><span data-stu-id="3f3d4-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="3f3d4-139">[前へ](life-cycle-ci-cd-pipelines-devops-tools.md)
>[次へ](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="3f3d4-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
