---
ms.openlocfilehash: 87c7abf6a20dd8e9769f3b3b3cbe271d32fd62c3
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507000"
---

### <a name="install-the-sdk"></a><span data-ttu-id="0b096-101">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="0b096-101">Install the SDK</span></span>

<span data-ttu-id="0b096-102">.NET SDK を使用すると、.NET を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="0b096-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="0b096-103">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0b096-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="0b096-104">.NET SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0b096-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="0b096-105">"**パッケージ dotnet-sdk-5.0 が見つかりません**" のようなエラー メッセージが表示される場合は、「[APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0b096-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-5.0**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="0b096-106">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="0b096-106">Install the runtime</span></span>

<span data-ttu-id="0b096-107">ASP.NET Core ランタイムを使用すると、ランタイムを提供しない .NET を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0b096-107">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="0b096-108">次のコマンドを実行すると、.NET の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0b096-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="0b096-109">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0b096-109">In your terminal, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="0b096-110">"**パッケージ aspnetcore-runtime-5.0 が見つかりません**" のようなエラー メッセージが表示される場合は、「[APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0b096-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-5.0**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="0b096-111">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-5.0` を `dotnet-runtime-5.0` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0b096-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo apt-get install -y dotnet-runtime-5.0
```
