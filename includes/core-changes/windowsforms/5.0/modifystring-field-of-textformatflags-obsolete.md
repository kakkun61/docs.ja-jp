---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400636"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="5f953-101">TextFormatFlags.ModifyString は古くなっています</span><span class="sxs-lookup"><span data-stu-id="5f953-101">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="5f953-102"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> フィールドには警告として非推奨マークが付いています。今後の .NET バージョンで削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5f953-102">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5f953-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="5f953-103">Change description</span></span>

<span data-ttu-id="5f953-104">以前のバージョンの .NET では、<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列挙フィールドは非推奨になっていません。</span><span class="sxs-lookup"><span data-stu-id="5f953-104">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="5f953-105">.NET 5.0 以降のバージョンでは、警告として非推奨マークが付いています。</span><span class="sxs-lookup"><span data-stu-id="5f953-105">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="5f953-106">このフィールドは今後の .NET バージョンで削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5f953-106">This field may be removed in a future .NET version.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5f953-107">変更理由</span><span class="sxs-lookup"><span data-stu-id="5f953-107">Reason for change</span></span>

<span data-ttu-id="5f953-108"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> で <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> に文字列を渡すと、その文字列が変化することがあります。</span><span class="sxs-lookup"><span data-stu-id="5f953-108">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="5f953-109">この動作は文字列の不変性という約束事を破るものであり、.NET ランタイムが致命的に破損するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="5f953-109">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5f953-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="5f953-110">Version introduced</span></span>

<span data-ttu-id="5f953-111">.NET 5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="5f953-111">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5f953-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="5f953-112">Recommended action</span></span>

<span data-ttu-id="5f953-113"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> に依存するコードがあれば、それを更新します。</span><span class="sxs-lookup"><span data-stu-id="5f953-113">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="5f953-114">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="5f953-114">Category</span></span>

<span data-ttu-id="5f953-115">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="5f953-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5f953-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="5f953-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
