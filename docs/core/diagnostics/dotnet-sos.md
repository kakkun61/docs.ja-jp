---
title: dotnet-sos 診断ツール - .NET CLI
description: dotnet-sos CLI ツールをインストールして使用し、Windows および Linux のネイティブ デバッガーで使われる SOS デバッガー拡張機能を管理する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: 59512c42a778f68bb3cd092dc854dcc727fd2881
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825443"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="246b6-103">SOS インストーラー (dotnet-sos)</span><span class="sxs-lookup"><span data-stu-id="246b6-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="246b6-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="246b6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="246b6-105">インストール</span><span class="sxs-lookup"><span data-stu-id="246b6-105">Install</span></span>

<span data-ttu-id="246b6-106">`dotnet-sos` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="246b6-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="246b6-107">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="246b6-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="246b6-108">`dotnet-sos` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-sos)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="246b6-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="246b6-109">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="246b6-109">**Direct download:**</span></span>

  <span data-ttu-id="246b6-110">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="246b6-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="246b6-111">OS</span><span class="sxs-lookup"><span data-stu-id="246b6-111">OS</span></span>  | <span data-ttu-id="246b6-112">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="246b6-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="246b6-113">Windows</span><span class="sxs-lookup"><span data-stu-id="246b6-113">Windows</span></span> | <span data-ttu-id="246b6-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="246b6-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="246b6-115">macOS</span><span class="sxs-lookup"><span data-stu-id="246b6-115">macOS</span></span>   | [<span data-ttu-id="246b6-116">x64</span><span class="sxs-lookup"><span data-stu-id="246b6-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="246b6-117">Linux</span><span class="sxs-lookup"><span data-stu-id="246b6-117">Linux</span></span>   | <span data-ttu-id="246b6-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="246b6-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="246b6-119">構文</span><span class="sxs-lookup"><span data-stu-id="246b6-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="246b6-120">説明</span><span class="sxs-lookup"><span data-stu-id="246b6-120">Description</span></span>

<span data-ttu-id="246b6-121">`dotnet-sos` グローバル ツールによって、[SOS デバッガー拡張機能](../../framework/tools/sos-dll-sos-debugging-extension.md)がインストールされます。これにより、Windows 上の WinDbg または cdb、Linux および macOS 上の lldb などのネイティブ デバッガーから[マネージド .NET Core 状態を検査](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md)できるようになります。</span><span class="sxs-lookup"><span data-stu-id="246b6-121">The `dotnet-sos` global tool installs the [SOS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and macOS.</span></span> <span data-ttu-id="246b6-122">最新バージョンの Windows デバッガー (WinDbg または cdb のバージョン 10.0.18317.1001 以降) では、Microsoft 拡張機能ギャラリーから SOS が自動的に読み込まれます。そのため、`dotnet-sos` ツールを使用して SOS をインストールする必要があるのは、Linux および macOS の場合、または古いデバッグ ツールを使用している場合のみとなります。</span><span class="sxs-lookup"><span data-stu-id="246b6-122">Recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and macOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="246b6-123">オプション</span><span class="sxs-lookup"><span data-stu-id="246b6-123">Options</span></span>

- **`--version`**

  <span data-ttu-id="246b6-124">バージョン情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="246b6-124">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="246b6-125">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="246b6-125">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="246b6-126">dotnet-sos install</span><span class="sxs-lookup"><span data-stu-id="246b6-126">dotnet-sos install</span></span>

<span data-ttu-id="246b6-127">.NET Core プロセスをデバッグするために、[SOS 拡張機能](../../framework/tools/sos-dll-sos-debugging-extension.md)をローカルにインストールします。</span><span class="sxs-lookup"><span data-stu-id="246b6-127">Installs the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="246b6-128">macOS および Linux では、lldb の起動時に拡張機能が自動的に読み込まれるように、.lldbinit ファイルが更新されます。</span><span class="sxs-lookup"><span data-stu-id="246b6-128">On macOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="246b6-129">古いデバッグ ツール (バージョン 10.0.18317.1001 より前) を使用して Windows に SOS をインストールする場合は、WinDbg または cdb で `.load %USERPROFILE%\.dotnet\sos\sos.dll` を実行して、デバッガーで拡張機能を手動で読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="246b6-129">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="246b6-130">構文</span><span class="sxs-lookup"><span data-stu-id="246b6-130">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="246b6-131">dotnet-sos uninstall</span><span class="sxs-lookup"><span data-stu-id="246b6-131">dotnet-sos uninstall</span></span>

<span data-ttu-id="246b6-132">[SOS 拡張機能](../../framework/tools/sos-dll-sos-debugging-extension.md)をアンインストールします。Linux または macOS の場合は、lldb 構成から削除します。</span><span class="sxs-lookup"><span data-stu-id="246b6-132">Uninstalls the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) and, if on Linux or macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="246b6-133">構文</span><span class="sxs-lookup"><span data-stu-id="246b6-133">Synopsis</span></span>

```console
dotnet-sos uninstall
```
