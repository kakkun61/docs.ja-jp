---
ms.openlocfilehash: 2cd5459ab7f2c8c96638bf27dd30980282036925
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506940"
---

### <a name="install-the-sdk"></a><span data-ttu-id="802ff-101">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="802ff-101">Install the SDK</span></span>

<span data-ttu-id="802ff-102">.NET SDK を使用すると、.NET を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="802ff-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="802ff-103">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="802ff-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="802ff-104">.NET SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="802ff-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="802ff-105">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="802ff-105">Install the runtime</span></span>

<span data-ttu-id="802ff-106">ASP.NET Core ランタイムを使用すると、ランタイムを提供しない .NET を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="802ff-106">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="802ff-107">次のコマンドを実行すると、.NET の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="802ff-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="802ff-108">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="802ff-108">In your terminal, run the following commands:</span></span>

```bash
sudo dnf install aspnetcore-runtime-5.0
```

<span data-ttu-id="802ff-109">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-5.0` を `dotnet-runtime-5.0` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="802ff-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo dnf install dotnet-runtime-5.0
```
