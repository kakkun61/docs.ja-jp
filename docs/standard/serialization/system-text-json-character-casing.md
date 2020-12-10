---
title: System.Text.Json で大文字と小文字を区別しないプロパティ名の照合を有効にする方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、大文字と小文字を区別しないプロパティ名の照合を有効にする方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2d663ac8c1c15d61959a62c40d9a3b0993484032
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599077"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="6962a-103">System.Text.Json で大文字と小文字を区別しないプロパティ名の照合を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="6962a-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="6962a-104">この記事では、`System.Text.Json` 名前空間を使用して、大文字と小文字を区別しないプロパティ名の照合を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6962a-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="6962a-105">大文字と小文字を区別しないプロパティ照合</span><span class="sxs-lookup"><span data-stu-id="6962a-105">Case-insensitive property matching</span></span>

<span data-ttu-id="6962a-106">既定では、逆シリアル化では JSON とターゲット オブジェクトのプロパティとの間で大文字と小文字を区別したプロパティ名の一致が検索されます。</span><span class="sxs-lookup"><span data-stu-id="6962a-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="6962a-107">この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="6962a-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="6962a-108">[Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)では大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="6962a-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="6962a-109">キャメル ケースのプロパティ名を持つ JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6962a-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="6962a-110">これはパスカル ケースのプロパティ名を持つ次の型に逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="6962a-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="6962a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6962a-111">See also</span></span>

* [<span data-ttu-id="6962a-112">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="6962a-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="6962a-113">JsonSerializerOptions をインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="6962a-113">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="6962a-114">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="6962a-114">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="6962a-115">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="6962a-115">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="6962a-116">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="6962a-116">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="6962a-117">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="6962a-117">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="6962a-118">循環参照の保持</span><span class="sxs-lookup"><span data-stu-id="6962a-118">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="6962a-119">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="6962a-119">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="6962a-120">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="6962a-120">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="6962a-121">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="6962a-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
