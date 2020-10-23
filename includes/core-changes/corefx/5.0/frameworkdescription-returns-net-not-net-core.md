---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050568"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="865b7-101">FrameworkDescription の値が .NET Core ではなく .NET になる</span><span class="sxs-lookup"><span data-stu-id="865b7-101">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="865b7-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、".NET Core" ではなく ".NET" が返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="865b7-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

#### <a name="change-description"></a><span data-ttu-id="865b7-103">変更内容</span><span class="sxs-lookup"><span data-stu-id="865b7-103">Change description</span></span>

<span data-ttu-id="865b7-104">以前のバージョンの .NET では、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET Core" が返されます。たとえば、`.NET Core 3.1.1` です。</span><span class="sxs-lookup"><span data-stu-id="865b7-104">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="865b7-105">.NET 5.0 以降は、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET" が返されます。たとえば、`.NET 5.0.0` です。</span><span class="sxs-lookup"><span data-stu-id="865b7-105">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="865b7-106">変更理由</span><span class="sxs-lookup"><span data-stu-id="865b7-106">Reason for change</span></span>

<span data-ttu-id="865b7-107">.NET 5 では、`netcoreapp` は、短いターゲット フレームワーク モニカーとして `net` に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="865b7-107">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="865b7-108">一貫性を確保するために、フレームワークの説明も更新されています。</span><span class="sxs-lookup"><span data-stu-id="865b7-108">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="865b7-109">`FrameworkName` は <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> プロパティ以外の場所ではエンコードされないため、変更は表面的なものになります。</span><span class="sxs-lookup"><span data-stu-id="865b7-109">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="865b7-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="865b7-110">Version introduced</span></span>

<span data-ttu-id="865b7-111">5.0</span><span class="sxs-lookup"><span data-stu-id="865b7-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="865b7-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="865b7-112">Recommended action</span></span>

<span data-ttu-id="865b7-113"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> によって返される文字列で ".NET Core" を検索するすべてのコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="865b7-113">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

#### <a name="category"></a><span data-ttu-id="865b7-114">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="865b7-114">Category</span></span>

<span data-ttu-id="865b7-115">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="865b7-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="865b7-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="865b7-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
