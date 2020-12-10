---
title: System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、変更できない型と非パブリック アクセサーを使用する方法について説明します。
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
ms.openlocfilehash: d3e61d44ce22b7f50838b6d3ba9cf64004bd3725
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439786"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a><span data-ttu-id="37534-103">System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法</span><span class="sxs-lookup"><span data-stu-id="37534-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="37534-104">この記事では、`System.Text.Json` 名前空間を使用して、レコードなどの変更できない型を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37534-104">In this article, you will learn how to use immutable types, such as Records, with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="37534-105">不変の型とレコード</span><span class="sxs-lookup"><span data-stu-id="37534-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="37534-106">`System.Text.Json` ではパラメーター化されたコンストラクターを使用できるので、不変のクラスまたは構造体を逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="37534-106">`System.Text.Json` can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="37534-107">クラスの場合、パラメーター化されたコンストラクターしかない場合は、そのコンストラクターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="37534-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="37534-108">構造体または複数のコンストラクターを持つクラスの場合は、[[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 属性を適用することにより、使用するコンストラクターを指定します。</span><span class="sxs-lookup"><span data-stu-id="37534-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="37534-109">その属性を使用しないと、パラメーターなしのパブリック コンストラクターが存在する場合は常にそれが使用されます。</span><span class="sxs-lookup"><span data-stu-id="37534-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="37534-110">その属性は、パブリック コンストラクターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="37534-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="37534-111">次の例では、`[JsonConstructor]` 属性が使用されています。</span><span class="sxs-lookup"><span data-stu-id="37534-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="37534-112">次の例で示されているように、C# 9 のレコードもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="37534-112">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="37534-113">すべてのプロパティ セッターが非パブリックであるために不変の型の場合は、[パブリックでないプロパティ アクセサー](#non-public-property-accessors)に関する次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37534-113">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="37534-114">`JsonConstructorAttribute` と C# 9 のレコードのサポートは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="37534-114">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="37534-115">パブリックでないプロパティ アクセサー</span><span class="sxs-lookup"><span data-stu-id="37534-115">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="37534-116">パブリックでないプロパティ アクセサーを使用できるようにするには、次の例で示されているように、[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="37534-116">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="37534-117">パブリックでないプロパティ アクセサーは、.NET Core 3.1 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="37534-117">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="37534-118">詳細については、[Newtonsoft.Json からの移行の記事](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37534-118">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="37534-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="37534-119">See also</span></span>

* [<span data-ttu-id="37534-120">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="37534-120">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="37534-121">JsonSerializerOptions をインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="37534-121">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="37534-122">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="37534-122">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="37534-123">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="37534-123">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="37534-124">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="37534-124">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="37534-125">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="37534-125">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="37534-126">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="37534-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="37534-127">循環参照の保持</span><span class="sxs-lookup"><span data-stu-id="37534-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="37534-128">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="37534-128">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="37534-129">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="37534-129">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
