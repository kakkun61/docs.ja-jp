---
title: GRPC-gRPC の WCF 開発者向けの概要
description: GRPC の開発に関する一連の原則について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 99e1bdb1f49469f444044027c3ac5d927f9cab13
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938404"
---
# <a name="grpc-overview"></a><span data-ttu-id="f0630-103">gRPC の概要</span><span class="sxs-lookup"><span data-stu-id="f0630-103">gRPC overview</span></span>

<span data-ttu-id="f0630-104">最後の章で Windows Communication Foundation (WCF) と gRPC の両方の genesis を確認した後、この章では gRPC の主な機能と WCF との比較を検討します。</span><span class="sxs-lookup"><span data-stu-id="f0630-104">After looking at the genesis of both Windows Communication Foundation (WCF) and gRPC in the last chapter, this chapter considers some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="f0630-105">ASP.NET Core 3.0 は、grpc をファーストクラスの市民としてネイティブにサポートする ASP.NET の最初のリリースであり、gRPC の公式の .NET 実装に貢献する Microsoft チームがいます。</span><span class="sxs-lookup"><span data-stu-id="f0630-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="f0630-106">.NET を使用して、他のすべての主要なプログラミング言語とフレームワークと相互運用できる分散アプリケーションを構築することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0630-106">It's recommended for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="f0630-107">基本原則</span><span class="sxs-lookup"><span data-stu-id="f0630-107">Key principles</span></span>

<span data-ttu-id="f0630-108">第1章で説明したように、Google は、Stubby、その内部、汎用 RPC インフラストラクチャを置き換えるために、HTTP/2 の導入を使用する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="f0630-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to replace Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="f0630-109">Stubby に基づく gRPC は、標準化を利用できるようになり、モバイルコンピューティング、クラウド、およびモノのインターネットへの適用性が拡張されます。</span><span class="sxs-lookup"><span data-stu-id="f0630-109">gRPC, based on Stubby, now can take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="f0630-110">この標準化を実現するために、 [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) は grpc を管理する一連の原則を確立しました。</span><span class="sxs-lookup"><span data-stu-id="f0630-110">To achieve this standardization, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="f0630-111">次の一覧は最も関連性の高いものを示しています。主にアクセシビリティと使いやすさを最大限に活用することに関係しています。</span><span class="sxs-lookup"><span data-stu-id="f0630-111">The following list shows the most relevant ones, which are primarily concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="f0630-112">**Free および open** –すべての成果物がオープンソースであり、開発者が grpc の採用を制限しないライセンスを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0630-112">**Free and open** – All artifacts should be open source, with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="f0630-113">**カバレッジとシンプル** さ– grpc は、すべての一般的なプラットフォームで利用でき、任意のプラットフォーム上で構築するのに十分です。</span><span class="sxs-lookup"><span data-stu-id="f0630-113">**Coverage and simplicity** – gRPC should be available across every popular platform, and simple enough to build on any platform.</span></span>
- <span data-ttu-id="f0630-114">**相互運用性と接続性** -広く使用可能なネットワーク標準を使用して、帯域幅や待機時間に関係なく、すべてのネットワークで grpc を使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0630-114">**Interoperability and reach** – It should be possible to use gRPC on any network, regardless of bandwidth or latency, by using widely available network standards.</span></span>
- <span data-ttu-id="f0630-115">**一般的な目的と** パフォーマンスの向上–パフォーマンスを低下させずに、可能な限り幅広いユースケースでフレームワークを使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0630-115">**General purpose and performant** – The framework should be usable by as broad a range of use-cases as possible, without compromising performance.</span></span>
- <span data-ttu-id="f0630-116">**ストリーミング** –プロトコルは、大規模なデータセットまたは非同期メッセージングのストリーミングセマンティクスを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0630-116">**Streaming** – The protocol should provide streaming semantics for large datasets or asynchronous messaging.</span></span>
- <span data-ttu-id="f0630-117">**メタデータ交換** –プロトコルを使用すると、認証トークンなどの非ビジネスデータを実際のビジネスデータとは別に処理できます。</span><span class="sxs-lookup"><span data-stu-id="f0630-117">**Metadata exchange** – The protocol allows non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="f0630-118">標準化された **状態コード**–エラー処理の決定を明確にするために、エラーコードの変動を減らす必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0630-118">**Standardized status codes** – The variability of error codes should be reduced to make error handling decisions clearer.</span></span> <span data-ttu-id="f0630-119">さらに充実したエラー処理が必要な場合は、メタデータ交換内の動作を管理するためのメカニズムを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0630-119">Where additional, richer error handling is required, a mechanism should be provided for managing behavior within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f0630-120">[前へ](introduction.md)
>[次へ](approach.md)</span><span class="sxs-lookup"><span data-stu-id="f0630-120">[Previous](introduction.md)
[Next](approach.md)</span></span>
