---
ms.openlocfilehash: 05aec429e28ef74515ef6988d5b064e6d16b7c1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032672"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="1c62e-101">SignalR:HandshakeProtocol.SuccessHandshakeData が置き換えられました</span><span class="sxs-lookup"><span data-stu-id="1c62e-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="1c62e-102">[HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) フィールドが削除され、特定の `IHubProtocol` が指定された場合に適切なハンドシェイク応答を生成するヘルパー メソッドに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="1c62e-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1c62e-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="1c62e-103">Version introduced</span></span>

<span data-ttu-id="1c62e-104">3.0</span><span class="sxs-lookup"><span data-stu-id="1c62e-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1c62e-105">以前の動作</span><span class="sxs-lookup"><span data-stu-id="1c62e-105">Old behavior</span></span>

<span data-ttu-id="1c62e-106">`HandshakeProtocol.SuccessHandshakeData` は、`public static ReadOnlyMemory<byte>` フィールドでした。</span><span class="sxs-lookup"><span data-stu-id="1c62e-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1c62e-107">新しい動作</span><span class="sxs-lookup"><span data-stu-id="1c62e-107">New behavior</span></span>

<span data-ttu-id="1c62e-108">`HandshakeProtocol.SuccessHandshakeData` は、指定されたプロトコルに基づいて `ReadOnlyMemory<byte>` を返す `static` `GetSuccessfulHandshake(IHubProtocol protocol)` メソッドに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="1c62e-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1c62e-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="1c62e-109">Reason for change</span></span>

<span data-ttu-id="1c62e-110">ハンドシェイク _応答_ に、選択したプロトコルによって変化する非定数の追加フィールドが加えられました。</span><span class="sxs-lookup"><span data-stu-id="1c62e-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1c62e-111">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="1c62e-111">Recommended action</span></span>

<span data-ttu-id="1c62e-112">なし。</span><span class="sxs-lookup"><span data-stu-id="1c62e-112">None.</span></span> <span data-ttu-id="1c62e-113">この型は、ユーザー コードから使用するように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="1c62e-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="1c62e-114">これは `public` であり、SignalR サーバーとクライアントの間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="1c62e-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="1c62e-115">また、.NET で記述されたユーザーの SignalR クライアントによって使用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="1c62e-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="1c62e-116">SignalR の **ユーザー** は、この変更による影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="1c62e-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="1c62e-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="1c62e-117">Category</span></span>

<span data-ttu-id="1c62e-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1c62e-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c62e-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="1c62e-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=nameWithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
