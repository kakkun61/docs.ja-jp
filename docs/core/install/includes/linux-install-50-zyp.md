---
ms.openlocfilehash: ed269683f5c4569c21ae53e9a3c1ec65eb5ebd43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506853"
---

### <a name="install-the-sdk"></a><span data-ttu-id="229f2-101">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="229f2-101">Install the SDK</span></span>

<span data-ttu-id="229f2-102">.NET SDK を使用すると、.NET を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="229f2-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="229f2-103">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="229f2-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="229f2-104">.NET SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="229f2-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo zypper install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="229f2-105">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="229f2-105">Install the runtime</span></span>

<span data-ttu-id="229f2-106">ASP.NET Core ランタイムを使用すると、ランタイムを提供しない .NET を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="229f2-106">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="229f2-107">次のコマンドを実行すると、.NET の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="229f2-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="229f2-108">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="229f2-108">In your terminal, run the following commands:</span></span>

```bash
sudo zypper install aspnetcore-runtime-5.0
```

<span data-ttu-id="229f2-109">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-5.0` を `dotnet-runtime-5.0` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="229f2-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo zypper install dotnet-runtime-5.0
```
