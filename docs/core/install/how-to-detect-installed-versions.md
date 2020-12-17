---
title: Windows、Linux、および macOS にインストールされた .NET バージョンを確認する - .NET
description: コンピューターにインストールされている .NET のバージョンを一覧表示する方法について説明します。 これには .NET ランタイムと SDK が含まれます。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2fc12c8c398b1a74d623e53884df666f4d4b85f1
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851615"
---
# <a name="how-to-check-that-net-is-already-installed"></a><span data-ttu-id="1176e-104">.NET が既にインストールされていることを確認する方法</span><span class="sxs-lookup"><span data-stu-id="1176e-104">How to check that .NET is already installed</span></span>

<span data-ttu-id="1176e-105">この記事では、コンピューターにインストールされている .NET ランタイムおよび SDK のバージョンを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1176e-105">This article teaches you how to check which versions of the .NET runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="1176e-106">Visual Studio や Visual Studio for Mac などの統合開発環境を使用している場合は、.NET が既にインストールされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1176e-106">If you have an integrated development environment, such as Visual Studio or Visual Studio for Mac, .NET may have already been installed.</span></span>

<span data-ttu-id="1176e-107">SDK をインストールすると、対応するランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1176e-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="1176e-108">この記事のいずれかのコマンドが失敗した場合は、ランタイムまたは SDK がインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="1176e-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="1176e-109">詳細については、[Windows](windows.md)、[macOS](macos.md)、または [Linux](linux.md) のインストールに関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1176e-109">For more information, see the install articles for [Windows](windows.md), [macOS](macos.md), or [Linux](linux.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="1176e-110">SDK バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="1176e-110">Check SDK versions</span></span>

<span data-ttu-id="1176e-111">現在インストールされている .NET SDK のバージョンをターミナルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="1176e-111">You can see which versions of the .NET SDK are currently installed with a terminal.</span></span> <span data-ttu-id="1176e-112">ターミナルを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1176e-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="1176e-113">次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="1176e-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
5.0.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
5.0.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="1176e-114">ランタイムのバージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="1176e-114">Check runtime versions</span></span>

<span data-ttu-id="1176e-115">次のコマンドで、現在インストールされている .NET ランタイムのバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1176e-115">You can see which versions of the .NET runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="1176e-116">次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="1176e-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="1176e-117">インストール フォルダーを確認する</span><span class="sxs-lookup"><span data-stu-id="1176e-117">Check for install folders</span></span>

<span data-ttu-id="1176e-118">.NET がインストールされていても、オペレーティング システムまたはユーザー プロファイルの `PATH` 変数に追加されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1176e-118">It's possible that .NET is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="1176e-119">この場合、前のセクションのコマンドが機能しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="1176e-119">In this case, the commands from the previous sections may not work.</span></span> <span data-ttu-id="1176e-120">別の方法として、.NET のインストール フォルダーが存在することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1176e-120">As an alternative, you can check that the .NET install folders exist.</span></span>

<span data-ttu-id="1176e-121">インストーラーまたはスクリプトから .NET をインストールすると、標準のフォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1176e-121">When you install .NET from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="1176e-122">通常、.NET のインストールに使用するインストーラーまたはスクリプトには、別のフォルダーにインストールするためのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1176e-122">Much of the time the installer or script you're using to install .NET gives you an option to install to a different folder.</span></span> <span data-ttu-id="1176e-123">別のフォルダーにインストールする場合は、フォルダー パスの先頭を調整します。</span><span class="sxs-lookup"><span data-stu-id="1176e-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="1176e-124">**dotnet 実行可能ファイル**</span><span class="sxs-lookup"><span data-stu-id="1176e-124">**dotnet executable**</span></span>\
<span data-ttu-id="1176e-125">_C:\\program files\\dotnet\\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="1176e-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="1176e-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="1176e-126">**.NET SDK**</span></span>\
<span data-ttu-id="1176e-127">_C:\\program files\\dotnet\\sdk\\<バージョン>\\_</span><span class="sxs-lookup"><span data-stu-id="1176e-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="1176e-128">**.NET ランタイム**</span><span class="sxs-lookup"><span data-stu-id="1176e-128">**.NET Runtime**</span></span>\
<span data-ttu-id="1176e-129">_C:\\program files\\dotnet\\shared\\<ランタイムの種類>\\<バージョン>\\_</span><span class="sxs-lookup"><span data-stu-id="1176e-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="1176e-130">**dotnet 実行可能ファイル**</span><span class="sxs-lookup"><span data-stu-id="1176e-130">**dotnet executable**</span></span>\
<span data-ttu-id="1176e-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="1176e-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="1176e-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="1176e-132">**.NET SDK**</span></span>\
<span data-ttu-id="1176e-133">_/home/user/share/dotnet/sdk/<バージョン>/_</span><span class="sxs-lookup"><span data-stu-id="1176e-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="1176e-134">**.NET ランタイム**</span><span class="sxs-lookup"><span data-stu-id="1176e-134">**.NET Runtime**</span></span>\
<span data-ttu-id="1176e-135">_/home/user/share/dotnet/shared/<ランタイムの種類>/<バージョン>/_</span><span class="sxs-lookup"><span data-stu-id="1176e-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="1176e-136">**dotnet 実行可能ファイル**</span><span class="sxs-lookup"><span data-stu-id="1176e-136">**dotnet executable**</span></span>\
<span data-ttu-id="1176e-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="1176e-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="1176e-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="1176e-138">**.NET SDK**</span></span>\
<span data-ttu-id="1176e-139">_/usr/local/share/dotnet/sdk/<バージョン>/_</span><span class="sxs-lookup"><span data-stu-id="1176e-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="1176e-140">**.NET ランタイム**</span><span class="sxs-lookup"><span data-stu-id="1176e-140">**.NET Runtime**</span></span>\
<span data-ttu-id="1176e-141">_/usr/local/share/dotnet/shared/<ランタイムの種類>/<バージョン>/_</span><span class="sxs-lookup"><span data-stu-id="1176e-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="1176e-142">詳細情報</span><span class="sxs-lookup"><span data-stu-id="1176e-142">More information</span></span>

<span data-ttu-id="1176e-143">コマンド `dotnet --info` を使用すると、SDK バージョンとランタイム バージョンの両方を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1176e-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="1176e-144">また、オペレーティング システムのバージョンやランタイム識別子 (RID) など、その他の環境に関連する情報も取得されます。</span><span class="sxs-lookup"><span data-stu-id="1176e-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1176e-145">次の手順</span><span class="sxs-lookup"><span data-stu-id="1176e-145">Next steps</span></span>

- <span data-ttu-id="1176e-146">[Windows 用の .NET ランタイムと SDK をインストールする](windows.md)。</span><span class="sxs-lookup"><span data-stu-id="1176e-146">[Install the .NET Runtime and SDK for Windows](windows.md).</span></span>
- <span data-ttu-id="1176e-147">[macOS 用の .NET ランタイムと SDK をインストールする](macos.md)。</span><span class="sxs-lookup"><span data-stu-id="1176e-147">[Install the .NET Runtime and SDK for macOS](macos.md).</span></span>
- <span data-ttu-id="1176e-148">[Linux 用の .NET ランタイムと SDK をインストールする](linux.md)。</span><span class="sxs-lookup"><span data-stu-id="1176e-148">[Install the .NET Runtime and SDK for Linux](linux.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1176e-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="1176e-149">See also</span></span>

- [<span data-ttu-id="1176e-150">インストールされている .NET Framework バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="1176e-150">Determine which .NET Framework versions are installed</span></span>](../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)
