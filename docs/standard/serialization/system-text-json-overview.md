---
title: C# を使用した JSON のシリアル化と逆シリアル化 - .NET
description: この概要では、.NET で JSON との間でシリアル化または逆シリアル化を行うための System.Text.Json 名前空間機能について説明します。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: cb5c15c2a5c336e2d5b4a3754fa7a02a370602f3
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009886"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="9a8e4-103">.NET での JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリング解除) - 概要</span><span class="sxs-lookup"><span data-stu-id="9a8e4-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="9a8e4-104">`System.Text.Json` 名前空間は、JavaScript Object Notation (JSON) との間でのシリアル化と逆シリアル化の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="9a8e4-105">ライブラリの設計では、ハイ パフォーマンスと、高度な豊富なセットに対する少ないメモリ割り当てが強調されています。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="9a8e4-106">組み込みの UTF-8 サポートによって、UTF-8 としてエンコードされた JSON テキストの読み取りと書き込みのプロセスが最適化されます。これは、web 上のデータおよびディスク上のファイルのための最も一般的なエンコードです。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="9a8e4-107">ライブラリには、メモリ内のドキュメント オブジェクト モデル (DOM) を操作するためのクラスも用意されています。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="9a8e4-108">この機能により、JSON ファイルまたは文字列内の要素に対する読み取り専用のランダムアクセスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="9a8e4-109">ライブラリの入手方法</span><span class="sxs-lookup"><span data-stu-id="9a8e4-109">How to get the library</span></span>

* <span data-ttu-id="9a8e4-110">ライブラリは、.NET Core 3.0 以降のバージョン用の共有フレームワークの一部として組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="9a8e4-111">それより前のバージョンの Framework では、[System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-111">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="9a8e4-112">このパッケージで以下がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9a8e4-112">The package supports:</span></span>

  * <span data-ttu-id="9a8e4-113">.NET Standard 2.0 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="9a8e4-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="9a8e4-114">.NET Framework 4.7.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="9a8e4-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="9a8e4-115">.NET Core 2.0、2.1、および 2.2</span><span class="sxs-lookup"><span data-stu-id="9a8e4-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9a8e4-116">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="9a8e4-116">Additional resources</span></span>

* [<span data-ttu-id="9a8e4-117">ライブラリを使用する方法</span><span class="sxs-lookup"><span data-stu-id="9a8e4-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="9a8e4-118">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="9a8e4-118">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="9a8e4-119">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="9a8e4-119">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="9a8e4-120">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="9a8e4-120">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="9a8e4-121">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="9a8e4-121">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="9a8e4-122">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="9a8e4-122">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="9a8e4-123">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="9a8e4-123">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="9a8e4-124">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="9a8e4-124">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="9a8e4-125">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="9a8e4-125">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="9a8e4-126">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="9a8e4-126">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="9a8e4-127">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="9a8e4-127">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="9a8e4-128">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="9a8e4-128">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="9a8e4-129">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="9a8e4-129">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="9a8e4-130">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="9a8e4-130">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="9a8e4-131">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="9a8e4-131">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="9a8e4-132">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="9a8e4-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="9a8e4-133">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="9a8e4-133">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
