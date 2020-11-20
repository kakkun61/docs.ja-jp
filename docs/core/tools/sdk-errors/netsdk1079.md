---
title: NETSDK1079:.NET Core 3.0 以降を対象とする場合、Microsoft.AspNetCore.All パッケージはサポートされません。
description: Microsoft.AspNetCore.App からの移行を解決する方法
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445685"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a><span data-ttu-id="c782d-103">NETSDK1079:.NET Core 3.0 以降を対象とする場合、Microsoft.AspNetCore.All パッケージはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c782d-103">NETSDK1079: The Microsoft.AspNetCore.All package is not supported when targeting .NET Core 3.0 or higher.</span></span>

<span data-ttu-id="c782d-104">**この記事の対象: ✔️** .NET Core SDK 3.1.100 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="c782d-104">**This article applies to:** ✔️ .NET Core SDK 3.1.100 and later versions</span></span>

<span data-ttu-id="c782d-105">このエラー メッセージは次の状況で表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="c782d-105">You may receive this error message when:</span></span>

- <span data-ttu-id="c782d-106">ASP.NET Core プロジェクトの対象を .NET Core 2.2 以前から .NET Core 3.0 以降に変更します。</span><span class="sxs-lookup"><span data-stu-id="c782d-106">You retarget an ASP.NET Core project from .NET Core 2.2 or earlier to .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="c782d-107">プロジェクトで Microsoft.AspNetCore.All パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="c782d-107">The project uses the Microsoft.AspNetCore.All package.</span></span>

<span data-ttu-id="c782d-108">Microsoft.AspNetCore.All の `PackageReference` を削除します。</span><span class="sxs-lookup"><span data-stu-id="c782d-108">Remove the `PackageReference` for Microsoft.AspNetCore.All.</span></span>  <span data-ttu-id="c782d-109">場合によっては、Microsoft.AspNetCore.All から参照されていたが、ASP.NET Core 共有フレームワークには含まれていないパッケージのパッケージ参照を追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="c782d-109">You may also need to add package references for packages that were referenced from Microsoft.AspNetCore.All but are not included in the ASP.NET Core shared framework.</span></span>  <span data-ttu-id="c782d-110">そのようなパッケージを以下に示します。[Microsoft.AspNetCore.All から Microsoft.AspNetCore.App への移行](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp)</span><span class="sxs-lookup"><span data-stu-id="c782d-110">These packages are listed here: [Migrating from Microsoft.AspNetCore.All to Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span></span>

<span data-ttu-id="c782d-111">「[ASP.NET Core 2.2 から 3.0 への移行](/aspnet/core/migration/22-to-30)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="c782d-111">See also [Migrate from ASP.NET Core 2.2 to 3.0](/aspnet/core/migration/22-to-30)</span></span>
