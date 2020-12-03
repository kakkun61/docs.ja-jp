---
title: 破壊的変更:PublishDepsFilePath の動作の変更
description: PublishDepsFilePath MSBuild プロパティがシングルファイル アプリケーションに対して空になるという、.NET 5.0 の破壊的変更について学習します。
ms.date: 09/17/2020
ms.openlocfilehash: 70631beff31aa3388e59f3b79875ef437351451a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760081"
---
# <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="e5306-103">PublishDepsFilePath の動作の変更</span><span class="sxs-lookup"><span data-stu-id="e5306-103">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="e5306-104">`PublishDepsFilePath` MSBuild プロパティは、単一ファイル アプリケーションの場合は空です。</span><span class="sxs-lookup"><span data-stu-id="e5306-104">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="e5306-105">また、非単一ファイル アプリケーションの場合は、ビルドの後半まで、*deps. json* ファイルを出力ディレクトリにコピーすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e5306-105">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e5306-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e5306-106">Version introduced</span></span>

<span data-ttu-id="e5306-107">5.0</span><span class="sxs-lookup"><span data-stu-id="e5306-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="e5306-108">変更の説明</span><span class="sxs-lookup"><span data-stu-id="e5306-108">Change description</span></span>

<span data-ttu-id="e5306-109">以前のバージョンの .NET での `PublishDepsFilePath` MSBuild プロパティは、非単一ファイル アプリケーションの場合は出力ディレクトリ内にあるアプリの *deps. json* ファイルへのパス、単一ファイル アプリの場合は中間ディレクトリ内のパスです。</span><span class="sxs-lookup"><span data-stu-id="e5306-109">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="e5306-110">.NET 5.0 以降では、単一ファイル アプリケーションの場合は `PublishDepsFilePath` が空になり、新しい `IntermediateDepsFilePath` プロパティによって中間ディレクトリ内に *deps.json* の場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e5306-110">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="e5306-111">また、非単一ファイル アプリケーションの場合は、ビルドの後半まで、*deps. json* ファイルを出力ディレクトリ (すなわち、`PublishDepsFilePath` によって指定されるパス) にコピーすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e5306-111">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e5306-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="e5306-112">Reason for change</span></span>

<span data-ttu-id="e5306-113">この変更は、次の 2 つの理由で行われました。</span><span class="sxs-lookup"><span data-stu-id="e5306-113">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="e5306-114">.NET 5 で[機能強化された単一ファイル アプリ](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)をサポートするための発行ロジックのリファクタリングに起因します。</span><span class="sxs-lookup"><span data-stu-id="e5306-114">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="e5306-115">単一ファイル アプリでは、*deps.json* がバンドルされた後に *deps.json* ファイルの書き換えを試行するターゲットに対する保護を支援するためです。これにより、アプリは、通知なしで影響を受けることがありません。</span><span class="sxs-lookup"><span data-stu-id="e5306-115">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="e5306-116">このため、単一ファイル アプリケーションの場合、`PublishDepsFilePath` が空になります。</span><span class="sxs-lookup"><span data-stu-id="e5306-116">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e5306-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="e5306-117">Recommended action</span></span>

<span data-ttu-id="e5306-118">*deps. json* ファイルを書き換えるターゲットは通常、`IntermediateDepsFilePath` プロパティを使用して書き換えを行います。</span><span class="sxs-lookup"><span data-stu-id="e5306-118">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e5306-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e5306-119">Affected APIs</span></span>

<span data-ttu-id="e5306-120">N/A</span><span class="sxs-lookup"><span data-stu-id="e5306-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
