---
title: Wcf 開発者向けの gRPC-gRPC への WCF ソリューションの移行
description: GRPC で異なる種類の WCF サービスを同等のものに移行する方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 3bd35cb6119368ff3db3be9ab5fabf89f2652b29
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937962"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="468b7-103">WCF ソリューションを gRPC に移行する</span><span class="sxs-lookup"><span data-stu-id="468b7-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="468b7-104">この章では、ASP.NET Core 5.0 gRPC プロジェクトを操作する方法と、異なる種類の Windows Communication Foundation (WCF) サービスを同等の gRPC に移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="468b7-104">This chapter will describe how to work with ASP.NET Core 5.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="468b7-105">ASP.NET Core 5.0 gRPC プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="468b7-105">Create an ASP.NET Core 5.0 gRPC project.</span></span>
- <span data-ttu-id="468b7-106">GRPC 単項 RPC への単純な要求/応答操作。</span><span class="sxs-lookup"><span data-stu-id="468b7-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="468b7-107">GRPC クライアントストリーミング RPC への一方向操作。</span><span class="sxs-lookup"><span data-stu-id="468b7-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="468b7-108">完全な二重サービスから gRPC 双方向ストリーミング RPC。</span><span class="sxs-lookup"><span data-stu-id="468b7-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="468b7-109">また、ストリーミングサービスの使用と、データセットを返すためのフィールドの繰り返しを比較しています。また、章の最後にクライアントライブラリを使用する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="468b7-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="468b7-110">サンプル WCF アプリケーションは、一連の stock 取引サービスの最小スタブです。</span><span class="sxs-lookup"><span data-stu-id="468b7-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="468b7-111">依存関係の挿入のために、Autofac という名前のオープンソースのコントロールの反転 (IoC) コンテナーライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="468b7-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="468b7-112">これには、WCF サービスの種類ごとに1つずつ、3つのサービスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="468b7-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="468b7-113">これらのサービスについては、以降のセクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="468b7-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="468b7-114">ソリューションは、GitHub の [dotnet/grpc-wcf-開発者](https://github.com/dotnet-architecture/grpc-for-wcf-developers) からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="468b7-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="468b7-115">サービスは、偽のデータを使用して外部の依存関係を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="468b7-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="468b7-116">サンプルには、各サービスの WCF および gRPC 実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="468b7-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="468b7-117">[前へ](ws-protocols.md)
>[次へ](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="468b7-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
