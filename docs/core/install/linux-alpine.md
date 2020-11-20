---
title: Alpine に .NET をインストールする - .NET
description: Alpine に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506813"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="33b9e-103">Alpine に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="33b9e-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="33b9e-104">この記事では、Alpine に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="33b9e-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="33b9e-105">Alpine のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="33b9e-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="33b9e-106">ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="33b9e-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="33b9e-107">Alpine には、インストーラーはありません。</span><span class="sxs-lookup"><span data-stu-id="33b9e-107">There are no installers for Alpine.</span></span> <span data-ttu-id="33b9e-108">[インストール スクリプト](#scripted-install)を使用するか、[手動でのインストール](#manual-install)手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="33b9e-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="33b9e-109">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="33b9e-109">Supported distributions</span></span>

<span data-ttu-id="33b9e-110">次の表に、現在サポートされている .NET リリースと、それらがサポートされている Alpine のバージョンの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="33b9e-110">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="33b9e-111">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Alpine のバージョンの有効期限が切れるまで](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="33b9e-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="33b9e-112">✔️ は、Alpine または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="33b9e-112">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="33b9e-113">❌ は、Alpine または .NET のバージョンがその Alpine のリリースではサポートされないことを示します。</span><span class="sxs-lookup"><span data-stu-id="33b9e-113">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="33b9e-114">Alpine のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="33b9e-114">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="33b9e-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="33b9e-115">Alpine</span></span>  | <span data-ttu-id="33b9e-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-116">.NET Core 2.1</span></span> | <span data-ttu-id="33b9e-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-117">.NET Core 3.1</span></span> | <span data-ttu-id="33b9e-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-118">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="33b9e-119">✔️ 3.12</span><span class="sxs-lookup"><span data-stu-id="33b9e-119">✔️ 3.12</span></span> | <span data-ttu-id="33b9e-120">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-120">✔️ 2.1</span></span>        | <span data-ttu-id="33b9e-121">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-121">✔️ 3.1</span></span>        | <span data-ttu-id="33b9e-122">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-122">✔️ 5.0</span></span> |
| <span data-ttu-id="33b9e-123">✔️ 3.11</span><span class="sxs-lookup"><span data-stu-id="33b9e-123">✔️ 3.11</span></span> | <span data-ttu-id="33b9e-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-124">✔️ 2.1</span></span>        | <span data-ttu-id="33b9e-125">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-125">✔️ 3.1</span></span>        | <span data-ttu-id="33b9e-126">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-126">✔️ 5.0</span></span> |
| <span data-ttu-id="33b9e-127">✔️ 3.10</span><span class="sxs-lookup"><span data-stu-id="33b9e-127">✔️ 3.10</span></span> | <span data-ttu-id="33b9e-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-128">✔️ 2.1</span></span>        | <span data-ttu-id="33b9e-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-129">✔️ 3.1</span></span>        | <span data-ttu-id="33b9e-130">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-130">❌ 5.0</span></span> |
| <span data-ttu-id="33b9e-131">❌ 3.9</span><span class="sxs-lookup"><span data-stu-id="33b9e-131">❌ 3.9</span></span>  | <span data-ttu-id="33b9e-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-132">✔️ 2.1</span></span>        | <span data-ttu-id="33b9e-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-133">✔️ 3.1</span></span>        | <span data-ttu-id="33b9e-134">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-134">❌ 5.0</span></span> |
| <span data-ttu-id="33b9e-135">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="33b9e-135">❌ 3.8</span></span>  | <span data-ttu-id="33b9e-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-136">✔️ 2.1</span></span>        | <span data-ttu-id="33b9e-137">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="33b9e-137">✔️ 3.1</span></span>        | <span data-ttu-id="33b9e-138">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-138">❌ 5.0</span></span> |

<span data-ttu-id="33b9e-139">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="33b9e-139">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="33b9e-140">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="33b9e-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="33b9e-141">3.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-141">3.0</span></span>
- <span data-ttu-id="33b9e-142">2.2</span><span class="sxs-lookup"><span data-stu-id="33b9e-142">2.2</span></span>
- <span data-ttu-id="33b9e-143">2.0</span><span class="sxs-lookup"><span data-stu-id="33b9e-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="33b9e-144">依存関係</span><span class="sxs-lookup"><span data-stu-id="33b9e-144">Dependencies</span></span>

<span data-ttu-id="33b9e-145">Alpine Linux 上の .NET には、次の依存関係がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="33b9e-145">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="33b9e-146">icu-libs</span><span class="sxs-lookup"><span data-stu-id="33b9e-146">icu-libs</span></span>
- <span data-ttu-id="33b9e-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="33b9e-147">krb5-libs</span></span>
- <span data-ttu-id="33b9e-148">libgcc</span><span class="sxs-lookup"><span data-stu-id="33b9e-148">libgcc</span></span>
- <span data-ttu-id="33b9e-149">libintl</span><span class="sxs-lookup"><span data-stu-id="33b9e-149">libintl</span></span>
- <span data-ttu-id="33b9e-150">libssl1.1 (Alpine v3.9 以上)</span><span class="sxs-lookup"><span data-stu-id="33b9e-150">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="33b9e-151">libssl1.0 (Alpine v3.8 以下)</span><span class="sxs-lookup"><span data-stu-id="33b9e-151">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="33b9e-152">libstdc++</span><span class="sxs-lookup"><span data-stu-id="33b9e-152">libstdc++</span></span>
- <span data-ttu-id="33b9e-153">zlib</span><span class="sxs-lookup"><span data-stu-id="33b9e-153">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="33b9e-154">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="33b9e-154">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="33b9e-155">手動インストール</span><span class="sxs-lookup"><span data-stu-id="33b9e-155">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="33b9e-156">次の手順</span><span class="sxs-lookup"><span data-stu-id="33b9e-156">Next steps</span></span>

- [<span data-ttu-id="33b9e-157">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="33b9e-157">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
