---
title: System.Text.Json で JsonSerializerOptions をインスタンス化する方法
description: 既存のインスタンスをコピーするか Web の既定値を使用して、JsonSerializerOptions インスタンスをインスタンス化する方法について説明します。
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
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439872"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="df934-103">System.Text.Json で JsonSerializerOptions インスタンスをインスタンス化する方法</span><span class="sxs-lookup"><span data-stu-id="df934-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="df934-104">この記事では、既存のインスタンスをコピーするか Web の既定値を使用して、<xref:System.Text.Json.JsonSerializerOptions> インスタンスをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="df934-104">In this article, you'll learn how to instantiate <xref:System.Text.Json.JsonSerializerOptions> instances by copying existing instances or with web defaults.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="df934-105">JsonSerializerOptions をコピーする</span><span class="sxs-lookup"><span data-stu-id="df934-105">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="df934-106">次の例で示されているように、既存のインスタンスと同じオプションを使用して新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions))があります。</span><span class="sxs-lookup"><span data-stu-id="df934-106">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="df934-107">既存のインスタンスを受け取る `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="df934-107">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="df934-108">JsonSerializerOptions の Web の既定値</span><span class="sxs-lookup"><span data-stu-id="df934-108">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="df934-109">Web アプリ用に異なる既定値があるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="df934-109">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="df934-110">次の例で示されているように、ASP.NET Core によって Web アプリ用に使用される既定のオプションで新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true)があります。</span><span class="sxs-lookup"><span data-stu-id="df934-110">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="df934-111">Web アプリ用に異なる既定値があるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="df934-111">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="df934-112">既定値のセットを指定する `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="df934-112">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="df934-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="df934-113">See also</span></span>

* [<span data-ttu-id="df934-114">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="df934-114">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="df934-115">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="df934-115">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="df934-116">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="df934-116">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="df934-117">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="df934-117">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="df934-118">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="df934-118">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="df934-119">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="df934-119">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="df934-120">循環参照の保持</span><span class="sxs-lookup"><span data-stu-id="df934-120">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="df934-121">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="df934-121">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="df934-122">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="df934-122">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="df934-123">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="df934-123">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
