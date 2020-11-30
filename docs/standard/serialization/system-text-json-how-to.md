---
title: C# を使用して JSON をシリアル化および逆シリアル化する方法 - .NET
description: System.Text.Json 名前空間を使用して .NET 内で JSON のシリアル化と逆シリアル化を行う方法について学習します。 サンプル コードが含まれています。
ms.date: 11/05/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1e8c46e11d3a82ca0bce29f9cb7bbc749c219198
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676726"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="35626-104">.NET 内で JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリングの解除) を行う方法</span><span class="sxs-lookup"><span data-stu-id="35626-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="35626-105">この記事では、<xref:System.Text.Json?displayProperty=fullName> 名前空間を使用して JavaScript Object Notation (JSON) のシリアル化と逆シリアル化を行う方法について示します。</span><span class="sxs-lookup"><span data-stu-id="35626-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="35626-106">`Newtonsoft.Json` から既存のコードを移植する場合は、[`System.Text.Json` に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="35626-107">指示とサンプル コードでは、ライブラリを [ASP.NET Core](/aspnet/core/) などのフレームワーク経由ではなく直接使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="35626-108">シリアル化のサンプル コードの大部分では、JSON を "整形" するために <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します (人間が読みやすいようにインデントと空白文字が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="35626-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="35626-109">実稼働環境で使用する場合、通常、この設定には既定値の `false` をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="35626-110">コード例では、次のクラスとそのバリアントを参照しています。</span><span class="sxs-lookup"><span data-stu-id="35626-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="35626-111">名前空間</span><span class="sxs-lookup"><span data-stu-id="35626-111">Namespaces</span></span>

<span data-ttu-id="35626-112"><xref:System.Text.Json> 名前空間には、すべてのエントリ ポイントと主要な型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="35626-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="35626-113"><xref:System.Text.Json.Serialization> 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="35626-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="35626-114">この記事に示されているコード例では、次のいずれかまたは両方の名前空間に `using` ディレクティブが必要です。</span><span class="sxs-lookup"><span data-stu-id="35626-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="35626-115"><xref:System.Runtime.Serialization> 名前空間の属性は、`System.Text.Json` ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35626-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="35626-116">.NET オブジェクトを JSON に書き込む方法 (シリアル化)</span><span class="sxs-lookup"><span data-stu-id="35626-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="35626-117">JSON を文字列またはファイルに書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35626-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="35626-118">次の例では、JSON を文字列として作成します。</span><span class="sxs-lookup"><span data-stu-id="35626-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-119">次の例では、同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="35626-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-120">次の例では、非同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="35626-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-121">前の例では、シリアル化する型に型の推定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="35626-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="35626-122">`Serialize()` のオーバーロードでは、ジェネリック型パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="35626-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="35626-123">シリアル化の例</span><span class="sxs-lookup"><span data-stu-id="35626-123">Serialization example</span></span>

