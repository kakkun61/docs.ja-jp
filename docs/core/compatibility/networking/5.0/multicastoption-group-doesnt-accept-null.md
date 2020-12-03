---
title: 破壊的変更:MulticastOption.Group で null 値を受け付けない
description: .NET 5.0 での破壊的変更について学習します。MulticastOption.Group で null 値は受け付けられないようになりました。
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759387"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="f52de-103">MulticastOption.Group で null 値を受け付けない</span><span class="sxs-lookup"><span data-stu-id="f52de-103">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="f52de-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> で `null` の値を受け付けなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f52de-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="f52de-105">プロパティを `null` に設定すると、<xref:System.ArgumentNullException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f52de-105">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f52de-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f52de-106">Version introduced</span></span>

<span data-ttu-id="f52de-107">5.0</span><span class="sxs-lookup"><span data-stu-id="f52de-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="f52de-108">変更の説明</span><span class="sxs-lookup"><span data-stu-id="f52de-108">Change description</span></span>

<span data-ttu-id="f52de-109">以前のバージョンの .NET では、<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> プロパティを `null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="f52de-109">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="f52de-110"><xref:System.Net.Sockets.MulticastOption> が後で <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> に渡される場合、ランタイムによって <xref:System.NullReferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f52de-110">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="f52de-111">.NET 5.0 以降では、プロパティを `null` に設定した場合、<xref:System.ArgumentNullException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f52de-111">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f52de-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="f52de-112">Reason for change</span></span>

<span data-ttu-id="f52de-113">Framework デザイン ガイドラインとの一貫性を保つため、値が `null` の場合に <xref:System.ArgumentNullException> をスローするようにプロパティは更新されました。</span><span class="sxs-lookup"><span data-stu-id="f52de-113">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f52de-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f52de-114">Recommended action</span></span>

<span data-ttu-id="f52de-115"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> に `null` を設定していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f52de-115">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f52de-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f52de-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
