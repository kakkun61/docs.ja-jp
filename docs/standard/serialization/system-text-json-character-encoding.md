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
ms.openlocfilehash: f6a50a3ca2a5e871294cf7c056cbf197a61cd668
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439807"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="2340f-103">System.Text.Json で文字エンコードをカスタマイズする方法</span><span class="sxs-lookup"><span data-stu-id="2340f-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="2340f-104">既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="2340f-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="2340f-105">つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。</span><span class="sxs-lookup"><span data-stu-id="2340f-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="2340f-106">たとえば、次の JSON の `Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="2340f-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="2340f-107">言語文字セットのシリアル化</span><span class="sxs-lookup"><span data-stu-id="2340f-107">Serialize language character sets</span></span>

<span data-ttu-id="2340f-108">1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。</span><span class="sxs-lookup"><span data-stu-id="2340f-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="2340f-109">このコードでは、キリル文字やギリシャ文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="2340f-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="2340f-110">`Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="2340f-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="2340f-111">すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="2340f-111">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="2340f-112">特定の文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="2340f-112">Serialize specific characters</span></span>

<span data-ttu-id="2340f-113">別の方法として、エスケープせずに許可する個々の文字を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2340f-113">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="2340f-114">次の例では、`жарко` の最初の 2 文字のみをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="2340f-114">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="2340f-115">上記のコードによって生成される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2340f-115">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a><span data-ttu-id="2340f-116">すべての文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="2340f-116">Serialize all characters</span></span>

<span data-ttu-id="2340f-117">エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2340f-117">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="2340f-118">既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。</span><span class="sxs-lookup"><span data-stu-id="2340f-118">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="2340f-119">`<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="2340f-119">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="2340f-120">クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。</span><span class="sxs-lookup"><span data-stu-id="2340f-120">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="2340f-121">安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="2340f-121">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="2340f-122">たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。</span><span class="sxs-lookup"><span data-stu-id="2340f-122">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="2340f-123">未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="2340f-123">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2340f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2340f-124">See also</span></span>

* [<span data-ttu-id="2340f-125">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="2340f-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="2340f-126">カスタム シリアライザーと逆シリアライザーを作成する方法</span><span class="sxs-lookup"><span data-stu-id="2340f-126">How to write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="2340f-127">JSON シリアル化のためのカスタム コンバーターを作成する方法</span><span class="sxs-lookup"><span data-stu-id="2340f-127">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="2340f-128">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="2340f-128">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
