---
ms.openlocfilehash: 3932cf51b5194dba7956cd62ced3985a2e6311f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506803"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="c7512-101">パッケージ マネージャーの代わりに、SDK とランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c7512-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="c7512-102">手動インストールは、通常、継続的インテグレーション テストの一環として、またはサポートされていない Linux ディストリビューションで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c7512-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="c7512-103">開発者またはユーザーにとっては、通常はパッケージ マネージャーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c7512-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="c7512-104">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c7512-104">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="c7512-105">まず、次のいずれかのサイトから SDK またはランタイムの **バイナリ** リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c7512-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="c7512-106">✔️ [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="c7512-106">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="c7512-107">✔️ [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="c7512-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="c7512-108">✔️ [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="c7512-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="c7512-109">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="c7512-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="c7512-110">次に、ダウンロードしたファイルを抽出し、`export` コマンドを使用して .NET で使用される変数を設定してから、.NET が PATH に含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c7512-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="c7512-111">ランタイムを抽出し、.NET CLI コマンドをターミナルで使用できるようにするには、最初に .NET のバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c7512-111">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="c7512-112">次に、ターミナルを開き、ファイルが保存されているディレクトリから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c7512-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="c7512-113">アーカイブ ファイル名は、ダウンロードした内容によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c7512-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="c7512-114">**次のコマンドを使用して、ランタイムを抽出します**。</span><span class="sxs-lookup"><span data-stu-id="c7512-114">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="c7512-115">**次のコマンドを使用して、SDK を抽出します**。</span><span class="sxs-lookup"><span data-stu-id="c7512-115">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="c7512-116">上記の `export` コマンドでは、それを実行したターミナル セッションでのみ .NET CLI コマンドを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c7512-116">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="c7512-117">シェル プロファイルを編集して、コマンドを永続的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="c7512-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="c7512-118">Linux ではさまざまなシェルを使用でき、それぞれに異なるプロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="c7512-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="c7512-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c7512-119">For example:</span></span>
>
> - <span data-ttu-id="c7512-120">**Bash シェル**: *~/.bash_profile*、 *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="c7512-120">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="c7512-121">**Korn シェル**: *~/.kshrc* または *.profile*</span><span class="sxs-lookup"><span data-stu-id="c7512-121">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="c7512-122">**Z シェル**: *~/.zshrc* または *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="c7512-122">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="c7512-123">シェルの適切なソース ファイルを編集し、既存の `PATH` ステートメントの末尾に `:$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="c7512-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="c7512-124">`PATH` ステートメントが含まれていない場合は、`export PATH=$PATH:$HOME/dotnet` を含む新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="c7512-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="c7512-125">また、ファイルの末尾に `export DOTNET_ROOT=$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="c7512-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="c7512-126">この方法では、別々の場所に異なるバージョンをインストールして、どのアプリケーションにどれを使用するかを明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="c7512-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
