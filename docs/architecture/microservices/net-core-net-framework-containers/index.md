---
title: Docker コンテナー用 .NET 5 と .NET Framework の選択
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Docker コンテナー用 .NET 5 と .NET Framework の選択
ms.date: 01/13/2021
ms.openlocfilehash: 5c7ea1be02722fce7c5784afa89c18defbe4eeaf
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188648"
---
# <a name="choosing-between-net-and-net-framework-for-docker-containers"></a><span data-ttu-id="2ecae-103">Docker コンテナー用 .NET と .NET Framework の選択</span><span class="sxs-lookup"><span data-stu-id="2ecae-103">Choosing Between .NET and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="2ecae-104">.NET を使用してサーバー側のコンテナー化された Docker アプリケーションをビルドする場合に選択できるサポート対象のフレームワークには、[.NET Framework と .NET 5](https://dotnet.microsoft.com/download) の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="2ecae-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET 5](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="2ecae-105">それらは多数の .NET プラットフォームのコンポーネントを共有しているため、両者でコードを共有できます。</span><span class="sxs-lookup"><span data-stu-id="2ecae-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="2ecae-106">ただし、それらには基本的な違いがあり、どちらのフレームワークを使用するかは実行内容によって決まります。</span><span class="sxs-lookup"><span data-stu-id="2ecae-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="2ecae-107">このセクションでは、それぞれのフレームワークを選択する場合のガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2ecae-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2ecae-108">[前へ](../container-docker-introduction/docker-containers-images-registries.md)
>[次へ](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="2ecae-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
