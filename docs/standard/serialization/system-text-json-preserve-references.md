---
title: System.Text.Json で参照を保持する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、参照を保持し、循環参照を処理する方法について説明します。
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
ms.openlocfilehash: d358c953c0979ca097c080fcd750d5ef95b07de0
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008735"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="fbcab-103">System.Text.Json で参照を保持して循環参照を処理する</span><span class="sxs-lookup"><span data-stu-id="fbcab-103">How to preserve references and handle circular references with System.Text.Json</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="fbcab-104">参照を保持し、循環参照を処理するには、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> を <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="fbcab-104">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="fbcab-105">これを設定すると、次のような動作になります。</span><span class="sxs-lookup"><span data-stu-id="fbcab-105">This setting causes the following behavior:</span></span>

* <span data-ttu-id="fbcab-106">シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="fbcab-106">On serialize:</span></span>

  <span data-ttu-id="fbcab-107">複合型を書き込むとき、シリアライザーによってメタデータのプロパティ (`$id`、`$values`、`$ref`) も書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-107">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="fbcab-108">逆シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="fbcab-108">On deserialize:</span></span>

  <span data-ttu-id="fbcab-109">メタデータが想定され (必須ではありません)、逆シリアライザーによってその理解が試みられます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-109">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="fbcab-110">次のコードでは、`Preserve` 設定の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fbcab-110">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="fbcab-111">この機能を使用して、値型または不変型を保持することはできません。</span><span class="sxs-lookup"><span data-stu-id="fbcab-111">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="fbcab-112">逆シリアル化のとき、不変型のインスタンスは、ペイロード全体が読み取られた後で作成されます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-112">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="fbcab-113">そのため、同じインスタンスへの参照が JSON ペイロード内に含まれている場合、それを逆シリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="fbcab-113">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="fbcab-114">値型、不変型、配列の場合、参照メタデータはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="fbcab-114">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="fbcab-115">逆シリアル化では、`$ref` または `$id` が検出されると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-115">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="fbcab-116">ただし、Newtonsoft.Json を使用してシリアル化されたペイロードを逆シリアル化できるようにするため、`$id` (および、コレクションの場合は `$values`) は値型で無視されます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-116">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="fbcab-117">Newtonsoft.Json の場合は、そのような型のメタデータがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-117">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="fbcab-118">オブジェクトが等しいかどうかを判断するために System.Text.Json によって使用される <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> では、2 つのオブジェクト インスタンスを比較するときに、値の等価性 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>) ではなく参照の等価性 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-118">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="fbcab-119">参照がシリアル化および逆シリアル化される方法の詳細については、<xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcab-119">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fbcab-120">シリアル化および逆シリアル化で参照を維持するための動作は、<xref:System.Text.Json.Serialization.ReferenceResolver> クラスによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-120">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="fbcab-121">カスタム動作を指定するには、派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fbcab-121">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="fbcab-122">例については、[GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcab-122">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="fbcab-123">.NET Core 3.1 の System.Text.Json でサポートされているのは値によるシリアル化のみであり、循環参照の場合は例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fbcab-123">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="fbcab-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbcab-124">See also</span></span>

* [<span data-ttu-id="fbcab-125">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="fbcab-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="fbcab-126">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="fbcab-126">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="fbcab-127">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="fbcab-127">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="fbcab-128">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="fbcab-128">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="fbcab-129">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="fbcab-129">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="fbcab-130">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="fbcab-130">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="fbcab-131">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="fbcab-131">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="fbcab-132">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="fbcab-132">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="fbcab-133">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="fbcab-133">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="fbcab-134">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="fbcab-134">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="fbcab-135">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="fbcab-135">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="fbcab-136">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="fbcab-136">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="fbcab-137">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="fbcab-137">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="fbcab-138">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="fbcab-138">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="fbcab-139">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="fbcab-139">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="fbcab-140">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="fbcab-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="fbcab-141">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="fbcab-141">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
