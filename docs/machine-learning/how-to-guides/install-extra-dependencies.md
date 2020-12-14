---
title: 追加の ML.NET 依存関係のインストール
description: ML.NET パッケージが依存しているものの NuGet パッケージと共にインストールされない、ネイティブ ライブラリをインストールする方法について説明します
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: 75d29c6bafdce5c9bb104229ddc8d7b847f57e29
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366807"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="281e8-103">追加の ML.NET 依存関係のインストール</span><span class="sxs-lookup"><span data-stu-id="281e8-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="281e8-104">ほとんどの場合、すべてのオペレーティング システムで、ML.NET をインストールすることは、適切な NuGet パッケージを参照するのと同じくらい簡単です。</span><span class="sxs-lookup"><span data-stu-id="281e8-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="281e8-105">ただし、場合によっては、特にネイティブ コンポーネントが必要であれば、追加のインストール要件が生じます。</span><span class="sxs-lookup"><span data-stu-id="281e8-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="281e8-106">このドキュメントでは、これらのケースでのインストール要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="281e8-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="281e8-107">各セクションは、追加の依存関係を持つ特定の `Microsoft.ML.*` NuGet パッケージによって分類されます。</span><span class="sxs-lookup"><span data-stu-id="281e8-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="281e8-108">Microsoft.ML.TimeSeries、Microsoft.ML.AutoML</span><span class="sxs-lookup"><span data-stu-id="281e8-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="281e8-109">これらのパッケージはどちらも `Microsoft.ML.MKL.Redist` に依存しており、これは `libomp` に依存しています。</span><span class="sxs-lookup"><span data-stu-id="281e8-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="281e8-110">Windows</span><span class="sxs-lookup"><span data-stu-id="281e8-110">Windows</span></span>

<span data-ttu-id="281e8-111">追加のインストール手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="281e8-111">No extra installation steps required.</span></span> <span data-ttu-id="281e8-112">プロジェクトに NuGet パッケージを追加すると、ライブラリがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="281e8-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="281e8-113">Linux</span><span class="sxs-lookup"><span data-stu-id="281e8-113">Linux</span></span>

1. <span data-ttu-id="281e8-114">リポジトリの GPG キーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="281e8-114">Install the GPG key for the repository</span></span>

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. <span data-ttu-id="281e8-115">MKL の APT リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="281e8-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="281e8-116">パッケージの更新</span><span class="sxs-lookup"><span data-stu-id="281e8-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="281e8-117">MKL をインストールします。</span><span class="sxs-lookup"><span data-stu-id="281e8-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="281e8-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="281e8-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="281e8-119">`libiomp.so` の場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="281e8-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="281e8-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="281e8-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="281e8-121">この場所を読み込みライブラリ パスに追加します。</span><span class="sxs-lookup"><span data-stu-id="281e8-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="281e8-122">Mac</span><span class="sxs-lookup"><span data-stu-id="281e8-122">Mac</span></span>

1. <span data-ttu-id="281e8-123">`Homebrew` と共にライブラリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="281e8-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
