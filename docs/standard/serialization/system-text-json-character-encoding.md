---
title: System.Text.Json で文字エンコードをカスタマイズする方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、文字エンコードをカスタマイズする方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: cfb83af0c58e0c9dfb73ecb8e2177d255e403fae
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009626"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="20438-103">System.Text.Json で文字エンコードをカスタマイズする方法</span><span class="sxs-lookup"><span data-stu-id="20438-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="20438-104">既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="20438-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="20438-105">つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。</span><span class="sxs-lookup"><span data-stu-id="20438-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="20438-106">たとえば、次の JSON の `Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="20438-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="20438-107">言語文字セットのシリアル化</span><span class="sxs-lookup"><span data-stu-id="20438-107">Serialize language character sets</span></span>

<span data-ttu-id="20438-108">1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。</span><span class="sxs-lookup"><span data-stu-id="20438-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="20438-109">このコードでは、キリル文字やギリシャ文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="20438-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="20438-110">`Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="20438-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="20438-111">すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="20438-111">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="20438-112">特定の文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="20438-112">Serialize specific characters</span></span>

<span data-ttu-id="20438-113">別の方法として、エスケープせずに許可する個々の文字を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="20438-113">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="20438-114">次の例では、`жарко` の最初の 2 文字のみをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="20438-114">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="20438-115">上記のコードによって生成される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="20438-115">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a><span data-ttu-id="20438-116">すべての文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="20438-116">Serialize all characters</span></span>

<span data-ttu-id="20438-117">エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="20438-117">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="20438-118">既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。</span><span class="sxs-lookup"><span data-stu-id="20438-118">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="20438-119">`<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="20438-119">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="20438-120">クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。</span><span class="sxs-lookup"><span data-stu-id="20438-120">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="20438-121">安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="20438-121">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="20438-122">たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。</span><span class="sxs-lookup"><span data-stu-id="20438-122">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="20438-123">未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="20438-123">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="20438-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="20438-124">See also</span></span>

* [<span data-ttu-id="20438-125">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="20438-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="20438-126">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="20438-126">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="20438-127">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="20438-127">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="20438-128">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="20438-128">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="20438-129">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="20438-129">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="20438-130">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="20438-130">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="20438-131">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="20438-131">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="20438-132">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="20438-132">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="20438-133">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="20438-133">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="20438-134">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="20438-134">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="20438-135">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="20438-135">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="20438-136">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="20438-136">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="20438-137">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="20438-137">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="20438-138">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="20438-138">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="20438-139">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="20438-139">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="20438-140">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="20438-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="20438-141">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="20438-141">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
