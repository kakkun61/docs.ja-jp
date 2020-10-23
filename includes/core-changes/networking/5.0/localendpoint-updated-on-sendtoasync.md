---
ms.openlocfilehash: 8de70b0c445aa48fc4c3249ccfc8c095890fb14c
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050524"
---
### <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="b8b10-101">Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される</span><span class="sxs-lookup"><span data-stu-id="b8b10-101">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="b8b10-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値がソケットのローカル アドレスに更新されます。</span><span class="sxs-lookup"><span data-stu-id="b8b10-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b8b10-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b8b10-103">Version introduced</span></span>

<span data-ttu-id="b8b10-104">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="b8b10-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="b8b10-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="b8b10-105">Change description</span></span>

<span data-ttu-id="b8b10-106">以前のバージョンの .NET では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、ソケット インスタンスの <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="b8b10-106">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="b8b10-107">.NET 5.0 以降では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> が正常に完了した場合、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値は暗黙的にバインドされたソケットのローカル アドレスになります。</span><span class="sxs-lookup"><span data-stu-id="b8b10-107">Starting in .NET 5.0, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="b8b10-108">この新しい動作は、<xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> および <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> の動作と同じです。</span><span class="sxs-lookup"><span data-stu-id="b8b10-108">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b8b10-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="b8b10-109">Reason for change</span></span>

<span data-ttu-id="b8b10-110">この変更によって、[バグが修正](https://github.com/dotnet/runtime/issues/915)され、`SendTo` バリアントとの間で動作に一貫性を持たせます。</span><span class="sxs-lookup"><span data-stu-id="b8b10-110">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b8b10-111">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="b8b10-111">Recommended action</span></span>

<span data-ttu-id="b8b10-112"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> によって <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値が変更されないことを前提とするコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="b8b10-112">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="b8b10-113">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="b8b10-113">Category</span></span>

<span data-ttu-id="b8b10-114">ネットワーキング</span><span class="sxs-lookup"><span data-stu-id="b8b10-114">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b8b10-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b8b10-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

-->
