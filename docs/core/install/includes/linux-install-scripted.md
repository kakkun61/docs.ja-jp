---
ms.openlocfilehash: 540eebd957ce8ce0928db2bd8317cb220cba30bb
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031770"
---

<span data-ttu-id="991cf-101">[dotnet-install スクリプト](../../tools/dotnet-install-script.md)は、**SDK** および **ランタイム** のインストールの自動化および管理者以外によるインストールのために使用されます。</span><span class="sxs-lookup"><span data-stu-id="991cf-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="991cf-102">このスクリプトは <https://dot.net/v1/dotnet-install.sh> からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="991cf-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="991cf-103">スクリプトでは、最新の SDK の[長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) が既定でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="991cf-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="991cf-104">(LTS) バージョンではない場合がある現在のリリースをインストールするには、`-c Current` パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="991cf-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="991cf-105">SDK の代わりに .NET ランタイムをインストールするには、`--runtime` パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="991cf-105">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="991cf-106">特定のバージョンをインストールするには、`-c` パラメーターを変更して特定のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="991cf-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="991cf-107">次のコマンドでは、.NET SDK 5.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="991cf-107">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="991cf-108">詳細については、「[dotnet-install スクリプト リファレンス](../../tools/dotnet-install-script.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="991cf-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
