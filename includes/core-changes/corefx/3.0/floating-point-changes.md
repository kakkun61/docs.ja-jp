---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032097"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="c7967-101">浮動小数点の書式設定と解析の動作が変更されました</span><span class="sxs-lookup"><span data-stu-id="c7967-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="c7967-102">(<xref:System.Double> および <xref:System.Single> 型による) 浮動小数点の解析と書式設定の動作が IEEE に準拠するようになりました。</span><span class="sxs-lookup"><span data-stu-id="c7967-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c7967-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="c7967-103">Change description</span></span>

<span data-ttu-id="c7967-104">.NET Core 2.2 以前のバージョンでは、<xref:System.Double.ToString%2A?displayProperty=nameWithType> および <xref:System.Single.ToString%2A?displayProperty=nameWithType> を使用した書式設定と <xref:System.Double.Parse%2A?displayProperty=nameWithType>、<xref:System.Double.TryParse%2A?displayProperty=nameWithType>、<xref:System.Single.Parse%2A?displayProperty=nameWithType>、および <xref:System.Single.TryParse%2A?displayProperty=nameWithType> を使用した解析は IEEE に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="c7967-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="c7967-105">その結果、任意のサポートされている標準またはカスタムの書式設定文字列について、値が往復することは保証できません。</span><span class="sxs-lookup"><span data-stu-id="c7967-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="c7967-106">一部の入力では、書式設定された値を解析しようとして失敗する場合や、解析された値は元の値と同じではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c7967-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="c7967-107">.NET Core 3.0 以降、解析および書式設定操作は IEEE 754 に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="c7967-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="c7967-108">これにより、.NET での浮動小数点型の動作が、C# などの IEEE 準拠言語の動作と一致するようになります。</span><span class="sxs-lookup"><span data-stu-id="c7967-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="c7967-109">詳細については、「[Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)」(.NET Core 3.0 での浮動小数点の解析と書式設定の強化) に関するブログ記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7967-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c7967-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="c7967-110">Version introduced</span></span>

<span data-ttu-id="c7967-111">3.0</span><span class="sxs-lookup"><span data-stu-id="c7967-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c7967-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="c7967-112">Recommended action</span></span>

<span data-ttu-id="c7967-113">「[Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)」(.NET Core 3.0 での浮動小数点の解析と書式設定の強化) に関するブログ記事の「Potential impact to existing code」(既存のコードに対して考えられる影響) セクションでは、.NET Core 2.2 アプリケーションと比較して動作の変化が見られた場合はコードの変更を提案しています。通常、これには、異なる標準またはカスタムの書式設定文字列を使用して目的の動作を強制することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c7967-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="c7967-114">一部の結果は、以前は正しくなかった場合、回避策がない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c7967-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="c7967-115">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="c7967-115">Category</span></span>

<span data-ttu-id="c7967-116">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="c7967-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c7967-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="c7967-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
