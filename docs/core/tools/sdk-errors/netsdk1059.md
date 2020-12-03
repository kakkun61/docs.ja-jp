---
title: NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています
description: プロジェクトに古い .NET CLI ツールが含まれている問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: b80f42495e1aff8d37008946f10f68c195d5a9ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713120"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a><span data-ttu-id="806f3-103">NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています</span><span class="sxs-lookup"><span data-stu-id="806f3-103">NETSDK1059: Project contains obsolete .NET CLI tool</span></span>

<span data-ttu-id="806f3-104">**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="806f3-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="806f3-105">.NET SDK によって警告 NETSDK1059 が発行される場合、プロジェクトには古い .NET CLI ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="806f3-105">When the .NET SDK issues warning NETSDK1059, your project contains an obsolete .NET CLI tool.</span></span> <span data-ttu-id="806f3-106">.NET Core 2.1 では、これらのツールは .NET SDK に含まれており、プロジェクトによって明示的に参照される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="806f3-106">As of .NET Core 2.1, these tools are included in the .NET SDK and do not need to be explicitly referenced by the project.</span></span> <span data-ttu-id="806f3-107">.NET Core 2.1 への移行の詳細については、[こちら](https://aka.ms/dotnetclitools-in-box)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="806f3-107">More information for migrating to .NET Core 2.1 can be found [here](https://aka.ms/dotnetclitools-in-box).</span></span>
