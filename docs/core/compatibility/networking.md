---
title: ネットワークに関する破壊的変更
description: .NET Core 2.0 および 3.0 でのネットワークに関する破壊的変更の一覧を示します。
ms.date: 05/05/2020
ms.openlocfilehash: 761c6481888bcb8e91f7b4212355aca067632495
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689213"
---
# <a name="networking-breaking-changes-in-net-core-20-and-30"></a><span data-ttu-id="81eb3-103">.NET Core 2.0 および 3.0 でのネットワークに関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="81eb3-103">Networking breaking changes in .NET Core 2.0 and 3.0</span></span>

<span data-ttu-id="81eb3-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="81eb3-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="81eb3-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="81eb3-105">Breaking change</span></span> | <span data-ttu-id="81eb3-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="81eb3-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="81eb3-107">HttpRequestMessage.Version の既定値が 1.1 に変更された</span><span class="sxs-lookup"><span data-stu-id="81eb3-107">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="81eb3-108">3.0</span><span class="sxs-lookup"><span data-stu-id="81eb3-108">3.0</span></span> |
| [<span data-ttu-id="81eb3-109">WebClient.CancelAsync がすぐにキャンセルされない場合がある</span><span class="sxs-lookup"><span data-stu-id="81eb3-109">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="81eb3-110">2.0</span><span class="sxs-lookup"><span data-stu-id="81eb3-110">2.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="81eb3-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="81eb3-111">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="81eb3-112">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="81eb3-112">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
