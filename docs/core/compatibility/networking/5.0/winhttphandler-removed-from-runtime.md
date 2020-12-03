---
title: 破壊的変更:.NET ランタイムからの WinHttpHandler の削除
description: .NET 5.0 での破壊的変更について学習します。WinHttpHandler が .NET ランタイムから削除されました。
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759383"
---
# <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="87da1-103">.NET ランタイムからの WinHttpHandler の削除</span><span class="sxs-lookup"><span data-stu-id="87da1-103">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="87da1-104">`WinHttpHandler` クラスが *System.Net.Http.dll* アセンブリから削除されました。</span><span class="sxs-lookup"><span data-stu-id="87da1-104">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="87da1-105">現在、これは帯域外 (OOB) [NuGet パッケージ](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)としてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="87da1-105">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="87da1-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="87da1-106">Version introduced</span></span>

<span data-ttu-id="87da1-107">5.0</span><span class="sxs-lookup"><span data-stu-id="87da1-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="87da1-108">変更の説明</span><span class="sxs-lookup"><span data-stu-id="87da1-108">Change description</span></span>

<span data-ttu-id="87da1-109">以前のバージョンの .NET では、<xref:System.Net.Http.WinHttpHandler> クラスは .NET のコア ライブラリの一部として使用できました。</span><span class="sxs-lookup"><span data-stu-id="87da1-109">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="87da1-110">.NET 5.0 以降、<xref:System.Net.Http.WinHttpHandler> クラスは、別にインストールする [NuGet パッケージ](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)のみとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="87da1-110">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="87da1-111">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="87da1-111">Recommended action</span></span>

<span data-ttu-id="87da1-112">[System.Net.Http.WinHttpHandler NuGet パッケージ](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="87da1-112">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="87da1-113">または、WinHTTP 固有の機能を必要としない場合は、代わりに <xref:System.Net.Http.SocketsHttpHandler> を使用します。</span><span class="sxs-lookup"><span data-stu-id="87da1-113">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="87da1-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="87da1-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
