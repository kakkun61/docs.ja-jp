---
title: C# を使用して JSON をシリアル化および逆シリアル化する方法 - .NET
description: System.Text.Json 名前空間を使用して .NET 内で JSON のシリアル化と逆シリアル化を行う方法について学習します。 サンプル コードが含まれています。
ms.date: 12/02/2020
ms.custom: contperfq2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1ea4ff71b9e21bd7c5b12598581b33e1e96ebb19
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008839"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="90a0c-104">.NET 内で JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリングの解除) を行う方法</span><span class="sxs-lookup"><span data-stu-id="90a0c-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="90a0c-105">この記事では、<xref:System.Text.Json?displayProperty=fullName> 名前空間を使用して JavaScript Object Notation (JSON) のシリアル化と逆シリアル化を行う方法について示します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="90a0c-106">`Newtonsoft.Json` から既存のコードを移植する場合は、[`System.Text.Json` に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90a0c-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="90a0c-107">指示とサンプル コードでは、ライブラリを [ASP.NET Core](/aspnet/core/) などのフレームワーク経由ではなく直接使用します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="90a0c-108">シリアル化のサンプル コードの大部分では、JSON を "整形" するために <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します (人間が読みやすいようにインデントと空白文字が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="90a0c-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="90a0c-109">実稼働環境で使用する場合、通常、この設定には既定値の `false` をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="90a0c-110">コード例では、次のクラスとそのバリアントを参照しています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="namespaces"></a><span data-ttu-id="90a0c-111">名前空間</span><span class="sxs-lookup"><span data-stu-id="90a0c-111">Namespaces</span></span>

<span data-ttu-id="90a0c-112"><xref:System.Text.Json> 名前空間には、すべてのエントリ ポイントと主要な型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="90a0c-113"><xref:System.Text.Json.Serialization> 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="90a0c-114">この記事に示されているコード例では、次のいずれかまたは両方の名前空間に `using` ディレクティブが必要です。</span><span class="sxs-lookup"><span data-stu-id="90a0c-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <span data-ttu-id="90a0c-115"><xref:System.Runtime.Serialization> 名前空間の属性は、`System.Text.Json` ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="90a0c-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="90a0c-116">.NET オブジェクトを JSON として書き込む方法 (シリアル化)</span><span class="sxs-lookup"><span data-stu-id="90a0c-116">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="90a0c-117">JSON を文字列またはファイルに書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="90a0c-118">次の例では、JSON を文字列として作成します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-118">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

<span data-ttu-id="90a0c-119">次の例では、同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-119">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

<span data-ttu-id="90a0c-120">次の例では、非同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-120">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

<span data-ttu-id="90a0c-121">前の例では、シリアル化する型に型の推定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="90a0c-122">`Serialize()` のオーバーロードでは、ジェネリック型パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="90a0c-123">シリアル化の例</span><span class="sxs-lookup"><span data-stu-id="90a0c-123">Serialization example</span></span>

<span data-ttu-id="90a0c-124">コレクション型のプロパティとユーザー定義型を含むクラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="90a0c-125">"POCO" は、[Plain Old CLR Object (単純な従来の CLR オブジェクト)](https://en.wikipedia.org/wiki/Plain_old_CLR_object) を表します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="90a0c-126">POCO は、継承や属性からなど、フレームワーク固有の型に依存しない .NET 型です。</span><span class="sxs-lookup"><span data-stu-id="90a0c-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="90a0c-127">前の型のインスタンスをシリアル化した場合の JSON 出力は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="90a0c-128">既定では、JSON 出力は縮小されます (空白、インデント、および改行文字が削除されます)。</span><span class="sxs-lookup"><span data-stu-id="90a0c-128">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="90a0c-129">次の例では、同じ JSON ですが、書式設定されているもの (空白とインデントで整形されています) を示しています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

## <a name="serialize-to-utf-8"></a><span data-ttu-id="90a0c-130">UTF-8 にシリアル化する</span><span class="sxs-lookup"><span data-stu-id="90a0c-130">Serialize to UTF-8</span></span>

<span data-ttu-id="90a0c-131">UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<span data-ttu-id="90a0c-132"><xref:System.Text.Json.Utf8JsonWriter> を受け取る <xref:System.Text.Json.JsonSerializer.Serialize%2A> オーバーロードも使用できます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="90a0c-133">UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約 5-10% 高速です。</span><span class="sxs-lookup"><span data-stu-id="90a0c-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="90a0c-134">違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないことから生じます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="90a0c-135">シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="90a0c-135">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="90a0c-136">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="90a0c-137">[無視するプロパティを指定する](system-text-json-ignore-properties.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-137">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="90a0c-138">[既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="90a0c-139">既定では、JSON は縮小されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-139">By default, JSON is minified.</span></span> <span data-ttu-id="90a0c-140">[JSON を整形](#serialize-to-formatted-json)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="90a0c-141">既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="90a0c-142">[JSON 名の大文字と小文字の区別をカスタマイズ](system-text-json-customize-properties.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-142">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="90a0c-143">既定では、循環参照が検出され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="90a0c-144">[参照を保持し、循環参照を処理する](system-text-json-preserve-references.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-144">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="90a0c-145">既定では、[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="90a0c-146">[フィールドを含める](#include-fields)ことができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="90a0c-147">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="90a0c-148">詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90a0c-148">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="90a0c-149">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="90a0c-150">[無視するプロパティを指定する](system-text-json-ignore-properties.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-150">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="90a0c-151">[既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="90a0c-152">既定では、JSON は縮小されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-152">By default, JSON is minified.</span></span> <span data-ttu-id="90a0c-153">[JSON を整形](#serialize-to-formatted-json)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="90a0c-154">既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="90a0c-155">[JSON 名の大文字と小文字の区別をカスタマイズ](system-text-json-customize-properties.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-155">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="90a0c-156">循環参照が検出され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="90a0c-157">[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="90a0c-158">サポートされる型には次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="90a0c-159">数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。</span><span class="sxs-lookup"><span data-stu-id="90a0c-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="90a0c-160">ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="90a0c-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="90a0c-161">1 次元配列とジャグ配列 (`T[][]`)。</span><span class="sxs-lookup"><span data-stu-id="90a0c-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="90a0c-162">次の名前空間のコレクションとディクショナリ。</span><span class="sxs-lookup"><span data-stu-id="90a0c-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="90a0c-163">数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。</span><span class="sxs-lookup"><span data-stu-id="90a0c-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="90a0c-164">ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="90a0c-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="90a0c-165">1 次元配列とジャグ配列 (`ArrayName[][]`)。</span><span class="sxs-lookup"><span data-stu-id="90a0c-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="90a0c-166">`Dictionary<string,TValue>`。`TValue` は `object`、`JsonElement`、または POCO です。</span><span class="sxs-lookup"><span data-stu-id="90a0c-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="90a0c-167">次の名前空間からのコレクション。</span><span class="sxs-lookup"><span data-stu-id="90a0c-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="90a0c-168">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、追加の型を処理したり、組み込みコンバーターではサポートされていない機能を提供したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="90a0c-169">JSON を .NET オブジェクトとして読み取る方法 (逆シリアル化)</span><span class="sxs-lookup"><span data-stu-id="90a0c-169">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="90a0c-170">文字列またはファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="90a0c-171">次の例では、文字列から JSON を読み取り、前に[シリアル化の例](#serialization-example)で示した `WeatherForecastWithPOCOs` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

<span data-ttu-id="90a0c-172">同期コードを使用してファイルから逆シリアル化するには、次の例に示すように、ファイルを文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

<span data-ttu-id="90a0c-173">非同期コードを使用してファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="90a0c-174">UTF-8 からの逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="90a0c-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="90a0c-175">UTF-8 から逆シリアル化するには、次の例に示すように、`ReadOnlySpan<byte>` または `Utf8JsonReader` を受け取る <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> オーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="90a0c-176">この例では、JSON が jsonUtf8Bytes という名前のバイト配列内にあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="90a0c-177">逆シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="90a0c-177">Deserialization behavior</span></span>

<span data-ttu-id="90a0c-178">JSON を逆シリアル化する場合、次の動作が適用されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="90a0c-179">既定では、プロパティ名の照合では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="90a0c-180">[大文字と小文字を区別しないことを指定](system-text-json-character-casing.md)できます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-180">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="90a0c-181">JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="90a0c-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="90a0c-182">非パブリック コンストラクターはシリアライザーにより無視されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="90a0c-183">不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="90a0c-184">「[不変の型とレコード](system-text-json-immutability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90a0c-184">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="90a0c-185">既定では、列挙型は数値としてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="90a0c-186">[列挙型名を文字列としてシリアル化](system-text-json-customize-properties.md#enums-as-strings)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-186">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="90a0c-187">既定では、フィールドは無視されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-187">By default, fields are ignored.</span></span> <span data-ttu-id="90a0c-188">[フィールドを含める](#include-fields)ことができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="90a0c-189">既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="90a0c-190">[コメントと末尾のコンマを許可](system-text-json-invalid-json.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-190">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="90a0c-191">[既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。</span><span class="sxs-lookup"><span data-stu-id="90a0c-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="90a0c-192">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="90a0c-193">詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90a0c-193">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="90a0c-194">既定では、プロパティ名の照合では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="90a0c-195">[大文字と小文字を区別しないことを指定](system-text-json-character-casing.md)できます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-195">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="90a0c-196">ASP.NET Core アプリの場合、[既定では大文字と小文字を区別しないことが指定](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-196">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="90a0c-197">JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="90a0c-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="90a0c-198">逆シリアル化には、パラメーターなしのコンストラクター (public、internal、private のいずれか) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="90a0c-199">不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="90a0c-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="90a0c-200">既定では、列挙型は数値としてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="90a0c-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="90a0c-201">[列挙型名を文字列としてシリアル化](system-text-json-customize-properties.md#enums-as-strings)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-201">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="90a0c-202">フィールドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="90a0c-202">Fields aren't supported.</span></span>
* <span data-ttu-id="90a0c-203">既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="90a0c-204">[コメントと末尾のコンマを許可](system-text-json-invalid-json.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-204">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="90a0c-205">[既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。</span><span class="sxs-lookup"><span data-stu-id="90a0c-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="90a0c-206">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="90a0c-207">詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90a0c-207">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="90a0c-208">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、組み込みコンバーターではサポートされていない機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="90a0c-209">書式設定された JSON へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="90a0c-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="90a0c-210">JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

<span data-ttu-id="90a0c-211">シリアル化され、整形された JSON 出力の型の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="90a0c-212">同じオプションで `JsonSerializerOptions` を繰り返し使用する場合、使用のたびに新しい `JsonSerializerOptions` インスタンスを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="90a0c-212">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="90a0c-213">すべての呼び出しで同じインスタンスを再利用します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-213">Reuse the same instance for every call.</span></span> <span data-ttu-id="90a0c-214">詳細については、[JsonSerializerOptions インスタンスの再利用](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90a0c-214">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="90a0c-215">フィールドを含める</span><span class="sxs-lookup"><span data-stu-id="90a0c-215">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="90a0c-216">次の例で示されているように、シリアル化または逆シリアル化のときにフィールドを含めるには、<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> グローバル設定または [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-216">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

<span data-ttu-id="90a0c-217">読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-217">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="90a0c-218">.NET Core 3.1 では、System.Text.Json メソッドはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="90a0c-218">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="90a0c-219">この機能は、[カスタム コンバーター](system-text-json-converters-how-to.md)で提供できます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-219">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="90a0c-220">HttpClient と HttpContent の拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="90a0c-220">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="90a0c-221">ネットワークからの JSON ペイロードのシリアル化と逆シリアル化は、一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="90a0c-221">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="90a0c-222">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) および [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) の拡張メソッドを使用すると、これらの操作を 1 行のコードで実行できます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-222">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="90a0c-223">これらの拡張メソッドにおいては、[JsonSerializerOptions の Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="90a0c-223">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="90a0c-224">次の例では、<xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> と <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90a0c-224">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

<span data-ttu-id="90a0c-225">[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) には System.Text.Json 用の拡張メソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="90a0c-225">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="90a0c-226">`HttpClient` および `HttpContent` の拡張メソッドは、.NET Core 3.1 の System.Text.Json では使用できません。</span><span class="sxs-lookup"><span data-stu-id="90a0c-226">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="90a0c-227">関連項目</span><span class="sxs-lookup"><span data-stu-id="90a0c-227">See also</span></span>

* [<span data-ttu-id="90a0c-228">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="90a0c-228">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="90a0c-229">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="90a0c-229">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="90a0c-230">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="90a0c-230">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="90a0c-231">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="90a0c-231">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="90a0c-232">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="90a0c-232">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="90a0c-233">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="90a0c-233">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="90a0c-234">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="90a0c-234">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="90a0c-235">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="90a0c-235">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="90a0c-236">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="90a0c-236">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="90a0c-237">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="90a0c-237">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="90a0c-238">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="90a0c-238">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="90a0c-239">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="90a0c-239">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="90a0c-240">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="90a0c-240">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="90a0c-241">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="90a0c-241">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="90a0c-242">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="90a0c-242">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="90a0c-243">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="90a0c-243">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="90a0c-244">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="90a0c-244">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
