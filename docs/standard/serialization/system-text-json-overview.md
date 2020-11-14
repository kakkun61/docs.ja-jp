---
title: C# を使用した JSON のシリアル化と逆シリアル化 - .NET
description: 'この概要では、.NET で JSON との間でシリアル化または逆シリアル化を行うための :::no-loc(System.Text.Json)::: 名前空間機能について説明します。'
ms.date: 01/10/2020
no-loc:
- ':::no-loc(System.Text.Json):::'
- ':::no-loc(Newtonsoft.Json):::'
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d8bd5bcf78db534bd722972db01253cbd13a7a06
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282399"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="60f97-103">.NET での JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリング解除) - 概要</span><span class="sxs-lookup"><span data-stu-id="60f97-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="60f97-104">`:::no-loc(System.Text.Json):::` 名前空間は、JavaScript Object Notation (JSON) との間でのシリアル化と逆シリアル化の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="60f97-104">The `:::no-loc(System.Text.Json):::` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="60f97-105">ライブラリの設計では、ハイ パフォーマンスと、高度な豊富なセットに対する少ないメモリ割り当てが強調されています。</span><span class="sxs-lookup"><span data-stu-id="60f97-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="60f97-106">組み込みの UTF-8 サポートによって、UTF-8 としてエンコードされた JSON テキストの読み取りと書き込みのプロセスが最適化されます。これは、web 上のデータおよびディスク上のファイルのための最も一般的なエンコードです。</span><span class="sxs-lookup"><span data-stu-id="60f97-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="60f97-107">ライブラリには、メモリ内のドキュメント オブジェクト モデル (DOM) を操作するためのクラスも用意されています。</span><span class="sxs-lookup"><span data-stu-id="60f97-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="60f97-108">この機能により、JSON ファイルまたは文字列内の要素に対する読み取り専用のランダムアクセスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="60f97-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="60f97-109">ライブラリの入手方法</span><span class="sxs-lookup"><span data-stu-id="60f97-109">How to get the library</span></span>

* <span data-ttu-id="60f97-110">ライブラリは、.NET Core 3.0 以降のバージョン用の共有フレームワークの一部として組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="60f97-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="60f97-111">それより前のバージョンの Framework では、[:::no-loc(System.Text.Json):::](https://www.nuget.org/packages/:::no-loc(System.Text.Json):::) NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="60f97-111">For earlier framework versions, install the [:::no-loc(System.Text.Json):::](https://www.nuget.org/packages/:::no-loc(System.Text.Json):::) NuGet package.</span></span> <span data-ttu-id="60f97-112">このパッケージで以下がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="60f97-112">The package supports:</span></span>

  * <span data-ttu-id="60f97-113">.NET Standard 2.0 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="60f97-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="60f97-114">.NET Framework 4.7.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="60f97-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="60f97-115">.NET Core 2.0、2.1、および 2.2</span><span class="sxs-lookup"><span data-stu-id="60f97-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="60f97-116">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="60f97-116">Additional resources</span></span>

* [<span data-ttu-id="60f97-117">ライブラリを使用する方法</span><span class="sxs-lookup"><span data-stu-id="60f97-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="60f97-118">:::no-loc(Newtonsoft.Json)::: から移行する方法</span><span class="sxs-lookup"><span data-stu-id="60f97-118">How to migrate from :::no-loc(Newtonsoft.Json):::</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="60f97-119">コンバーターを記述する方法</span><span class="sxs-lookup"><span data-stu-id="60f97-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="60f97-120">[:::no-loc(System.Text.Json)::: ソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::)</span><span class="sxs-lookup"><span data-stu-id="60f97-120">[:::no-loc(System.Text.Json)::: source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::)</span></span>
* <span data-ttu-id="60f97-121">[:::no-loc(System.Text.Json)::: API リファレンス](xref::::no-loc(System.Text.Json):::)</span><span class="sxs-lookup"><span data-stu-id="60f97-121">[:::no-loc(System.Text.Json)::: API reference](xref::::no-loc(System.Text.Json):::)</span></span>
* <span data-ttu-id="60f97-122">[:::no-loc(System.Text.Json):::.Serialization API リファレンス](xref::::no-loc(System.Text.Json):::.Serialization)</span><span class="sxs-lookup"><span data-stu-id="60f97-122">[:::no-loc(System.Text.Json):::.Serialization API reference](xref::::no-loc(System.Text.Json):::.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/roadmap/README.md)-->
