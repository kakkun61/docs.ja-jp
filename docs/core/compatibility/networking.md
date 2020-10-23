---
title: ネットワークに関する破壊的変更
description: .NET Core のネットワークに関する破壊的変更の一覧を示します。
ms.date: 05/05/2020
ms.openlocfilehash: fdbd3f3bdcae5048b4f01e4d827f8a0e876c5c15
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050522"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="1158d-103">ネットワークに関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="1158d-103">Networking breaking changes</span></span>

<span data-ttu-id="1158d-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="1158d-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="1158d-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="1158d-105">Breaking change</span></span> | <span data-ttu-id="1158d-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="1158d-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="1158d-107">NegotiateStream と SslStream によって連続した Begin 操作を許可する</span><span class="sxs-lookup"><span data-stu-id="1158d-107">NegotiateStream and SslStream allow successive Begin operations</span></span>](#negotiatestream-and-sslstream-allow-successive-begin-operations) | <span data-ttu-id="1158d-108">5.0</span><span class="sxs-lookup"><span data-stu-id="1158d-108">5.0</span></span> |
| [<span data-ttu-id="1158d-109">Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される</span><span class="sxs-lookup"><span data-stu-id="1158d-109">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>](#socketlocalendpoint-is-updated-after-calling-sendtoasync) | <span data-ttu-id="1158d-110">5.0</span><span class="sxs-lookup"><span data-stu-id="1158d-110">5.0</span></span> |
| [<span data-ttu-id="1158d-111">.NET ランタイムからの WinHttpHandler の削除</span><span class="sxs-lookup"><span data-stu-id="1158d-111">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="1158d-112">5.0</span><span class="sxs-lookup"><span data-stu-id="1158d-112">5.0</span></span> |
| [<span data-ttu-id="1158d-113">MulticastOption.Group で null 値を受け付けない</span><span class="sxs-lookup"><span data-stu-id="1158d-113">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="1158d-114">5.0</span><span class="sxs-lookup"><span data-stu-id="1158d-114">5.0</span></span> |
| [<span data-ttu-id="1158d-115">現在、Cookie パスの処理は、RFC 6265 に準拠している</span><span class="sxs-lookup"><span data-stu-id="1158d-115">Cookie Path handling now conforms to RFC 6265</span></span>](#cookie-path-handling-now-conforms-to-rfc-6265) | <span data-ttu-id="1158d-116">5.0</span><span class="sxs-lookup"><span data-stu-id="1158d-116">5.0</span></span> |
| [<span data-ttu-id="1158d-117">HttpRequestMessage.Version の既定値が 1.1 に変更された</span><span class="sxs-lookup"><span data-stu-id="1158d-117">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="1158d-118">3.0</span><span class="sxs-lookup"><span data-stu-id="1158d-118">3.0</span></span> |
| [<span data-ttu-id="1158d-119">WebClient.CancelAsync がすぐにキャンセルされない場合がある</span><span class="sxs-lookup"><span data-stu-id="1158d-119">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="1158d-120">2.0</span><span class="sxs-lookup"><span data-stu-id="1158d-120">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="1158d-121">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1158d-121">.NET 5.0</span></span>

[!INCLUDE [negotiatestream-sslstream-dont-fail-on-successive-begin-calls](../../../includes/core-changes/networking/5.0/negotiatestream-sslstream-dont-fail-on-successive-begin-calls.md)]

***

[!INCLUDE [localendpoint-updated-on-sendtoasync](../../../includes/core-changes/networking/5.0/localendpoint-updated-on-sendtoasync.md)]

***

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="1158d-122">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1158d-122">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="1158d-123">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1158d-123">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
