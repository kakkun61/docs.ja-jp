---
title: MSBuild に関する破壊的変更
description: MSBuild for .NET Core 3.0 から 3.1 の破壊的変更を一覧で示します。
ms.date: 12/14/2020
ms.openlocfilehash: 1ed5878845406fa7727c644f1e196d63a860646a
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593449"
---
# <a name="msbuild-breaking-changes-in-net-core-30---31"></a><span data-ttu-id="8969a-103">.NET Core 3.0 から 3.1 の MSBuild に関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="8969a-103">MSBuild breaking changes in .NET Core 3.0 - 3.1</span></span>

<span data-ttu-id="8969a-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="8969a-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8969a-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="8969a-105">Breaking change</span></span> | <span data-ttu-id="8969a-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8969a-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="8969a-107">デザイン時のビルドから最上位のパッケージ参照のみが返される</span><span class="sxs-lookup"><span data-stu-id="8969a-107">Design-time builds only return top-level package references</span></span>](#design-time-builds-only-return-top-level-package-references) | <span data-ttu-id="8969a-108">3.1</span><span class="sxs-lookup"><span data-stu-id="8969a-108">3.1</span></span> |
| [<span data-ttu-id="8969a-109">リソース マニフェストのファイル名の変更</span><span class="sxs-lookup"><span data-stu-id="8969a-109">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="8969a-110">3.0</span><span class="sxs-lookup"><span data-stu-id="8969a-110">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="8969a-111">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8969a-111">.NET Core 3.1</span></span>

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="8969a-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8969a-112">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
