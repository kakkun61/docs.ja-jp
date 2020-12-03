---
title: NETSDK1013:TargetFramework 値が認識されませんでした。
description: 有効な TargetFramework 値を決定し、設定する方法
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: 915ac22ad822d17c082498b469acbfb3f1a93efc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717873"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a><span data-ttu-id="e16da-103">NETSDK1013:TargetFramework 値が認識されませんでした</span><span class="sxs-lookup"><span data-stu-id="e16da-103">NETSDK1013: The TargetFramework value was not recognized</span></span>

<span data-ttu-id="e16da-104">**この記事の対象:** ✔️ .NET Core 3.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="e16da-104">**This article applies to:** ✔️ .NET Core 3.1.100 SDK and later versions</span></span>

<span data-ttu-id="e16da-105">SDK によって、`<TargetFramework>` または `<TargetFrameworks>` のプロジェクト ファイルで指定された値が既知の値に解析されます。</span><span class="sxs-lookup"><span data-stu-id="e16da-105">The SDK tries to parse the values provided in the project file for `<TargetFramework>` or `<TargetFrameworks>` into a well known value.</span></span>  <span data-ttu-id="e16da-106">値が認識されない場合、`TargetFrameworkIdentifier` または `TargetFrameworkVersion` 値は空の文字列か `Unsupported` に設定されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e16da-106">If the value is not recognized, the `TargetFrameworkIdentifier` or `TargetFrameworkVersion` value may be set to an empty string or `Unsupported`.</span></span>

<span data-ttu-id="e16da-107">これを解決するには、[サポートされているフレームワーク](../../../standard/frameworks.md)の一覧で `TargetFramework` 値の綴りを確認します。</span><span class="sxs-lookup"><span data-stu-id="e16da-107">To resolve this, check the spelling of your `TargetFramework` value from the list of [supported frameworks](../../../standard/frameworks.md).</span></span>
<span data-ttu-id="e16da-108">プロジェクト ファイルで直接、`TargetFrameworkIdentifier` プロパティと `TargetFrameworkVersion` プロパティを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e16da-108">You can also set the `TargetFrameworkIdentifier` and `TargetFrameworkVersion` properties directly in your project file.</span></span>

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
