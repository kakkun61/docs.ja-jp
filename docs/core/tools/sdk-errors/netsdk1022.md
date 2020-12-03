---
title: NETSDK1022:重複する項目が含まれていました。
description: 既定のインクルードに基づいて重複する項目メッセージを解決する方法。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: c2bdbbb5503e5e4f6e6826f95f5a2cb08c908ceb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717872"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="fbffb-103">NETSDK1022:重複する項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="fbffb-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="fbffb-104">**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="fbffb-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="fbffb-105">Visual Studio 2017 または MSBuild バージョン 15.3 以降、.NET SDK に既定でプロジェクト ディレクトリの項目が自動的に含まれています。</span><span class="sxs-lookup"><span data-stu-id="fbffb-105">Starting in Visual Studio 2017 / MSBuild version 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="fbffb-106">これには、`Compile` および `Content` のターゲットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fbffb-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="fbffb-107">これにより、プロジェクト ファイルの大部分がクリーンアップされ、複雑さが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="fbffb-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="fbffb-108">適切なプロパティを false に設定すると、以前の動作に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="fbffb-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="fbffb-109">`Compile` 項目の例:</span><span class="sxs-lookup"><span data-stu-id="fbffb-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
