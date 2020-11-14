---
title: JSON シリアル化のためのカスタム コンバーターを作成する方法 - .NET
description: 'System.Text.Json 名前空間で提供される JSON シリアル化クラス用のカスタム コンバーターを作成する方法について説明します。'
ms.date: 01/10/2020
no-loc:
- 'System.Text.Json'
- 'Newtonsoft.Json'
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: ba6b61232ccf7ed493fe5809e5c0b8ba21091d3d
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329808"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="a5aaf-103">.NET で JSON シリアル化 (マーシャリング) のためのカスタム コンバーターを作成する方法</span><span class="sxs-lookup"><span data-stu-id="a5aaf-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="a5aaf-104">この記事では、<xref:System.Text.Json> 名前空間で提供される JSON シリアル化クラス用のカスタム コンバーターを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="a5aaf-105">`System.Text.Json` の概要については、[.NET で JSON のシリアル化と逆シリアル化を行う方法](system-text-json-how-to.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-105">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="a5aaf-106">" *コンバーター* " は、オブジェクトまたは値を JSON との間で双方向に変換するクラスです。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="a5aaf-107">`System.Text.Json` 名前空間には、JavaScript のプリミティブに対応するほとんどのプリミティブ型に対して、組み込みのコンバーターがあります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-107">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="a5aaf-108">次の目的で、カスタム コンバーターを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-108">You can write custom converters:</span></span>

* <span data-ttu-id="a5aaf-109">組み込みコンバーターの既定の動作をオーバーライドするため。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="a5aaf-110">たとえば、`DateTime` の値を、既定の ISO 8601-1:2019 形式ではなく、mm/dd/yyyy 形式で表すことができます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="a5aaf-111">カスタム値型をサポートするため。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-111">To support a custom value type.</span></span> <span data-ttu-id="a5aaf-112">たとえば、`PhoneNumber` 構造体などです。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-112">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="a5aaf-113">また、カスタム コンバーターを作成し、現在のリリースには含まれない機能で `System.Text.Json` をカスタマイズまたは拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-113">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="a5aaf-114">この記事ではこの後、次のシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-114">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="a5aaf-115">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-115">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="a5aaf-116">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="a5aaf-117">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="a5aaf-118">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-118">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="a5aaf-119">[文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-119">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="a5aaf-120">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-120">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="a5aaf-121">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-121">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

## <a name="custom-converter-patterns"></a><span data-ttu-id="a5aaf-122">カスタム コンバーターのパターン</span><span class="sxs-lookup"><span data-stu-id="a5aaf-122">Custom converter patterns</span></span>

<span data-ttu-id="a5aaf-123">カスタム コンバーターの作成には、基本パターンとファクトリ パターンという 2 つのパターンがあります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-123">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="a5aaf-124">ファクトリ パターンは、`Enum` 型またはオープン ジェネリックを処理するコンバーター用です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-124">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="a5aaf-125">基本パターンは、非ジェネリック型およびクローズ ジェネリック型用です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-125">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="a5aaf-126">たとえば、次のような型のコンバーターには、ファクトリ パターンが必要です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-126">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="a5aaf-127">基本パターンで処理できる型の例としては、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-127">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="a5aaf-128">基本パターンでは、1 つの型を処理できるクラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-128">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="a5aaf-129">ファクトリ パターンによって作成されるクラスの場合は、実行時に必要な特定の型が決定されて、適切なコンバーターが動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-129">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="a5aaf-130">基本コンバーターのサンプル</span><span class="sxs-lookup"><span data-stu-id="a5aaf-130">Sample basic converter</span></span>

<span data-ttu-id="a5aaf-131">次のサンプルは、既存のデータ型に対する既定のシリアル化をオーバーライドするコンバーターです。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-131">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="a5aaf-132">そのコンバーターでは、`DateTimeOffset` のプロパティに対して mm/dd/yyyy の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-132">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="a5aaf-133">ファクトリ パターン コンバーターのサンプル</span><span class="sxs-lookup"><span data-stu-id="a5aaf-133">Sample factory pattern converter</span></span>

<span data-ttu-id="a5aaf-134">次のコードでは、`Dictionary<Enum,TValue>` で動作するカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-134">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="a5aaf-135">そのコードは、1 番目のジェネリック型パラメーターが `Enum` で、2 番目がオープンであるため、ファクトリ パターンに従います。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-135">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="a5aaf-136">`CanConvert` メソッドでは、2 つのジェネリック パラメーターを持つ `Dictionary` に対してのみ `true` が返されます。最初のパラメーターは `Enum` 型です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-136">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="a5aaf-137">内部のコンバーターでは、実行時に `TValue` に対して提供される任意の型を処理するために、既存のコンバーターが取得されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-137">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="a5aaf-138">上記のコードは、後の「[文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)」で示されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-138">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="a5aaf-139">基本パターンに従うための手順</span><span class="sxs-lookup"><span data-stu-id="a5aaf-139">Steps to follow the basic pattern</span></span>

<span data-ttu-id="a5aaf-140">次の手順では、基本パターンに従ってコンバーターを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-140">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="a5aaf-141"><xref:System.Text.Json.Serialization.JsonConverter%601> から派生するクラスを作成します。`T` は、シリアル化および逆シリアル化される型です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-141">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="a5aaf-142">受信した JSON を逆シリアル化して `T` 型に変換するように、`Read` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-142">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="a5aaf-143">JSON を読み取るには、メソッドに渡される <xref:System.Text.Json.Utf8JsonReader> を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-143">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="a5aaf-144">受信した `T` 型のオブジェクトをシリアル化するように、`Write` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-144">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="a5aaf-145">JSON を書き込むには、メソッドに渡される <xref:System.Text.Json.Utf8JsonWriter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-145">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="a5aaf-146">`CanConvert` メソッドは、必要な場合にのみオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-146">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="a5aaf-147">変換する型が `T` 型である場合、既定の実装では `true` が返されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-147">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="a5aaf-148">したがって、`T` 型だけをサポートするコンバーターでは、このメソッドをオーバーライドする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-148">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="a5aaf-149">このメソッドをオーバーライドする必要があるコンバーターの例については、後の「[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-149">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="a5aaf-150">カスタム コンバーターを作成するための参考の実装として、[組み込みコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/)を参照できます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-150">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="a5aaf-151">ファクトリ パターンに従うための手順</span><span class="sxs-lookup"><span data-stu-id="a5aaf-151">Steps to follow the factory pattern</span></span>

<span data-ttu-id="a5aaf-152">次の手順では、ファクトリ パターンに従ってコンバーターを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-152">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="a5aaf-153"><xref:System.Text.Json.Serialization.JsonConverterFactory> から派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-153">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="a5aaf-154">変換する型がコンバーターで処理できる型である場合は true を返すように、`CanConvert` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-154">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="a5aaf-155">たとえば、コンバーターが `List<T>` 用の場合は、`List<int>`、`List<string>`、`List<DateTime>` だけを処理できます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-155">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="a5aaf-156">実行時に提供される変換対象の型を処理するコンバーター クラスのインスタンスを返すように、`CreateConverter` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-156">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="a5aaf-157">`CreateConverter` メソッドによってインスタンス化されるコンバーター クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-157">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="a5aaf-158">オブジェクトと文字列を双方向に変換するコードは、すべての型に対して同じではないため、オープン ジェネリックにはファクトリ パターンが必要です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-158">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="a5aaf-159">オープン ジェネリック型 (`List<T>` など) 用のコンバーターでは、背後にあるクローズ ジェネリック型 (`List<DateTime>` など) 用のコンバーターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-159">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="a5aaf-160">コンバーターで処理できる各クローズ ジェネリック型を処理するためのにコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-160">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="a5aaf-161">`Enum` 型はオープン ジェネリック型に似ています。`Enum` 用のコンバーターでは、背後にある特定の `Enum` (`WeekdaysEnum` など) に対するコンバーターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-161">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="a5aaf-162">エラー処理</span><span class="sxs-lookup"><span data-stu-id="a5aaf-162">Error handling</span></span>

<span data-ttu-id="a5aaf-163">エラー処理コードで例外をスローする必要がある場合は、メッセージを含まない <xref:System.Text.Json.JsonException> をスローすることを検討します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-163">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="a5aaf-164">この例外型では、エラーの原因となった JSON の部分へのパスを含むメッセージが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-164">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="a5aaf-165">たとえば、`throw new JsonException();` というステートメントでは、次の例のようなエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-165">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="a5aaf-166">メッセージ (`throw new JsonException("Error occurred")` など) を指定した場合でも、例外の <xref:System.Text.Json.JsonException.Path> プロパティでパスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-166">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="a5aaf-167">カスタム コンバーターを登録する</span><span class="sxs-lookup"><span data-stu-id="a5aaf-167">Register a custom converter</span></span>

<span data-ttu-id="a5aaf-168">" *カスタム コンバーター* " を登録して、`Serialize` メソッドと `Deserialize` メソッドでそれが使用されるようにします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-168">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="a5aaf-169">次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-169">Choose one of the following approaches:</span></span>

* <span data-ttu-id="a5aaf-170">コンバーター クラスのインスタンスを <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-170">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="a5aaf-171">カスタム コンバーターを必要とするプロパティに、[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-171">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="a5aaf-172">カスタム値型を表すクラスまたは構造体に、[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-172">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="a5aaf-173">登録の例 - Converters コレクション</span><span class="sxs-lookup"><span data-stu-id="a5aaf-173">Registration sample - Converters collection</span></span>

<span data-ttu-id="a5aaf-174"><xref:System.ComponentModel.DateTimeOffsetConverter> を <xref:System.DateTimeOffset> 型のプロパティの既定値にする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-174">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="a5aaf-175">次の型のインスタンスをシリアル化するとします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-175">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="a5aaf-176">カスタム コンバーターが使用されたことを示す JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-176">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="a5aaf-177">次のコードでは、同じ方法を使用し、カスタム `DateTimeOffset` コンバーターを使用して逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-177">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="a5aaf-178">登録の例 - [JsonConverter] プロパティ</span><span class="sxs-lookup"><span data-stu-id="a5aaf-178">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="a5aaf-179">次のコードでは、`Date` プロパティのカスタム コンバーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-179">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="a5aaf-180">`WeatherForecastWithConverterAttribute` をシリアル化するコードでは、`JsonSerializeOptions.Converters` を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-180">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="a5aaf-181">逆シリアル化するコードでも、`Converters` を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-181">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="a5aaf-182">登録の例 - 型での [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="a5aaf-182">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="a5aaf-183">構造体を作成し、それに `[JsonConverter]` 属性を適用するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-183">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="a5aaf-184">上記の構造体のカスタム コンバーターは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-184">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="a5aaf-185">構造体の `[JsonConvert]` 属性では、`Temperature` 型のプロパティに対する既定値としてカスタム コンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-185">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="a5aaf-186">次の型の `TemperatureCelsius` プロパティでは、シリアル化または逆シリアル化のときに、コンバーターが自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-186">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="a5aaf-187">コンバーターの登録の優先順位</span><span class="sxs-lookup"><span data-stu-id="a5aaf-187">Converter registration precedence</span></span>

<span data-ttu-id="a5aaf-188">シリアル化または逆シリアル化のとき、コンバーターは各 JSON 要素に対して次の順序 (優先度が高い順) で選択されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-188">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="a5aaf-189">`[JsonConverter]` がプロパティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-189">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="a5aaf-190">`Converters` コレクションにコンバーターが追加されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-190">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="a5aaf-191">`[JsonConverter]` がカスタム値型または POCO に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-191">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="a5aaf-192">1 つの型に対して複数のカスタム コンバーターが `Converters` コレクションに登録されている場合は、`CanConvert` に対して true を返す最初のコンバーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-192">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="a5aaf-193">適用可能なカスタム コンバーターが登録されていない場合にのみ、組み込みコンバーターが選択されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-193">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="a5aaf-194">一般的なシナリオでのコンバーターの例</span><span class="sxs-lookup"><span data-stu-id="a5aaf-194">Converter samples for common scenarios</span></span>

<span data-ttu-id="a5aaf-195">以下のセクションでは、組み込み機能では処理されない一般的なシナリオに対処するコンバーターの例を示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-195">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="a5aaf-196">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-196">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="a5aaf-197">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-197">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="a5aaf-198">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-198">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="a5aaf-199">[推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-199">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="a5aaf-200">[文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-200">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="a5aaf-201">[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-201">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="a5aaf-202">[Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-202">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="a5aaf-203">推論された型をオブジェクトのプロパティに逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="a5aaf-203">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="a5aaf-204">`object` 型のプロパティに逆シリアル化すると、`JsonElement` オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-204">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="a5aaf-205">その理由は、逆シリアライザーでは、作成する CLR 型がわからず、推測が試みられないためです。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-205">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="a5aaf-206">たとえば、JSON プロパティが "true" である場合、逆シリアライザーでは値が `Boolean` であることは推定されません。また、要素が "01/01/2019" である場合、逆シリアライザーではそれが `DateTime` であることは推定されません。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-206">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="a5aaf-207">型の推定は不正確になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-207">Type inference can be inaccurate.</span></span> <span data-ttu-id="a5aaf-208">逆シリアライザーで、小数点を含まない JSON の数値が `long` と解析された場合、値がもともと `ulong` または `BigInteger` としてシリアル化されていたとすると、範囲外の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-208">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="a5aaf-209">数値がもともと `decimal` としてシリアル化されていた場合、小数点を含む数値が `double` と解析されると、精度が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-209">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="a5aaf-210">次のコードでは、型の推定が必要なシナリオでの、`object` プロパティに対するカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-210">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="a5aaf-211">次のような変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-211">The code converts:</span></span>

* <span data-ttu-id="a5aaf-212">`true` と `false` は `Boolean` に</span><span class="sxs-lookup"><span data-stu-id="a5aaf-212">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="a5aaf-213">小数点を含まない数値は `long` に</span><span class="sxs-lookup"><span data-stu-id="a5aaf-213">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="a5aaf-214">小数点を含む数値は `double` に</span><span class="sxs-lookup"><span data-stu-id="a5aaf-214">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="a5aaf-215">日付は `DateTime` に</span><span class="sxs-lookup"><span data-stu-id="a5aaf-215">Dates to `DateTime`</span></span>
* <span data-ttu-id="a5aaf-216">文字列は `string` に</span><span class="sxs-lookup"><span data-stu-id="a5aaf-216">Strings to `string`</span></span>
* <span data-ttu-id="a5aaf-217">それ以外はすべて `JsonElement` に</span><span class="sxs-lookup"><span data-stu-id="a5aaf-217">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="a5aaf-218">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-218">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="a5aaf-219">`object` プロパティを含む型の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-219">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="a5aaf-220">次の逆シリアル化を行う JSON の例には、`DateTime`、`long`、`string` として逆シリアル化される値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-220">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="a5aaf-221">カスタム コンバーターを使用しないと、逆シリアル化によって各プロパティに `JsonElement` が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-221">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="a5aaf-222">`System.Text.Json.Serialization` 名前空間の[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、`object` プロパティへの逆シリアル化を処理するカスタム コンバーターの例がさらにあります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="a5aaf-223">文字列以外のキーでディクショナリをサポートする</span><span class="sxs-lookup"><span data-stu-id="a5aaf-223">Support Dictionary with non-string key</span></span>

<span data-ttu-id="a5aaf-224">ディクショナリ コレクションに対する組み込みのサポートは `Dictionary<string, TValue>` 用です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-224">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="a5aaf-225">つまり、キーは文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-225">That is, the key must be a string.</span></span> <span data-ttu-id="a5aaf-226">キーが整数または他の型であるディクショナリをサポートするには、カスタム コンバーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-226">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="a5aaf-227">次のコードでは、`Dictionary<Enum,TValue>` で動作するカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-227">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="a5aaf-228">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-228">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="a5aaf-229">このコンバーターでは、次の `Enum` を使用する次のクラスの `TemperatureRanges` プロパティをシリアル化および逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-229">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="a5aaf-230">シリアル化からの JSON 出力は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-230">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="a5aaf-231">`System.Text.Json.Serialization` 名前空間の[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、文字列以外のキーのディクショナリを処理するカスタム コンバーターの例がさらにあります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-231">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="a5aaf-232">ポリモーフィックな逆シリアル化をサポートする</span><span class="sxs-lookup"><span data-stu-id="a5aaf-232">Support polymorphic deserialization</span></span>

<span data-ttu-id="a5aaf-233">組み込み機能では、[ポリモーフィックなシリアル化](system-text-json-how-to.md#serialize-properties-of-derived-classes)は限られた範囲で提供されていますが、逆シリアル化はまったくサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-233">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="a5aaf-234">逆シリアル化を行うには、カスタム コンバーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-234">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="a5aaf-235">たとえば、抽象基底クラス `Person` と、派生クラス `Employee` および `Customer` があるとします。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-235">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="a5aaf-236">ポリモーフィックな逆シリアル化とは、デザイン時に逆シリアル化ターゲットとして `Person` を指定すると、実行時に JSON 内の `Customer` オブジェクトと `Employee` オブジェクトが正しく逆シリアル化されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-236">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="a5aaf-237">逆シリアル化の間に、JSON で必要な型を識別する手掛かりを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-237">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="a5aaf-238">使用できる手掛かりの種類は、シナリオによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-238">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="a5aaf-239">たとえば、識別子プロパティを使用できる場合や、特定のプロパティの有無に依存しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-239">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="a5aaf-240">`System.Text.Json` の現在のリリースでは、ポリモーフィックな逆シリアル化のシナリオを処理する方法を指定する属性が提供されていないため、カスタム コンバーターが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-240">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="a5aaf-241">次のコードでは、基底クラス、2 つの派生クラス、およびそれらのカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-241">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="a5aaf-242">コンバーターでは、識別子プロパティを使用して、ポリモーフィックな逆シリアル化を行います。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-242">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="a5aaf-243">型の識別子はクラス定義には含まれていませんが、シリアル化の間に作成され、逆シリアル化の間に読み取られます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-243">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="a5aaf-244">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-244">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="a5aaf-245">コンバーターでは、次のように、同じコンバーターを使用してシリアル化することによって作成された JSON を逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-245">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="a5aaf-246">前の例のコンバーターのコードでは、各プロパティの読み取りと書き込みを手動で行います。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-246">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="a5aaf-247">別の方法として、`Deserialize` または `Serialize` を呼び出すことにより、一部の作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-247">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="a5aaf-248">例としては、[こちらの StackOverflow の投稿](https://stackoverflow.com/a/59744873/12509023)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-248">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="a5aaf-249">Stack\<T> のラウンド トリップをサポートする</span><span class="sxs-lookup"><span data-stu-id="a5aaf-249">Support round trip for Stack\<T></span></span>

<span data-ttu-id="a5aaf-250">JSON 文字列を <xref:System.Collections.Generic.Stack%601> オブジェクトに逆シリアル化した後、そのオブジェクトをシリアル化した場合、スタックの内容は逆の順序になります。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-250">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="a5aaf-251">この動作は、次の型とインターフェイス、およびそれらから派生するユーザー定義型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-251">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="a5aaf-252">スタックの元の順序を維持するシリアル化と逆シリアル化をサポートするには、カスタム コンバーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-252">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="a5aaf-253">次のコードでは、`Stack<T>` オブジェクトとの間でのラウンドトリップを可能にするカスタム コンバーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-253">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="a5aaf-254">次のコードではコンバーターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-254">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="handle-null-values"></a><span data-ttu-id="a5aaf-255">null 値を処理する</span><span class="sxs-lookup"><span data-stu-id="a5aaf-255">Handle null values</span></span>

<span data-ttu-id="a5aaf-256">既定では、null 値はシリアライザーにより次のように処理されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-256">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="a5aaf-257">参照型と `Nullable<T>` 型の場合:</span><span class="sxs-lookup"><span data-stu-id="a5aaf-257">For reference types and `Nullable<T>` types:</span></span>

  * <span data-ttu-id="a5aaf-258">シリアル化のときにカスタム コンバーターに `null` は渡されません。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-258">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="a5aaf-259">逆シリアル化のときにカスタム コンバーターに `JsonTokenType.Null` は渡されません。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-259">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="a5aaf-260">逆シリアル化では `null` インスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-260">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="a5aaf-261">シリアル化ではライターを使用して `null` が直接書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-261">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="a5aaf-262">null 非許容値型の場合:</span><span class="sxs-lookup"><span data-stu-id="a5aaf-262">For non-nullable value types:</span></span>

  * <span data-ttu-id="a5aaf-263">逆シリアル化のときにカスタム コンバーターに `JsonTokenType.Null` が渡されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-263">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="a5aaf-264">(カスタム コンバーターが使用できない場合は、その型の内部コンバーターによって `JsonException` 例外がスローされます)。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-264">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="a5aaf-265">この null 処理動作は、主に、コンバーターの余分な呼び出しをスキップすることでパフォーマンスを最適化するためのものです。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-265">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="a5aaf-266">また、すべての `Read` および `Write` メソッドのオーバーライドの開始時に、null 許容型のコンバーターで `null` のチェックを強制的に行うことが回避されます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-266">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="a5aaf-267">カスタム コンバーターで参照型または値型の `null` を処理できるようにするには、次の例で示すように、<xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> をオーバーライドして `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-267">To enable a custom converter to handle `null` for a reference or value type, override <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="a5aaf-268">他のカスタム コンバーターのサンプル</span><span class="sxs-lookup"><span data-stu-id="a5aaf-268">Other custom converter samples</span></span>

<span data-ttu-id="a5aaf-269">[Newtonsoft.Json から System.Text.Json への移行](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事には、カスタム コンバーターの他のサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-269">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="a5aaf-270">`System.Text.Json.Serialization` のソース コードの[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、次のような他のカスタム コンバーターのサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-270">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="a5aaf-271">[逆シリアル化時に null を 0 に変換する Int32 コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-271">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="a5aaf-272">[逆シリアル化時に文字列値と数値の両方に対応できる Int32 コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-272">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="a5aaf-273">[Enum コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-273">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="a5aaf-274">[外部データを受け入れる List\<T> コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-274">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="a5aaf-275">[コンマ区切りの数値リストを処理する Long[] コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-275">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="a5aaf-276">既存の組み込みコンバーターの動作を変更するコンバーターを作成する必要がある場合は、[既存のコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)を入手し、それを基にしてカスタマイズを始めることができ ます。</span><span class="sxs-lookup"><span data-stu-id="a5aaf-276">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a5aaf-277">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="a5aaf-277">Additional resources</span></span>

* <span data-ttu-id="a5aaf-278">[組み込みコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-278">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="a5aaf-279">System.Text.Json での DateTime と DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="a5aaf-279">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="a5aaf-280">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="a5aaf-280">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="a5aaf-281">System.Text.Json の使用方法</span><span class="sxs-lookup"><span data-stu-id="a5aaf-281">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="a5aaf-282">Newtonsoft.Json から移行する方法</span><span class="sxs-lookup"><span data-stu-id="a5aaf-282">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* <span data-ttu-id="a5aaf-283">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-283">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="a5aaf-284">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="a5aaf-284">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
