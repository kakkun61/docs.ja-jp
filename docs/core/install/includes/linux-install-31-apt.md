---
ms.openlocfilehash: cac1fbd2369277b3a322247a7008f07929502437
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507019"
---

### <a name="install-the-sdk"></a><span data-ttu-id="54423-101">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="54423-101">Install the SDK</span></span>

<span data-ttu-id="54423-102">.NET Core SDK を使用すると、.NET Core を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="54423-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="54423-103">.NET Core SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="54423-103">If you install the .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="54423-104">.NET Core SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="54423-104">To install the .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="54423-105">"**パッケージ dotnet-sdk-3.1 が見つかりません**" のようなエラー メッセージが表示される場合は、「[APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="54423-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="54423-106">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="54423-106">Install the runtime</span></span>

<span data-ttu-id="54423-107">.NET Core ランタイムを使用すると、ランタイムを含まない .NET Core を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="54423-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="54423-108">次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="54423-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="54423-109">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="54423-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="54423-110">"**パッケージ aspnetcore-runtime-3.1 が見つかりません**" のようなエラー メッセージが表示される場合は、「[APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="54423-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="54423-111">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET Core ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-3.1` を `dotnet-runtime-3.1` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="54423-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
