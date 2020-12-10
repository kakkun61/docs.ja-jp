---
title: System.Text.Json でいくつかの種類の無効な JSON を許可する方法
description: .NET で JSON との間のシリアル化または逆シリアル化を行うときに、コメント、末尾のコンマ、および引用符で囲まれた数値を許可する方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 60cbb98bb65ee5c1ffdd3043e42a04004530a115
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439782"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a><span data-ttu-id="e3d5d-103">System.Text.Json でいくつかの種類の無効な JSON を許可する方法</span><span class="sxs-lookup"><span data-stu-id="e3d5d-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="e3d5d-104">この記事では、JSON でコメント、末尾のコンマ、および引用符で囲まれた数値を許可する方法と、数値を文字列として書き込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="e3d5d-105">コメントと末尾のコンマを許可する</span><span class="sxs-lookup"><span data-stu-id="e3d5d-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="e3d5d-106">既定では、JSON 内でコメントと末尾のコンマは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="e3d5d-107">JSON 内でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="e3d5d-108">また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="e3d5d-109">両方を許可する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

<span data-ttu-id="e3d5d-110">次に、コメントと末尾のコンマを含む JSON の例を示します。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="e3d5d-111">引用符で囲まれた数値を許可または記述する</span><span class="sxs-lookup"><span data-stu-id="e3d5d-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="e3d5d-112">シリアライザーの中には、数値が JSON 文字列としてエンコードされる (引用符で囲まれる) ものがあります。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="e3d5d-113">例:</span><span class="sxs-lookup"><span data-stu-id="e3d5d-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="e3d5d-114">次の表記の代わりに、</span><span class="sxs-lookup"><span data-stu-id="e3d5d-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="e3d5d-115">引用符で囲まれた数値をシリアル化したり、引用符で囲まれた数値を入力オブジェクト グラフ全体で受け付けるには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> を設定します。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

<span data-ttu-id="e3d5d-116">ASP.NET Core を通じて間接的に `System.Text.Json` を使用すると、ASP.NET Core により [Web の既定のオプション](xref:System.Text.Json.JsonSerializerDefaults.Web)が指定されるため、逆シリアル化のときに引用符で囲まれた数値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="e3d5d-117">特定のプロパティ、フィールド、または型について引用符で囲まれた数値を許可または記述するには、[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="e3d5d-118">.NET Core 3.1 の `System.Text.Json` では、引用符で囲まれた数値のシリアル化または逆シリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="e3d5d-119">詳細については、「[引用符で囲まれた数値を許可または記述する](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3d5d-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="e3d5d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3d5d-120">See also</span></span>

* [<span data-ttu-id="e3d5d-121">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="e3d5d-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e3d5d-122">JsonSerializerOptions をインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="e3d5d-122">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="e3d5d-123">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="e3d5d-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="e3d5d-124">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="e3d5d-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="e3d5d-125">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="e3d5d-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="e3d5d-126">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="e3d5d-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="e3d5d-127">循環参照の保持</span><span class="sxs-lookup"><span data-stu-id="e3d5d-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="e3d5d-128">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="e3d5d-128">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="e3d5d-129">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="e3d5d-129">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="e3d5d-130">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="e3d5d-130">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
