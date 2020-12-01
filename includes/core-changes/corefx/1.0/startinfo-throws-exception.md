---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032058"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a><span data-ttu-id="c1042-101">開始されなかったプロセスについて Process.StartInfo が InvalidOperationException をスローする</span><span class="sxs-lookup"><span data-stu-id="c1042-101">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>

<span data-ttu-id="c1042-102">コードで開始されなかったプロセスの <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> プロパティの読み取りによって、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c1042-102">Reading the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start throws an <xref:System.InvalidOperationException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c1042-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="c1042-103">Change description</span></span>

<span data-ttu-id="c1042-104">.NET Framework では、コードで開始されなかったプロセスの <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> プロパティにアクセスすると、ダミーの <xref:System.Diagnostics.ProcessStartInfo> オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="c1042-104">In .NET Framework, accessing the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start returns a dummy <xref:System.Diagnostics.ProcessStartInfo> object.</span></span> <span data-ttu-id="c1042-105">ダミー オブジェクトには、<xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> を除くすべてのプロパティの既定値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1042-105">The dummy object contains default values for all of its properties except <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables>.</span></span>

<span data-ttu-id="c1042-106">.NET Core 1.0 以降では、開始されなかった (<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> が呼びされなかった) プロセスの <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> プロパティを読み取ると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c1042-106">Starting in .NET Core 1.0, if you read the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for a process that you didn't start (that is, by calling <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>), an <xref:System.InvalidOperationException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c1042-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="c1042-107">Version introduced</span></span>

<span data-ttu-id="c1042-108">1</span><span class="sxs-lookup"><span data-stu-id="c1042-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c1042-109">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="c1042-109">Recommended action</span></span>

<span data-ttu-id="c1042-110">コードで開始されなかったプロセスの <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> プロパティにアクセスしません。</span><span class="sxs-lookup"><span data-stu-id="c1042-110">Do not access the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start.</span></span> <span data-ttu-id="c1042-111">たとえば、<xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> によって返されるプロセスについて、このプロパティは読み取らないでください。</span><span class="sxs-lookup"><span data-stu-id="c1042-111">For example, don't read this property for processes returned by <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="c1042-112">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="c1042-112">Category</span></span>

<span data-ttu-id="c1042-113">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="c1042-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c1042-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="c1042-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
