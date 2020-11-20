---
ms.openlocfilehash: 3bb59ba23214f67100d3a78bb689c941b2d187e6
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506987"
---

<span data-ttu-id="9c81f-101">.NET パッケージのインストール中に、`Failed to fetch ... File has unexpected size ... Mirror sync in progress?` のようなエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="9c81f-101">While installing the .NET package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="9c81f-102">このエラーは、.NET のパッケージ フィードが新しいバージョンのパッケージでアップグレード中であり、後でもう一度試す必要があることを意味している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9c81f-102">This error could mean that the package feed for .NET is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="9c81f-103">アップグレード中は、30 分以上パッケージ フィードを利用できません。</span><span class="sxs-lookup"><span data-stu-id="9c81f-103">During an upgrade, the package feed shouldn't be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="9c81f-104">30 分以上このエラーが継続的に発生する場合は、<https://github.com/dotnet/core/issues> でイシューを報告してください。</span><span class="sxs-lookup"><span data-stu-id="9c81f-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
