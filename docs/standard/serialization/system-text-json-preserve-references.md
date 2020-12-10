---
title: System.Text.Json で参照を保持する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、参照を保持し、循環参照を処理する方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439788"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="54099-103">System.Text.Json で循環参照を処理する方法</span><span class="sxs-lookup"><span data-stu-id="54099-103">How to handle circular references with System.Text.Json</span></span>

<span data-ttu-id="54099-104">この記事では、`System.Text.Json` 名前空間を使用して循環参照を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="54099-104">In this article, you will learn how to handle circular references with the `System.Text.Json` namespace.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="54099-105">参照を保持し、循環参照を処理する</span><span class="sxs-lookup"><span data-stu-id="54099-105">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="54099-106">参照を保持し、循環参照を処理するには、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> を <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="54099-106">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="54099-107">これを設定すると、次のような動作になります。</span><span class="sxs-lookup"><span data-stu-id="54099-107">This setting causes the following behavior:</span></span>

* <span data-ttu-id="54099-108">シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="54099-108">On serialize:</span></span>

  <span data-ttu-id="54099-109">複合型を書き込むとき、シリアライザーによってメタデータのプロパティ (`$id`、`$values`、`$ref`) も書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="54099-109">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="54099-110">逆シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="54099-110">On deserialize:</span></span>

  <span data-ttu-id="54099-111">メタデータが想定され (必須ではありません)、逆シリアライザーによってその理解が試みられます。</span><span class="sxs-lookup"><span data-stu-id="54099-111">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="54099-112">次のコードでは、`Preserve` 設定の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54099-112">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="54099-113">この機能を使用して、値型または不変型を保持することはできません。</span><span class="sxs-lookup"><span data-stu-id="54099-113">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="54099-114">逆シリアル化のとき、不変型のインスタンスは、ペイロード全体が読み取られた後で作成されます。</span><span class="sxs-lookup"><span data-stu-id="54099-114">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="54099-115">そのため、同じインスタンスへの参照が JSON ペイロード内に含まれている場合、それを逆シリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="54099-115">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="54099-116">値型、不変型、配列の場合、参照メタデータはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="54099-116">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="54099-117">逆シリアル化では、`$ref` または `$id` が検出されると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="54099-117">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="54099-118">ただし、Newtonsoft.Json を使用してシリアル化されたペイロードを逆シリアル化できるようにするため、`$id` (および、コレクションの場合は `$values`) は値型で無視されます。</span><span class="sxs-lookup"><span data-stu-id="54099-118">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="54099-119">Newtonsoft.Json の場合は、そのような型のメタデータがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="54099-119">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="54099-120">オブジェクトが等しいかどうかを判断するために System.Text.Json によって使用される <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> では、2 つのオブジェクト インスタンスを比較するときに、値の等価性 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>) ではなく参照の等価性 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="54099-120">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="54099-121">参照がシリアル化および逆シリアル化される方法の詳細については、<xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="54099-121">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="54099-122">シリアル化および逆シリアル化で参照を維持するための動作は、<xref:System.Text.Json.Serialization.ReferenceResolver> クラスによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="54099-122">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="54099-123">カスタム動作を指定するには、派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="54099-123">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="54099-124">例については、[GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="54099-124">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="54099-125">.NET Core 3.1 の System.Text.Json でサポートされているのは値によるシリアル化のみであり、循環参照の場合は例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="54099-125">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="54099-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="54099-126">See also</span></span>

* [<span data-ttu-id="54099-127">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="54099-127">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="54099-128">JsonSerializerOptions をインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="54099-128">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="54099-129">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="54099-129">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="54099-130">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="54099-130">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="54099-131">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="54099-131">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="54099-132">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="54099-132">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="54099-133">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="54099-133">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="54099-134">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="54099-134">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="54099-135">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="54099-135">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="54099-136">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="54099-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
