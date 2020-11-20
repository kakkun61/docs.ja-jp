---
title: dotnet コマンドの特権アクセス
description: 特権アクセスを必要とする dotnet コマンドのベスト プラクティスについて説明します。
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: b34a4d631ec0e5ef641e1ffbc91e081d25645157
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634052"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="88795-103">dotnet コマンドの特権アクセス</span><span class="sxs-lookup"><span data-stu-id="88795-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="88795-104">ソフトウェア開発のベスト プラクティスでは、最小限の特権を要求するソフトウェアを記述するように開発者に指導しています。</span><span class="sxs-lookup"><span data-stu-id="88795-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="88795-105">しかしながら、パフォーマンス監視ツールなど、一部のソフトウェアでは、オペレーティング システムのルールに起因し、管理者権限を必要とします。</span><span class="sxs-lookup"><span data-stu-id="88795-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="88795-106">次のガイダンスでは、そのようなソフトウェアを .NET Core で開発する場合にサポートされるシナリオを紹介しています。</span><span class="sxs-lookup"><span data-stu-id="88795-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span>

<span data-ttu-id="88795-107">次のコマンドは管理者特権で実行できます。</span><span class="sxs-lookup"><span data-stu-id="88795-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="88795-108">[dotnet tool install](dotnet-tool-install.md) など、`dotnet tool` コマンド。</span><span class="sxs-lookup"><span data-stu-id="88795-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`
- `dotnet-core-uninstall`

<span data-ttu-id="88795-109">その他のコマンドを管理者特権で実行することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="88795-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="88795-110">具体的には、[dotnet restore](dotnet-restore.md)、[dotnet build](dotnet-build.md)、[dotnet run](dotnet-run.md) など、MSBuild を使用するコマンドで特権昇格を推奨していません。</span><span class="sxs-lookup"><span data-stu-id="88795-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="88795-111">主な問題は、dotnet コマンドの実行後、ルートと制限付きアカウントの間をユーザーが行ったり来たりするという、アクセス管理の問題です。</span><span class="sxs-lookup"><span data-stu-id="88795-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="88795-112">制限付きユーザーであれば、ルート ユーザーが作成したファイルにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="88795-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="88795-113">この状況を解決する方法はありますが、このような状況になることがそもそも不要です。</span><span class="sxs-lookup"><span data-stu-id="88795-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="88795-114">ルートと制限付きアカウントの間を行ったり来たりしない限り、ルートでコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="88795-114">You can run commands as root as long as you don't transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="88795-115">たとえば、Docker コンテナーは既定でルートとして実行するため、この特性があります。</span><span class="sxs-lookup"><span data-stu-id="88795-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="88795-116">グローバル ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="88795-116">Global tool installation</span></span>

<span data-ttu-id="88795-117">次の手順は、実行に特権昇格を必要とする .NET ツールをインストール、実行、アンインストールするときの推奨方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="88795-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="88795-118">Windows</span><span class="sxs-lookup"><span data-stu-id="88795-118">Windows</span></span>](#tab/windows)

### <a name="install-the-tool"></a><span data-ttu-id="88795-119">ツールをインストールする</span><span class="sxs-lookup"><span data-stu-id="88795-119">Install the tool</span></span>

<span data-ttu-id="88795-120">フォルダー `%ProgramFiles%\dotnet-tools` が既に存在する場合、次を行い、そのディレクトリを記述または変更する許可が "Users" グループに与えられているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="88795-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="88795-121">`%ProgramFiles%\dotnet-tools` フォルダーを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="88795-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="88795-122">**[共通プロパティ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="88795-122">The **Common Properties** dialog box opens.</span></span>
- <span data-ttu-id="88795-123">**[セキュリティ]** タブを選択します **[グループ名またはユーザー名]** で、"Users" グループにディレクトリを記述または変更する権限が与えられているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="88795-123">Select the **Security** tab. Under **Group or user names**, check whether the "Users" group has permission to write or modify the directory.</span></span>
- <span data-ttu-id="88795-124">"Users" グループでディレクトリを記述または変更できる場合、*dotnet-tools* 以外のツールをインストールするとき、別のディレクトリ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="88795-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="88795-125">ツールをインストールするには、管理者特権のプロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="88795-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="88795-126">インストール中、*dotnet-tools* フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="88795-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="88795-127">グローバル ツールを実行する</span><span class="sxs-lookup"><span data-stu-id="88795-127">Run the global tool</span></span>

<span data-ttu-id="88795-128">**オプション 1** 管理者特権プロンプトで完全パスを使用します。</span><span class="sxs-lookup"><span data-stu-id="88795-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="88795-129">**オプション 2** 新しく作成したフォルダーを `%Path%` に追加します。</span><span class="sxs-lookup"><span data-stu-id="88795-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="88795-130">この操作を行うのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="88795-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="88795-131">次で実行します。</span><span class="sxs-lookup"><span data-stu-id="88795-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="88795-132">グローバル ツールをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="88795-132">Uninstall the global tool</span></span>

<span data-ttu-id="88795-133">管理者特権プロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="88795-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="88795-134">Linux</span><span class="sxs-lookup"><span data-stu-id="88795-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="88795-135">macOS</span><span class="sxs-lookup"><span data-stu-id="88795-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="88795-136">ローカル ツール</span><span class="sxs-lookup"><span data-stu-id="88795-136">Local tools</span></span>

<span data-ttu-id="88795-137">ローカル ツールの範囲は、サブディレクトリごとに/ユーザーごとに設定されます。</span><span class="sxs-lookup"><span data-stu-id="88795-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="88795-138">管理者特権で実行するとき、ローカル ツールによって、制限付きユーザー環境が特権環境に与えられます。</span><span class="sxs-lookup"><span data-stu-id="88795-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="88795-139">Linux と macOS では、この結果、ファイルが root ユーザー専用アクセスで設定されます。</span><span class="sxs-lookup"><span data-stu-id="88795-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="88795-140">ユーザーが制限付きアカウントに戻ると、そのファイルにアクセスしたり、書き込んだりできなくなります。</span><span class="sxs-lookup"><span data-stu-id="88795-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="88795-141">そのため、特権昇格を必要とするツールをローカル ツールとしてインストールすることは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="88795-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="88795-142">その代わり、`--tool-path` オプションとグローバル ツールに関する前述のガイドラインをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="88795-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="88795-143">開発中の特権昇格</span><span class="sxs-lookup"><span data-stu-id="88795-143">Elevation during development</span></span>

<span data-ttu-id="88795-144">開発中、アプリケーションをテストする目的で管理者特権が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="88795-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="88795-145">これは、たとえば、IoT アプリで一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="88795-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="88795-146">Microsoft では、特権昇格なしでアプリケーションを開発し、管理者特権でそれを実行することをお勧めしています。</span><span class="sxs-lookup"><span data-stu-id="88795-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="88795-147">次のようにいくつかのパターンがあります。</span><span class="sxs-lookup"><span data-stu-id="88795-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="88795-148">生成された実行可能ファイルを使用する (最高のスタートアップ パフォーマンスが与えられます):</span><span class="sxs-lookup"><span data-stu-id="88795-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- <span data-ttu-id="88795-149">[dotnet run](dotnet-run.md) コマンドを使用するとき、`—no-build` フラグを指定し、新しいバイナリの生成を回避します。</span><span class="sxs-lookup"><span data-stu-id="88795-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="88795-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="88795-150">See also</span></span>

- [<span data-ttu-id="88795-151">.NET ツールの概要</span><span class="sxs-lookup"><span data-stu-id="88795-151">.NET tools overview</span></span>](global-tools.md)
