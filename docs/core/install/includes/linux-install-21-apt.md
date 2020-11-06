---
ms.openlocfilehash: 188fef66444cd60f59a3cb9619c0d86efd155f99
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93136326"
---

### <a name="install-the-sdk"></a><span data-ttu-id="1aa4c-101">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="1aa4c-101">Install the SDK</span></span>

<span data-ttu-id="1aa4c-102">.NET Core SDK を使用すると、.NET Core を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="1aa4c-103">.NET Core SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="1aa4c-104">.NET Core SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="1aa4c-105">" **パッケージ dotnet-sdk-2.1 が見つかりません** " のようなエラー メッセージが表示される場合は、「 [APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="1aa4c-106">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="1aa4c-106">Install the runtime</span></span>

<span data-ttu-id="1aa4c-107">.NET Core ランタイムを使用すると、ランタイムを含まない .NET Core を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="1aa4c-108">次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="1aa4c-109">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="1aa4c-110">" **パッケージ aspnetcore-runtime-2.1 が見つかりません** " のようなエラー メッセージが表示される場合は、「 [APT のトラブルシューティング](#apt-troubleshooting)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="1aa4c-111">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET Core ランタイムをインストールできます。それには、前のコマンドの `aspnetcore-runtime-2.1` を `dotnet-runtime-2.1` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1aa4c-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-2.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
