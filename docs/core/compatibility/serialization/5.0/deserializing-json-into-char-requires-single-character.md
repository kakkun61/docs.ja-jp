---
title: 破壊的変更:逆シリアル化で 1 文字の文字列が求められる
description: .NET 5.0 での破壊的変更について学習します。JsonSerializer.Deserialize によって 1 文字の文字列が求められます。
ms.date: 10/18/2020
ms.openlocfilehash: 780f2928d776ecb6db9a7fc05a720e889eb363e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759969"
---
# <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="67ac4-103">JsonSerializer.Deserialize によって 1 文字の文字列が求められる</span><span class="sxs-lookup"><span data-stu-id="67ac4-103">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="67ac4-104">型パラメーターが <xref:System.Char> の場合、正常に逆シリアル化を行うには、<xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> の文字列引数に 1 文字を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="67ac4-104">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

## <a name="change-description"></a><span data-ttu-id="67ac4-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="67ac4-105">Change description</span></span>

<span data-ttu-id="67ac4-106">以前の .NET バージョンでは、複数文字の文字列を <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> に渡し、型パラメーターが <xref:System.Char> の場合、逆シリアル化は正常に行われ、最初の文字のみが逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="67ac4-106">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="67ac4-107">.NET 5.0 以降では、型パラメーターが <xref:System.Char> の場合、1 文字の文字列以外のものを渡すと、<xref:System.Text.Json.JsonException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="67ac4-107">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="67ac4-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="67ac4-108">Version introduced</span></span>

<span data-ttu-id="67ac4-109">5.0</span><span class="sxs-lookup"><span data-stu-id="67ac4-109">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="67ac4-110">変更理由</span><span class="sxs-lookup"><span data-stu-id="67ac4-110">Reason for change</span></span>

<span data-ttu-id="67ac4-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> を使用すると、1 つの JSON 値を表すテキストが、ジェネリック型パラメーターで指定された型のインスタンスに解析されます。</span><span class="sxs-lookup"><span data-stu-id="67ac4-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="67ac4-112">解析が正常に行われるのは、指定されたペイロードが指定されたジェネリック型パラメーターに対して有効な場合のみです。</span><span class="sxs-lookup"><span data-stu-id="67ac4-112">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="67ac4-113"><xref:System.Char> 値の型の場合、有効なペイロードは 1 文字の文字列です。</span><span class="sxs-lookup"><span data-stu-id="67ac4-113">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="67ac4-114">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="67ac4-114">Recommended action</span></span>

<span data-ttu-id="67ac4-115"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> を使用して文字列を <xref:System.Char> 型に解析する場合は、文字列が 1 文字で構成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="67ac4-115">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="67ac4-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="67ac4-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
