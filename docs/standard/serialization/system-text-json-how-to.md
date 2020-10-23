---
title: C# を使用して JSON をシリアル化および逆シリアル化する方法 - .NET
description: System.Text.Json 名前空間を使用して .NET 内で JSON のシリアル化と逆シリアル化を行う方法について学習します。 これにはサンプル コードが含まれます。
ms.date: 10/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 0fda248b7d2e5a7cfa748447d0265565cb160b7e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997782"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="bc94b-104">.NET 内で JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリングの解除) を行う方法</span><span class="sxs-lookup"><span data-stu-id="bc94b-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="bc94b-105">この記事では、<xref:System.Text.Json?displayProperty=fullName> 名前空間を使用して JavaScript Object Notation (JSON) のシリアル化と逆シリアル化を行う方法について示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="bc94b-106">`Newtonsoft.Json` から既存のコードを移植する場合は、[`System.Text.Json` に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc94b-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="bc94b-107">指示とサンプル コードでは、ライブラリを [ASP.NET Core](/aspnet/core/) などのフレームワーク経由ではなく直接使用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="bc94b-108">シリアル化のサンプル コードの大部分では、JSON を "整形" するために <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します (人間が読みやすいようにインデントと空白文字が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="bc94b-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="bc94b-109">実稼働環境で使用する場合、通常、この設定には既定値の `false` をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="bc94b-110">コード例では、次のクラスとそのバリアントを参照しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="bc94b-111">名前空間</span><span class="sxs-lookup"><span data-stu-id="bc94b-111">Namespaces</span></span>

<span data-ttu-id="bc94b-112"><xref:System.Text.Json> 名前空間には、すべてのエントリ ポイントと主要な型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="bc94b-113"><xref:System.Text.Json.Serialization> 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="bc94b-114">この記事に示されているコード例では、次のいずれかまたは両方の名前空間に `using` ディレクティブが必要です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="bc94b-115"><xref:System.Runtime.Serialization> 名前空間からの属性は、現在 `System.Text.Json`ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="bc94b-116">.NET オブジェクトを JSON に書き込む方法 (シリアル化)</span><span class="sxs-lookup"><span data-stu-id="bc94b-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="bc94b-117">JSON を文字列またはファイルに書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="bc94b-118">次の例では、JSON を文字列として作成します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-119">次の例では、同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-120">次の例では、非同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-121">前の例では、シリアル化する型に型の推定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="bc94b-122">`Serialize()` のオーバーロードでは、ジェネリック型パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="bc94b-123">シリアル化の例</span><span class="sxs-lookup"><span data-stu-id="bc94b-123">Serialization example</span></span>

<span data-ttu-id="bc94b-124">コレクション型のプロパティとユーザー定義型を含むクラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> <span data-ttu-id="bc94b-125">"POCO" は、[Plain Old CLR Object (単純な従来の CLR オブジェクト)](https://en.wikipedia.org/wiki/Plain_old_CLR_object) を表します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="bc94b-126">POCO は、継承や属性からなど、フレームワーク固有の型に依存しない .NET 型です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="bc94b-127">前の型のインスタンスをシリアル化した場合の JSON 出力は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="bc94b-128">JSON 出力は既定で縮小されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-128">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="bc94b-129">次の例では、同じ JSON ですが、書式設定されているもの (空白とインデントで整形されています) を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a><span data-ttu-id="bc94b-130">UTF-8 にシリアル化する</span><span class="sxs-lookup"><span data-stu-id="bc94b-130">Serialize to UTF-8</span></span>

<span data-ttu-id="bc94b-131">UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-132"><xref:System.Text.Json.Utf8JsonWriter> を受け取る <xref:System.Text.Json.JsonSerializer.Serialize%2A> オーバーロードも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="bc94b-133">UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約 5-10% 高速です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="bc94b-134">違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないことから生じます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="bc94b-135">シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="bc94b-135">Serialization behavior</span></span>

* <span data-ttu-id="bc94b-136">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="bc94b-137">[除外するプロパティを指定](#exclude-properties-from-serialization)できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-137">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="bc94b-138">[既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="bc94b-139">既定では、JSON は縮小されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-139">By default, JSON is minified.</span></span> <span data-ttu-id="bc94b-140">[JSON を整形](#serialize-to-formatted-json)することができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="bc94b-141">既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="bc94b-142">[JSON 名の大文字と小文字の区別をカスタマイズ](#customize-json-names-and-values)することができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-142">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="bc94b-143">循環参照が検出され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-143">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="bc94b-144">現在、[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は除外されています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-144">Currently, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are excluded.</span></span>

<span data-ttu-id="bc94b-145">サポートされる型には次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-145">Supported types include:</span></span>

* <span data-ttu-id="bc94b-146">数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。</span><span class="sxs-lookup"><span data-stu-id="bc94b-146">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="bc94b-147">ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="bc94b-147">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="bc94b-148">1 次元配列とジャグ配列 (`ArrayName[][]`)。</span><span class="sxs-lookup"><span data-stu-id="bc94b-148">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="bc94b-149">`Dictionary<string,TValue>`。`TValue` は `object`、`JsonElement`、または POCO です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-149">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="bc94b-150">次の名前空間からのコレクション。</span><span class="sxs-lookup"><span data-stu-id="bc94b-150">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="bc94b-151">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、追加の型を処理したり、組み込みコンバーターではサポートされていない機能を提供したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-151">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="bc94b-152">JSON を .NET オブジェクトに読み取る方法 (逆シリアル化)</span><span class="sxs-lookup"><span data-stu-id="bc94b-152">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="bc94b-153">文字列またはファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-153">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="bc94b-154">次の例では、文字列から JSON を読み取り、前に[シリアル化の例](#serialization-example)で示した `WeatherForecastWithPOCOs` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-154">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="bc94b-155">同期コードを使用してファイルから逆シリアル化するには、次の例に示すように、ファイルを文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-155">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="bc94b-156">非同期コードを使用してファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-156">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="bc94b-157">UTF-8 からの逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="bc94b-157">Deserialize from UTF-8</span></span>

<span data-ttu-id="bc94b-158">UTF-8 から逆シリアル化するには、次の例に示すように、`Utf8JsonReader` または `ReadOnlySpan<byte>` を受け取る <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> オーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-158">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="bc94b-159">この例では、JSON が jsonUtf8Bytes という名前のバイト配列内にあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-159">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="bc94b-160">逆シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="bc94b-160">Deserialization behavior</span></span>

<span data-ttu-id="bc94b-161">JSON を逆シリアル化する場合、次の動作が適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-161">The following behaviors apply when deserializing JSON:</span></span>

* <span data-ttu-id="bc94b-162">既定では、プロパティ名の照合では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-162">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="bc94b-163">[大文字と小文字を区別しないことを指定](#case-insensitive-property-matching)できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-163">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="bc94b-164">JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-164">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="bc94b-165">逆シリアル化のコンストラクター:</span><span class="sxs-lookup"><span data-stu-id="bc94b-165">Constructors for deserialization:</span></span>
  - <span data-ttu-id="bc94b-166">.NET Core 3.0 および 3.1 により、パラメーターなしのコンストラクター (public、internal、private のいずれか) が逆シリアル化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-166">On .NET Core 3.0 and 3.1, a parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
  - <span data-ttu-id="bc94b-167">.NET 5.0 以降は、非パブリック コンストラクターはシリアライザーにより無視されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-167">In .NET 5.0 and later, non-public constructors are ignored by the serializer.</span></span> <span data-ttu-id="bc94b-168">ただし、パラメーターなしのコンストラクターを使用できない場合は、パラメーター化されたコンストラクターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-168">However, parameterized constructors can be used if a parameterless constructor isn't available.</span></span>
* <span data-ttu-id="bc94b-169">不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-169">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="bc94b-170">既定では、列挙型は数値としてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-170">By default, enums are supported as numbers.</span></span> <span data-ttu-id="bc94b-171">[列挙型名を文字列としてシリアル化](#enums-as-strings)することができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-171">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="bc94b-172">フィールドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-172">Fields aren't supported.</span></span>
* <span data-ttu-id="bc94b-173">既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-173">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="bc94b-174">[コメントと末尾のコンマを許可](#allow-comments-and-trailing-commas)することができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-174">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="bc94b-175">[既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-175">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="bc94b-176">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、組み込みコンバーターではサポートされていない機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-176">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="bc94b-177">書式設定された JSON へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="bc94b-177">Serialize to formatted JSON</span></span>

<span data-ttu-id="bc94b-178">JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-178">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="bc94b-179">シリアル化され、整形された JSON 出力の型の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-179">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="bc94b-180">JSON の名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="bc94b-180">Customize JSON names and values</span></span>

<span data-ttu-id="bc94b-181">既定では、プロパティ名とディクショナリ キーは、大文字と小文字の区別を含め、JSON の出力では変更されません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-181">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="bc94b-182">列挙型の値は数値として表されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-182">Enum values are represented as numbers.</span></span> <span data-ttu-id="bc94b-183">このセクションでは、次の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-183">This section explains how to:</span></span>

* [<span data-ttu-id="bc94b-184">個々のプロパティ名をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="bc94b-184">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="bc94b-185">すべてのプロパティ名をキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="bc94b-185">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="bc94b-186">カスタム プロパティの名前付けポリシーを実装する</span><span class="sxs-lookup"><span data-stu-id="bc94b-186">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="bc94b-187">ディクショナリ キーをキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="bc94b-187">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="bc94b-188">列挙型を文字列およびキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="bc94b-188">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="bc94b-189">JSON プロパティの名前と値の特別な処理を必要とするその他のシナリオでは、[カスタム コンバーターを実装](system-text-json-converters-how-to.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-189">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="bc94b-190">個々のプロパティ名をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="bc94b-190">Customize individual property names</span></span>

<span data-ttu-id="bc94b-191">個々のプロパティの名前を設定するには、[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-191">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="bc94b-192">シリアル化する型と、結果として得られる JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-192">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="bc94b-193">この属性によって設定されるプロパティ名は:</span><span class="sxs-lookup"><span data-stu-id="bc94b-193">The property name set by this attribute:</span></span>

* <span data-ttu-id="bc94b-194">シリアル化と逆シリアル化の両方の方向に適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-194">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="bc94b-195">プロパティの名前付けポリシーよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-195">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="bc94b-196">すべての JSON プロパティ名にキャメル ケースを使用する</span><span class="sxs-lookup"><span data-stu-id="bc94b-196">Use camel case for all JSON property names</span></span>

<span data-ttu-id="bc94b-197">すべての JSON プロパティ名にキャメル ケースを使用するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> を `JsonNamingPolicy.CamelCase` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-197">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="bc94b-198">シリアル化するクラスと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-198">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="bc94b-199">キャメル ケースのプロパティの名前付けポリシーは:</span><span class="sxs-lookup"><span data-stu-id="bc94b-199">The camel case property naming policy:</span></span>

* <span data-ttu-id="bc94b-200">シリアル化と逆シリアル化に適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="bc94b-201">`[JsonPropertyName]` 属性によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-201">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="bc94b-202">このため、この例の JSON プロパティ名 `Wind` はキャメル ケースではありません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-202">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="bc94b-203">カスタム JSON プロパティの名前付けポリシーを使用する</span><span class="sxs-lookup"><span data-stu-id="bc94b-203">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="bc94b-204">カスタム JSON プロパティの名前付けポリシーを使用するには、次の例に示すように、<xref:System.Text.Json.JsonNamingPolicy> から派生するクラスを作成し、<xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-204">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="bc94b-205">次に、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> プロパティを名前付けポリシー クラスのインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-205">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-206">シリアル化するクラスと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-206">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="bc94b-207">JSON プロパティの名前付けポリシーは:</span><span class="sxs-lookup"><span data-stu-id="bc94b-207">The JSON property naming policy:</span></span>

* <span data-ttu-id="bc94b-208">シリアル化と逆シリアル化に適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-208">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="bc94b-209">`[JsonPropertyName]` 属性によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-209">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="bc94b-210">このため、この例の JSON プロパティ名 `Wind` は大文字ではありません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-210">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="bc94b-211">キャメル ケースのディクショナリ キー</span><span class="sxs-lookup"><span data-stu-id="bc94b-211">Camel case dictionary keys</span></span>

<span data-ttu-id="bc94b-212">シリアル化するオブジェクトのプロパティが `Dictionary<string,TValue>` 型である場合は、`string` キーをキャメル ケースに変換できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-212">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="bc94b-213">これを行うには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> を `JsonNamingPolicy.CamelCase` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-213">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-214">キーと値のペア `"ColdMinTemp", 20` および `"HotMinTemp", 40` を持つ `TemperatureRanges` という名前のディクショナリを使用してオブジェクトをシリアル化すると、次の例のような JSON 出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-214">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="bc94b-215">ディクショナリ キーに対するキャメル ケースの名前付けポリシーは、シリアル化にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-215">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="bc94b-216">ディクショナリを逆シリアル化すると、`DictionaryKeyPolicy` に `JsonNamingPolicy.CamelCase` を指定した場合でも、キーが JSON ファイルと一致します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-216">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="bc94b-217">文字列としての列挙型</span><span class="sxs-lookup"><span data-stu-id="bc94b-217">Enums as strings</span></span>

<span data-ttu-id="bc94b-218">既定では、列挙型は数値としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-218">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="bc94b-219">列挙型名を文字列としてシリアル化するには、<xref:System.Text.Json.Serialization.JsonStringEnumConverter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-219">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="bc94b-220">たとえば、列挙型を持つ次のクラスをシリアル化する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-220">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="bc94b-221">Summary が `Hot` の場合、既定では、シリアル化された JSON には数値 3 があります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-221">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="bc94b-222">次のサンプル コードでは、数値ではなく列挙型名をシリアル化し、名前をキャメル ケースに変換します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-222">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-223">結果として生成される JSON は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-223">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="bc94b-224">列挙型の文字列名も、次の例に示すように逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-224">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="bc94b-225">シリアル化からプロパティを除外する</span><span class="sxs-lookup"><span data-stu-id="bc94b-225">Exclude properties from serialization</span></span>

<span data-ttu-id="bc94b-226">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-226">By default, all public properties are serialized.</span></span> <span data-ttu-id="bc94b-227">その一部が JSON 出力に出現しないようにするには、いくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-227">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="bc94b-228">このセクションでは、以下を除外する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-228">This section explains how to exclude:</span></span>

* [<span data-ttu-id="bc94b-229">個々のプロパティ</span><span class="sxs-lookup"><span data-stu-id="bc94b-229">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="bc94b-230">すべての読み取り専用プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc94b-230">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="bc94b-231">すべての null 値プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc94b-231">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="bc94b-232">個々のプロパティを除外する</span><span class="sxs-lookup"><span data-stu-id="bc94b-232">Exclude individual properties</span></span>

<span data-ttu-id="bc94b-233">個々のプロパティを無視するには、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-233">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="bc94b-234">シリアル化する型と JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-234">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="bc94b-235">すべての読み取り専用プロパティを除外する</span><span class="sxs-lookup"><span data-stu-id="bc94b-235">Exclude all read-only properties</span></span>

<span data-ttu-id="bc94b-236">パブリック ゲッターが含まれていてもパブリック セッターがない場合、プロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-236">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="bc94b-237">すべての読み取り専用プロパティを除外するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-237">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-238">シリアル化する型と JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-238">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="bc94b-239">このオプションは、シリアル化にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-239">This option applies only to serialization.</span></span> <span data-ttu-id="bc94b-240">逆シリアル化中、既定では読み取り専用プロパティが無視されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-240">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="bc94b-241">すべての null 値プロパティを除外する</span><span class="sxs-lookup"><span data-stu-id="bc94b-241">Exclude all null value properties</span></span>

<span data-ttu-id="bc94b-242">すべての null 値プロパティを除外するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-242">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-243">シリアル化するオブジェクトと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-243">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="bc94b-244">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc94b-244">Property</span></span> |<span data-ttu-id="bc94b-245">値</span><span class="sxs-lookup"><span data-stu-id="bc94b-245">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="bc94b-246">Date</span><span class="sxs-lookup"><span data-stu-id="bc94b-246">Date</span></span>    | <span data-ttu-id="bc94b-247">8/1/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="bc94b-247">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="bc94b-248">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="bc94b-248">TemperatureCelsius</span></span>| <span data-ttu-id="bc94b-249">25</span><span class="sxs-lookup"><span data-stu-id="bc94b-249">25</span></span> |
| <span data-ttu-id="bc94b-250">まとめ</span><span class="sxs-lookup"><span data-stu-id="bc94b-250">Summary</span></span>| <span data-ttu-id="bc94b-251">null</span><span class="sxs-lookup"><span data-stu-id="bc94b-251">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="bc94b-252">この設定はシリアル化と逆シリアル化に適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-252">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="bc94b-253">逆シリアル化に対する影響については、「[逆シリアル化時に null を無視する](#ignore-null-when-deserializing)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc94b-253">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="bc94b-254">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="bc94b-254">Customize character encoding</span></span>

<span data-ttu-id="bc94b-255">既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-255">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="bc94b-256">つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。</span><span class="sxs-lookup"><span data-stu-id="bc94b-256">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="bc94b-257">たとえば、`Summary` プロパティがキリル文字の жарко に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-257">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="bc94b-258">言語文字セットのシリアル化</span><span class="sxs-lookup"><span data-stu-id="bc94b-258">Serialize language character sets</span></span>

<span data-ttu-id="bc94b-259">1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-259">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="bc94b-260">このコードでは、キリル文字やギリシャ文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-260">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="bc94b-261">`Summary` プロパティがキリル文字の жарко に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-261">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="bc94b-262">すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-262">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="bc94b-263">特定の文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="bc94b-263">Serialize specific characters</span></span>

<span data-ttu-id="bc94b-264">別の方法として、エスケープせずに許可する個々の文字を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-264">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="bc94b-265">次の例では、жарко の最初の 2 文字のみをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-265">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="bc94b-266">上記のコードによって生成される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-266">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="bc94b-267">すべての文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="bc94b-267">Serialize all characters</span></span>

<span data-ttu-id="bc94b-268">エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-268">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="bc94b-269">既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-269">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="bc94b-270">`<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-270">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="bc94b-271">クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-271">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="bc94b-272">安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="bc94b-272">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="bc94b-273">たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-273">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="bc94b-274">未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bc94b-274">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="bc94b-275">派生クラスのプロパティのシリアル化</span><span class="sxs-lookup"><span data-stu-id="bc94b-275">Serialize properties of derived classes</span></span>

<span data-ttu-id="bc94b-276">ポリモーフィックな型階層のシリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-276">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="bc94b-277">たとえば、プロパティがインターフェイスまたは抽象クラスとして定義されている場合は、ランタイム型に追加のプロパティがある場合でも、インターフェイスまたは抽象クラスに定義されたプロパティのみがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-277">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="bc94b-278">この動作の例外については、このセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-278">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="bc94b-279">たとえば、`WeatherForecast` クラスと派生クラス `WeatherForecastDerived` があるとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-279">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="bc94b-280">また、コンパイル時の `Serialize` メソッドの型引数が `WeatherForecast` であるとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-280">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="bc94b-281">このシナリオでは、`weatherForecast` オブジェクトが実際には `WeatherForecastDerived` オブジェクトであっても、`WindSpeed` プロパティはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-281">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="bc94b-282">基本クラスのプロパティのみがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-282">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="bc94b-283">この動作は、ランタイムによって作成される派生型内でデータが誤って公開されるのを防ぐためのものです。</span><span class="sxs-lookup"><span data-stu-id="bc94b-283">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="bc94b-284">前の例で派生型のプロパティをシリアル化するには、次のいずれかのアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-284">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="bc94b-285">実行時に型を指定できるようにする <xref:System.Text.Json.JsonSerializer.Serialize%2A> のオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-285">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="bc94b-286">オブジェクトを `object` としてシリアル化するように宣言します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-286">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="bc94b-287">前の例のシナリオでは、どちらのアプローチでも、`WindSpeed` プロパティが JSON 出力に含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-287">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="bc94b-288">これらのアプローチでは、シリアル化するルート オブジェクトに対してのみポリモーフィックなシリアル化が提供され、そのルート オブジェクトのプロパティに対しては提供されません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-288">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="bc94b-289">`object` 型として定義すると、下位レベルのオブジェクトのポリモーフィックなシリアル化を取得できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-289">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="bc94b-290">たとえば、`WeatherForecast` クラスに、`WeatherForecast` または `object` 型として定義できる `PreviousForecast` という名前のプロパティがあるとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-290">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="bc94b-291">`PreviousForecast` プロパティに `WeatherForecastDerived` のインスタンスが含まれる場合:</span><span class="sxs-lookup"><span data-stu-id="bc94b-291">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="bc94b-292">`WeatherForecastWithPrevious` のシリアル化からの JSON 出力には `WindSpeed` が**含まれていません**。</span><span class="sxs-lookup"><span data-stu-id="bc94b-292">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="bc94b-293">`WeatherForecastWithPreviousAsObject` のシリアル化からの JSON 出力には `WindSpeed` が**含まれています**。</span><span class="sxs-lookup"><span data-stu-id="bc94b-293">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="bc94b-294">ルート オブジェクトは派生型である可能性があるものではないため、`WeatherForecastWithPreviousAsObject` をシリアル化するために `Serialize<object>` または `GetType` を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-294">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="bc94b-295">次のコード例では `Serialize<object>` または `GetType` は呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-295">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="bc94b-296">上記のコードでは、`WeatherForecastWithPreviousAsObject` が正しくシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-296">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="bc94b-297">`object` と同じプロパティ定義のアプローチがインターフェイスで機能します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-297">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="bc94b-298">次のインターフェイスと実装があり、実装インスタンスを含むプロパティを使用してクラスをシリアル化するとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-298">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="bc94b-299">`Forecasts` のインスタンスをシリアル化する場合、`Tuesday` は `object` として定義されているので、`Tuesday` にのみ `WindSpeed` プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-299">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="bc94b-300">次の例は、前のコードから生成された JSON を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-300">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="bc94b-301">ポリモーフィック **シリアル化**の詳細、および**逆シリアル化**の詳細については、「[Newtonsoft.Json から System.Text.Json に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc94b-301">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="bc94b-302">コメントと末尾のコンマを許可する</span><span class="sxs-lookup"><span data-stu-id="bc94b-302">Allow comments and trailing commas</span></span>

<span data-ttu-id="bc94b-303">既定では、JSON 内でコメントと末尾のコンマは使用できません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-303">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="bc94b-304">JSON 内でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-304">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="bc94b-305">また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-305">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="bc94b-306">両方を許可する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-306">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="bc94b-307">次に、コメントと末尾のコンマを含む JSON の例を示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-307">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="bc94b-308">大文字と小文字を区別しないプロパティ照合</span><span class="sxs-lookup"><span data-stu-id="bc94b-308">Case-insensitive property matching</span></span>

<span data-ttu-id="bc94b-309">既定では、逆シリアル化では JSON とターゲット オブジェクトのプロパティとの間で大文字と小文字を区別したプロパティ名の一致が検索されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-309">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="bc94b-310">この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-310">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="bc94b-311">キャメル ケースのプロパティ名を持つ JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-311">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="bc94b-312">これはパスカル ケースのプロパティ名を持つ次の型に逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-312">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="bc94b-313">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="bc94b-313">Handle overflow JSON</span></span>

<span data-ttu-id="bc94b-314">逆シリアル化中に、ターゲット型のプロパティで表されないデータを JSON 内で受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-314">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="bc94b-315">たとえば、ターゲット型が次のようになっているとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-315">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="bc94b-316">逆シリアル化される JSON は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bc94b-316">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="bc94b-317">表示されている JSON を示されている型に逆シリアル化すると、`DatesAvailable` と `SummaryWords` のプロパティは行き先がなくなり、失われます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-317">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="bc94b-318">これらのプロパティなどの余分なデータをキャプチャするには、[JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 属性を型 `Dictionary<string,object>` または `Dictionary<string,JsonElement>` のプロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-318">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="bc94b-319">前に示した JSON をこのサンプル型に逆シリアル化すると、余分なデータが `ExtensionData` プロパティのキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-319">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="bc94b-320">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc94b-320">Property</span></span> |<span data-ttu-id="bc94b-321">値</span><span class="sxs-lookup"><span data-stu-id="bc94b-321">Value</span></span>  |<span data-ttu-id="bc94b-322">メモ</span><span class="sxs-lookup"><span data-stu-id="bc94b-322">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="bc94b-323">Date</span><span class="sxs-lookup"><span data-stu-id="bc94b-323">Date</span></span>    | <span data-ttu-id="bc94b-324">8/1/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="bc94b-324">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="bc94b-325">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="bc94b-325">TemperatureCelsius</span></span>| <span data-ttu-id="bc94b-326">0</span><span class="sxs-lookup"><span data-stu-id="bc94b-326">0</span></span> | <span data-ttu-id="bc94b-327">大文字と小文字の区別が一致しないため (JSON では `temperatureCelsius`)、プロパティは設定されません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-327">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="bc94b-328">まとめ</span><span class="sxs-lookup"><span data-stu-id="bc94b-328">Summary</span></span> | <span data-ttu-id="bc94b-329">ホット</span><span class="sxs-lookup"><span data-stu-id="bc94b-329">Hot</span></span> ||
| <span data-ttu-id="bc94b-330">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="bc94b-330">ExtensionData</span></span> | <span data-ttu-id="bc94b-331">temperatureCelsius:25</span><span class="sxs-lookup"><span data-stu-id="bc94b-331">temperatureCelsius: 25</span></span> |<span data-ttu-id="bc94b-332">大文字と小文字の区別が一致しなかったため、この JSON プロパティは余分で、ディクショナリ内のキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-332">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="bc94b-333">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="bc94b-333">DatesAvailable:</span></span><br>  <span data-ttu-id="bc94b-334">8/1/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="bc94b-334">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="bc94b-335">8/2/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="bc94b-335">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="bc94b-336">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-336">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="bc94b-337">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="bc94b-337">SummaryWords:</span></span><br><span data-ttu-id="bc94b-338">Cool</span><span class="sxs-lookup"><span data-stu-id="bc94b-338">Cool</span></span><br><span data-ttu-id="bc94b-339">強風</span><span class="sxs-lookup"><span data-stu-id="bc94b-339">Windy</span></span><br><span data-ttu-id="bc94b-340">Humid</span><span class="sxs-lookup"><span data-stu-id="bc94b-340">Humid</span></span> |<span data-ttu-id="bc94b-341">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-341">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="bc94b-342">ターゲット オブジェクトがシリアル化されると、拡張データのキーと値のペアは、受信 JSON 内にあった場合と同様に JSON プロパティになります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-342">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="bc94b-343">JSON には `ExtensionData` プロパティ名が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bc94b-343">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="bc94b-344">この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンド トリップを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-344">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="bc94b-345">逆シリアル化時に null を無視する</span><span class="sxs-lookup"><span data-stu-id="bc94b-345">Ignore null when deserializing</span></span>

<span data-ttu-id="bc94b-346">既定では、JSON 内のプロパティが null の場合、ターゲット オブジェクト内の対応するプロパティは null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-346">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="bc94b-347">場合によっては、ターゲット プロパティに既定値が設定されていて、既定値を null 値でオーバーライドしたくないことがあります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-347">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="bc94b-348">たとえば、次のコードがターゲット オブジェクトを表しているとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-348">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="bc94b-349">次の JSON が逆シリアル化されるとします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-349">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="bc94b-350">逆シリアル化後、`WeatherForecastWithDefault` オブジェクトの `Summary` プロパティは null になります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-350">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="bc94b-351">この動作を変更するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-351">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="bc94b-352">このオプションを使用すると、逆シリアル化後に、`WeatherForecastWithDefault` オブジェクトの `Summary` プロパティが既定値の "No summary" になります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-352">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="bc94b-353">JSON 内の Null 値は、有効な場合にのみ無視されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-353">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="bc94b-354">null 非許容の値の型に対して Null 値を指定すると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-354">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="bc94b-355">Utf8JsonReader、Utf8JsonWriter、JsonDocument</span><span class="sxs-lookup"><span data-stu-id="bc94b-355">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="bc94b-356"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> は、UTF-8 でエンコードされた JSON テキスト用の、ハイパフォーマンス、低割り当て、順方向専用のリーダーです。`ReadOnlySpan<byte>` または `ReadOnlySequence<byte>` から読み取られます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-356"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="bc94b-357">`Utf8JsonReader` は低レベルの型であり、カスタム パーサーとデシリアライザーを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-357">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="bc94b-358"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonReader` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-358">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="bc94b-359"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> は、`String`、`Int32`、`DateTime` のような一般的な .NET 型から UTF-8 でエンコードされた JSON テキストを書き込むための、ハイパフォーマンスな方法です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-359"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="bc94b-360">ライターは低レベルの型であり、カスタム シリアライザーを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-360">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="bc94b-361"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonWriter` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-361">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="bc94b-362"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> では、`Utf8JsonReader` を使用して、読み取り専用のドキュメント オブジェクト モデル (DOM) を構築する機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-362"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="bc94b-363">DOM では、JSON ペイロード内のデータへのランダム アクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-363">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="bc94b-364">ペイロードを構成する JSON 要素には、<xref:System.Text.Json.JsonElement> 型を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-364">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="bc94b-365">`JsonElement` 型では、配列とオブジェクト列挙子と共に、JSON テキストを一般的な .NET 型に変換する API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-365">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="bc94b-366">`JsonDocument` では <xref:System.Text.Json.JsonDocument.RootElement> プロパティが公開されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-366">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="bc94b-367">以下のセクションでは、これらのツールを使用して JSON の読み取りと書き込みを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-367">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="bc94b-368">JsonDocument を使用してデータにアクセスする</span><span class="sxs-lookup"><span data-stu-id="bc94b-368">Use JsonDocument for access to data</span></span>

<span data-ttu-id="bc94b-369">次の例は、<xref:System.Text.Json.JsonDocument> クラスを使用して JSON 文字列内のデータにランダム アクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-369">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="bc94b-370">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-370">The preceding code:</span></span>

* <span data-ttu-id="bc94b-371">分析する JSON が `jsonString` という名前の文字列に含まれていると想定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-371">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="bc94b-372">`Grade` プロパティを持つ `Students` 配列内のオブジェクトの平均グレードを計算します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-372">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="bc94b-373">グレードのない学生には既定のグレード 70 を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-373">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="bc94b-374">反復するたびに `count` 変数をインクリメントして学生をカウントします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-374">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="bc94b-375">別の方法として、次の例に示すように <xref:System.Text.Json.JsonElement.GetArrayLength%2A> を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-375">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="bc94b-376">このコードで処理される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-376">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="bc94b-377">JsonDocument を使用して JSON を書き込む</span><span class="sxs-lookup"><span data-stu-id="bc94b-377">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="bc94b-378">次の例では、<xref:System.Text.Json.JsonDocument> から JSON を書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-378">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="bc94b-379">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-379">The preceding code:</span></span>

* <span data-ttu-id="bc94b-380">JSON ファイルを読み取り、データを `JsonDocument` に読み込み、書式設定された (整形された) JSON をファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-380">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="bc94b-381"><xref:System.Text.Json.JsonDocumentOptions> を使用して、入力 JSON 内でコメントは許可されるが無視されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-381">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="bc94b-382">完了したら、ライターに対して <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-382">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="bc94b-383">別の方法として、破棄されたときにライターを自動フラッシュすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-383">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="bc94b-384">コード例によって処理される JSON 入力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-384">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="bc94b-385">その結果は、次のような整形された JSON 出力になります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-385">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="bc94b-386">Utf8JsonWriter を使用する</span><span class="sxs-lookup"><span data-stu-id="bc94b-386">Use Utf8JsonWriter</span></span>

<span data-ttu-id="bc94b-387"><xref:System.Text.Json.Utf8JsonWriter> クラスを使用する方法を示す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-387">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="bc94b-388">Utf8JsonReader を使用する</span><span class="sxs-lookup"><span data-stu-id="bc94b-388">Use Utf8JsonReader</span></span>

<span data-ttu-id="bc94b-389"><xref:System.Text.Json.Utf8JsonReader> クラスを使用する方法を示す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-389">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="bc94b-390">上記のコードでは、`jsonUtf8` 変数が、UTF-8 としてエンコードされた有効な JSON を含むバイト配列であることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-390">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="bc94b-391">Utf8JsonReader を使用してデータをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="bc94b-391">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="bc94b-392">次の例は、ファイルを同期的に読み取り、値を検索する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-392">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="bc94b-393">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-393">The preceding code:</span></span>

* <span data-ttu-id="bc94b-394">JSON にオブジェクトの配列が含まれ、各オブジェクトに文字列型の "name" プロパティが含まれている可能性があると想定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-394">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="bc94b-395">オブジェクトと "University" で終わる "name" プロパティ値をカウントします。</span><span class="sxs-lookup"><span data-stu-id="bc94b-395">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="bc94b-396">ファイルが UTF-16 としてエンコードされ、UTF-8 にトランスコードされるものと想定します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-396">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="bc94b-397">UTF-8 としてエンコードされたファイルは、次のコードを使用して、`ReadOnlySpan<byte>` に直接読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-397">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="bc94b-398">リーダーではテキストが想定されるため、ファイルに UTF-8 バイト オーダー マーク (BOM) が含まれている場合は、バイトを `Utf8JsonReader` に渡す前にそれを削除します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-398">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="bc94b-399">そうしないと、BOM は無効な JSON と見なされ、リーダーによって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-399">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="bc94b-400">上記のコードで読み取ることができる JSON のサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-400">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="bc94b-401">結果として生成される概要メッセージは、"2 out of 4 have names that end with 'University'" です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-401">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="bc94b-402">Utf8JsonReader を使用してストリームから読み取る</span><span class="sxs-lookup"><span data-stu-id="bc94b-402">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="bc94b-403">大きなファイル (ギガバイト以上のサイズなど) を読み取る場合、一度にファイル全体をメモリに読み込む必要を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-403">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="bc94b-404">このシナリオでは、<xref:System.IO.FileStream> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-404">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="bc94b-405">`Utf8JsonReader` を使用してストリームから読み取る場合、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-405">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="bc94b-406">部分的な JSON ペイロードを含むバッファーは、リーダーが処理を進めることができるように、少なくともその中で最大の JSON トークンと同じ大きさにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-406">The buffer containing the partial JSON payload must be at least as big as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="bc94b-407">バッファーは、少なくとも JSON 内の空白の最大シーケンスと同じ大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-407">The buffer must be at least as big as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="bc94b-408">リーダーでは、JSON ペイロード内の次の <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> が完全に読み取られるまで、読み取られたデータが追跡されません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-408">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="bc94b-409">そのため、バッファー内にバイトが残っている場合は、再びリーダーに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-409">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="bc94b-410"><xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> を使用して、残っているバイト数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-410">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="bc94b-411">次のコードは、ストリームから読み取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-411">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="bc94b-412">この例は、<xref:System.IO.MemoryStream> を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-412">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="bc94b-413">同様のコードが <xref:System.IO.FileStream> で機能しますが、開始時に UTF-8 BOM が `FileStream` に含まれている場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-413">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="bc94b-414">その場合は、残りのバイトを `Utf8JsonReader` に渡す前に、バッファーからこれらの 3 バイトを取り除く必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-414">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="bc94b-415">そうしないと、BOM は JSON の有効な部分と見なされないため、リーダーによって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-415">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="bc94b-416">このサンプル コードでは、4 KB のバッファーから開始し、サイズが完全な JSON トークンに対応するのに十分な大きさではないことが判明するたびにバッファー サイズを 2 倍にします。これは、リーダーが JSON ペイロードの処理を進めるために必要です。</span><span class="sxs-lookup"><span data-stu-id="bc94b-416">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not big enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="bc94b-417">スニペットに用意されている JSON サンプルでは、非常に小さい初期バッファー サイズ (たとえば、10 バイト) を設定した場合にのみ、バッファー サイズが増加します。</span><span class="sxs-lookup"><span data-stu-id="bc94b-417">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="bc94b-418">初期バッファー サイズを 10 に設定すると、`Console.WriteLine` ステートメントによって、バッファー サイズの増加の原因と影響が示されます。</span><span class="sxs-lookup"><span data-stu-id="bc94b-418">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="bc94b-419">4 KB の初期バッファー サイズで、サンプルの JSON 全体が各 `Console.WriteLine` によって表示され、バッファー サイズを増やす必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bc94b-419">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="bc94b-420">前の例では、バッファーをどの大きさまで拡大できるかに対して無制限を設定しています。</span><span class="sxs-lookup"><span data-stu-id="bc94b-420">The preceding example sets no limit to how big the buffer can grow.</span></span> <span data-ttu-id="bc94b-421">トークン サイズが大きすぎる場合、コードは <xref:System.OutOfMemoryException> 例外で失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bc94b-421">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="bc94b-422">これは、JSON にサイズが約 1 GB 以上のトークンが含まれている場合に発生する可能性があります。1 GB のサイズを 2 倍にすると、サイズが大きすぎて `int32` バッファーに入り切らないためです。</span><span class="sxs-lookup"><span data-stu-id="bc94b-422">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bc94b-423">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="bc94b-423">Additional resources</span></span>

* [<span data-ttu-id="bc94b-424">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="bc94b-424">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="bc94b-425">カスタム コンバーターを記述する方法</span><span class="sxs-lookup"><span data-stu-id="bc94b-425">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="bc94b-426">Newtonsoft.Json から移行する方法</span><span class="sxs-lookup"><span data-stu-id="bc94b-426">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="bc94b-427">System.Text.Json での DateTime と DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="bc94b-427">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="bc94b-428">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="bc94b-428">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
