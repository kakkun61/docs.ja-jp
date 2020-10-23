---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050523"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="0f44e-101">NegotiateStream と SslStream によって連続した Begin 操作を許可する</span><span class="sxs-lookup"><span data-stu-id="0f44e-101">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="0f44e-102">セキュリティ ストリームでのエラー ケースの処理は異なり、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` に対する連続した呼び出しが失敗しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0f44e-102">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f44e-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="0f44e-103">Version introduced</span></span>

<span data-ttu-id="0f44e-104">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="0f44e-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="0f44e-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="0f44e-105">Change description</span></span>

<span data-ttu-id="0f44e-106">以前のバージョンの .NET では、最初に `EndAuthenticateAsServer` または `EndAuthenticateAsClient` を呼び出さずに、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出すと、<xref:System.NotSupportedException> になります。</span><span class="sxs-lookup"><span data-stu-id="0f44e-106">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="0f44e-107">.NET 5.0 以降では、これらの API は <xref:System.Threading.Tasks.Task> ベースの実装によってサポートされるため、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出しても <xref:System.NotSupportedException> にはなりません。</span><span class="sxs-lookup"><span data-stu-id="0f44e-107">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0f44e-108">変更理由</span><span class="sxs-lookup"><span data-stu-id="0f44e-108">Reason for change</span></span>

<span data-ttu-id="0f44e-109">内部実装を非同期プログラミング モデル (APM) から <xref:System.Threading.Tasks.Task> ベースに切り替えると、パフォーマンスが向上し、コードの複雑さが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="0f44e-109">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f44e-110">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="0f44e-110">Recommended action</span></span>

<span data-ttu-id="0f44e-111">開発者側では、何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0f44e-111">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="0f44e-112">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="0f44e-112">Category</span></span>

<span data-ttu-id="0f44e-113">ネットワーキング</span><span class="sxs-lookup"><span data-stu-id="0f44e-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f44e-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="0f44e-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

-->
