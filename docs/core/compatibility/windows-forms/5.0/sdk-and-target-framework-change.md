---
title: '破壊的変更: WinForms と WPF アプリで Microsoft.NET.Sdk が使用される'
description: .NET 5.0 での破壊的変更について学習します。この変更により、Windows フォーム アプリと Windows Presentation Framework (WPF) アプリでは、.NET Core WinForms と WPF SDK ではなく、.NET SDK が使用されるようになりました。
ms.date: 09/18/2020
ms.openlocfilehash: 5eafed03fbf034f6a6457217a8527a877214e239
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633820"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="9a9f0-103">WinForms と WPF アプリで Microsoft.NET.Sdk が使用される</span><span class="sxs-lookup"><span data-stu-id="9a9f0-103">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="9a9f0-104">Windows フォームと Windows Presentation Framework (WPF) アプリで、.NET Core WinForms および WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`) ではなく、.NET SDK (`Microsoft.NET.Sdk`) が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-104">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

## <a name="change-description"></a><span data-ttu-id="9a9f0-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="9a9f0-105">Change description</span></span>

<span data-ttu-id="9a9f0-106">以前のバージョンの .NET Core では、WinForms および WPF アプリで別の[プロジェクト SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`) が使用されていました。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-106">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="9a9f0-107">.NET 5.0 以降、WinForms および WPF SDK の両方で .NET SDK (`Microsoft.NET.Sdk`) が統合されました。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-107">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="9a9f0-108">また、.NET 5 では、`netcoreapp` と `netstandard` が新しい[ターゲット フレーム ワークモニカー (TFM)](../../../../standard/frameworks.md) に置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-108">In addition, new [target framework monikers (TFM)](../../../../standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="9a9f0-109">次の例では、WPF プロジェクト ファイルを .NET 5.0 以降に変更する場合に、行う必要がある変更を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-109">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="9a9f0-110">以前の .NET Core バージョンの場合:</span><span class="sxs-lookup"><span data-stu-id="9a9f0-110">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="9a9f0-111">.NET 5.0 以降のバージョンの場合:</span><span class="sxs-lookup"><span data-stu-id="9a9f0-111">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a><span data-ttu-id="9a9f0-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9a9f0-112">Version introduced</span></span>

<span data-ttu-id="9a9f0-113">.NET SDK 5.0.100</span><span class="sxs-lookup"><span data-stu-id="9a9f0-113">.NET SDK 5.0.100</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9a9f0-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="9a9f0-114">Recommended action</span></span>

<span data-ttu-id="9a9f0-115">お使いの WPF または Windows フォーム プロジェクト ファイル:</span><span class="sxs-lookup"><span data-stu-id="9a9f0-115">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="9a9f0-116">`Sdk` 属性を `Microsoft.NET.Sdk` に更新します。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-116">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="9a9f0-117">`TargetFramework` プロパティを `net5.0-windows` に更新します。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-117">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9a9f0-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9a9f0-118">Affected APIs</span></span>

<span data-ttu-id="9a9f0-119">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="9a9f0-119">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
