---
title: WCF 開発者向け ASP.NET Core gRPC - WCF 開発者向け gRPC
description: WCF 開発者向け ASP.NET Core 3.0 で gRPC サービスを構築する方法の概要
ms.date: 09/02/2019
ms.openlocfilehash: c9cc5ef9c06d5262fb85850f8a3b178d46e5c6fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689278"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="eaa1b-103">WCF 開発者向け ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="eaa1b-103">ASP.NET Core gRPC for WCF Developers</span></span>

![カバーの画像](./media/cover.png)

<span data-ttu-id="eaa1b-105">発行者</span><span class="sxs-lookup"><span data-stu-id="eaa1b-105">PUBLISHED BY</span></span>

<span data-ttu-id="eaa1b-106">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="eaa1b-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="eaa1b-107">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="eaa1b-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="eaa1b-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="eaa1b-108">One Microsoft Way</span></span>

<span data-ttu-id="eaa1b-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="eaa1b-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="eaa1b-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="eaa1b-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="eaa1b-111">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="eaa1b-111">All rights reserved.</span></span> <span data-ttu-id="eaa1b-112">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="eaa1b-113">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="eaa1b-114">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="eaa1b-115">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="eaa1b-116">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="eaa1b-117"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="eaa1b-118">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="eaa1b-119">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="eaa1b-120">作成者:</span><span class="sxs-lookup"><span data-stu-id="eaa1b-120">Authors:</span></span>

> <span data-ttu-id="eaa1b-121">**Mark Rendle** - 技術部門最高責任者 - [Visual ReCode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="eaa1b-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="eaa1b-122">**Miranda Steiner** - 技術文書作成者</span><span class="sxs-lookup"><span data-stu-id="eaa1b-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="eaa1b-123">エディター:</span><span class="sxs-lookup"><span data-stu-id="eaa1b-123">Editor:</span></span>

> <span data-ttu-id="eaa1b-124">**Maira Wenzel** - シニア コンテンツ開発者 - Microsoft</span><span class="sxs-lookup"><span data-stu-id="eaa1b-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="eaa1b-125">はじめに</span><span class="sxs-lookup"><span data-stu-id="eaa1b-125">Introduction</span></span>

<span data-ttu-id="eaa1b-126">gRPC とは、ネットワーク接続されたサービスと分散型アプリケーションを構築するための最新のフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="eaa1b-127">SOAP のクロスプラットフォーム相互運用性と組み合わせた、Windows Communication Foundation (WCF) NetTCP バインドのパフォーマンスを想像してください。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="eaa1b-128">gRPC は、アプリケーションとサービス間のハイ パフォーマンスで低帯域幅の通信を実現できるように、HTTP/2 および Protobuf メッセージエンコード プロトコルに基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="eaa1b-129">.NET、Java、Python、Node.js、Go、C++ など、最も一般的なプログラミング言語およびプラットフォームにわたって、サーバー コードおよびクライアント コードの生成がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="eaa1b-130">ASP.NET Core 3.0 での gRPC 用の最上級のサポートと共に、.NET Framework 4.x 用の既存の gRPC ツールとライブラリを利用できることから、.NET Core を組織で採用することを検討している開発チームにとって、これは WCF に替わる優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET Framework 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="eaa1b-131">対象読者</span><span class="sxs-lookup"><span data-stu-id="eaa1b-131">Who should use this guide</span></span>

<span data-ttu-id="eaa1b-132">このガイドは、.NET Framework または .NET Core で作業している開発者の中でも、以前に WCF を使用したことがある方々、使用しているアプリケーションを .NET Core 3.0 以降のバージョン用の最新の RPC 環境に移行しようとしている方々向けに作成されています。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="eaa1b-133">より一般的に、このガイドは、NET Core 3.0 へのアップグレードを実施または検討していて、組み込みの gRPC ツールを使用する場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="eaa1b-134">このガイドを使用する方法</span><span class="sxs-lookup"><span data-stu-id="eaa1b-134">How you can use this guide</span></span>

<span data-ttu-id="eaa1b-135">ここでは、ASP.NET Core 3.0 で gRPC サービスを構築する方法について簡単に説明します。特に、類似のプラットフォームとして WCF について説明します。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="eaa1b-136">gRPC の原則について説明しており、各概念をそれに相当する WCF の機能に関連付けています。また、既存の WCF アプリケーションを gRPC に移行する方法を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="eaa1b-137">WCF の経験があり、新しいサービスを構築する目的で gRPC の知識を求めている開発者にとっても役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="eaa1b-138">独自のプロジェクトのためのテンプレートまたは参照としてサンプル アプリケーションを利用できます。本書やそのサンプルのコードは自由にコピーしたり、再利用したりしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="eaa1b-139">これらの考慮事項と営業案件の共通理解を確保するために、チームにこのガイドを自由に転送してください。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="eaa1b-140">用語の共通セットと基本原則を理解して全員が作業すると、アーキテクチャのパターンと実践方法を一貫して適用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eaa1b-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="eaa1b-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="eaa1b-141">References</span></span>

- <span data-ttu-id="eaa1b-142">**gRPC の Web サイト**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="eaa1b-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="eaa1b-143">**サーバー アプリ用 .NET Core と .NET Framework の選択**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="eaa1b-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="eaa1b-144">次へ</span><span class="sxs-lookup"><span data-stu-id="eaa1b-144">Next</span></span>](introduction.md)
