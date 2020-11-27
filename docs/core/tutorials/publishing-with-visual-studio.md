---
title: Visual Studio を使用して .NET コンソール アプリケーションを発行する
description: Visual Studio を使用して、.NET アプリケーションを実行するために必要なファイルのセットを作成する方法について学習します。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: b0c6bd85ddf86f0eb11c56f01abb74a7e9786363
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916006"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio"></a><span data-ttu-id="c1b9b-103">チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="c1b9b-103">Tutorial: Publish a .NET console application using Visual Studio</span></span>

<span data-ttu-id="c1b9b-104">このチュートリアルでは、他のユーザーが実行できるコンソール アプリを発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="c1b9b-105">発行では、アプリケーションを実行するために必要なファイルのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="c1b9b-106">ファイルを配置するには、それをターゲット マシンにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1b9b-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c1b9b-107">Prerequisites</span></span>

- <span data-ttu-id="c1b9b-108">このチュートリアルでは、「[Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」で作成するコンソール アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-108">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="c1b9b-109">アプリの発行</span><span class="sxs-lookup"><span data-stu-id="c1b9b-109">Publish the app</span></span>

1. <span data-ttu-id="c1b9b-110">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="c1b9b-111">「[Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」で作成した *HelloWorld* プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-111">Open the *HelloWorld* project that you created in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="c1b9b-112">Visual Studio でリリース ビルド構成が使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="c1b9b-113">必要に応じて、ツール バーのビルド構成の設定を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/visual-studio-toolbar-release.png" alt-text="リリース ビルドが選択された Visual Studio のツールバー":::

1. <span data-ttu-id="c1b9b-115">**HelloWorld** プロジェクト (HelloWorld ソリューションではなく) を右クリックし、メニューから **[発行]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-context-menu.png" alt-text="Visual Studio の [発行] コンテキスト メニュー":::

1. <span data-ttu-id="c1b9b-117">**[発行]** ページの **[ターゲット]** タブで、 **[フォルダー]** 、 **[次へ]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/pick-publish-target.png" alt-text="Visual Studio で発行先を選択します":::

1. <span data-ttu-id="c1b9b-119">**[発行]** ページの **[特定のターゲット]** タブで、 **[フォルダー]** 、 **[次へ]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-119">On the **Specific Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/pick-specific-publish-target.png" alt-text="Visual Studio で特定の発行先を選択する":::

1. <span data-ttu-id="c1b9b-121">**[発行]** ページの **[場所]** タブで、 **[完了]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-121">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-page-loc-tab.png" alt-text="Visual Studio の [発行] ページの [場所] タブ":::

1. <span data-ttu-id="c1b9b-123">**[発行]** ウィンドウの **[発行]** タブで、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-123">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-page.png" alt-text="Visual Studio の [発行] ウィンドウ":::

## <a name="inspect-the-files"></a><span data-ttu-id="c1b9b-125">ファイルを検査する</span><span class="sxs-lookup"><span data-stu-id="c1b9b-125">Inspect the files</span></span>

<span data-ttu-id="c1b9b-126">この発行プロセスでは、フレームワークに依存する展開が既定で作成されます。これは、.NET ランタイムがインストールされているコンピューター上で発行されたアプリケーションが実行される展開の種類です。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-126">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET runtime installed.</span></span> <span data-ttu-id="c1b9b-127">ユーザーは、実行可能ファイルをダブルクリックするか、コマンドプロンプトから `dotnet HelloWorld.dll` コマンドを実行することで、発行されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-127">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="c1b9b-128">次の手順で、発行プロセスによって作成されるファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-128">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="c1b9b-129">**ソリューション エクスプローラー** で、 **[すべてのファイルを表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-129">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="c1b9b-130">プロジェクト フォルダーで、*bin/Release/net5.0/publish* を展開します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-130">In the project folder, expand *bin/Release/net5.0/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="発行されたファイルを表示しているソリューション エクスプローラー":::

   <span data-ttu-id="c1b9b-132">この図に示すように、発行された出力には次のファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-132">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="c1b9b-133">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="c1b9b-133">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="c1b9b-134">このファイルは、アプリケーションのランタイム依存関係ファイルです。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-134">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="c1b9b-135">アプリの実行に必要な .NET コンポーネントとライブラリ (アプリケーションが含まれる動的リンク ライブラリを含む) を定義します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-135">It defines the .NET components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="c1b9b-136">詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-136">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="c1b9b-137">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="c1b9b-137">*HelloWorld.dll*</span></span>

      <span data-ttu-id="c1b9b-138">これは、[フレームワークに依存する展開](../deploying/deploy-with-cli.md#framework-dependent-deployment)バージョンのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-138">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="c1b9b-139">このダイナミック リンク ライブラリを実行するには、コマンド プロンプトで`dotnet HelloWorld.dll` を入力します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-139">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="c1b9b-140">このアプリの実行方法は、.NET ランタイムがインストールされている任意のプラットフォームで動作します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-140">This method of running the app works on any platform that has the .NET runtime installed.</span></span>

   * <span data-ttu-id="c1b9b-141">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="c1b9b-141">*HelloWorld.exe*</span></span>

      <span data-ttu-id="c1b9b-142">これは、[フレームワークに依存する実行可能ファイル](../deploying/deploy-with-cli.md#framework-dependent-executable) バージョンのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-142">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="c1b9b-143">これを実行するには、コマンド プロンプトで `HelloWorld.exe` を入力します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-143">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="c1b9b-144">ファイルはオペレーティング システム固有のものです。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-144">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="c1b9b-145">*HelloWorld.pdb* (配置は省略可能)</span><span class="sxs-lookup"><span data-stu-id="c1b9b-145">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="c1b9b-146">これは、デバッグ シンボル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-146">This is the debug symbols file.</span></span> <span data-ttu-id="c1b9b-147">このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-147">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="c1b9b-148">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="c1b9b-148">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="c1b9b-149">これは、アプリケーションのランタイム構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-149">This is the application's run-time configuration file.</span></span> <span data-ttu-id="c1b9b-150">ビルドされたアプリケーションの実行対象となる .NET のバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-150">It identifies the version of .NET that your application was built to run on.</span></span> <span data-ttu-id="c1b9b-151">構成オプションを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-151">You can also add configuration options to it.</span></span> <span data-ttu-id="c1b9b-152">詳細については、[.NET ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-152">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="c1b9b-153">発行済みアプリを実行する</span><span class="sxs-lookup"><span data-stu-id="c1b9b-153">Run the published app</span></span>

1. <span data-ttu-id="c1b9b-154">**ソリューション エクスプローラー** で、 *[publish]* フォルダーを右クリックし、 **[完全なパスのコピー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-154">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="c1b9b-155">コマンド プロンプトを開いて、*publish* フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-155">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="c1b9b-156">これを行うには、「`cd`」と入力して、完全なパスを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-156">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="c1b9b-157">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-157">For example:</span></span>

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="c1b9b-158">実行可能ファイルを使用してアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-158">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="c1b9b-159">「`HelloWorld.exe`」と入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-159">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="c1b9b-160">プロンプトに応答して名前を入力し、任意のキーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-160">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="c1b9b-161">`dotnet` コマンドを使用して、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-161">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="c1b9b-162">「`dotnet HelloWorld.dll`」と入力して、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-162">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="c1b9b-163">プロンプトに応答して名前を入力し、任意のキーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-163">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c1b9b-164">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c1b9b-164">Additional resources</span></span>

- [<span data-ttu-id="c1b9b-165">.NET アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="c1b9b-165">.NET application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="c1b9b-166">次の手順</span><span class="sxs-lookup"><span data-stu-id="c1b9b-166">Next steps</span></span>

<span data-ttu-id="c1b9b-167">このチュートリアルでは、コンソール アプリを発行しました。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-167">In this tutorial, you published a console app.</span></span> <span data-ttu-id="c1b9b-168">次のチュートリアルでは、クラス ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1b9b-168">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1b9b-169">Visual Studio を使用して .NET クラス ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="c1b9b-169">Create a .NET class library using Visual Studio</span></span>](library-with-visual-studio.md)
