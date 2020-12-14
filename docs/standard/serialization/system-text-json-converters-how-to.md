---
title: JSON シリアル化のためのカスタム コンバーターを作成する方法 - .NET
description: System.Text.Json 名前空間で提供される JSON シリアル化クラス用のカスタム コンバーターを作成する方法について説明します。
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 33334ccd8bad4ac5a9f5dccde79ff3ae09ca8f89
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008865"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="89b4f-103">.NET で JSON シリアル化 (マーシャリング) のためのカスタム コンバーターを作成する方法</span><span class="sxs-lookup"><span data-stu-id="89b4f-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="89b4f-104">この記事では、<xref:System.Text.Json> 名前空間で提供される JSON シリアル化クラス用のカスタム コンバーターを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="89b4f-105">`System.Text.Json` の概要については、[.NET で JSON のシリアル化と逆シリアル化を行う方法](system-text-json-how-to.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b4f-105">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="89b4f-106">"*コンバーター*" は、オブジェクトまたは値を JSON との間で双方向に変換するクラスです。</span><span class="sxs-lookup"><span data-stu-id="89b4f-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="89b4f-107">`System.Text.Json` 名前空間には、JavaScript のプリミティブに対応するほとんどのプリミティブ型に対して、組み込みのコンバーターがあります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-107">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="89b4f-108">次の目的で、カスタム コンバーターを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-108">You can write custom converters:</span></span>

* <span data-ttu-id="89b4f-109">組み込みコンバーターの既定の動作をオーバーライドするため。</span><span class="sxs-lookup"><span data-stu-id="89b4f-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="89b4f-110">たとえば、`DateTime` の値を、mm/dd/yyyy の形式で表したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format.</span></span> <span data-ttu-id="89b4f-111">既定では、RFC 3339 プロファイルを含め、ISO 8601-1:2019 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="89b4f-111">By default, ISO 8601-1:2019 is supported, including the RFC 3339 profile.</span></span> <span data-ttu-id="89b4f-112">詳細については、「[System.Text.Json での DateTime と DateTimeOffset のサポート](../datetime/system-text-json-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b4f-112">For more information, see [DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).</span></span>
* <span data-ttu-id="89b4f-113">カスタム値型をサポートするため。</span><span class="sxs-lookup"><span data-stu-id="89b4f-113">To support a custom value type.</span></span> <span data-ttu-id="89b4f-114">たとえば、`PhoneNumber` 構造体などです。</span><span class="sxs-lookup"><span data-stu-id="89b4f-114">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="89b4f-115">また、カスタム コンバーターを作成し、現在のリリースには含まれない機能で `System.Text.Json` をカスタマイズまたは拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-115">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="89b4f-116">この記事ではこの後、次のシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-116">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="89b4f-117">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-117">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="89b4f-118">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-118">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="89b4f-119">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-119">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="89b4f-120">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-120">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="89b4f-121">[文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-121">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="89b4f-122">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-122">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="89b4f-123">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-123">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

<span data-ttu-id="89b4f-124">カスタム コンバーター用に作成したコードでは、新しい <xref:System.Text.Json.JsonSerializerOptions> インスタンスを使用することによってパフォーマンスが大幅に低下することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="89b4f-124">In the code you write for a custom converter, be aware of the substantial performance penalty for using new <xref:System.Text.Json.JsonSerializerOptions> instances.</span></span> <span data-ttu-id="89b4f-125">詳細については、[JsonSerializerOptions インスタンスの再利用](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b4f-125">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="89b4f-126">カスタム コンバーターのパターン</span><span class="sxs-lookup"><span data-stu-id="89b4f-126">Custom converter patterns</span></span>

<span data-ttu-id="89b4f-127">カスタム コンバーターの作成には、基本パターンとファクトリ パターンという 2 つのパターンがあります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-127">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="89b4f-128">ファクトリ パターンは、`Enum` 型またはオープン ジェネリックを処理するコンバーター用です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-128">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="89b4f-129">基本パターンは、非ジェネリック型およびクローズ ジェネリック型用です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-129">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="89b4f-130">たとえば、次のような型のコンバーターには、ファクトリ パターンが必要です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-130">For example, converters for the following types require the factory pattern:</span></span>

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

<span data-ttu-id="89b4f-131">基本パターンで処理できる型の例としては、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-131">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

<span data-ttu-id="89b4f-132">基本パターンでは、1 つの型を処理できるクラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-132">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="89b4f-133">ファクトリ パターンによって作成されるクラスの場合は、実行時に必要な特定の型が決定されて、適切なコンバーターが動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-133">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="89b4f-134">基本コンバーターのサンプル</span><span class="sxs-lookup"><span data-stu-id="89b4f-134">Sample basic converter</span></span>

<span data-ttu-id="89b4f-135">次のサンプルは、既存のデータ型に対する既定のシリアル化をオーバーライドするコンバーターです。</span><span class="sxs-lookup"><span data-stu-id="89b4f-135">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="89b4f-136">そのコンバーターでは、`DateTimeOffset` のプロパティに対して mm/dd/yyyy の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-136">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="89b4f-137">ファクトリ パターン コンバーターのサンプル</span><span class="sxs-lookup"><span data-stu-id="89b4f-137">Sample factory pattern converter</span></span>

<span data-ttu-id="89b4f-138">次のコードでは、`Dictionary<Enum,TValue>` で動作するカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-138">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="89b4f-139">そのコードは、1 番目のジェネリック型パラメーターが `Enum` で、2 番目がオープンであるため、ファクトリ パターンに従います。</span><span class="sxs-lookup"><span data-stu-id="89b4f-139">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="89b4f-140">`CanConvert` メソッドでは、2 つのジェネリック パラメーターを持つ `Dictionary` に対してのみ `true` が返されます。最初のパラメーターは `Enum` 型です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-140">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="89b4f-141">内部のコンバーターでは、実行時に `TValue` に対して提供される任意の型を処理するために、既存のコンバーターが取得されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-141">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="89b4f-142">上記のコードは、後の「[文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)」で示されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="89b4f-142">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="89b4f-143">基本パターンに従うための手順</span><span class="sxs-lookup"><span data-stu-id="89b4f-143">Steps to follow the basic pattern</span></span>

<span data-ttu-id="89b4f-144">次の手順では、基本パターンに従ってコンバーターを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-144">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="89b4f-145"><xref:System.Text.Json.Serialization.JsonConverter%601> から派生するクラスを作成します。`T` は、シリアル化および逆シリアル化される型です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-145">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="89b4f-146">受信した JSON を逆シリアル化して `T` 型に変換するように、`Read` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-146">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="89b4f-147">JSON を読み取るには、メソッドに渡される <xref:System.Text.Json.Utf8JsonReader> を使用します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-147">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="89b4f-148">受信した `T` 型のオブジェクトをシリアル化するように、`Write` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-148">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="89b4f-149">JSON を書き込むには、メソッドに渡される <xref:System.Text.Json.Utf8JsonWriter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-149">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="89b4f-150">`CanConvert` メソッドは、必要な場合にのみオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-150">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="89b4f-151">変換する型が `T` 型である場合、既定の実装では `true` が返されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-151">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="89b4f-152">したがって、`T` 型だけをサポートするコンバーターでは、このメソッドをオーバーライドする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-152">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="89b4f-153">このメソッドをオーバーライドする必要があるコンバーターの例については、後の「[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b4f-153">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="89b4f-154">カスタム コンバーターを作成するための参考の実装として、[組み込みコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/)を参照できます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-154">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="89b4f-155">ファクトリ パターンに従うための手順</span><span class="sxs-lookup"><span data-stu-id="89b4f-155">Steps to follow the factory pattern</span></span>

<span data-ttu-id="89b4f-156">次の手順では、ファクトリ パターンに従ってコンバーターを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-156">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="89b4f-157"><xref:System.Text.Json.Serialization.JsonConverterFactory> から派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-157">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="89b4f-158">変換する型がコンバーターで処理できる型である場合は true を返すように、`CanConvert` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-158">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="89b4f-159">たとえば、コンバーターが `List<T>` 用の場合は、`List<int>`、`List<string>`、`List<DateTime>` だけを処理できます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-159">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="89b4f-160">実行時に提供される変換対象の型を処理するコンバーター クラスのインスタンスを返すように、`CreateConverter` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-160">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="89b4f-161">`CreateConverter` メソッドによってインスタンス化されるコンバーター クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-161">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="89b4f-162">オブジェクトと文字列を双方向に変換するコードは、すべての型に対して同じではないため、オープン ジェネリックにはファクトリ パターンが必要です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-162">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="89b4f-163">オープン ジェネリック型 (`List<T>` など) 用のコンバーターでは、背後にあるクローズ ジェネリック型 (`List<DateTime>` など) 用のコンバーターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-163">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="89b4f-164">コンバーターで処理できる各クローズ ジェネリック型を処理するためのにコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-164">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="89b4f-165">`Enum` 型はオープン ジェネリック型に似ています。`Enum` 用のコンバーターでは、背後にある特定の `Enum` (`WeekdaysEnum` など) に対するコンバーターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-165">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="89b4f-166">エラー処理</span><span class="sxs-lookup"><span data-stu-id="89b4f-166">Error handling</span></span>

<span data-ttu-id="89b4f-167">シリアライザーは、<xref:System.Text.Json.JsonException> および <xref:System.NotSupportedException> の例外の種類を特別に処理します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-167">The serializer provides special handling for exception types <xref:System.Text.Json.JsonException> and <xref:System.NotSupportedException>.</span></span>

### <a name="jsonexception"></a><span data-ttu-id="89b4f-168">JsonException</span><span class="sxs-lookup"><span data-stu-id="89b4f-168">JsonException</span></span>

<span data-ttu-id="89b4f-169">メッセージなしで `JsonException` をスローする場合、シリアライザーがそのエラーの原因となった JSON の部分へのパスを含むメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-169">If you throw a `JsonException` without a message, the serializer creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="89b4f-170">たとえば、`throw new JsonException()` というステートメントでは、次の例のようなエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-170">For example, the statement `throw new JsonException()` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="89b4f-171">メッセージを指定した場合 (たとえば `throw new JsonException("Error occurred")` でも、シリアライザーは <xref:System.Text.Json.JsonException.Path>、<xref:System.Text.Json.JsonException.LineNumber>、および <xref:System.Text.Json.JsonException.BytePositionInLine> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-171">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the serializer still sets the <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber>, and <xref:System.Text.Json.JsonException.BytePositionInLine> properties.</span></span>

### <a name="notsupportedexception"></a><span data-ttu-id="89b4f-172">NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="89b4f-172">NotSupportedException</span></span>

<span data-ttu-id="89b4f-173">`NotSupportedException` をスローした場合は、メッセージには常にパス情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-173">If you throw a `NotSupportedException`, you always get the path information in the message.</span></span> <span data-ttu-id="89b4f-174">メッセージを指定すると、そのメッセージにパス情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-174">If you provide a message, the path information is appended to it.</span></span> <span data-ttu-id="89b4f-175">たとえば、`throw new NotSupportedException("Error occurred.")` というステートメントでは、次の例のようなエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-175">For example, the statement `throw new NotSupportedException("Error occurred.")` produces an error message like the following example:</span></span>

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a><span data-ttu-id="89b4f-176">どのようなときにどのような種類の例外をスローするか</span><span class="sxs-lookup"><span data-stu-id="89b4f-176">When to throw which exception type</span></span>

<span data-ttu-id="89b4f-177">JSON ペイロードに、逆シリアル化される型に無効なトークンが含まれている場合は `JsonException` をスローします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-177">When the JSON payload contains tokens that are not valid for the type being deserialized, throw a `JsonException`.</span></span>

<span data-ttu-id="89b4f-178">特定の型を許可しない場合は、`NotSupportedException` をスローします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-178">When you want to disallow certain types, throw a `NotSupportedException`.</span></span> <span data-ttu-id="89b4f-179">この例外は、サポートされていない型にシリアライザーが自動的にスローします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-179">This exception is what the serializer automatically throws for types that are not supported.</span></span> <span data-ttu-id="89b4f-180">たとえば、セキュリティ上の理由で `System.Type` はサポートされていないため、これを逆シリアル化しようとすると、`NotSupportedException` になります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-180">For example, `System.Type` is not supported for security reasons, so an attempt to deserialize it results in a `NotSupportedException`.</span></span>

<span data-ttu-id="89b4f-181">必要に応じて他の例外をスローすることもできますが、それらには JSON パス情報は自動的に含まれません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-181">You can throw other exceptions as needed, but they don't automatically include JSON path information.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="89b4f-182">カスタム コンバーターを登録する</span><span class="sxs-lookup"><span data-stu-id="89b4f-182">Register a custom converter</span></span>

<span data-ttu-id="89b4f-183">"*カスタム コンバーター*" を登録して、`Serialize` メソッドと `Deserialize` メソッドでそれが使用されるようにします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-183">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="89b4f-184">次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-184">Choose one of the following approaches:</span></span>

* <span data-ttu-id="89b4f-185">コンバーター クラスのインスタンスを <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-185">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="89b4f-186">カスタム コンバーターを必要とするプロパティに、[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-186">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="89b4f-187">カスタム値型を表すクラスまたは構造体に、[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-187">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="89b4f-188">登録の例 - Converters コレクション</span><span class="sxs-lookup"><span data-stu-id="89b4f-188">Registration sample - Converters collection</span></span>

<span data-ttu-id="89b4f-189"><xref:System.ComponentModel.DateTimeOffsetConverter> を <xref:System.DateTimeOffset> 型のプロパティの既定値にする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-189">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

<span data-ttu-id="89b4f-190">次の型のインスタンスをシリアル化するとします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-190">Suppose you serialize an instance of the following type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="89b4f-191">カスタム コンバーターが使用されたことを示す JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-191">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="89b4f-192">次のコードでは、同じ方法を使用し、カスタム `DateTimeOffset` コンバーターを使用して逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-192">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="89b4f-193">登録の例 - [JsonConverter] プロパティ</span><span class="sxs-lookup"><span data-stu-id="89b4f-193">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="89b4f-194">次のコードでは、`Date` プロパティのカスタム コンバーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-194">The following code selects a custom converter for the `Date` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

<span data-ttu-id="89b4f-195">`WeatherForecastWithConverterAttribute` をシリアル化するコードでは、`JsonSerializeOptions.Converters` を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-195">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

<span data-ttu-id="89b4f-196">逆シリアル化するコードでも、`Converters` を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-196">The code to deserialize also doesn't require the use of `Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="89b4f-197">登録の例 - 型での [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="89b4f-197">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="89b4f-198">構造体を作成し、それに `[JsonConverter]` 属性を適用するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-198">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

<span data-ttu-id="89b4f-199">上記の構造体のカスタム コンバーターは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-199">Here's the custom converter for the preceding struct:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

<span data-ttu-id="89b4f-200">構造体の `[JsonConvert]` 属性では、`Temperature` 型のプロパティに対する既定値としてカスタム コンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-200">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="89b4f-201">次の型の `TemperatureCelsius` プロパティでは、シリアル化または逆シリアル化のときに、コンバーターが自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-201">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a><span data-ttu-id="89b4f-202">コンバーターの登録の優先順位</span><span class="sxs-lookup"><span data-stu-id="89b4f-202">Converter registration precedence</span></span>

<span data-ttu-id="89b4f-203">シリアル化または逆シリアル化のとき、コンバーターは各 JSON 要素に対して次の順序 (優先度が高い順) で選択されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-203">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="89b4f-204">`[JsonConverter]` がプロパティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-204">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="89b4f-205">`Converters` コレクションにコンバーターが追加されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-205">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="89b4f-206">`[JsonConverter]` がカスタム値型または POCO に適用されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-206">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="89b4f-207">1 つの型に対して複数のカスタム コンバーターが `Converters` コレクションに登録されている場合は、`CanConvert` に対して true を返す最初のコンバーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-207">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="89b4f-208">適用可能なカスタム コンバーターが登録されていない場合にのみ、組み込みコンバーターが選択されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-208">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="89b4f-209">一般的なシナリオでのコンバーターの例</span><span class="sxs-lookup"><span data-stu-id="89b4f-209">Converter samples for common scenarios</span></span>

<span data-ttu-id="89b4f-210">以下のセクションでは、組み込み機能では処理されない一般的なシナリオに対処するコンバーターの例を示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-210">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="89b4f-211">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-211">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="89b4f-212">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-212">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="89b4f-213">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-213">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="89b4f-214">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-214">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="89b4f-215">[文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-215">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="89b4f-216">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-216">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="89b4f-217">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-217">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="89b4f-218">推論された型をオブジェクトのプロパティに逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="89b4f-218">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="89b4f-219">`object` 型のプロパティに逆シリアル化すると、`JsonElement` オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-219">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="89b4f-220">その理由は、逆シリアライザーでは、作成する CLR 型がわからず、推測が試みられないためです。</span><span class="sxs-lookup"><span data-stu-id="89b4f-220">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="89b4f-221">たとえば、JSON プロパティが "true" である場合、逆シリアライザーでは値が `Boolean` であることは推定されません。また、要素が "01/01/2019" である場合、逆シリアライザーではそれが `DateTime` であることは推定されません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-221">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="89b4f-222">型の推定は不正確になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-222">Type inference can be inaccurate.</span></span> <span data-ttu-id="89b4f-223">逆シリアライザーで、小数点を含まない JSON の数値が `long` と解析された場合、値がもともと `ulong` または `BigInteger` としてシリアル化されていたとすると、範囲外の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-223">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="89b4f-224">数値がもともと `decimal` としてシリアル化されていた場合、小数点を含む数値が `double` と解析されると、精度が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-224">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="89b4f-225">次のコードでは、型の推定が必要なシナリオでの、`object` プロパティに対するカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-225">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="89b4f-226">次のような変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-226">The code converts:</span></span>

* <span data-ttu-id="89b4f-227">`true` と `false` は `Boolean` に</span><span class="sxs-lookup"><span data-stu-id="89b4f-227">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="89b4f-228">小数点を含まない数値は `long` に</span><span class="sxs-lookup"><span data-stu-id="89b4f-228">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="89b4f-229">小数点を含む数値は `double` に</span><span class="sxs-lookup"><span data-stu-id="89b4f-229">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="89b4f-230">日付は `DateTime` に</span><span class="sxs-lookup"><span data-stu-id="89b4f-230">Dates to `DateTime`</span></span>
* <span data-ttu-id="89b4f-231">文字列は `string` に</span><span class="sxs-lookup"><span data-stu-id="89b4f-231">Strings to `string`</span></span>
* <span data-ttu-id="89b4f-232">それ以外はすべて `JsonElement` に</span><span class="sxs-lookup"><span data-stu-id="89b4f-232">Everything else to `JsonElement`</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

<span data-ttu-id="89b4f-233">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-233">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

<span data-ttu-id="89b4f-234">`object` プロパティを含む型の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-234">Here's an example type with `object` properties:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

<span data-ttu-id="89b4f-235">次の逆シリアル化を行う JSON の例には、`DateTime`、`long`、`string` として逆シリアル化される値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="89b4f-235">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="89b4f-236">カスタム コンバーターを使用しないと、逆シリアル化によって各プロパティに `JsonElement` が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-236">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="89b4f-237">`System.Text.Json.Serialization` 名前空間の[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、`object` プロパティへの逆シリアル化を処理するカスタム コンバーターの例がさらにあります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-237">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="89b4f-238">文字列以外のキーでディクショナリをサポートする</span><span class="sxs-lookup"><span data-stu-id="89b4f-238">Support Dictionary with non-string key</span></span>

<span data-ttu-id="89b4f-239">ディクショナリ コレクションに対する組み込みのサポートは `Dictionary<string, TValue>` 用です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-239">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="89b4f-240">つまり、キーは文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-240">That is, the key must be a string.</span></span> <span data-ttu-id="89b4f-241">キーが整数または他の型であるディクショナリをサポートするには、カスタム コンバーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-241">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="89b4f-242">次のコードでは、`Dictionary<Enum,TValue>` で動作するカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-242">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="89b4f-243">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-243">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

<span data-ttu-id="89b4f-244">このコンバーターでは、次の `Enum` を使用する次のクラスの `TemperatureRanges` プロパティをシリアル化および逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-244">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

<span data-ttu-id="89b4f-245">シリアル化からの JSON 出力は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-245">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="89b4f-246">`System.Text.Json.Serialization` 名前空間の[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、文字列以外のキーのディクショナリを処理するカスタム コンバーターの例がさらにあります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-246">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="89b4f-247">ポリモーフィックな逆シリアル化をサポートする</span><span class="sxs-lookup"><span data-stu-id="89b4f-247">Support polymorphic deserialization</span></span>

<span data-ttu-id="89b4f-248">組み込み機能では、[ポリモーフィックなシリアル化](system-text-json-polymorphism.md)は限られた範囲で提供されていますが、逆シリアル化はまったくサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-248">Built-in features provide a limited range of [polymorphic serialization](system-text-json-polymorphism.md) but no support for deserialization at all.</span></span> <span data-ttu-id="89b4f-249">逆シリアル化を行うには、カスタム コンバーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-249">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="89b4f-250">たとえば、抽象基底クラス `Person` と、派生クラス `Employee` および `Customer` があるとします。</span><span class="sxs-lookup"><span data-stu-id="89b4f-250">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="89b4f-251">ポリモーフィックな逆シリアル化とは、デザイン時に逆シリアル化ターゲットとして `Person` を指定すると、実行時に JSON 内の `Customer` オブジェクトと `Employee` オブジェクトが正しく逆シリアル化されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-251">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="89b4f-252">逆シリアル化の間に、JSON で必要な型を識別する手掛かりを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-252">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="89b4f-253">使用できる手掛かりの種類は、シナリオによって異なります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-253">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="89b4f-254">たとえば、識別子プロパティを使用できる場合や、特定のプロパティの有無に依存しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-254">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="89b4f-255">`System.Text.Json` の現在のリリースでは、ポリモーフィックな逆シリアル化のシナリオを処理する方法を指定する属性が提供されていないため、カスタム コンバーターが必要になります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-255">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="89b4f-256">次のコードでは、基底クラス、2 つの派生クラス、およびそれらのカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-256">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="89b4f-257">コンバーターでは、識別子プロパティを使用して、ポリモーフィックな逆シリアル化を行います。</span><span class="sxs-lookup"><span data-stu-id="89b4f-257">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="89b4f-258">型の識別子はクラス定義には含まれていませんが、シリアル化の間に作成され、逆シリアル化の間に読み取られます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-258">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

<span data-ttu-id="89b4f-259">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-259">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

<span data-ttu-id="89b4f-260">コンバーターでは、次のように、同じコンバーターを使用してシリアル化することによって作成された JSON を逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-260">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

<span data-ttu-id="89b4f-261">前の例のコンバーターのコードでは、各プロパティの読み取りと書き込みを手動で行います。</span><span class="sxs-lookup"><span data-stu-id="89b4f-261">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="89b4f-262">別の方法として、`Deserialize` または `Serialize` を呼び出すことにより、一部の作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-262">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="89b4f-263">例としては、[こちらの StackOverflow の投稿](https://stackoverflow.com/a/59744873/12509023)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b4f-263">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="89b4f-264">Stack\<T> のラウンド トリップをサポートする</span><span class="sxs-lookup"><span data-stu-id="89b4f-264">Support round trip for Stack\<T></span></span>

<span data-ttu-id="89b4f-265">JSON 文字列を <xref:System.Collections.Generic.Stack%601> オブジェクトに逆シリアル化した後、そのオブジェクトをシリアル化した場合、スタックの内容は逆の順序になります。</span><span class="sxs-lookup"><span data-stu-id="89b4f-265">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="89b4f-266">この動作は、次の型とインターフェイス、およびそれらから派生するユーザー定義型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-266">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="89b4f-267">スタックの元の順序を維持するシリアル化と逆シリアル化をサポートするには、カスタム コンバーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="89b4f-267">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="89b4f-268">次のコードでは、`Stack<T>` オブジェクトとの間でのラウンドトリップを可能にするカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-268">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

<span data-ttu-id="89b4f-269">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-269">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a><span data-ttu-id="89b4f-270">null 値を処理する</span><span class="sxs-lookup"><span data-stu-id="89b4f-270">Handle null values</span></span>

<span data-ttu-id="89b4f-271">既定では、null 値はシリアライザーにより次のように処理されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-271">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="89b4f-272">参照型と <xref:System.Nullable%601> 型の場合:</span><span class="sxs-lookup"><span data-stu-id="89b4f-272">For reference types and <xref:System.Nullable%601> types:</span></span>

  * <span data-ttu-id="89b4f-273">シリアル化のときにカスタム コンバーターに `null` は渡されません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-273">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="89b4f-274">逆シリアル化のときにカスタム コンバーターに `JsonTokenType.Null` は渡されません。</span><span class="sxs-lookup"><span data-stu-id="89b4f-274">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="89b4f-275">逆シリアル化では `null` インスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-275">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="89b4f-276">シリアル化ではライターを使用して `null` が直接書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-276">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="89b4f-277">null 非許容値型の場合:</span><span class="sxs-lookup"><span data-stu-id="89b4f-277">For non-nullable value types:</span></span>

  * <span data-ttu-id="89b4f-278">逆シリアル化のときにカスタム コンバーターに `JsonTokenType.Null` が渡されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-278">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="89b4f-279">(カスタム コンバーターが使用できない場合は、その型の内部コンバーターによって `JsonException` 例外がスローされます)。</span><span class="sxs-lookup"><span data-stu-id="89b4f-279">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="89b4f-280">この null 処理動作は、主に、コンバーターの余分な呼び出しをスキップすることでパフォーマンスを最適化するためのものです。</span><span class="sxs-lookup"><span data-stu-id="89b4f-280">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="89b4f-281">また、すべての `Read` および `Write` メソッドのオーバーライドの開始時に、null 許容型のコンバーターで `null` のチェックを強制的に行うことが回避されます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-281">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="89b4f-282">カスタム コンバーターで参照型または値型の `null` を処理できるようにするには、次の例で示すように、<xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> をオーバーライドして `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="89b4f-282">To enable a custom converter to handle `null` for a reference or value type, override <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="89b4f-283">他のカスタム コンバーターのサンプル</span><span class="sxs-lookup"><span data-stu-id="89b4f-283">Other custom converter samples</span></span>

<span data-ttu-id="89b4f-284">[Newtonsoft.Json から System.Text.Json への移行](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事には、カスタム コンバーターの他のサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89b4f-284">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="89b4f-285">`System.Text.Json.Serialization` のソース コードの[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、次のような他のカスタム コンバーターのサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89b4f-285">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="89b4f-286">[逆シリアル化時に null を 0 に変換する Int32 コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="89b4f-286">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="89b4f-287">[逆シリアル化時に文字列値と数値の両方に対応できる Int32 コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="89b4f-287">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="89b4f-288">[Enum コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="89b4f-288">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="89b4f-289">[外部データを受け入れる List\<T> コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="89b4f-289">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="89b4f-290">[コンマ区切りの数値リストを処理する Long[] コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="89b4f-290">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="89b4f-291">既存の組み込みコンバーターの動作を変更するコンバーターを作成する必要がある場合は、[既存のコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)を入手し、それを基にしてカスタマイズを始めることができ ます。</span><span class="sxs-lookup"><span data-stu-id="89b4f-291">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="89b4f-292">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="89b4f-292">Additional resources</span></span>

* <span data-ttu-id="89b4f-293">[組み込みコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="89b4f-293">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="89b4f-294">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="89b4f-294">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="89b4f-295">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="89b4f-295">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="89b4f-296">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="89b4f-296">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="89b4f-297">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="89b4f-297">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="89b4f-298">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="89b4f-298">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="89b4f-299">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="89b4f-299">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="89b4f-300">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="89b4f-300">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="89b4f-301">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="89b4f-301">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="89b4f-302">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="89b4f-302">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="89b4f-303">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="89b4f-303">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="89b4f-304">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="89b4f-304">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="89b4f-305">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="89b4f-305">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="89b4f-306">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="89b4f-306">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="89b4f-307">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="89b4f-307">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="89b4f-308">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="89b4f-308">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="89b4f-309">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="89b4f-309">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="89b4f-310">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="89b4f-310">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
