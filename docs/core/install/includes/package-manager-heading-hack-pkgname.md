---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506864"
---

<span data-ttu-id="04801-101">パッケージ マネージャーのフィードに追加されるパッケージは、変更可能な `{product}-{type}-{version}` の形式で名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="04801-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="04801-102">**product**</span><span class="sxs-lookup"><span data-stu-id="04801-102">**product**</span></span>\
<span data-ttu-id="04801-103">インストールする .NET 製品の種類。</span><span class="sxs-lookup"><span data-stu-id="04801-103">The type of .NET product to install.</span></span> <span data-ttu-id="04801-104">有効なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="04801-104">Valid options are:</span></span>

  - <span data-ttu-id="04801-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="04801-105">dotnet</span></span>
  - <span data-ttu-id="04801-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="04801-106">aspnetcore</span></span>

- <span data-ttu-id="04801-107">**type**</span><span class="sxs-lookup"><span data-stu-id="04801-107">**type**</span></span>\
<span data-ttu-id="04801-108">SDK またはランタイムを選択します。</span><span class="sxs-lookup"><span data-stu-id="04801-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="04801-109">有効なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="04801-109">Valid options are:</span></span>

  - <span data-ttu-id="04801-110">SDK</span><span class="sxs-lookup"><span data-stu-id="04801-110">sdk</span></span>
  - <span data-ttu-id="04801-111">ランタイム</span><span class="sxs-lookup"><span data-stu-id="04801-111">runtime</span></span>

- <span data-ttu-id="04801-112">**version**</span><span class="sxs-lookup"><span data-stu-id="04801-112">**version**</span></span>\
<span data-ttu-id="04801-113">インストールする SDK またはランタイムのバージョン。</span><span class="sxs-lookup"><span data-stu-id="04801-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="04801-114">この記事では常に、サポートされている最新バージョンの手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="04801-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="04801-115">有効なオプションは、次のようなリリース バージョンです。</span><span class="sxs-lookup"><span data-stu-id="04801-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="04801-116">5.0</span><span class="sxs-lookup"><span data-stu-id="04801-116">5.0</span></span>
  - <span data-ttu-id="04801-117">3.1</span><span class="sxs-lookup"><span data-stu-id="04801-117">3.1</span></span>
  - <span data-ttu-id="04801-118">3.0</span><span class="sxs-lookup"><span data-stu-id="04801-118">3.0</span></span>
  - <span data-ttu-id="04801-119">2.1</span><span class="sxs-lookup"><span data-stu-id="04801-119">2.1</span></span>

  <span data-ttu-id="04801-120">ダウンロードしようとしている SDK/ランタイムが Linux ディストリビューションで使用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04801-120">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="04801-121">サポートされているディストリビューションの一覧については、「[.NET Core の依存関係と要件](../linux.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04801-121">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="04801-122">使用例</span><span class="sxs-lookup"><span data-stu-id="04801-122">Examples</span></span>

- <span data-ttu-id="04801-123">ASP.NET Core 5.0 ランタイムをインストールする: `aspnetcore-runtime-5.0`</span><span class="sxs-lookup"><span data-stu-id="04801-123">Install the ASP.NET Core 5.0 runtime: `aspnetcore-runtime-5.0`</span></span>
- <span data-ttu-id="04801-124">.NET Core 2.1 ランタイムをインストールする: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="04801-124">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="04801-125">.NET 5.0 SDK をインストールする: `dotnet-sdk-5.0`</span><span class="sxs-lookup"><span data-stu-id="04801-125">Install the .NET 5.0 SDK: `dotnet-sdk-5.0`</span></span>
- <span data-ttu-id="04801-126">.NET Core 3.1 SDK をインストールする: `dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="04801-126">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="04801-127">パッケージがない</span><span class="sxs-lookup"><span data-stu-id="04801-127">Package missing</span></span>

<span data-ttu-id="04801-128">パッケージ バージョンの組み合わせが正しくない場合は、使用できません。</span><span class="sxs-lookup"><span data-stu-id="04801-128">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="04801-129">たとえば、ASP.NET Core SDK がない場合、SDK コンポーネントは .NET SDK に含まれています。</span><span class="sxs-lookup"><span data-stu-id="04801-129">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET SDK.</span></span> <span data-ttu-id="04801-130">値 `aspnetcore-sdk-2.2` は正しくありません。`dotnet-sdk-2.2` にする必要があります</span><span class="sxs-lookup"><span data-stu-id="04801-130">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="04801-131">.NET Core によってサポートされている Linux ディストリビューションの一覧については、[.NET の依存関係と要件](../linux.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04801-131">For a list of Linux distributions supported by .NET Core, see [.NET dependencies and requirements](../linux.md).</span></span>
