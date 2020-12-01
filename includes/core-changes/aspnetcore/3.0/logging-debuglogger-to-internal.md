---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032601"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="c55cc-101">ログ:internal になった DebugLogger クラス</span><span class="sxs-lookup"><span data-stu-id="c55cc-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="c55cc-102">`DebugLogger` のアクセス修飾子は、ASP.NET Core 3.0 より前では `public` でした。</span><span class="sxs-lookup"><span data-stu-id="c55cc-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="c55cc-103">このアクセス修飾子は、ASP.NET Core 3.0 では、`internal` に変わっています。</span><span class="sxs-lookup"><span data-stu-id="c55cc-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c55cc-104">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="c55cc-104">Version introduced</span></span>

<span data-ttu-id="c55cc-105">3.0</span><span class="sxs-lookup"><span data-stu-id="c55cc-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c55cc-106">変更理由</span><span class="sxs-lookup"><span data-stu-id="c55cc-106">Reason for change</span></span>

<span data-ttu-id="c55cc-107">次の理由により変更されています。</span><span class="sxs-lookup"><span data-stu-id="c55cc-107">The change is being made to:</span></span>

* <span data-ttu-id="c55cc-108">`ConsoleLogger` などの、その他のロガーの実装との整合性を確保します。</span><span class="sxs-lookup"><span data-stu-id="c55cc-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="c55cc-109">API サーフェイスを減らします。</span><span class="sxs-lookup"><span data-stu-id="c55cc-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c55cc-110">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="c55cc-110">Recommended action</span></span>

<span data-ttu-id="c55cc-111"><xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` 拡張メソッドを使用して、デバッグ ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c55cc-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="c55cc-112">サービスを手動で登録する必要がある場合、<xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> もまだ `public` です。</span><span class="sxs-lookup"><span data-stu-id="c55cc-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="c55cc-113">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="c55cc-113">Category</span></span>

<span data-ttu-id="c55cc-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c55cc-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c55cc-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="c55cc-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
