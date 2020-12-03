---
title: 破壊的変更:単一ファイル発行形式のアセンブリ関連 API 動作の変更
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。アセンブリのファイルの場所に関連する複数の API は、単一ファイルの公開形式で呼び出されたときに動作が変更されます。
ms.date: 11/01/2020
ms.openlocfilehash: d77e30318040c8298065073a41caab56f2ca3875
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759788"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="321d1-103">単一ファイル発行形式のアセンブリ関連 API 動作の変更</span><span class="sxs-lookup"><span data-stu-id="321d1-103">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="321d1-104">アセンブリのファイルの場所に関連する複数の API は、単一ファイルの公開形式で呼び出されたときに動作が変更されます。</span><span class="sxs-lookup"><span data-stu-id="321d1-104">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

## <a name="change-description"></a><span data-ttu-id="321d1-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="321d1-105">Change description</span></span>

<span data-ttu-id="321d1-106">.NET 5.0 以降のバージョンの単一ファイル公開では、バンドルされたアセンブリは、ディスクに展開されるのではなく、メモリから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="321d1-106">In single-file publishing for .NET 5.0 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="321d1-107">単一ファイルで公開されたアプリの場合、これは、特定の場所関連の API が .NET 5.0 以降で以前のバージョンの .NET とは異なる値を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="321d1-107">For single-file published apps, this means that certain location-related APIs return different values on .NET 5.0 and later than on previous versions of .NET.</span></span> <span data-ttu-id="321d1-108">変更点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="321d1-108">The changes are as follows:</span></span>

| <span data-ttu-id="321d1-109">API</span><span class="sxs-lookup"><span data-stu-id="321d1-109">API</span></span> | <span data-ttu-id="321d1-110">以前のバージョン</span><span class="sxs-lookup"><span data-stu-id="321d1-110">Previous versions</span></span> | <span data-ttu-id="321d1-111">.NET 5.0 以降</span><span class="sxs-lookup"><span data-stu-id="321d1-111">.NET 5.0 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="321d1-112">展開された DLL ファイル パスを返します</span><span class="sxs-lookup"><span data-stu-id="321d1-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="321d1-113">バンドルされたアセンブリに対して空の文字列を返します</span><span class="sxs-lookup"><span data-stu-id="321d1-113">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="321d1-114">展開された DLL ファイル パスを返します</span><span class="sxs-lookup"><span data-stu-id="321d1-114">Returns extracted DLL file path</span></span> | <span data-ttu-id="321d1-115">バンドルされたアセンブリの例外をスローします</span><span class="sxs-lookup"><span data-stu-id="321d1-115">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="321d1-116">バンドルされたアセンブリの `null` を返します</span><span class="sxs-lookup"><span data-stu-id="321d1-116">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="321d1-117">バンドルされたアセンブリの例外をスローします</span><span class="sxs-lookup"><span data-stu-id="321d1-117">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="321d1-118">値はエントリ ポイント DLL の名前です</span><span class="sxs-lookup"><span data-stu-id="321d1-118">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="321d1-119">値はホストの実行可能ファイルの名前です</span><span class="sxs-lookup"><span data-stu-id="321d1-119">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="321d1-120">値は一時的な展開ディレクトリです</span><span class="sxs-lookup"><span data-stu-id="321d1-120">Value is the temporary extraction directory</span></span> | <span data-ttu-id="321d1-121">値は、ホストの実行可能ファイルの格納ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="321d1-121">Value is the containing directory of the host executable</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="321d1-122">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="321d1-122">Version introduced</span></span>

<span data-ttu-id="321d1-123">5.0</span><span class="sxs-lookup"><span data-stu-id="321d1-123">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="321d1-124">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="321d1-124">Recommended action</span></span>

<span data-ttu-id="321d1-125">1 つのファイルとして公開する場合は、アセンブリのファイルの場所に依存しないようにします。</span><span class="sxs-lookup"><span data-stu-id="321d1-125">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="321d1-126">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="321d1-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
