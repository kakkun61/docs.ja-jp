---
title: System.Text.Json でオーバーフロー JSON を処理する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、オーバーフロー JSON を処理する方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c40d42b26bc5bd05f592cc51c6b5b9b4c6bbd9e
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439796"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="599ea-103">System.Text.Json でオーバーフロー JSON を処理する方法</span><span class="sxs-lookup"><span data-stu-id="599ea-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="599ea-104">この記事では、`System.Text.Json` 名前空間を使用してオーバーフロー JSON を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="599ea-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="599ea-105">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="599ea-105">Handle overflow JSON</span></span>

<span data-ttu-id="599ea-106">逆シリアル化中に、ターゲット型のプロパティで表されないデータを JSON 内で受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="599ea-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="599ea-107">たとえば、ターゲット型が次のようになっているとします。</span><span class="sxs-lookup"><span data-stu-id="599ea-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="599ea-108">逆シリアル化される JSON は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="599ea-108">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="599ea-109">表示されている JSON を示されている型に逆シリアル化すると、`DatesAvailable` と `SummaryWords` のプロパティは行き先がなくなり、失われます。</span><span class="sxs-lookup"><span data-stu-id="599ea-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="599ea-110">これらのプロパティのような余分なデータをキャプチャするには、[[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 属性を `Dictionary<string,object>` 型または `Dictionary<string,JsonElement>` 型のプロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="599ea-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="599ea-111">前に示した JSON をこのサンプル型に逆シリアル化すると、余分なデータが `ExtensionData` プロパティのキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="599ea-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="599ea-112">プロパティ</span><span class="sxs-lookup"><span data-stu-id="599ea-112">Property</span></span> | <span data-ttu-id="599ea-113">値</span><span class="sxs-lookup"><span data-stu-id="599ea-113">Value</span></span> | <span data-ttu-id="599ea-114">メモ</span><span class="sxs-lookup"><span data-stu-id="599ea-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="599ea-115">大文字と小文字の区別が一致しないため (JSON では `temperatureCelsius`)、プロパティは設定されません。</span><span class="sxs-lookup"><span data-stu-id="599ea-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="599ea-116">大文字と小文字の区別が一致しなかったため、この JSON プロパティは余分で、ディクショナリ内のキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="599ea-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="599ea-117">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="599ea-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="599ea-118">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="599ea-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="599ea-119">ターゲット オブジェクトがシリアル化されると、拡張データのキーと値のペアは、受信 JSON 内にあった場合と同様に JSON プロパティになります。</span><span class="sxs-lookup"><span data-stu-id="599ea-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="599ea-120">JSON には `ExtensionData` プロパティ名が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="599ea-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="599ea-121">この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンド トリップを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="599ea-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="599ea-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="599ea-122">See also</span></span>

* [<span data-ttu-id="599ea-123">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="599ea-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="599ea-124">JsonSerializerOptions をインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="599ea-124">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="599ea-125">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="599ea-125">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="599ea-126">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="599ea-126">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="599ea-127">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="599ea-127">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="599ea-128">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="599ea-128">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="599ea-129">循環参照の保持</span><span class="sxs-lookup"><span data-stu-id="599ea-129">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="599ea-130">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="599ea-130">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="599ea-131">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="599ea-131">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="599ea-132">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="599ea-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
