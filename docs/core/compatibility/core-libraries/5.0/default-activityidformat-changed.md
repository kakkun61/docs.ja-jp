---
title: '破壊的変更: 既定の ActivityIdFormat は W3C'
description: Core .NET ライブラリでの .NET 5.0 に関する破壊的変更について学習します。この変更により、既定の ActivityIdFormat は W3C になりました。
ms.date: 11/01/2020
ms.openlocfilehash: 77ee705ac18065c84ddeab3127e01b6a40c3b84d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759836"
---
# <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="f107a-103">既定の ActivityIdFormat は W3C</span><span class="sxs-lookup"><span data-stu-id="f107a-103">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="f107a-104">アクティビティ (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) の既定の ID 形式が <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> になりました。</span><span class="sxs-lookup"><span data-stu-id="f107a-104">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="change-description"></a><span data-ttu-id="f107a-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="f107a-105">Change description</span></span>

<span data-ttu-id="f107a-106">W3C アクティビティ ID 形式は、階層 ID 形式の代替として .NET Core 3.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="f107a-106">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="f107a-107">ただし、互換性を維持するため、W3C 形式は .NET 5.0 まで既定になりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f107a-107">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="f107a-108">[W3C 形式が承認](https://www.w3.org/TR/trace-context/)され、複数の言語実装で牽引力を得たため、.NET 5.0 で既定が変更されました。</span><span class="sxs-lookup"><span data-stu-id="f107a-108">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="f107a-109">アプリのターゲットが .NET 5.0 以降のプラットフォームであれば、<xref:System.Diagnostics.ActivityIdFormat.Hierarchical> が既定の形式となる以前の動作が見られます。</span><span class="sxs-lookup"><span data-stu-id="f107a-109">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="f107a-110">この既定は net45+、netstandard1.1+、netcoreapp (1.x、2.x、3.x) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f107a-110">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="f107a-111">.NET 5.0 以降では、<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> は <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f107a-111">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f107a-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f107a-112">Version introduced</span></span>

<span data-ttu-id="f107a-113">5.0</span><span class="sxs-lookup"><span data-stu-id="f107a-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f107a-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f107a-114">Recommended action</span></span>

<span data-ttu-id="f107a-115">分散トレースに使用されている ID にアプリケーションが依存しない場合、何の措置も必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f107a-115">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="f107a-116">ASP.NET Core や <xref:System.Net.Http.HttpClient> などのライブラリでは、両方のバージョンの <xref:System.Diagnostics.ActivityIdFormat> を使用したり、伝搬したりできます。</span><span class="sxs-lookup"><span data-stu-id="f107a-116">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="f107a-117">既存のシステムとの相互運用性が必要であるか、現行のシステムが ID の形式に依存している場合、<xref:System.Diagnostics.Activity.DefaultIdFormat> を <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> に設定することで以前の動作を保持できます。</span><span class="sxs-lookup"><span data-stu-id="f107a-117">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f107a-118">あるいは、次の 3 つの方法のいずれかで AppContext スイッチを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f107a-118">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="f107a-119">プロジェクト ファイルで。</span><span class="sxs-lookup"><span data-stu-id="f107a-119">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="f107a-120">*runtimeconfig.json ファイル* で。</span><span class="sxs-lookup"><span data-stu-id="f107a-120">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="f107a-121">環境変数を利用して。</span><span class="sxs-lookup"><span data-stu-id="f107a-121">Through an environment variable.</span></span>

  <span data-ttu-id="f107a-122">`DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` を `true` または 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="f107a-122">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f107a-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f107a-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
