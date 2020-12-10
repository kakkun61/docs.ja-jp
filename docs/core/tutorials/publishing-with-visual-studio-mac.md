---
title: Visual Studio for Mac を使用して .NET コンソール アプリケーションを発行する
description: Visual Studio for Mac を使用して、.NET アプリケーションを実行するために必要なファイルのセットを作成する方法について学習します。
ms.date: 11/30/2020
ms.openlocfilehash: 88f143011b19ca8eda6610803c894e619d06a635
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599188"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="702df-103">チュートリアル: Visual Studio for Mac を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="702df-103">Tutorial: Publish a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="702df-104">このチュートリアルでは、他のユーザーが実行できるコンソール アプリを発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="702df-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="702df-105">発行では、アプリケーションを実行するために必要なファイルのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="702df-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="702df-106">ファイルを配置するには、それをターゲット マシンにコピーします。</span><span class="sxs-lookup"><span data-stu-id="702df-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="702df-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="702df-107">Prerequisites</span></span>

- <span data-ttu-id="702df-108">このチュートリアルでは、「[Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-mac.md)」で作成したコンソール アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="702df-108">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="702df-109">アプリの発行</span><span class="sxs-lookup"><span data-stu-id="702df-109">Publish the app</span></span>

1. <span data-ttu-id="702df-110">Visual Studio for Mac を起動します。</span><span class="sxs-lookup"><span data-stu-id="702df-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="702df-111">「[Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-mac.md)」で作成した HelloWorld プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="702df-111">Open the HelloWorld project that you created in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="702df-112">Visual Studio がアプリケーションのリリース バージョンをビルドしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="702df-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="702df-113">必要に応じて、ツール バーのビルド構成の設定を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="702df-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="リリース ビルドが選択された Visual Studio のツールバー":::

1. <span data-ttu-id="702df-115">メイン メニューから、 **[ビルド]**  >  **[フォルダーに発行...]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="702df-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio の [発行] コンテキスト メニュー":::

1. <span data-ttu-id="702df-117">**[フォルダーに発行]** ダイアログで、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="702df-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio の [フォルダーに発行] ":::

   <span data-ttu-id="702df-119">publish フォルダーが開き、作成されたファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="702df-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="publish フォルダー":::

1. <span data-ttu-id="702df-121">歯車アイコンを選択し、コンテキスト メニューから **[Copy "publish" as Pathname]\("publish" をパス名としてコピー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="702df-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="publish フォルダーへのパスをコピーする":::

## <a name="inspect-the-files"></a><span data-ttu-id="702df-123">ファイルを検査する</span><span class="sxs-lookup"><span data-stu-id="702df-123">Inspect the files</span></span>

<span data-ttu-id="702df-124">この発行プロセスでは、フレームワークに依存する配置が作成されます。これは、.NET ランタイムがインストールされているコンピューター上で発行されたアプリケーションが実行される配置の種類です。</span><span class="sxs-lookup"><span data-stu-id="702df-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET runtime installed.</span></span> <span data-ttu-id="702df-125">ユーザーは、コマンド プロンプトから `dotnet HelloWorld.dll` コマンドを実行することで、発行されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="702df-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="702df-126">上の図に示すように、発行された出力には次のファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="702df-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="702df-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="702df-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="702df-128">このファイルは、アプリケーションのランタイム依存関係ファイルです。</span><span class="sxs-lookup"><span data-stu-id="702df-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="702df-129">アプリの実行に必要な .NET コンポーネントとライブラリ (アプリケーションが含まれる動的リンク ライブラリを含む) を定義します。</span><span class="sxs-lookup"><span data-stu-id="702df-129">It defines the .NET components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="702df-130">詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="702df-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="702df-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="702df-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="702df-132">これは、[フレームワークに依存する展開](../deploying/deploy-with-cli.md#framework-dependent-deployment)バージョンのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="702df-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="702df-133">このダイナミック リンク ライブラリを実行するには、コマンド プロンプトで`dotnet HelloWorld.dll` を入力します。</span><span class="sxs-lookup"><span data-stu-id="702df-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="702df-134">このアプリの実行方法は、.NET ランタイムがインストールされている任意のプラットフォームで動作します。</span><span class="sxs-lookup"><span data-stu-id="702df-134">This method of running the app works on any platform that has the .NET runtime installed.</span></span>

* <span data-ttu-id="702df-135">*HelloWorld.pdb* (配置は省略可能)</span><span class="sxs-lookup"><span data-stu-id="702df-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="702df-136">これは、デバッグ シンボル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="702df-136">This is the debug symbols file.</span></span> <span data-ttu-id="702df-137">このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="702df-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="702df-138">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="702df-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="702df-139">これは、アプリケーションのランタイム構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="702df-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="702df-140">ビルドされたアプリケーションの実行対象となる .NET のバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="702df-140">It identifies the version of .NET that your application was built to run on.</span></span> <span data-ttu-id="702df-141">構成オプションを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="702df-141">You can also add configuration options to it.</span></span> <span data-ttu-id="702df-142">詳細については、[.NET ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="702df-142">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="702df-143">発行済みアプリを実行する</span><span class="sxs-lookup"><span data-stu-id="702df-143">Run the published app</span></span>

1. <span data-ttu-id="702df-144">ターミナルを開いて *publish* フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="702df-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="702df-145">これを行うには、「`cd`」と入力してから前にコピーしたパスを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="702df-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="702df-146">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="702df-146">For example:</span></span>

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/net5.0/publish/
   ```

1. <span data-ttu-id="702df-147">`dotnet` コマンドを使用して、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="702df-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="702df-148">「`dotnet HelloWorld.dll`」と入力し、<kbd>enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="702df-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="702df-149">プロンプトに応答して名前を入力し、任意のキーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="702df-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="702df-150">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="702df-150">Additional resources</span></span>

- [<span data-ttu-id="702df-151">.NET アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="702df-151">.NET application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="702df-152">次の手順</span><span class="sxs-lookup"><span data-stu-id="702df-152">Next steps</span></span>

<span data-ttu-id="702df-153">このチュートリアルでは、コンソール アプリを発行しました。</span><span class="sxs-lookup"><span data-stu-id="702df-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="702df-154">次のチュートリアルでは、クラス ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="702df-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="702df-155">Visual Studio for Mac を使用して .NET ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="702df-155">Create a .NET library using Visual Studio for Mac</span></span>](library-with-visual-studio-mac.md)
