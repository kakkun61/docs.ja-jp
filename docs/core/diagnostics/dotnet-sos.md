---
title: dotnet-sos 診断ツール - .NET CLI
description: dotnet-sos CLI ツールをインストールして使用し、Windows および Linux のネイティブ デバッガーで使われる SOS デバッガー拡張機能を管理する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: 09e8228c47bdc632bccf3c9ad2296d55fe420060
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765008"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="0a974-103">SOS インストーラー (dotnet-sos)</span><span class="sxs-lookup"><span data-stu-id="0a974-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="0a974-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="0a974-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="0a974-105">インストール</span><span class="sxs-lookup"><span data-stu-id="0a974-105">Install</span></span>

<span data-ttu-id="0a974-106">`dotnet-sos` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="0a974-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="0a974-107">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="0a974-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="0a974-108">`dotnet-sos` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-sos)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0a974-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="0a974-109">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="0a974-109">**Direct download:**</span></span>

  <span data-ttu-id="0a974-110">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="0a974-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="0a974-111">OS</span><span class="sxs-lookup"><span data-stu-id="0a974-111">OS</span></span>  | <span data-ttu-id="0a974-112">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="0a974-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="0a974-113">Windows</span><span class="sxs-lookup"><span data-stu-id="0a974-113">Windows</span></span> | <span data-ttu-id="0a974-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="0a974-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="0a974-115">macOS</span><span class="sxs-lookup"><span data-stu-id="0a974-115">macOS</span></span>   | [<span data-ttu-id="0a974-116">x64</span><span class="sxs-lookup"><span data-stu-id="0a974-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="0a974-117">Linux</span><span class="sxs-lookup"><span data-stu-id="0a974-117">Linux</span></span>   | <span data-ttu-id="0a974-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="0a974-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="0a974-119">構文</span><span class="sxs-lookup"><span data-stu-id="0a974-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="0a974-120">説明</span><span class="sxs-lookup"><span data-stu-id="0a974-120">Description</span></span>

<span data-ttu-id="0a974-121">`dotnet-sos` グローバル ツールによって [SOS デバッガー拡張機能](sos-debugging-extension.md)が追加されます。</span><span class="sxs-lookup"><span data-stu-id="0a974-121">The `dotnet-sos` global tool installs the [SOS debugger extension](sos-debugging-extension.md).</span></span> <span data-ttu-id="0a974-122">この拡張機能では、lldb や windbg のようなネイティブ デバッガーからマネージド .NET Core の状態を検査できます。</span><span class="sxs-lookup"><span data-stu-id="0a974-122">This extension lets you inspect managed .NET Core state from native debuggers like lldb and windbg.</span></span>

> [!NOTE]
> <span data-ttu-id="0a974-123">`dotnet-sos` ツールから SOS をインストールすることは、Linux または macOS の場合のみ必要です。</span><span class="sxs-lookup"><span data-stu-id="0a974-123">Installing SOS via the `dotnet-sos` tool is only needed on Linux or macOS.</span></span>  <span data-ttu-id="0a974-124">古いデバッグ ツールを使用している場合、Windows でも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="0a974-124">It may also be needed on Windows if you're using older debugging tools.</span></span> <span data-ttu-id="0a974-125">[Windows Debugger](/windows-hardware/drivers/debugger/debugger-download-tools) (>= WinDbg または cdb のバージョン 10.0.18317.1001) の最近のバージョンでは、Microsoft 拡張機能ギャラリーから自動的に SOS がロードされます。</span><span class="sxs-lookup"><span data-stu-id="0a974-125">Recent versions of the [Windows Debugger](/windows-hardware/drivers/debugger/debugger-download-tools) (>= version 10.0.18317.1001 of WinDbg or cdb) load SOS automatically from the Microsoft extension gallery.</span></span>  

## <a name="options"></a><span data-ttu-id="0a974-126">オプション</span><span class="sxs-lookup"><span data-stu-id="0a974-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="0a974-127">バージョン情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="0a974-127">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0a974-128">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="0a974-128">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="0a974-129">dotnet-sos install</span><span class="sxs-lookup"><span data-stu-id="0a974-129">dotnet-sos install</span></span>

<span data-ttu-id="0a974-130">.NET Core プロセスをデバッグするために、[SOS 拡張機能](sos-debugging-extension.md)をローカルにインストールします。</span><span class="sxs-lookup"><span data-stu-id="0a974-130">Installs the [SOS extension](sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="0a974-131">macOS および Linux では、lldb の起動時に拡張機能が自動的に読み込まれるように、 *.lldbinit* ファイルが更新されます。</span><span class="sxs-lookup"><span data-stu-id="0a974-131">On macOS and Linux, the *.lldbinit* file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="0a974-132">古いデバッグ ツール (バージョン 10.0.18317.1001 より前) を使用して Windows に SOS をインストールする場合は、WinDbg または cdb で `.load %USERPROFILE%\.dotnet\sos\sos.dll` を実行して、デバッガーで拡張機能を手動で読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a974-132">If you're installing SOS on Windows with older debugging tools (prior to version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="0a974-133">概要</span><span class="sxs-lookup"><span data-stu-id="0a974-133">Synopsis</span></span>

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a><span data-ttu-id="0a974-134">オプション</span><span class="sxs-lookup"><span data-stu-id="0a974-134">Options</span></span>

- **`--architecture <arch>`**

  <span data-ttu-id="0a974-135">インストールする SOS バイナリのプロセッサ アーキテクチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a974-135">Specifies the processor architecture of the SOS binaries to install.</span></span> <span data-ttu-id="0a974-136">既定では、`dotnet-sos` によってホスト コンピューターのアーキテクチャがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0a974-136">By default, `dotnet-sos` installs the architecture of the host machine.</span></span> <span data-ttu-id="0a974-137">dotnet ホスト アーキテクチャとは異なるアーキテクチャに対して SOS をインストールするときにこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="0a974-137">Use this option when you want to install SOS for an architecture that's different from the dotnet host architecture.</span></span> <span data-ttu-id="0a974-138">たとえば、Arm64 ホストから Arm32 バイナリを実行している場合、`dotnet-sos install --architecture Arm` で SOS をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a974-138">For example, if you're running Arm32 binaries from an Arm64 host, you will need to install SOS with `dotnet-sos install --architecture Arm`.</span></span>

  <span data-ttu-id="0a974-139">次のアーキテクチャを利用できます。</span><span class="sxs-lookup"><span data-stu-id="0a974-139">The following architectures are available:</span></span>

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="0a974-140">dotnet-sos uninstall</span><span class="sxs-lookup"><span data-stu-id="0a974-140">dotnet-sos uninstall</span></span>

<span data-ttu-id="0a974-141">[SOS 拡張機能](sos-debugging-extension.md)をアンインストールします。Linux と macOS の場合、lldb 構成から削除します。</span><span class="sxs-lookup"><span data-stu-id="0a974-141">Uninstalls the [SOS extension](sos-debugging-extension.md) and, on Linux and macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="0a974-142">構文</span><span class="sxs-lookup"><span data-stu-id="0a974-142">Synopsis</span></span>

```console
dotnet-sos uninstall
```
