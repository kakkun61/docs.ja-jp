---
title: 破壊的変更:Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される
description: .NET 5.0 での破壊的変更について学習します。SendToAsync によって、ローカル エンドポイント プロパティの値がソケットのローカル アドレスに更新されます。
ms.date: 10/18/2020
ms.openlocfilehash: 53d7da350eac6e65832012331044427fd90fe796
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759391"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="f8177-103">Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される</span><span class="sxs-lookup"><span data-stu-id="f8177-103">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="f8177-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値がソケットのローカル アドレスに更新されます。</span><span class="sxs-lookup"><span data-stu-id="f8177-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f8177-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f8177-105">Version introduced</span></span>

<span data-ttu-id="f8177-106">5.0</span><span class="sxs-lookup"><span data-stu-id="f8177-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="f8177-107">変更の説明</span><span class="sxs-lookup"><span data-stu-id="f8177-107">Change description</span></span>

<span data-ttu-id="f8177-108">以前のバージョンの .NET では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、ソケット インスタンスの <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f8177-108">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="f8177-109">.NET 5.0 以降では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> が正常に完了した場合、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値は暗黙的にバインドされたソケットのローカル アドレスになります。</span><span class="sxs-lookup"><span data-stu-id="f8177-109">Starting in .NET 5.0, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="f8177-110">この新しい動作は、<xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> および <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> の動作と同じです。</span><span class="sxs-lookup"><span data-stu-id="f8177-110">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f8177-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="f8177-111">Reason for change</span></span>

<span data-ttu-id="f8177-112">この変更によって、[バグが修正](https://github.com/dotnet/runtime/issues/915)され、`SendTo` バリアントとの間で動作に一貫性を持たせます。</span><span class="sxs-lookup"><span data-stu-id="f8177-112">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f8177-113">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="f8177-113">Recommended action</span></span>

<span data-ttu-id="f8177-114"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> によって <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値が変更されないことを前提とするコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="f8177-114">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f8177-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f8177-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