<span data-ttu-id="35626-124">コレクション型のプロパティとユーザー定義型を含むクラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> <span data-ttu-id="35626-125">"POCO" は、[Plain Old CLR Object (単純な従来の CLR オブジェクト)](https://en.wikipedia.org/wiki/Plain_old_CLR_object) を表します。</span><span class="sxs-lookup"><span data-stu-id="35626-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="35626-126">POCO は、継承や属性からなど、フレームワーク固有の型に依存しない .NET 型です。</span><span class="sxs-lookup"><span data-stu-id="35626-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="35626-127">前の型のインスタンスをシリアル化した場合の JSON 出力は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="35626-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="35626-128">JSON 出力は既定で縮小されます。</span><span class="sxs-lookup"><span data-stu-id="35626-128">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="35626-129">次の例では、同じ JSON ですが、書式設定されているもの (空白とインデントで整形されています) を示しています。</span><span class="sxs-lookup"><span data-stu-id="35626-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="35626-130">UTF-8 にシリアル化する</span><span class="sxs-lookup"><span data-stu-id="35626-130">Serialize to UTF-8</span></span>

<span data-ttu-id="35626-131">UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35626-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-132"><xref:System.Text.Json.Utf8JsonWriter> を受け取る <xref:System.Text.Json.JsonSerializer.Serialize%2A> オーバーロードも使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="35626-133">UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約 5-10% 高速です。</span><span class="sxs-lookup"><span data-stu-id="35626-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="35626-134">違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないことから生じます。</span><span class="sxs-lookup"><span data-stu-id="35626-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="35626-135">シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="35626-135">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="35626-136">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="35626-137">[無視するプロパティを指定する](#ignore-properties)ことができます。</span><span class="sxs-lookup"><span data-stu-id="35626-137">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="35626-138">[既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="35626-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="35626-139">既定では、JSON は縮小されます。</span><span class="sxs-lookup"><span data-stu-id="35626-139">By default, JSON is minified.</span></span> <span data-ttu-id="35626-140">[JSON を整形](#serialize-to-formatted-json)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="35626-141">既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。</span><span class="sxs-lookup"><span data-stu-id="35626-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="35626-142">[JSON 名の大文字と小文字の区別をカスタマイズ](#customize-json-names-and-values)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-142">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="35626-143">既定では、循環参照が検出され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="35626-144">[参照を保持し、循環参照を処理する](#preserve-references-and-handle-circular-references)ことができます。</span><span class="sxs-lookup"><span data-stu-id="35626-144">You can [preserve references and handle circular references](#preserve-references-and-handle-circular-references).</span></span>
* <span data-ttu-id="35626-145">既定では、[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="35626-146">[フィールドを含める](#include-fields)ことができます。</span><span class="sxs-lookup"><span data-stu-id="35626-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="35626-147">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="35626-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="35626-148">詳細については、「[JsonSerializerOptions の Web の規定値](#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-148">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="35626-149">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="35626-150">[無視するプロパティを指定する](#ignore-properties)ことができます。</span><span class="sxs-lookup"><span data-stu-id="35626-150">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="35626-151">[既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="35626-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="35626-152">既定では、JSON は縮小されます。</span><span class="sxs-lookup"><span data-stu-id="35626-152">By default, JSON is minified.</span></span> <span data-ttu-id="35626-153">[JSON を整形](#serialize-to-formatted-json)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="35626-154">既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。</span><span class="sxs-lookup"><span data-stu-id="35626-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="35626-155">[JSON 名の大文字と小文字の区別をカスタマイズ](#customize-json-names-and-values)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-155">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="35626-156">循環参照が検出され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="35626-157">[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="35626-158">サポートされる型には次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="35626-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="35626-159">数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。</span><span class="sxs-lookup"><span data-stu-id="35626-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="35626-160">ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="35626-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="35626-161">1 次元配列とジャグ配列 (`T[][]`)。</span><span class="sxs-lookup"><span data-stu-id="35626-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="35626-162">次の名前空間のコレクションとディクショナリ。</span><span class="sxs-lookup"><span data-stu-id="35626-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="35626-163">数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。</span><span class="sxs-lookup"><span data-stu-id="35626-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="35626-164">ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="35626-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="35626-165">1 次元配列とジャグ配列 (`ArrayName[][]`)。</span><span class="sxs-lookup"><span data-stu-id="35626-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="35626-166">`Dictionary<string,TValue>`。`TValue` は `object`、`JsonElement`、または POCO です。</span><span class="sxs-lookup"><span data-stu-id="35626-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="35626-167">次の名前空間からのコレクション。</span><span class="sxs-lookup"><span data-stu-id="35626-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="35626-168">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、追加の型を処理したり、組み込みコンバーターではサポートされていない機能を提供したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="35626-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="35626-169">JSON を .NET オブジェクトに読み取る方法 (逆シリアル化)</span><span class="sxs-lookup"><span data-stu-id="35626-169">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="35626-170">文字列またはファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35626-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="35626-171">次の例では、文字列から JSON を読み取り、前に[シリアル化の例](#serialization-example)で示した `WeatherForecastWithPOCOs` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="35626-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="35626-172">同期コードを使用してファイルから逆シリアル化するには、次の例に示すように、ファイルを文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="35626-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="35626-173">非同期コードを使用してファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35626-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="35626-174">UTF-8 からの逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="35626-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="35626-175">UTF-8 から逆シリアル化するには、次の例に示すように、`Utf8JsonReader` または `ReadOnlySpan<byte>` を受け取る <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> オーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35626-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="35626-176">この例では、JSON が jsonUtf8Bytes という名前のバイト配列内にあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="35626-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="35626-177">逆シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="35626-177">Deserialization behavior</span></span>

<span data-ttu-id="35626-178">JSON を逆シリアル化する場合、次の動作が適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="35626-179">既定では、プロパティ名の照合では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="35626-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="35626-180">[大文字と小文字を区別しないことを指定](#case-insensitive-property-matching)できます。</span><span class="sxs-lookup"><span data-stu-id="35626-180">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="35626-181">JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="35626-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="35626-182">非パブリック コンストラクターはシリアライザーにより無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="35626-183">不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="35626-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="35626-184">「[不変の型とレコード](#immutable-types-and-records)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-184">See [Immutable types and Records](#immutable-types-and-records).</span></span>
* <span data-ttu-id="35626-185">既定では、列挙型は数値としてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="35626-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="35626-186">[列挙型名を文字列としてシリアル化](#enums-as-strings)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-186">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="35626-187">既定では、フィールドは無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-187">By default, fields are ignored.</span></span> <span data-ttu-id="35626-188">[フィールドを含める](#include-fields)ことができます。</span><span class="sxs-lookup"><span data-stu-id="35626-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="35626-189">既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="35626-190">[コメントと末尾のコンマを許可](#allow-comments-and-trailing-commas)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-190">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="35626-191">[既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。</span><span class="sxs-lookup"><span data-stu-id="35626-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="35626-192">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="35626-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="35626-193">詳細については、「[JsonSerializerOptions の Web の規定値](#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-193">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="35626-194">既定では、プロパティ名の照合では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="35626-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="35626-195">[大文字と小文字を区別しないことを指定](#case-insensitive-property-matching)できます。</span><span class="sxs-lookup"><span data-stu-id="35626-195">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span> <span data-ttu-id="35626-196">ASP.NET Core アプリの場合、[既定では大文字と小文字を区別しないことが指定](#web-defaults-for-jsonserializeroptions)されます。</span><span class="sxs-lookup"><span data-stu-id="35626-196">ASP.NET Core apps [specify case-insensitivity by default](#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="35626-197">JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="35626-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="35626-198">逆シリアル化には、パラメーターなしのコンストラクター (public、internal、private のいずれか) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="35626-199">不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35626-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="35626-200">既定では、列挙型は数値としてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="35626-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="35626-201">[列挙型名を文字列としてシリアル化](#enums-as-strings)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-201">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="35626-202">フィールドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="35626-202">Fields aren't supported.</span></span>
* <span data-ttu-id="35626-203">既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="35626-204">[コメントと末尾のコンマを許可](#allow-comments-and-trailing-commas)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-204">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="35626-205">[既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。</span><span class="sxs-lookup"><span data-stu-id="35626-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="35626-206">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="35626-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="35626-207">詳細については、「[JsonSerializerOptions の Web の規定値](#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-207">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="35626-208">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、組み込みコンバーターではサポートされていない機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="35626-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="35626-209">書式設定された JSON へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="35626-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="35626-210">JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="35626-211">シリアル化され、整形された JSON 出力の型の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a><span data-ttu-id="35626-212">フィールドを含める</span><span class="sxs-lookup"><span data-stu-id="35626-212">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-213">次の例で示されているように、シリアル化または逆シリアル化のときにフィールドを含めるには、<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> グローバル設定または [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-213">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

<span data-ttu-id="35626-214">読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-214">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-215">.NET Core 3.1 では、System.Text.Json メソッドはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35626-215">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="35626-216">この機能は、[カスタム コンバーター](system-text-json-converters-how-to.md)で提供できます。</span><span class="sxs-lookup"><span data-stu-id="35626-216">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="customize-json-names-and-values"></a><span data-ttu-id="35626-217">JSON の名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="35626-217">Customize JSON names and values</span></span>

<span data-ttu-id="35626-218">既定では、プロパティ名とディクショナリ キーは、大文字と小文字の区別を含め、JSON の出力では変更されません。</span><span class="sxs-lookup"><span data-stu-id="35626-218">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="35626-219">列挙型の値は数値として表されます。</span><span class="sxs-lookup"><span data-stu-id="35626-219">Enum values are represented as numbers.</span></span> <span data-ttu-id="35626-220">このセクションでは、次の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35626-220">This section explains how to:</span></span>

* [<span data-ttu-id="35626-221">個々のプロパティ名をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="35626-221">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="35626-222">すべてのプロパティ名をキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="35626-222">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="35626-223">カスタム プロパティの名前付けポリシーを実装する</span><span class="sxs-lookup"><span data-stu-id="35626-223">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="35626-224">ディクショナリ キーをキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="35626-224">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="35626-225">列挙型を文字列およびキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="35626-225">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="35626-226">JSON プロパティの名前と値の特別な処理を必要とするその他のシナリオでは、[カスタム コンバーターを実装](system-text-json-converters-how-to.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-226">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="35626-227">個々のプロパティ名をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="35626-227">Customize individual property names</span></span>

<span data-ttu-id="35626-228">個々のプロパティの名前を設定するには、[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-228">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="35626-229">シリアル化する型と、結果として得られる JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-229">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="35626-230">この属性によって設定されるプロパティ名は:</span><span class="sxs-lookup"><span data-stu-id="35626-230">The property name set by this attribute:</span></span>

* <span data-ttu-id="35626-231">シリアル化と逆シリアル化の両方の方向に適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-231">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="35626-232">プロパティの名前付けポリシーよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="35626-232">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="35626-233">すべての JSON プロパティ名にキャメル ケースを使用する</span><span class="sxs-lookup"><span data-stu-id="35626-233">Use camel case for all JSON property names</span></span>

<span data-ttu-id="35626-234">すべての JSON プロパティ名にキャメル ケースを使用するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> を `JsonNamingPolicy.CamelCase` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-234">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="35626-235">シリアル化するクラスと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-235">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="35626-236">キャメル ケースのプロパティの名前付けポリシーは:</span><span class="sxs-lookup"><span data-stu-id="35626-236">The camel case property naming policy:</span></span>

* <span data-ttu-id="35626-237">シリアル化と逆シリアル化に適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-237">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="35626-238">`[JsonPropertyName]` 属性によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="35626-238">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="35626-239">このため、この例の JSON プロパティ名 `Wind` はキャメル ケースではありません。</span><span class="sxs-lookup"><span data-stu-id="35626-239">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="35626-240">カスタム JSON プロパティの名前付けポリシーを使用する</span><span class="sxs-lookup"><span data-stu-id="35626-240">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="35626-241">カスタム JSON プロパティの名前付けポリシーを使用するには、次の例に示すように、<xref:System.Text.Json.JsonNamingPolicy> から派生するクラスを作成し、<xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="35626-241">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="35626-242">次に、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> プロパティを名前付けポリシー クラスのインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-242">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-243">シリアル化するクラスと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-243">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="35626-244">JSON プロパティの名前付けポリシーは:</span><span class="sxs-lookup"><span data-stu-id="35626-244">The JSON property naming policy:</span></span>

* <span data-ttu-id="35626-245">シリアル化と逆シリアル化に適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-245">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="35626-246">`[JsonPropertyName]` 属性によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="35626-246">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="35626-247">このため、この例の JSON プロパティ名 `Wind` は大文字ではありません。</span><span class="sxs-lookup"><span data-stu-id="35626-247">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="35626-248">キャメル ケースのディクショナリ キー</span><span class="sxs-lookup"><span data-stu-id="35626-248">Camel case dictionary keys</span></span>

<span data-ttu-id="35626-249">シリアル化するオブジェクトのプロパティが `Dictionary<string,TValue>` 型である場合は、`string` キーをキャメル ケースに変換できます。</span><span class="sxs-lookup"><span data-stu-id="35626-249">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="35626-250">これを行うには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> を `JsonNamingPolicy.CamelCase` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-250">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-251">キーと値のペア `"ColdMinTemp", 20` および `"HotMinTemp", 40` を持つ `TemperatureRanges` という名前のディクショナリを使用してオブジェクトをシリアル化すると、次の例のような JSON 出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="35626-251">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="35626-252">ディクショナリ キーに対するキャメル ケースの名前付けポリシーは、シリアル化にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-252">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="35626-253">ディクショナリを逆シリアル化すると、`DictionaryKeyPolicy` に `JsonNamingPolicy.CamelCase` を指定した場合でも、キーが JSON ファイルと一致します。</span><span class="sxs-lookup"><span data-stu-id="35626-253">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="35626-254">文字列としての列挙型</span><span class="sxs-lookup"><span data-stu-id="35626-254">Enums as strings</span></span>

<span data-ttu-id="35626-255">既定では、列挙型は数値としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-255">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="35626-256">列挙型名を文字列としてシリアル化するには、<xref:System.Text.Json.Serialization.JsonStringEnumConverter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-256">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="35626-257">たとえば、列挙型を持つ次のクラスをシリアル化する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="35626-257">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="35626-258">Summary が `Hot` の場合、既定では、シリアル化された JSON には数値 3 があります。</span><span class="sxs-lookup"><span data-stu-id="35626-258">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="35626-259">次のサンプル コードでは、数値ではなく列挙型名をシリアル化し、名前をキャメル ケースに変換します。</span><span class="sxs-lookup"><span data-stu-id="35626-259">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-260">結果として生成される JSON は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="35626-260">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="35626-261">列挙型の文字列名も、次の例に示すように逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="35626-261">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a><span data-ttu-id="35626-262">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="35626-262">Ignore properties</span></span>

<span data-ttu-id="35626-263">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-263">By default, all public properties are serialized.</span></span> <span data-ttu-id="35626-264">その一部が JSON 出力に出現しないようにするには、いくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="35626-264">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="35626-265">このセクションでは、以下のものを無視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35626-265">This section explains how to ignore:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="35626-266">個々のプロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-266">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="35626-267">すべての読み取り専用プロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-267">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="35626-268">すべての null 値プロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-268">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="35626-269">すべての既定値のプロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-269">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="35626-270">個々のプロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-270">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="35626-271">すべての読み取り専用プロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-271">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="35626-272">すべての null 値プロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-272">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a><span data-ttu-id="35626-273">個々のプロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="35626-273">Ignore individual properties</span></span>

<span data-ttu-id="35626-274">個々のプロパティを無視するには、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-274">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="35626-275">シリアル化する型と JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-275">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-276">[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティを設定することによって、条件付き除外を指定できます。</span><span class="sxs-lookup"><span data-stu-id="35626-276">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="35626-277"><xref:System.Text.Json.Serialization.JsonIgnoreCondition> 列挙型には、次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="35626-277">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="35626-278">`Always` - プロパティを常に無視します。</span><span class="sxs-lookup"><span data-stu-id="35626-278">`Always` - The property is always ignored.</span></span> <span data-ttu-id="35626-279">`Condition` を指定しないと、このオプションが想定されます。</span><span class="sxs-lookup"><span data-stu-id="35626-279">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="35626-280">`Never` - グローバル設定 `DefaultIgnoreCondition`、`IgnoreReadOnlyProperties`、`IgnoreReadOnlyFields` に関係なく、プロパティは常にシリアル化および逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-280">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="35626-281">`WhenWritingDefault` - プロパティは、参照型 `null` または値型 `default` の場合、シリアル化で無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-281">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null` or a value type `default`.</span></span>
* <span data-ttu-id="35626-282">`WhenWritingNull` - プロパティは、参照型 `null` の場合、シリアル化で無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-282">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`.</span></span>

<span data-ttu-id="35626-283">次の例では、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35626-283">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a><span data-ttu-id="35626-284">すべての読み取り専用プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="35626-284">Ignore all read-only properties</span></span>

<span data-ttu-id="35626-285">パブリック ゲッターが含まれていてもパブリック セッターがない場合、プロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="35626-285">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="35626-286">シリアル化のときにすべての読み取り専用プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-286">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-287">シリアル化する型と JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-287">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="35626-288">このオプションは、シリアル化にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-288">This option applies only to serialization.</span></span> <span data-ttu-id="35626-289">逆シリアル化中、既定では読み取り専用プロパティが無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-289">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-290">このオプションは、プロパティにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-290">This option applies only to properties.</span></span> <span data-ttu-id="35626-291">[フィールドをシリアル化する](#include-fields)ときに読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-291">To ignore read-only fields when [serializing fields](#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

### <a name="ignore-all-null-value-properties"></a><span data-ttu-id="35626-292">すべての null 値プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="35626-292">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-293">すべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-293">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-294">シリアル化のときにすべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-294">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-295">シリアル化するオブジェクトと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-295">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="35626-296">プロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-296">Property</span></span> |<span data-ttu-id="35626-297">値</span><span class="sxs-lookup"><span data-stu-id="35626-297">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="35626-298">Date</span><span class="sxs-lookup"><span data-stu-id="35626-298">Date</span></span>    | <span data-ttu-id="35626-299">8/1/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="35626-299">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="35626-300">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="35626-300">TemperatureCelsius</span></span>| <span data-ttu-id="35626-301">25</span><span class="sxs-lookup"><span data-stu-id="35626-301">25</span></span> |
| <span data-ttu-id="35626-302">まとめ</span><span class="sxs-lookup"><span data-stu-id="35626-302">Summary</span></span>| <span data-ttu-id="35626-303">null</span><span class="sxs-lookup"><span data-stu-id="35626-303">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a><span data-ttu-id="35626-304">既定値のプロパティをすべて無視する</span><span class="sxs-lookup"><span data-stu-id="35626-304">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-305">値型プロパティで既定値がシリアル化されないようにするには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-305">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="35626-306">`WhenWritingDefault` を設定すると、null 値参照型プロパティもシリアル化されなくなります。</span><span class="sxs-lookup"><span data-stu-id="35626-306">The `WhenWritingDefault` setting also prevents serialization of null-value reference type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-307">.NET Core 3.1 の System.Text.Json で、値型の既定値のプロパティがシリアル化されないようにするための組み込みの方法はありません。</span><span class="sxs-lookup"><span data-stu-id="35626-307">There is no built-in way to prevent serialization of properties with value type defaults in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="customize-character-encoding"></a><span data-ttu-id="35626-308">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="35626-308">Customize character encoding</span></span>

<span data-ttu-id="35626-309">既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="35626-309">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="35626-310">つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。</span><span class="sxs-lookup"><span data-stu-id="35626-310">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="35626-311">たとえば、`Summary` プロパティがキリル文字の жарко に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-311">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="35626-312">言語文字セットのシリアル化</span><span class="sxs-lookup"><span data-stu-id="35626-312">Serialize language character sets</span></span>

<span data-ttu-id="35626-313">1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。</span><span class="sxs-lookup"><span data-stu-id="35626-313">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="35626-314">このコードでは、キリル文字やギリシャ文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="35626-314">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="35626-315">`Summary` プロパティがキリル文字の жарко に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-315">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="35626-316">すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-316">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="35626-317">特定の文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="35626-317">Serialize specific characters</span></span>

<span data-ttu-id="35626-318">別の方法として、エスケープせずに許可する個々の文字を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="35626-318">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="35626-319">次の例では、жарко の最初の 2 文字のみをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="35626-319">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="35626-320">上記のコードによって生成される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-320">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="35626-321">すべての文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="35626-321">Serialize all characters</span></span>

<span data-ttu-id="35626-322">エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-322">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="35626-323">既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。</span><span class="sxs-lookup"><span data-stu-id="35626-323">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="35626-324">`<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="35626-324">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="35626-325">クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。</span><span class="sxs-lookup"><span data-stu-id="35626-325">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="35626-326">安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="35626-326">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="35626-327">たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-327">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="35626-328">未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="35626-328">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="35626-329">派生クラスのプロパティのシリアル化</span><span class="sxs-lookup"><span data-stu-id="35626-329">Serialize properties of derived classes</span></span>

<span data-ttu-id="35626-330">ポリモーフィックな型階層のシリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35626-330">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="35626-331">たとえば、プロパティがインターフェイスまたは抽象クラスとして定義されている場合は、ランタイム型に追加のプロパティがある場合でも、インターフェイスまたは抽象クラスに定義されたプロパティのみがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-331">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="35626-332">この動作の例外については、このセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="35626-332">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="35626-333">たとえば、`WeatherForecast` クラスと派生クラス `WeatherForecastDerived` があるとします。</span><span class="sxs-lookup"><span data-stu-id="35626-333">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="35626-334">また、コンパイル時の `Serialize` メソッドの型引数が `WeatherForecast` であるとします。</span><span class="sxs-lookup"><span data-stu-id="35626-334">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="35626-335">このシナリオでは、`weatherForecast` オブジェクトが実際には `WeatherForecastDerived` オブジェクトであっても、`WindSpeed` プロパティはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="35626-335">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="35626-336">基本クラスのプロパティのみがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-336">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="35626-337">この動作は、ランタイムによって作成される派生型内でデータが誤って公開されるのを防ぐためのものです。</span><span class="sxs-lookup"><span data-stu-id="35626-337">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="35626-338">前の例で派生型のプロパティをシリアル化するには、次のいずれかのアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-338">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="35626-339">実行時に型を指定できるようにする <xref:System.Text.Json.JsonSerializer.Serialize%2A> のオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35626-339">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="35626-340">オブジェクトを `object` としてシリアル化するように宣言します。</span><span class="sxs-lookup"><span data-stu-id="35626-340">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="35626-341">前の例のシナリオでは、どちらのアプローチでも、`WindSpeed` プロパティが JSON 出力に含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="35626-341">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="35626-342">これらのアプローチでは、シリアル化するルート オブジェクトに対してのみポリモーフィックなシリアル化が提供され、そのルート オブジェクトのプロパティに対しては提供されません。</span><span class="sxs-lookup"><span data-stu-id="35626-342">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="35626-343">`object` 型として定義すると、下位レベルのオブジェクトのポリモーフィックなシリアル化を取得できます。</span><span class="sxs-lookup"><span data-stu-id="35626-343">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="35626-344">たとえば、`WeatherForecast` クラスに、`WeatherForecast` または `object` 型として定義できる `PreviousForecast` という名前のプロパティがあるとします。</span><span class="sxs-lookup"><span data-stu-id="35626-344">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="35626-345">`PreviousForecast` プロパティに `WeatherForecastDerived` のインスタンスが含まれる場合:</span><span class="sxs-lookup"><span data-stu-id="35626-345">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="35626-346">`WeatherForecastWithPrevious` のシリアル化からの JSON 出力には `WindSpeed` が **含まれていません**。</span><span class="sxs-lookup"><span data-stu-id="35626-346">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="35626-347">`WeatherForecastWithPreviousAsObject` のシリアル化からの JSON 出力には `WindSpeed` が **含まれています**。</span><span class="sxs-lookup"><span data-stu-id="35626-347">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="35626-348">ルート オブジェクトは派生型である可能性があるものではないため、`WeatherForecastWithPreviousAsObject` をシリアル化するために `Serialize<object>` または `GetType` を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="35626-348">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="35626-349">次のコード例では `Serialize<object>` または `GetType` は呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="35626-349">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="35626-350">上記のコードでは、`WeatherForecastWithPreviousAsObject` が正しくシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-350">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="35626-351">`object` と同じプロパティ定義のアプローチがインターフェイスで機能します。</span><span class="sxs-lookup"><span data-stu-id="35626-351">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="35626-352">次のインターフェイスと実装があり、実装インスタンスを含むプロパティを使用してクラスをシリアル化するとします。</span><span class="sxs-lookup"><span data-stu-id="35626-352">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="35626-353">`Forecasts` のインスタンスをシリアル化する場合、`Tuesday` は `object` として定義されているので、`Tuesday` にのみ `WindSpeed` プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="35626-353">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="35626-354">次の例は、前のコードから生成された JSON を示しています。</span><span class="sxs-lookup"><span data-stu-id="35626-354">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="35626-355">ポリモーフィック **シリアル化** の詳細、および **逆シリアル化** の詳細については、「[Newtonsoft.Json から System.Text.Json に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-355">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="35626-356">コメントと末尾のコンマを許可する</span><span class="sxs-lookup"><span data-stu-id="35626-356">Allow comments and trailing commas</span></span>

<span data-ttu-id="35626-357">既定では、JSON 内でコメントと末尾のコンマは使用できません。</span><span class="sxs-lookup"><span data-stu-id="35626-357">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="35626-358">JSON 内でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-358">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="35626-359">また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-359">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="35626-360">両方を許可する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-360">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="35626-361">次に、コメントと末尾のコンマを含む JSON の例を示します。</span><span class="sxs-lookup"><span data-stu-id="35626-361">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="35626-362">大文字と小文字を区別しないプロパティ照合</span><span class="sxs-lookup"><span data-stu-id="35626-362">Case-insensitive property matching</span></span>

<span data-ttu-id="35626-363">既定では、逆シリアル化では JSON とターゲット オブジェクトのプロパティとの間で大文字と小文字を区別したプロパティ名の一致が検索されます。</span><span class="sxs-lookup"><span data-stu-id="35626-363">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="35626-364">この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-364">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="35626-365">キャメル ケースのプロパティ名を持つ JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-365">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="35626-366">これはパスカル ケースのプロパティ名を持つ次の型に逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="35626-366">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="35626-367">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="35626-367">Handle overflow JSON</span></span>

<span data-ttu-id="35626-368">逆シリアル化中に、ターゲット型のプロパティで表されないデータを JSON 内で受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="35626-368">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="35626-369">たとえば、ターゲット型が次のようになっているとします。</span><span class="sxs-lookup"><span data-stu-id="35626-369">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="35626-370">逆シリアル化される JSON は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35626-370">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="35626-371">表示されている JSON を示されている型に逆シリアル化すると、`DatesAvailable` と `SummaryWords` のプロパティは行き先がなくなり、失われます。</span><span class="sxs-lookup"><span data-stu-id="35626-371">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="35626-372">これらのプロパティのような余分なデータをキャプチャするには、[[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 属性を `Dictionary<string,object>` 型または `Dictionary<string,JsonElement>` 型のプロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="35626-372">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="35626-373">前に示した JSON をこのサンプル型に逆シリアル化すると、余分なデータが `ExtensionData` プロパティのキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="35626-373">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="35626-374">プロパティ</span><span class="sxs-lookup"><span data-stu-id="35626-374">Property</span></span> |<span data-ttu-id="35626-375">値</span><span class="sxs-lookup"><span data-stu-id="35626-375">Value</span></span>  |<span data-ttu-id="35626-376">メモ</span><span class="sxs-lookup"><span data-stu-id="35626-376">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="35626-377">Date</span><span class="sxs-lookup"><span data-stu-id="35626-377">Date</span></span>    | <span data-ttu-id="35626-378">8/1/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="35626-378">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="35626-379">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="35626-379">TemperatureCelsius</span></span>| <span data-ttu-id="35626-380">0</span><span class="sxs-lookup"><span data-stu-id="35626-380">0</span></span> | <span data-ttu-id="35626-381">大文字と小文字の区別が一致しないため (JSON では `temperatureCelsius`)、プロパティは設定されません。</span><span class="sxs-lookup"><span data-stu-id="35626-381">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="35626-382">まとめ</span><span class="sxs-lookup"><span data-stu-id="35626-382">Summary</span></span> | <span data-ttu-id="35626-383">ホット</span><span class="sxs-lookup"><span data-stu-id="35626-383">Hot</span></span> ||
| <span data-ttu-id="35626-384">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="35626-384">ExtensionData</span></span> | <span data-ttu-id="35626-385">temperatureCelsius:25</span><span class="sxs-lookup"><span data-stu-id="35626-385">temperatureCelsius: 25</span></span> |<span data-ttu-id="35626-386">大文字と小文字の区別が一致しなかったため、この JSON プロパティは余分で、ディクショナリ内のキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="35626-386">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="35626-387">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="35626-387">DatesAvailable:</span></span><br>  <span data-ttu-id="35626-388">8/1/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="35626-388">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="35626-389">8/2/2019 12:00:00 AM -07:00</span><span class="sxs-lookup"><span data-stu-id="35626-389">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="35626-390">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="35626-390">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="35626-391">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="35626-391">SummaryWords:</span></span><br><span data-ttu-id="35626-392">Cool</span><span class="sxs-lookup"><span data-stu-id="35626-392">Cool</span></span><br><span data-ttu-id="35626-393">強風</span><span class="sxs-lookup"><span data-stu-id="35626-393">Windy</span></span><br><span data-ttu-id="35626-394">Humid</span><span class="sxs-lookup"><span data-stu-id="35626-394">Humid</span></span> |<span data-ttu-id="35626-395">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="35626-395">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="35626-396">ターゲット オブジェクトがシリアル化されると、拡張データのキーと値のペアは、受信 JSON 内にあった場合と同様に JSON プロパティになります。</span><span class="sxs-lookup"><span data-stu-id="35626-396">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="35626-397">JSON には `ExtensionData` プロパティ名が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="35626-397">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="35626-398">この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンド トリップを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35626-398">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="35626-399">参照を保持し、循環参照を処理する</span><span class="sxs-lookup"><span data-stu-id="35626-399">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="35626-400">参照を保持し、循環参照を処理するには、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> を <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-400">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="35626-401">これを設定すると、次のような動作になります。</span><span class="sxs-lookup"><span data-stu-id="35626-401">This setting causes the following behavior:</span></span>

* <span data-ttu-id="35626-402">シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="35626-402">On serialize:</span></span>

  <span data-ttu-id="35626-403">複合型を書き込むとき、シリアライザーによってメタデータのプロパティ (`$id`、`$values`、`$ref`) も書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="35626-403">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="35626-404">逆シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="35626-404">On deserialize:</span></span>

  <span data-ttu-id="35626-405">メタデータが想定され (必須ではありません)、逆シリアライザーによってその理解が試みられます。</span><span class="sxs-lookup"><span data-stu-id="35626-405">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="35626-406">次のコードでは、`Preserve` 設定の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35626-406">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="35626-407">この機能を使用して、値型または不変型を保持することはできません。</span><span class="sxs-lookup"><span data-stu-id="35626-407">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="35626-408">逆シリアル化のとき、不変型のインスタンスは、ペイロード全体が読み取られた後で作成されます。</span><span class="sxs-lookup"><span data-stu-id="35626-408">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="35626-409">そのため、同じインスタンスへの参照が JSON ペイロード内に含まれている場合、それを逆シリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="35626-409">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="35626-410">値型、不変型、配列の場合、参照メタデータはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="35626-410">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="35626-411">逆シリアル化では、`$ref` または `$id` が検出されると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-411">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="35626-412">ただし、Newtonsoft.Json を使用してシリアル化されたペイロードを逆シリアル化できるようにするため、`$id` (および、コレクションの場合は `$values`) は値型で無視されます。</span><span class="sxs-lookup"><span data-stu-id="35626-412">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="35626-413">Newtonsoft.Json の場合は、そのような型のメタデータがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="35626-413">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="35626-414">オブジェクトが等しいかどうかを判断するために System.Text.Json によって使用される <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> では、2 つのオブジェクト インスタンスを比較するときに、値の等価性 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>) ではなく参照の等価性 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-414">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="35626-415">参照がシリアル化および逆シリアル化される方法の詳細については、<xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-415">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="35626-416">シリアル化および逆シリアル化で参照を維持するための動作は、<xref:System.Text.Json.Serialization.ReferenceResolver> クラスによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="35626-416">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="35626-417">カスタム動作を指定するには、派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="35626-417">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="35626-418">例については、[GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-418">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-419">.NET Core 3.1 の System.Text.Json でサポートされているのは値によるシリアル化のみであり、循環参照の場合は例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-419">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="35626-420">引用符で囲まれた数値を許可または記述する</span><span class="sxs-lookup"><span data-stu-id="35626-420">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="35626-421">シリアライザーの中には、数値が JSON 文字列としてエンコードされる (引用符で囲まれる) ものがあります。</span><span class="sxs-lookup"><span data-stu-id="35626-421">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span> <span data-ttu-id="35626-422">たとえば、`{"DegreesCelsius":23}` ではなく `{"DegreesCelsius":"23"}` になります。</span><span class="sxs-lookup"><span data-stu-id="35626-422">For example: `{"DegreesCelsius":"23"}` instead of `{"DegreesCelsius":23}`.</span></span> <span data-ttu-id="35626-423">引用符で囲まれた数値をシリアル化したり、引用符で囲まれた数値を入力オブジェクト グラフ全体で受け付けるには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> を設定します。</span><span class="sxs-lookup"><span data-stu-id="35626-423">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

<span data-ttu-id="35626-424">ASP.NET Core を通じて間接的に System.Text.Json を使用すると、ASP.NET Core により [Web の既定のオプション](xref:System.Text.Json.JsonSerializerDefaults.Web)が指定されるため、逆シリアル化のときに引用符で囲まれた数値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-424">When you use System.Text.Json indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="35626-425">特定のプロパティ、フィールド、または型について引用符で囲まれた数値を許可または記述するには、[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-425">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-426">.NET Core 3.1 の System.Text.Json では、引用符で囲まれた数値のシリアル化または逆シリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35626-426">System.Text.Json in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="35626-427">詳細については、「[引用符で囲まれた数値を許可または記述する](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-427">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="immutable-types-and-records"></a><span data-ttu-id="35626-428">不変の型とレコード</span><span class="sxs-lookup"><span data-stu-id="35626-428">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-429">System.Text.Json ではパラメーター化されたコンストラクターを使用できるので、不変のクラスまたは構造体を逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="35626-429">System.Text.Json can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="35626-430">クラスの場合、パラメーター化されたコンストラクターしかない場合は、そのコンストラクターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-430">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="35626-431">構造体または複数のコンストラクターを持つクラスの場合は、[[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 属性を適用することにより、使用するコンストラクターを指定します。</span><span class="sxs-lookup"><span data-stu-id="35626-431">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="35626-432">その属性を使用しないと、パラメーターなしのパブリック コンストラクターが存在する場合は常にそれが使用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-432">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="35626-433">その属性は、パブリック コンストラクターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-433">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="35626-434">次の例では、`[JsonConstructor]` 属性が使用されています。</span><span class="sxs-lookup"><span data-stu-id="35626-434">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="35626-435">次の例で示されているように、C# 9 のレコードもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="35626-435">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="35626-436">すべてのプロパティ セッターが非パブリックであるために不変の型の場合は、[パブリックでないプロパティ アクセサー](#non-public-property-accessors)に関する次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-436">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-437">`JsonConstructorAttribute` と C# 9 のレコードのサポートは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="35626-437">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="35626-438">パブリックでないプロパティ アクセサー</span><span class="sxs-lookup"><span data-stu-id="35626-438">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-439">パブリックでないプロパティ アクセサーを使用できるようにするには、次の例で示されているように、[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="35626-439">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-440">パブリックでないプロパティ アクセサーは、.NET Core 3.1 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35626-440">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="35626-441">詳細については、[Newtonsoft.Json からの移行の記事](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35626-441">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="35626-442">JsonSerializerOptions をコピーする</span><span class="sxs-lookup"><span data-stu-id="35626-442">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-443">次の例で示されているように、既存のインスタンスと同じオプションを使用して新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions))があります。</span><span class="sxs-lookup"><span data-stu-id="35626-443">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-444">既存のインスタンスを受け取る `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="35626-444">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="35626-445">JsonSerializerOptions の Web の既定値</span><span class="sxs-lookup"><span data-stu-id="35626-445">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="35626-446">Web アプリ用に異なる既定値があるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35626-446">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="35626-447">次の例で示されているように、ASP.NET Core によって Web アプリ用に使用される既定のオプションで新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true)があります。</span><span class="sxs-lookup"><span data-stu-id="35626-447">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-448">Web アプリ用に異なる既定値があるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35626-448">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="35626-449">既定値のセットを指定する `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="35626-449">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="35626-450">HttpClient と HttpContent の拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="35626-450">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="35626-451">ネットワークからの JSON ペイロードのシリアル化と逆シリアル化は、一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="35626-451">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="35626-452">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) および [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) の拡張メソッドを使用すると、これらの操作を 1 行のコードで実行できます。</span><span class="sxs-lookup"><span data-stu-id="35626-452">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="35626-453">これらの拡張メソッドにおいては、[JsonSerializerOptions の Web の既定値](#web-defaults-for-jsonserializeroptions)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-453">These extension methods use [web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="35626-454">次の例では、<xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> と <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35626-454">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

<span data-ttu-id="35626-455">[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) には System.Text.Json 用の拡張メソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="35626-455">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="35626-456">`HttpClient` および `HttpContent` の拡張メソッドは、.NET Core 3.1 の System.Text.Json では使用できません。</span><span class="sxs-lookup"><span data-stu-id="35626-456">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="35626-457">Utf8JsonReader、Utf8JsonWriter、JsonDocument</span><span class="sxs-lookup"><span data-stu-id="35626-457">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="35626-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> は、UTF-8 でエンコードされた JSON テキスト用の、ハイパフォーマンス、低割り当て、順方向専用のリーダーです。`ReadOnlySpan<byte>` または `ReadOnlySequence<byte>` から読み取られます。</span><span class="sxs-lookup"><span data-stu-id="35626-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="35626-459">`Utf8JsonReader` は低レベルの型であり、カスタム パーサーとデシリアライザーを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-459">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="35626-460"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonReader` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-460">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="35626-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> は、`String`、`Int32`、`DateTime` のような一般的な .NET 型から UTF-8 でエンコードされた JSON テキストを書き込むための、ハイパフォーマンスな方法です。</span><span class="sxs-lookup"><span data-stu-id="35626-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="35626-462">ライターは低レベルの型であり、カスタム シリアライザーを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-462">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="35626-463"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonWriter` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-463">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="35626-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> では、`Utf8JsonReader` を使用して、読み取り専用のドキュメント オブジェクト モデル (DOM) を構築する機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="35626-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="35626-465">DOM では、JSON ペイロード内のデータへのランダム アクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="35626-465">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="35626-466">ペイロードを構成する JSON 要素には、<xref:System.Text.Json.JsonElement> 型を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="35626-466">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="35626-467">`JsonElement` 型では、配列とオブジェクト列挙子と共に、JSON テキストを一般的な .NET 型に変換する API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="35626-467">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="35626-468">`JsonDocument` では <xref:System.Text.Json.JsonDocument.RootElement> プロパティが公開されます。</span><span class="sxs-lookup"><span data-stu-id="35626-468">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="35626-469">以下のセクションでは、これらのツールを使用して JSON の読み取りと書き込みを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35626-469">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="35626-470">JsonDocument を使用してデータにアクセスする</span><span class="sxs-lookup"><span data-stu-id="35626-470">Use JsonDocument for access to data</span></span>

<span data-ttu-id="35626-471">次の例は、<xref:System.Text.Json.JsonDocument> クラスを使用して JSON 文字列内のデータにランダム アクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="35626-471">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="35626-472">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="35626-472">The preceding code:</span></span>

* <span data-ttu-id="35626-473">分析する JSON が `jsonString` という名前の文字列に含まれていると想定します。</span><span class="sxs-lookup"><span data-stu-id="35626-473">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="35626-474">`Grade` プロパティを持つ `Students` 配列内のオブジェクトの平均グレードを計算します。</span><span class="sxs-lookup"><span data-stu-id="35626-474">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="35626-475">グレードのない学生には既定のグレード 70 を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="35626-475">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="35626-476">反復するたびに `count` 変数をインクリメントして学生をカウントします。</span><span class="sxs-lookup"><span data-stu-id="35626-476">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="35626-477">別の方法として、次の例に示すように <xref:System.Text.Json.JsonElement.GetArrayLength%2A> を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="35626-477">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="35626-478">このコードで処理される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-478">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="35626-479">JsonDocument を使用して JSON を書き込む</span><span class="sxs-lookup"><span data-stu-id="35626-479">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="35626-480">次の例では、<xref:System.Text.Json.JsonDocument> から JSON を書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35626-480">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="35626-481">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="35626-481">The preceding code:</span></span>

* <span data-ttu-id="35626-482">JSON ファイルを読み取り、データを `JsonDocument` に読み込み、書式設定された (整形された) JSON をファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="35626-482">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="35626-483"><xref:System.Text.Json.JsonDocumentOptions> を使用して、入力 JSON 内でコメントは許可されるが無視されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="35626-483">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="35626-484">完了したら、ライターに対して <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35626-484">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="35626-485">別の方法として、破棄されたときにライターを自動フラッシュすることもできます。</span><span class="sxs-lookup"><span data-stu-id="35626-485">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="35626-486">コード例によって処理される JSON 入力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-486">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="35626-487">その結果は、次のような整形された JSON 出力になります。</span><span class="sxs-lookup"><span data-stu-id="35626-487">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="35626-488">Utf8JsonWriter を使用する</span><span class="sxs-lookup"><span data-stu-id="35626-488">Use Utf8JsonWriter</span></span>

<span data-ttu-id="35626-489"><xref:System.Text.Json.Utf8JsonWriter> クラスを使用する方法を示す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-489">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="35626-490">Utf8JsonReader を使用する</span><span class="sxs-lookup"><span data-stu-id="35626-490">Use Utf8JsonReader</span></span>

<span data-ttu-id="35626-491"><xref:System.Text.Json.Utf8JsonReader> クラスを使用する方法を示す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-491">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="35626-492">上記のコードでは、`jsonUtf8` 変数が、UTF-8 としてエンコードされた有効な JSON を含むバイト配列であることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="35626-492">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="35626-493">Utf8JsonReader を使用してデータをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="35626-493">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="35626-494">次の例は、ファイルを同期的に読み取り、値を検索する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="35626-494">The following example shows how to read a file synchronously and search for a value.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="35626-495">([この例の非同期バージョン](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs)は利用できます)</span><span class="sxs-lookup"><span data-stu-id="35626-495">(An [async version of this example](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs) is available.)</span></span>

<span data-ttu-id="35626-496">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="35626-496">The preceding code:</span></span>

* <span data-ttu-id="35626-497">JSON にオブジェクトの配列が含まれ、各オブジェクトに文字列型の "name" プロパティが含まれている可能性があると想定します。</span><span class="sxs-lookup"><span data-stu-id="35626-497">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="35626-498">オブジェクトと "University" で終わる "name" プロパティ値をカウントします。</span><span class="sxs-lookup"><span data-stu-id="35626-498">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="35626-499">ファイルが UTF-16 としてエンコードされ、UTF-8 にトランスコードされるものと想定します。</span><span class="sxs-lookup"><span data-stu-id="35626-499">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="35626-500">UTF-8 としてエンコードされたファイルは、次のコードを使用して、`ReadOnlySpan<byte>` に直接読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="35626-500">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="35626-501">リーダーではテキストが想定されるため、ファイルに UTF-8 バイト オーダー マーク (BOM) が含まれている場合は、バイトを `Utf8JsonReader` に渡す前にそれを削除します。</span><span class="sxs-lookup"><span data-stu-id="35626-501">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="35626-502">そうしないと、BOM は無効な JSON と見なされ、リーダーによって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-502">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="35626-503">上記のコードで読み取ることができる JSON のサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="35626-503">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="35626-504">結果として生成される概要メッセージは、"2 out of 4 have names that end with 'University'" です。</span><span class="sxs-lookup"><span data-stu-id="35626-504">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="35626-505">Utf8JsonReader を使用してストリームから読み取る</span><span class="sxs-lookup"><span data-stu-id="35626-505">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="35626-506">大きなファイル (ギガバイト以上のサイズなど) を読み取る場合、一度にファイル全体をメモリに読み込む必要を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="35626-506">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="35626-507">このシナリオでは、<xref:System.IO.FileStream> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="35626-507">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="35626-508">`Utf8JsonReader` を使用してストリームから読み取る場合、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="35626-508">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="35626-509">部分的な JSON ペイロードが格納されるバッファーは、リーダーが処理を進めることができるように、少なくともその中で最大の JSON トークンと同じ大きさにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="35626-509">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="35626-510">バッファーは、少なくとも JSON 内の空白の最大シーケンスと同じ大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="35626-510">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="35626-511">リーダーでは、JSON ペイロード内の次の <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> が完全に読み取られるまで、読み取られたデータが追跡されません。</span><span class="sxs-lookup"><span data-stu-id="35626-511">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="35626-512">そのため、バッファー内にバイトが残っている場合は、再びリーダーに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="35626-512">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="35626-513"><xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> を使用して、残っているバイト数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="35626-513">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="35626-514">次のコードは、ストリームから読み取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="35626-514">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="35626-515">この例は、<xref:System.IO.MemoryStream> を示しています。</span><span class="sxs-lookup"><span data-stu-id="35626-515">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="35626-516">同様のコードが <xref:System.IO.FileStream> で機能しますが、開始時に UTF-8 BOM が `FileStream` に含まれている場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="35626-516">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="35626-517">その場合は、残りのバイトを `Utf8JsonReader` に渡す前に、バッファーからこれらの 3 バイトを取り除く必要があります。</span><span class="sxs-lookup"><span data-stu-id="35626-517">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="35626-518">そうしないと、BOM は JSON の有効な部分と見なされないため、リーダーによって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35626-518">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="35626-519">このサンプル コードでは、4 KB のバッファーから開始し、サイズが完全な JSON トークンに対応するのに十分な大きさではないことが判明するたびにバッファー サイズを 2 倍にします。これは、リーダーが JSON ペイロードの処理を進めるために必要です。</span><span class="sxs-lookup"><span data-stu-id="35626-519">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="35626-520">スニペットに用意されている JSON サンプルでは、非常に小さい初期バッファー サイズ (たとえば、10 バイト) を設定した場合にのみ、バッファー サイズが増加します。</span><span class="sxs-lookup"><span data-stu-id="35626-520">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="35626-521">初期バッファー サイズを 10 に設定すると、`Console.WriteLine` ステートメントによって、バッファー サイズの増加の原因と影響が示されます。</span><span class="sxs-lookup"><span data-stu-id="35626-521">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="35626-522">4 KB の初期バッファー サイズで、サンプルの JSON 全体が各 `Console.WriteLine` によって表示され、バッファー サイズを増やす必要はありません。</span><span class="sxs-lookup"><span data-stu-id="35626-522">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="35626-523">前の例では、バッファーを拡大できる最大の大きさを無制限に設定しています。</span><span class="sxs-lookup"><span data-stu-id="35626-523">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="35626-524">トークン サイズが大きすぎる場合、コードは <xref:System.OutOfMemoryException> 例外で失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35626-524">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="35626-525">これは、JSON にサイズが約 1 GB 以上のトークンが含まれている場合に発生する可能性があります。1 GB のサイズを 2 倍にすると、サイズが大きすぎて `int32` バッファーに入り切らないためです。</span><span class="sxs-lookup"><span data-stu-id="35626-525">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="35626-526">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="35626-526">Additional resources</span></span>

* [<span data-ttu-id="35626-527">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="35626-527">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="35626-528">カスタム コンバーターを記述する方法</span><span class="sxs-lookup"><span data-stu-id="35626-528">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="35626-529">Newtonsoft.Json から移行する方法</span><span class="sxs-lookup"><span data-stu-id="35626-529">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="35626-530">System.Text.Json での DateTime と DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="35626-530">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="35626-531">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="35626-531">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
