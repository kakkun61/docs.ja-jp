---
title: MSBuild に関する破壊的変更
description: MSBuild for .NET Core における破壊的変更の一覧を示します。
ms.date: 02/10/2020
ms.openlocfilehash: 9b0fba30c8955a6099bde0dc95b4df65a151d9e6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159490"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="56144-103">MSBuild に関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="56144-103">MSBuild breaking changes</span></span>

<span data-ttu-id="56144-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="56144-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="56144-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="56144-105">Breaking change</span></span> | <span data-ttu-id="56144-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="56144-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="56144-107">TargetFramework が netcoreapp から net に変更される</span><span class="sxs-lookup"><span data-stu-id="56144-107">TargetFramework change from netcoreapp to net</span></span>](#targetframework-change-from-netcoreapp-to-net) | <span data-ttu-id="56144-108">5.0</span><span class="sxs-lookup"><span data-stu-id="56144-108">5.0</span></span> |
| [<span data-ttu-id="56144-109">.NET 5 を対象とする場合に NETCOREAPP3_1 プリプロセッサ シンボルが定義されない</span><span class="sxs-lookup"><span data-stu-id="56144-109">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="56144-110">5.0</span><span class="sxs-lookup"><span data-stu-id="56144-110">5.0</span></span> |
| [<span data-ttu-id="56144-111">PublishDepsFilePath の動作の変更</span><span class="sxs-lookup"><span data-stu-id="56144-111">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="56144-112">5.0</span><span class="sxs-lookup"><span data-stu-id="56144-112">5.0</span></span> |
| [<span data-ttu-id="56144-113">Directory.Packages.props ファイルが既定でインポートされる</span><span class="sxs-lookup"><span data-stu-id="56144-113">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="56144-114">5.0</span><span class="sxs-lookup"><span data-stu-id="56144-114">5.0</span></span> |
| [<span data-ttu-id="56144-115">リソース マニフェストのファイル名の変更</span><span class="sxs-lookup"><span data-stu-id="56144-115">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="56144-116">3.0</span><span class="sxs-lookup"><span data-stu-id="56144-116">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="56144-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="56144-117">.NET 5.0</span></span>

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="56144-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="56144-118">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
