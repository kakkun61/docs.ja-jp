---
title: NETSDK1022:重複する項目が含まれていました。
description: 既定のインクルードに基づいて重複する項目メッセージを解決する方法。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: bc803f5316bf09c12c563f1a63b8385d1be4e9ce
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506637"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="6cc97-103">NETSDK1022:重複する項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="6cc97-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="6cc97-104">**この記事の対象:**  ✔️ .NET 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="6cc97-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="6cc97-105">Visual Studio 2017 または MSBuild バージョン 15.3 以降、.NET SDK に既定でプロジェクト ディレクトリの項目が自動的に含まれています。</span><span class="sxs-lookup"><span data-stu-id="6cc97-105">Starting in Visual Studio 2017 / MSBuild version 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="6cc97-106">これには、`Compile` および `Content` のターゲットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6cc97-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="6cc97-107">これにより、プロジェクト ファイルの大部分がクリーンアップされ、複雑さが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="6cc97-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="6cc97-108">適切なプロパティを false に設定すると、以前の動作に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="6cc97-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="6cc97-109">`Compile` 項目の例:</span><span class="sxs-lookup"><span data-stu-id="6cc97-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
