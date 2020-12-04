---
title: .NET のツールと診断
author: IEvangelist
description: .NET 開発者が使用できる開発ツールと診断ツールについて説明します。
ms.author: dapine
ms.date: 10/21/2020
ms.topic: overview
ms.openlocfilehash: 07c1a161a0bb429403db6852fe77749d83c19ec0
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "96593833"
---
# <a name="tools-and-diagnostics-in-net"></a><span data-ttu-id="dbf05-103">.NET のツールと診断</span><span class="sxs-lookup"><span data-stu-id="dbf05-103">Tools and diagnostics in .NET</span></span>

<span data-ttu-id="dbf05-104">この記事では、.NET 開発者が使用できるさまざまなツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dbf05-104">In this article, you'll learn about the various tools available to .NET developers.</span></span> <span data-ttu-id="dbf05-105">.NET には、コマンドラインインターフェイス (CLI) を備えた堅牢なソフトウェア開発キット (SDK) があります。</span><span class="sxs-lookup"><span data-stu-id="dbf05-105">With .NET, you have a robust software development kit (SDK) that includes a command-line interface (CLI).</span></span> <span data-ttu-id="dbf05-106">.NET CLI では、の多くの機能が有効になります。NET ready の統合開発環境 (Ide)。</span><span class="sxs-lookup"><span data-stu-id="dbf05-106">The .NET CLI enables many of the features throughout the .NET-ready integrated development environments (IDEs).</span></span> <span data-ttu-id="dbf05-107">この記事では、パフォーマンスの問題を診断するための .NET CLI ツール、メモリリーク、高 CPU、デッドロック、コード分析のためのツールサポートなど、生産性機能に関するリソースも提供します。</span><span class="sxs-lookup"><span data-stu-id="dbf05-107">This article also provides resources to productivity capabilities, such as .NET CLI tools for diagnosing performance issues, memory leaks, high CPU, deadlocks, and tooling support for code analysis.</span></span>

## <a name="net-sdk"></a><span data-ttu-id="dbf05-108">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="dbf05-108">.NET SDK</span></span>

<span data-ttu-id="dbf05-109">.Net SDK には、.NET ランタイムと .NET CLI の両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbf05-109">The .NET SDK includes both the .NET Runtime and the .NET CLI.</span></span> <span data-ttu-id="dbf05-110">Windows、Linux、macOS、または Docker 用の [.NET SDK](https://dotnet.microsoft.com/download) をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="dbf05-110">You can download the [.NET SDK](https://dotnet.microsoft.com/download) for Windows, Linux, macOS, or Docker.</span></span> <span data-ttu-id="dbf05-111">詳細については、「 [.NET SDK の概要](../core/sdk.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf05-111">For more information, see [.NET SDK overview](../core/sdk.md).</span></span>

## <a name="net-cli"></a><span data-ttu-id="dbf05-112">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="dbf05-112">.NET CLI</span></span>

<span data-ttu-id="dbf05-113">.NET CLI は、.NET アプリケーションを開発、ビルド、実行、および発行するためのクロスプラットフォームツールチェーンです。</span><span class="sxs-lookup"><span data-stu-id="dbf05-113">The .NET CLI is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span> <span data-ttu-id="dbf05-114">.NET CLI は、.NET SDK に含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbf05-114">The .NET CLI is included with the .NET SDK.</span></span> <span data-ttu-id="dbf05-115">詳細については、「 [.NET CLI の概要](../core/tools/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf05-115">For more information, see [.NET CLI overview](../core/tools/index.md).</span></span>

## <a name="ides"></a><span data-ttu-id="dbf05-116">IDE</span><span class="sxs-lookup"><span data-stu-id="dbf05-116">IDEs</span></span>

<span data-ttu-id="dbf05-117">.NET アプリケーションは、 [Visual Studio Code](https://code.visualstudio.com/docs)、 [Visual Studio](/visualstudio/windows)、または [Visual Studio for Mac](/visualstudio/mac)で作成できます。</span><span class="sxs-lookup"><span data-stu-id="dbf05-117">You can write .NET applications in [Visual Studio Code](https://code.visualstudio.com/docs), [Visual Studio](/visualstudio/windows), or [Visual Studio for Mac](/visualstudio/mac).</span></span> <span data-ttu-id="dbf05-118">クラウドを利用した開発環境の詳細については、「 [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf05-118">For information on cloud-powered development environments, see [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline).</span></span>

## <a name="additional-tools"></a><span data-ttu-id="dbf05-119">その他のツール</span><span class="sxs-lookup"><span data-stu-id="dbf05-119">Additional tools</span></span>

<span data-ttu-id="dbf05-120">.NET では、より一般的なツールだけでなく、特定のシナリオ用のツールも用意されています。</span><span class="sxs-lookup"><span data-stu-id="dbf05-120">In addition to the more common tools, .NET also provides tools for specific scenarios.</span></span> <span data-ttu-id="dbf05-121">一部のユースケースには、.NET SDK または .NET ランタイムのアンインストール、Windows Communication Foundation (WCF) メタデータの取得、プロキシソースコードの生成、XML のシリアル化などがあります。</span><span class="sxs-lookup"><span data-stu-id="dbf05-121">Some of the use cases include uninstalling the .NET SDK or the .NET Runtime, retrieving Windows Communication Foundation (WCF) metadata, generating proxy source code, and serializing XML.</span></span> <span data-ttu-id="dbf05-122">詳細については、「 [.net の追加ツールの概要](../core/additional-tools/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf05-122">For more information, see [.NET additional tools overview](../core/additional-tools/index.md).</span></span>

## <a name="diagnostics-and-instrumentation"></a><span data-ttu-id="dbf05-123">診断とインストルメンテーション</span><span class="sxs-lookup"><span data-stu-id="dbf05-123">Diagnostics and instrumentation</span></span>

<span data-ttu-id="dbf05-124">.NET 開発者は、一般的なパフォーマンス診断ツールを利用して、アプリのパフォーマンスの監視、トレースによるアプリのプロファイリング、パフォーマンスメトリックの収集、およびダンプファイルの分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="dbf05-124">As a .NET developer, you can make use of common performance diagnostic tools to monitor app performance, profile apps with tracing, collect performance metrics, and analyze dump files.</span></span> <span data-ttu-id="dbf05-125">イベントカウンターを使用してパフォーマンスメトリックを収集し、プロファイリングツールを使用して、アプリの動作についての洞察を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="dbf05-125">You collect performance metrics with event counters, and use profiling tools to gain insights into how apps perform.</span></span> <span data-ttu-id="dbf05-126">詳細については、「 [.net 診断ツール](../core/diagnostics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf05-126">For more information, see [.NET diagnostics tools](../core/diagnostics/index.md).</span></span>

## <a name="code-analysis"></a><span data-ttu-id="dbf05-127">コード分析</span><span class="sxs-lookup"><span data-stu-id="dbf05-127">Code analysis</span></span>

<span data-ttu-id="dbf05-128">.NET compiler platform (Roslyn) アナライザーは、コード品質とコードスタイルの問題について、C# または Visual Basic コードを検査します。</span><span class="sxs-lookup"><span data-stu-id="dbf05-128">The .NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="dbf05-129">詳細については、「 [.net ソースコード分析の概要](code-analysis/overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbf05-129">For more information, see [.NET source code analysis overview](code-analysis/overview.md).</span></span>
