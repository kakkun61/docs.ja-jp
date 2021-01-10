---
title: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
description: Docker および Microsoft のプラットフォームとツールでコンテナー化されたアプリケーションを開発およびデプロイするための、開発とデプロイのプロセスの概要を説明します。
ms.date: 01/06/2021
ms.openlocfilehash: 94c277e349bacee9b9fc7b160043005dd4135958
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970116"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="2cfde-103">Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル</span><span class="sxs-lookup"><span data-stu-id="2cfde-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![本の表紙](./media/devops-book-cover-large-we.png)

<span data-ttu-id="2cfde-105">**エディション v5.0** - ASP.NET Core 5.0 に更新されました</span><span class="sxs-lookup"><span data-stu-id="2cfde-105">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="2cfde-106">書籍の更新とコミュニティへの投稿については、「[changelog](https://aka.ms/DockerLifecycleEbookChangelog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cfde-106">Refer [changelog](https://aka.ms/DockerLifecycleEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="2cfde-107">このガイドは、Microsoft のプラットフォームとツールを使用して、コンテナー化された ASP.NET Core アプリケーションを Docker で開発およびデプロイするための一般的な概要です。</span><span class="sxs-lookup"><span data-stu-id="2cfde-107">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="2cfde-108">このガイドには、CI/CD パイプラインを実装するための Azure DevOps の概要、Azure Container Registry (ACR)、デプロイ用の Azure Kubernetes Services AKS が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2cfde-108">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="2cfde-109">開発に関連した低レベルの詳細については、『[.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ](../microservices/index.md)』 ガイドと IT 関連の参照アプリケーション [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2cfde-109">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](../microservices/index.md) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="2cfde-110">フィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="2cfde-110">Send us your feedback!</span></span>

<span data-ttu-id="2cfde-111">このガイドは、コンテナー化されたアプリケーションと .NET のマイクロサービスのアーキテクチャの理解を促進する目的で書かれています。</span><span class="sxs-lookup"><span data-stu-id="2cfde-111">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="2cfde-112">ガイドと関連する参照アプリケーションは進化していくため、お客様のフィードバックをお待ちしています。</span><span class="sxs-lookup"><span data-stu-id="2cfde-112">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="2cfde-113">このガイドを改善する方法に関するコメントがある場合は、<https://aka.ms/ebookfeedback> にフィードバックを送信してください。</span><span class="sxs-lookup"><span data-stu-id="2cfde-113">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="2cfde-114">謝辞</span><span class="sxs-lookup"><span data-stu-id="2cfde-114">Credits</span></span>

<span data-ttu-id="2cfde-115">作成者:</span><span class="sxs-lookup"><span data-stu-id="2cfde-115">Author:</span></span>

> <span data-ttu-id="2cfde-116">**Cesar de la Torre**、Microsoft Corp.、.NET 製品チーム、シニア PM</span><span class="sxs-lookup"><span data-stu-id="2cfde-116">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="2cfde-117">総合編集者:</span><span class="sxs-lookup"><span data-stu-id="2cfde-117">Acquisitions Editor:</span></span>

> <span data-ttu-id="2cfde-118">**Janine Patrick**</span><span class="sxs-lookup"><span data-stu-id="2cfde-118">**Janine Patrick**</span></span>

<span data-ttu-id="2cfde-119">監修者:</span><span class="sxs-lookup"><span data-stu-id="2cfde-119">Developmental Editor:</span></span>

> <span data-ttu-id="2cfde-120">**Bob Russell**、Microsoft、ソリューション プロフェッショナル</span><span class="sxs-lookup"><span data-stu-id="2cfde-120">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="2cfde-121">**Octal Publishing, Inc.**</span><span class="sxs-lookup"><span data-stu-id="2cfde-121">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="2cfde-122">制作者:</span><span class="sxs-lookup"><span data-stu-id="2cfde-122">Editorial Production:</span></span>

> [<span data-ttu-id="2cfde-123">Dianne Russell</span><span class="sxs-lookup"><span data-stu-id="2cfde-123">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="2cfde-124">**Octal Publishing, Inc.**</span><span class="sxs-lookup"><span data-stu-id="2cfde-124">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="2cfde-125">原稿整理編集者:</span><span class="sxs-lookup"><span data-stu-id="2cfde-125">Copyeditor:</span></span>

> <span data-ttu-id="2cfde-126">**Bob Russell**、Microsoft、ソリューション プロフェッショナル</span><span class="sxs-lookup"><span data-stu-id="2cfde-126">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="2cfde-127">参加者とレビュー担当者:</span><span class="sxs-lookup"><span data-stu-id="2cfde-127">Participants and reviewers:</span></span>

> <span data-ttu-id="2cfde-128">**Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="2cfde-128">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="2cfde-129">**Miguel Veloso**、Plain Concepts のソフトウェア開発エンジニア</span><span class="sxs-lookup"><span data-stu-id="2cfde-129">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="2cfde-130">**Sumit Ghosh**、Neudesic、主席コンサルタント</span><span class="sxs-lookup"><span data-stu-id="2cfde-130">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="2cfde-131">Copyright</span><span class="sxs-lookup"><span data-stu-id="2cfde-131">Copyright</span></span>

<span data-ttu-id="2cfde-132">発行者</span><span class="sxs-lookup"><span data-stu-id="2cfde-132">PUBLISHED BY</span></span>

<span data-ttu-id="2cfde-133">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="2cfde-133">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="2cfde-134">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2cfde-134">A division of Microsoft Corporation</span></span>

<span data-ttu-id="2cfde-135">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="2cfde-135">One Microsoft Way</span></span>

<span data-ttu-id="2cfde-136">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="2cfde-136">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="2cfde-137">Copyright &copy; 2021 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2cfde-137">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="2cfde-138">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="2cfde-138">All rights reserved.</span></span> <span data-ttu-id="2cfde-139">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="2cfde-139">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="2cfde-140">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="2cfde-140">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="2cfde-141">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2cfde-141">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="2cfde-142">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="2cfde-142">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="2cfde-143">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="2cfde-143">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="2cfde-144"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="2cfde-144">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="2cfde-145">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="2cfde-145">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="2cfde-146">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="2cfde-146">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="2cfde-147">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="2cfde-147">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="2cfde-148">次へ</span><span class="sxs-lookup"><span data-stu-id="2cfde-148">Next</span></span>](introduction-to-containers-and-docker.md)
