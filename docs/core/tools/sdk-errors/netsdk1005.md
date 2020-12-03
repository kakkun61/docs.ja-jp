---
title: NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません
description: ターゲットがないアセット ファイルの問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 207c8b0274c13e7af594e05cfac2a95907f85b81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717904"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="08cd2-103">NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません</span><span class="sxs-lookup"><span data-stu-id="08cd2-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="08cd2-104">**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="08cd2-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="08cd2-105">.NET SDK でエラー NETSDK1005 または NETSDK1047 が発生した場合、プロジェクトのアセット ファイルには、ターゲット フレームワークのいずれかに関する情報が存在しません。</span><span class="sxs-lookup"><span data-stu-id="08cd2-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="08cd2-106">これは通常、復元が実行され、不足しているターゲット値がプロジェクトの `TargetFrameworks` プロパティに含まれていることを確認することによって解決できます。</span><span class="sxs-lookup"><span data-stu-id="08cd2-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="08cd2-107">Visual Studio 16.8 プレビューのバージョンで .NET 5 preview 8 の初期ビルドが使用された場合の既知の問題があり、それがこのエラーの原因となりました。</span><span class="sxs-lookup"><span data-stu-id="08cd2-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="08cd2-108">具体的には、不足しているターゲットが `net5.0-windows7.0` または `net5.0` の場合は、Visual Studio と .NET 5 SDK の最新バージョンに更新したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="08cd2-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
