---
title: NETSDK1071:'{0}' に対する PackageReference に指定された `{1}` のバージョン。
description: バージョン付きのフレームワークに含まれているメタパッケージに対する PackageReference の問題を解決する方法。
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 1381fc63941ec04efb31035d13913620a195c236
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713081"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a><span data-ttu-id="2b5bd-103">NETSDK1071:フレームワークに含まれるメタパッケージに対する明示的にバージョン管理された PackageReference。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-103">NETSDK1071: Explicitly versioned PackageReference to a metapackage that would be included with the framework.</span></span>

<span data-ttu-id="2b5bd-104">**この記事の対象:**  ✔️ .NET 5.0.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="2b5bd-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="2b5bd-105">.NET SDK から警告 NETSDK1071 を発行される場合、PackageReference に指定されているメタパッケージのバージョンと、TargetFramework プロパティを介して暗黙的に参照されているメタパッケージのバージョンとの間に、将来的にバージョンの競合が発生する可能性があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-105">When the .NET SDK issues warning NETSDK1071, it suggests there may be a version conflict in the future between the version of a metapackage specified in a PackageReference and the version of that metapackage as implicitly referenced via a TargetFramework property:</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="2b5bd-106">TargetFramework によってメタパッケージのバージョンが自動的に取り込まれるため、バージョンが異なる場合は競合します。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-106">Since the TargetFramework automatically brings in a version of the metapackage, the versions will conflict should they ever differ.</span></span>

<span data-ttu-id="2b5bd-107">それを解決するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-107">To resolve this:</span></span>

1. <span data-ttu-id="2b5bd-108">.NET Core または .NET Standard をターゲットとする場合は、プロジェクト ファイル内の `Microsoft.NETCore.App` または `NETStandard.Library` に対する明示的な参照を回避することを検討します。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-108">Consider, when targeting .NET Core or .NET Standard, avoiding explicit references to `Microsoft.NETCore.App` or `NETStandard.Library` in your project file.</span></span>
2. <span data-ttu-id="2b5bd-109">.NET Core をターゲットとするときに特定バージョンのランタイムが必要な場合は、メタパッケージを直接参照するのではなく、`<RuntimeFrameworkVersion>` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-109">If you need a specific version of the runtime when targeting .NET Core, use the `<RuntimeFrameworkVersion>`property instead of referencing the metapackage directly.</span></span> <span data-ttu-id="2b5bd-110">たとえば、これは、[自己完結型の展開](../../deploying/index.md#publish-self-contained)を使用していて、1.0.0 LTS ランタイムの特定のパッチが必要な場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-110">As an example, this could happen if you're using [self-contained deployments](../../deploying/index.md#publish-self-contained) and need a specific patch of the 1.0.0 LTS runtime.</span></span>
3. <span data-ttu-id="2b5bd-111">.NET Standard を対象にするときに特定バージョンの `NetStandard.Library` が必要な場合は、`<NetStandardImplicitPackageVersion>` プロパティを使用し、必要なバージョンに設定することができます。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-111">If you need a specific version of `NetStandard.Library` when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set it to the version you need.</span></span>
4. <span data-ttu-id="2b5bd-112">.NET Framework プロジェクトで `Microsoft.NETCore.App` または `NETSTandard.Library` に対する参照を明示的に追加したり、更新したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-112">Don't explicitly add or update references to either `Microsoft.NETCore.App` or `NETSTandard.Library` in .NET Framework projects.</span></span> <span data-ttu-id="2b5bd-113">NuGet により、.NET Standard ベースの NuGet パッケージを使用するときに必要な `NETStandard.Library` のバージョンが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-113">NuGet automatically installs any version of `NETStandard.Library` you need when using a .NET Standard-based NuGet package.</span></span>
5. <span data-ttu-id="2b5bd-114">.NET Core 2.1 以降を使用する場合は、.NET Core SDK によって適切なバージョンが自動的に選択されるため、`Microsoft.AspNetCore.App` または `Microsoft.AspNetCore.All` のバージョンを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-114">Do not specify a version for `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` when using .NET Core 2.1+, as the .NET Core SDK automatically selects the appropriate version.</span></span> <span data-ttu-id="2b5bd-115">(メモ: これは、プロジェクトに `Microsoft.NET.Sdk.Web` も使用されている場合に、.NET Core 2.1 をターゲットとする場合にのみ機能します</span><span class="sxs-lookup"><span data-stu-id="2b5bd-115">(Note: This only works when targeting .NET Core 2.1 if the project also uses `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="2b5bd-116">この問題は、.NET Core 2.2 SDK で解決されました)。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-116">This problem was resolved in the .NET Core 2.2 SDK.)</span></span>
6. <span data-ttu-id="2b5bd-117">警告が表示されないように、無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2b5bd-117">If you want the warning to go away, you can also disable it:</span></span>

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
