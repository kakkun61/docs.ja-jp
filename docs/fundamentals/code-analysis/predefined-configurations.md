---
title: 定義済みの構成ファイル (コード分析)
description: 定義済みの editorconfig ファイルとルールセットファイルを使用して、特定の種類のコード分析を対象にする方法について説明します。
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2020
ms.locfileid: "96591664"
---
# <a name="predefined-configuration-files"></a><span data-ttu-id="a0a01-103">定義済みの構成ファイル</span><span class="sxs-lookup"><span data-stu-id="a0a01-103">Predefined configuration files</span></span>

<span data-ttu-id="a0a01-104">定義済みの EditorConfig ファイルと [ルールセット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルを使用して、セキュリティや設計ルールなどのコード品質ルールのカテゴリをすばやく簡単に有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a0a01-104">Predefined EditorConfig and [rule set](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) files are available that make it quick and easy to enable a category of code quality rules, such as security or design rules.</span></span> <span data-ttu-id="a0a01-105">特定のカテゴリのルールを有効にすることで、対象となる問題と特定の条件を特定できます。</span><span class="sxs-lookup"><span data-stu-id="a0a01-105">By enabling a specific category of rules, you can identify targeted issues and specific conditions.</span></span> <span data-ttu-id="a0a01-106">これらの定義済みのファイルにアクセスするには、 [Microsoft CodeAnalysis. netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet アナライザーパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a0a01-106">To access these predefined files, install the [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer package.</span></span>

<span data-ttu-id="a0a01-107">[Microsoft CodeAnalysis. netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) には、次のルールカテゴリの定義済みの editorconfig ファイルとルールセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0a01-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) includes predefined EditorConfig files and rule sets for the following rule categories:</span></span>

- <span data-ttu-id="a0a01-108">すべてのルール</span><span class="sxs-lookup"><span data-stu-id="a0a01-108">All rules</span></span>
- <span data-ttu-id="a0a01-109">データフロー</span><span class="sxs-lookup"><span data-stu-id="a0a01-109">Dataflow</span></span>
- <span data-ttu-id="a0a01-110">設計</span><span class="sxs-lookup"><span data-stu-id="a0a01-110">Design</span></span>
- <span data-ttu-id="a0a01-111">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="a0a01-111">Documentation</span></span>
- <span data-ttu-id="a0a01-112">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="a0a01-112">Globalization</span></span>
- <span data-ttu-id="a0a01-113">相互運用性</span><span class="sxs-lookup"><span data-stu-id="a0a01-113">Interoperability</span></span>
- <span data-ttu-id="a0a01-114">保守容易性</span><span class="sxs-lookup"><span data-stu-id="a0a01-114">Maintainability</span></span>
- <span data-ttu-id="a0a01-115">名前を付ける</span><span class="sxs-lookup"><span data-stu-id="a0a01-115">Naming</span></span>
- <span data-ttu-id="a0a01-116">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="a0a01-116">Performance</span></span>
- <span data-ttu-id="a0a01-117">FxCop からの移植</span><span class="sxs-lookup"><span data-stu-id="a0a01-117">Ported from FxCop</span></span>
- <span data-ttu-id="a0a01-118">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="a0a01-118">Reliability</span></span>
- <span data-ttu-id="a0a01-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a0a01-119">Security</span></span>
- <span data-ttu-id="a0a01-120">使用</span><span class="sxs-lookup"><span data-stu-id="a0a01-120">Usage</span></span>

<span data-ttu-id="a0a01-121">これらの規則の各カテゴリには、次のように EditorConfig ファイルまたは規則セットファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="a0a01-121">Each of those categories of rules has an EditorConfig or rule set file to:</span></span>

- <span data-ttu-id="a0a01-122">カテゴリ内のすべてのルールを有効にします (他のすべてのルールを無効にします)。</span><span class="sxs-lookup"><span data-stu-id="a0a01-122">Enable all the rules in the category (and disable all other rules)</span></span>
- <span data-ttu-id="a0a01-123">各ルールの既定の重要度を使用し、既定の設定で有効にします (他のすべてのルールを無効にします)。</span><span class="sxs-lookup"><span data-stu-id="a0a01-123">Use each rule's default severity and enabled by default setting (and disable all other rules)</span></span>

> [!TIP]
> <span data-ttu-id="a0a01-124">[すべてのルール] カテゴリには、すべてのルールを無効にするための追加の EditorConfig ファイルまたはルールセットファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="a0a01-124">The "all rules" category has an additional EditorConfig or rule set file to disable all rules.</span></span> <span data-ttu-id="a0a01-125">このファイルを使用すると、プロジェクト内のアナライザーの警告またはエラーがすぐに除去されます。</span><span class="sxs-lookup"><span data-stu-id="a0a01-125">Use this file to quickly get rid of any analyzer warnings or errors in a project.</span></span>

## <a name="predefined-editorconfig-files"></a><span data-ttu-id="a0a01-126">定義済みの EditorConfig ファイル</span><span class="sxs-lookup"><span data-stu-id="a0a01-126">Predefined EditorConfig files</span></span>

<span data-ttu-id="a0a01-127">Microsoft. CodeAnalysis. NetAnalyzers アナライザーパッケージの定義済み EditorConfig ファイルは、NuGet パッケージがインストールされているの *EditorConfig* サブディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="a0a01-127">The predefined EditorConfig files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *editorconfig* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="a0a01-128">たとえば、すべてのセキュリティ規則を有効にする EditorConfig ファイルは、 *editorconfig/Securityrules enabled/editorconfig* にあります。</span><span class="sxs-lookup"><span data-stu-id="a0a01-128">For example, the EditorConfig file to enable all security rules is located at *editorconfig/SecurityRulesEnabled/.editorconfig*.</span></span>

<span data-ttu-id="a0a01-129">選択した *editorconfig* ファイルをプロジェクトのルートディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a0a01-129">Copy the chosen *.editorconfig* file to your project's root directory.</span></span>

## <a name="predefined-rule-sets"></a><span data-ttu-id="a0a01-130">定義済みの規則セット</span><span class="sxs-lookup"><span data-stu-id="a0a01-130">Predefined rule sets</span></span>

<span data-ttu-id="a0a01-131">Microsoft CodeAnalysis. NetAnalyzers アナライザーパッケージの定義済みの規則セットファイルは、NuGet パッケージがインストールされている *のルールセットサブディレクトリ* にあります。</span><span class="sxs-lookup"><span data-stu-id="a0a01-131">The predefined rule set files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *rulesets* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="a0a01-132">たとえば、すべてのセキュリティ規則を有効にする規則セットファイルは、ルールセット */securityrules enabled にあります。*</span><span class="sxs-lookup"><span data-stu-id="a0a01-132">For example, the rule set file to enable all security rules is located at *rulesets/SecurityRulesEnabled.ruleset*.</span></span> <span data-ttu-id="a0a01-133">1つまたは複数の規則セットをコピーし、プロジェクトが格納されているディレクトリに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a0a01-133">Copy one or more of the rule sets and paste them in the directory that contains your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0a01-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0a01-134">See also</span></span>

- [<span data-ttu-id="a0a01-135">アナライザーの構成</span><span class="sxs-lookup"><span data-stu-id="a0a01-135">Analyzer configuration</span></span>](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [<span data-ttu-id="a0a01-136">EditorConfig の .NET コードスタイル規則オプション</span><span class="sxs-lookup"><span data-stu-id="a0a01-136">.NET code style rule options for EditorConfig</span></span>](code-style-rule-options.md)
