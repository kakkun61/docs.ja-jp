---
ms.openlocfilehash: 8c05af045d2d9666b20f36e36c68cc853f906eae
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506855"
---

<span data-ttu-id="b49d2-101">.NET パッケージのインストール中に、`signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'` のようなエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b49d2-101">While installing the .NET package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="b49d2-102">一般に、このエラーは、.NET のパッケージ フィードが新しいバージョンのパッケージでアップグレード中であり、後でもう一度試す必要があることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="b49d2-102">Generally speaking, this error means that the package feed for .NET is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="b49d2-103">アップグレード中は、2 時間以上パッケージ フィードを利用できません。</span><span class="sxs-lookup"><span data-stu-id="b49d2-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="b49d2-104">2 時間以上このエラーが継続的に発生する場合は、<https://github.com/dotnet/core/issues> でイシューを報告してください。</span><span class="sxs-lookup"><span data-stu-id="b49d2-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
