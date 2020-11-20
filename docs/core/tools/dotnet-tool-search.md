---
title: dotnet tool search コマンド
description: dotnet tool search コマンドは、NuGet.org に発行されている .NET ツールを検索します。
ms.date: 11/11/2020
ms.openlocfilehash: e0289e651ec4a439c791c8c948bef2d85d9c3794
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634143"
---
# <a name="dotnet-tool-search"></a><span data-ttu-id="bcb69-103">dotnet tool search</span><span class="sxs-lookup"><span data-stu-id="bcb69-103">dotnet tool search</span></span>

<span data-ttu-id="bcb69-104">**この記事の対象:**  ✔️ .NET 5.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bcb69-104">**This article applies to:** ✔️ .NET 5.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bcb69-105">名前</span><span class="sxs-lookup"><span data-stu-id="bcb69-105">Name</span></span>

<span data-ttu-id="bcb69-106">`dotnet tool search` - NuGet に発行されているすべての [.NET ツール](global-tools.md)を検索します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-106">`dotnet tool search` - Searches all [.NET tools](global-tools.md) that are published to NuGet.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bcb69-107">構文</span><span class="sxs-lookup"><span data-stu-id="bcb69-107">Synopsis</span></span>

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a><span data-ttu-id="bcb69-108">説明</span><span class="sxs-lookup"><span data-stu-id="bcb69-108">Description</span></span>

<span data-ttu-id="bcb69-109">`dotnet tool search` コマンドを使用すると、NuGet で .NET のグローバル、ツールパス、またはローカル ツールとして使用できるツールを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="bcb69-109">The `dotnet tool search` command provides a way for you to search NuGet for tools that can be used as .NET global, tool-path, or local tools.</span></span> <span data-ttu-id="bcb69-110">このコマンドは、ツールの名前とメタデータ (タイトル、説明、タグなど) を検索します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-110">The command searches the tool names and metadata such as titles, descriptions, and tags.</span></span>

<span data-ttu-id="bcb69-111">このコマンドでは、[NuGet Search API](/nuget/api/search-query-service-resource#search-for-packages) を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-111">The command uses the [NuGet Search API](/nuget/api/search-query-service-resource#search-for-packages).</span></span> <span data-ttu-id="bcb69-112">これにより `packageType=dotnettool` がフィルター処理され、.NET ツール パッケージのみが選択されます。</span><span class="sxs-lookup"><span data-stu-id="bcb69-112">It filters on `packageType=dotnettool` to select only .NET tool packages.</span></span>

## <a name="options"></a><span data-ttu-id="bcb69-113">Options</span><span class="sxs-lookup"><span data-stu-id="bcb69-113">Options</span></span>

- **`--detail`**

  <span data-ttu-id="bcb69-114">クエリの詳細な結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-114">Shows detailed results from the query.</span></span>

- **`--prerelease`**

  <span data-ttu-id="bcb69-115">プレリリース パッケージを含めます。</span><span class="sxs-lookup"><span data-stu-id="bcb69-115">Includes pre-release packages.</span></span>

- **`--skip <NUMBER>`**

  <span data-ttu-id="bcb69-116">スキップするクエリ結果の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-116">Specifies the number of query results to skip.</span></span> <span data-ttu-id="bcb69-117">改ページ位置の自動修正に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bcb69-117">Used for pagination.</span></span>

- **`--take <NUMBER>`**

  <span data-ttu-id="bcb69-118">表示するクエリ結果の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-118">Specifies the number of query results to show.</span></span> <span data-ttu-id="bcb69-119">改ページ位置の自動修正に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bcb69-119">Used for pagination.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bcb69-120">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-120">Shows command-line help.</span></span>

## <a name="examples"></a><span data-ttu-id="bcb69-121">例</span><span class="sxs-lookup"><span data-stu-id="bcb69-121">Examples</span></span>

- <span data-ttu-id="bcb69-122">NuGet.org でパッケージ名または説明に "format" が含まれている .NET ツールを検索します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-122">Search NuGet.org for .NET tools that have "format" in their package name or description:</span></span>

  ```dotnetcli
  dotnet tool search format
  ```

  <span data-ttu-id="bcb69-123">出力は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="bcb69-123">The output looks like the following example:</span></span>

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- <span data-ttu-id="bcb69-124">NuGet.org でパッケージ名またはメタデータに "format" が含まれている .NET ツールを検索し、最初の結果のみを表示して、詳細ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="bcb69-124">Search NuGet.org for .NET tools that have "format" in their package name or metadata, show only the first result, and show a detailed view.</span></span>

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  <span data-ttu-id="bcb69-125">出力は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="bcb69-125">The output looks like the following example:</span></span>

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a><span data-ttu-id="bcb69-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcb69-126">See also</span></span>

- [<span data-ttu-id="bcb69-127">.NET ツール</span><span class="sxs-lookup"><span data-stu-id="bcb69-127">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="bcb69-128">チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="bcb69-128">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="bcb69-129">チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="bcb69-129">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
