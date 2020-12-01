---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032055"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="a5ab7-101">UseShellExecute の既定値の変更</span><span class="sxs-lookup"><span data-stu-id="a5ab7-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="a5ab7-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> の .NET Core での既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="a5ab7-103">.NET Framework での既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a5ab7-104">変更の説明</span><span class="sxs-lookup"><span data-stu-id="a5ab7-104">Change description</span></span>

<span data-ttu-id="a5ab7-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> では、たとえば、ペイントを起動する `Process.Start("mspaint.exe")` などのコードを使用して、アプリケーションを直接起動することができます。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="a5ab7-106">また、<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> が `true` に設定されている場合、関連付けられているアプリケーションを間接的に起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="a5ab7-107">.NET Framework では、<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> の既定値は `true` です。つまり、 *.txt* ファイルをメモ帳に関連付けていれば、`Process.Start("mytextfile.txt")` のようなコードではそのエディターが起動されます。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="a5ab7-108">.NET Framework でアプリケーションを間接的に起動しないようにするには、明示的に <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> を `false` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="a5ab7-109">.NET Core で、<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> の既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="a5ab7-110">つまり、既定では、`Process.Start` を呼び出したとき、関連付けられているアプリケーションは起動されません。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="a5ab7-111">この変更は、パフォーマンス上の理由で .NET Core に導入されました。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="a5ab7-112">通常、<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> は、アプリケーションを直接起動するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="a5ab7-113">アプリケーションを直接起動するのに、Windows シェルを使用して、関連するパフォーマンス コストを生じさせる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="a5ab7-114">この既定のケースを高速化するために、.NET Core では、<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> の既定値を `false` に変更します。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="a5ab7-115">必要に応じて、低速パスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a5ab7-116">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a5ab7-116">Version introduced</span></span>

<span data-ttu-id="a5ab7-117">2.1</span><span class="sxs-lookup"><span data-stu-id="a5ab7-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="a5ab7-118">.NET Core の以前のバージョンでは、Windows に対して `UseShellExecute` は実装されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a5ab7-119">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a5ab7-119">Recommended action</span></span>

<span data-ttu-id="a5ab7-120">アプリが古い動作に依存している場合は、<xref:System.Diagnostics.ProcessStartInfo> オブジェクトで <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> を `true` に設定して <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a5ab7-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="a5ab7-121">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="a5ab7-121">Category</span></span>

<span data-ttu-id="a5ab7-122">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a5ab7-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a5ab7-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a5ab7-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
