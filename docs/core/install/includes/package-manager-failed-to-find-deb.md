---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506986"
---

<span data-ttu-id="8eee8-101">"**パッケージ {dotnet-package} が見つかりません**" や "**一部のパッケージをインストールできませんでした**" のようなエラー メッセージが表示される場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8eee8-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="8eee8-102">次の一連のコマンドには、2 つのプレースホルダーがあります。</span><span class="sxs-lookup"><span data-stu-id="8eee8-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="8eee8-103">これは、`aspnetcore-runtime-3.1` など、インストールする .NET パッケージを表します。</span><span class="sxs-lookup"><span data-stu-id="8eee8-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="8eee8-104">これは、次の `sudo apt-get install` コマンドで使用されます。</span><span class="sxs-lookup"><span data-stu-id="8eee8-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="8eee8-105">これは、使用している Linux のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="8eee8-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="8eee8-106">これは、次の `wget` コマンドで使用されます。</span><span class="sxs-lookup"><span data-stu-id="8eee8-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="8eee8-107">まず、パッケージ リストを消去してみてください。</span><span class="sxs-lookup"><span data-stu-id="8eee8-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="8eee8-108">次に、.NET を再度インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="8eee8-108">Then, try to install .NET again.</span></span> <span data-ttu-id="8eee8-109">それでも解決しない場合は、次のコマンドを使用して手動インストールを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8eee8-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
