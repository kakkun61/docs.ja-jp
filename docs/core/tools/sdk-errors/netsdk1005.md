---
title: NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません
description: ターゲットがないアセット ファイルの問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678172"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="5f8ed-103">NETSDK1005 および NETSDK1047:アセット ファイルにターゲットがありません</span><span class="sxs-lookup"><span data-stu-id="5f8ed-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="5f8ed-104">**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="5f8ed-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="5f8ed-105">.NET SDK でエラー NETSDK1005 または NETSDK1047 が発生した場合、プロジェクトのアセット ファイルには、ターゲット フレームワークのいずれかに関する情報が存在しません。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="5f8ed-106">NuGet によって、*project.assets.json* という名前のファイルが *obj* フォルダーに書き込まれます。これはコンパイラに渡すパッケージに関する情報を取得するために .NET SDK によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-106">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="5f8ed-107">.NET 5 では、NuGet で `TargetFrameworkAlias` という名前の新しいフィールドが追加されたため、以前のバージョンの MSBuild または NuGet では、新しいフィールドのないアセット ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-107">In .NET 5, NuGet added a new field named `TargetFrameworkAlias`, so earlier versions of MSBuild or NuGet generate an assets file without the new field.</span></span> <span data-ttu-id="5f8ed-108">詳細については、[エラー NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-108">For more information, see [error NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span></span>

<span data-ttu-id="5f8ed-109">このエラーを解決するために実行できるアクションをいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-109">Here are some actions you can take that may resolve the error:</span></span>

* <span data-ttu-id="5f8ed-110">MSBuild バージョン 16.8 以降および NuGet バージョン 5.8 以降を使用していることを確認し、ツールを更新した後でプロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-110">Make sure that you're using MSBuild version 16.8 or later and NuGet version 5.8 or later, and restore the project after updating your tools.</span></span> <span data-ttu-id="5f8ed-111">NuGet バージョン 5.8 以降を使用している場合は、Visual Studio 2019 バージョン 16.8 以降、MSBuild バージョン 16.8 以降、.NET 5.0 SDK 以降を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-111">When you're using NuGet version 5.8 or later, you should be using Visual Studio 2019 version 16.8 or later, MSBuild version 16.8 or later, and .NET 5.0 SDK or later.</span></span>

* <span data-ttu-id="5f8ed-112">バージョン 16.8 をインストールした後、またはプロジェクトのターゲット フレームワークを変更した後に、Visual Studio 2019 でプロジェクトを初めてビルドするときにエラーが発生した場合は、プロジェクトをもう一度ビルドします。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-112">If you get the error while building a project in Visual Studio 2019 for the first time after installing version 16.8 or after changing the project's target framework, build the project a second time.</span></span>

* <span data-ttu-id="5f8ed-113">プロジェクトをビルドする前に、*obj* フォルダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-113">Delete the *obj* folder before building the project.</span></span>

* <span data-ttu-id="5f8ed-114">見つからないターゲット値がプロジェクトの `TargetFrameworks` プロパティに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f8ed-114">Make sure that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>
