---
title: コンテナーと Docker の概要
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | コンテナーと Docker の概要'
ms.date: 01/13/2021
ms.openlocfilehash: 5e114ae893176954cae6eb4425459527b248c0ad
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189331"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="de2f4-103">コンテナーと Docker の概要</span><span class="sxs-lookup"><span data-stu-id="de2f4-103">Introduction to Containers and Docker</span></span>

<span data-ttu-id="de2f4-104">コンテナリゼーションは、ソフトウェア開発のアプローチであり、アプリケーションまたはサービス、その依存関係、その構成 (展開マニフェスト ファイルとして抽象化) がコンテナー イメージとしてパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="de2f4-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="de2f4-105">コンテナー化アプリケーションは、ユニットとしてテストし、ホスト オペレーティング システム (OS) にコンテナー イメージ インスタンスとして展開することができます。</span><span class="sxs-lookup"><span data-stu-id="de2f4-105">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="de2f4-106">輸送用のコンテナーが、内部の貨物に関係なく商品を船舶、列車、またはトラックによって輸送できるのと同様に、ソフトウェア コンテナーは、別のコードと依存関係を含めることができるソフトウェア デプロイの標準的なユニットとして機能します。</span><span class="sxs-lookup"><span data-stu-id="de2f4-106">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software deployment that can contain different code and dependencies.</span></span> <span data-ttu-id="de2f4-107">ソフトウェアをこのようにコンテナー化することで、開発者や IT プロフェッショナルは、ほとんどまたはまったく変更せずに環境全体にソフトウェアを展開できます。</span><span class="sxs-lookup"><span data-stu-id="de2f4-107">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="de2f4-108">コンテナーは、共有 OS 上で個々のアプリケーションも分離します。</span><span class="sxs-lookup"><span data-stu-id="de2f4-108">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="de2f4-109">コンテナー化アプリケーションは、さらに、OS (Linux または Windows) で実行されているコンテナー ホスト上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="de2f4-109">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="de2f4-110">したがって、コンテナーは、仮想マシン (VM) のイメージよりもフット プリントが大幅に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="de2f4-110">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="de2f4-111">各コンテナーは、図 2-1 に示すように、Web アプリケーションまたはサービスの全体を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="de2f4-111">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="de2f4-112">この例では、Docker ホストが、コンテナー ホストであり、App1、App2、Svc 1、および Svc 2 はコンテナー化アプリケーションまたはサービスです。</span><span class="sxs-lookup"><span data-stu-id="de2f4-112">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![VM またはサーバーで実行されている 4 つのコンテナーを示す図。](./media/index/multiple-containers-single-host.png)

<span data-ttu-id="de2f4-114">**(図 2-1)** 。</span><span class="sxs-lookup"><span data-stu-id="de2f4-114">**Figure 2-1**.</span></span> <span data-ttu-id="de2f4-115">コンテナー ホストで実行されている複数のコンテナー</span><span class="sxs-lookup"><span data-stu-id="de2f4-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="de2f4-116">コンテナリゼーションのもう 1 つの利点はスケーラビリティです。</span><span class="sxs-lookup"><span data-stu-id="de2f4-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="de2f4-117">短期的なタスク用の新しいコンテナーを作成することでに簡単にスケール アウトできます。</span><span class="sxs-lookup"><span data-stu-id="de2f4-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="de2f4-118">アプリケーションの観点から、イメージのインスタンス化 (コンテナーの作成) は、サービスまたは Web アプリのようなプロセスのインスタンス化に似ています。</span><span class="sxs-lookup"><span data-stu-id="de2f4-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or a web app.</span></span> <span data-ttu-id="de2f4-119">ただし、信頼性のために、同じイメージの複数のインスタンスを複数のホスト サーバーで実行するときには通常、各コンテナー (イメージのインスタンス) を異なるフォールト ドメイン内の別のホスト サーバーまたは VM で実行します。</span><span class="sxs-lookup"><span data-stu-id="de2f4-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="de2f4-120">つまり、コンテナーには、アプリケーション ライフサイクル ワークフロー全体にわたり、分離、移植性、敏捷性、スケーラビリティ、およびコントロールの利点があります。</span><span class="sxs-lookup"><span data-stu-id="de2f4-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="de2f4-121">最も重要な利点は、開発と運用間で提供される環境の分離です。</span><span class="sxs-lookup"><span data-stu-id="de2f4-121">The most important benefit is the environment's isolation provided between Dev and Ops.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="de2f4-122">[前へ](../index.md)
>[次へ](docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="de2f4-122">[Previous](../index.md)
[Next](docker-defined.md)</span></span>
