---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032072"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="de7f7-101">UriBuilder では今後、先頭に文字が付加されない</span><span class="sxs-lookup"><span data-stu-id="de7f7-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="de7f7-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> では今後、`#` 文字が先頭に付加されず、<xref:System.UriBuilder.Query?displayProperty=nameWithType> では今後、`?` 文字が先頭に付加されません (既に付いている場合)。</span><span class="sxs-lookup"><span data-stu-id="de7f7-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="de7f7-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="de7f7-103">Change description</span></span>

<span data-ttu-id="de7f7-104">.NET Framework では、<xref:System.UriBuilder.Fragment?displayProperty=nameWithType> プロパティと <xref:System.UriBuilder.Query?displayProperty=nameWithType> プロパティでは常にそれぞれ、`#` 文字と `?` 文字が保存中の値の先頭に付加されます。</span><span class="sxs-lookup"><span data-stu-id="de7f7-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="de7f7-105">この動作の結果、文字列に既に `#` 文字または `?` 文字が含まれている場合、保存中の値にこれらの先頭文字が複数与えられることになります。</span><span class="sxs-lookup"><span data-stu-id="de7f7-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="de7f7-106">たとえば、<xref:System.UriBuilder.Fragment?displayProperty=nameWithType> の値が `##main` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="de7f7-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="de7f7-107">.NET Core 1.0 以降、これらのプロパティでは今後、文字列の先頭に `#` 文字または `?` 文字が既に存在する場合、これらの文字が先頭に付加されません。</span><span class="sxs-lookup"><span data-stu-id="de7f7-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="de7f7-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="de7f7-108">Version introduced</span></span>

<span data-ttu-id="de7f7-109">1</span><span class="sxs-lookup"><span data-stu-id="de7f7-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="de7f7-110">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="de7f7-110">Recommended action</span></span>

<span data-ttu-id="de7f7-111">プロパティ値を設定するとき、これらの先頭文字を明示的に削除する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="de7f7-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="de7f7-112">これは特に、値を付加するときに便利です。付加するたびに先頭の `#` または `?` を削除する必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="de7f7-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="de7f7-113">たとえば、次のコード スニペットからは、.NET Framework と .NET Core では動作に違いがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="de7f7-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="de7f7-114">.NET Framework の場合、出力は `????one=1&two=2&three=3&four=4` です。</span><span class="sxs-lookup"><span data-stu-id="de7f7-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="de7f7-115">.NET Core の場合、出力は `?one=1&two=2&three=3&four=4` です。</span><span class="sxs-lookup"><span data-stu-id="de7f7-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="de7f7-116">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="de7f7-116">Category</span></span>

<span data-ttu-id="de7f7-117">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="de7f7-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="de7f7-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="de7f7-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
