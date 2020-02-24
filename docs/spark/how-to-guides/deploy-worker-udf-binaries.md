---
title: .NET for Apache Spark ワーカーとユーザー定義関数のバイナリを展開する
description: .NET for Apache Spark ワーカーとユーザー定義関数のバイナリを展開する方法について説明します。
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f9197ca3cf8066f0849ebbe70d7757c9035d02f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748543"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a><span data-ttu-id="f2f15-103">.NET for Apache Spark ワーカーとユーザー定義関数のバイナリを展開する</span><span class="sxs-lookup"><span data-stu-id="f2f15-103">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>

<span data-ttu-id="f2f15-104">この手引きでは、.NET for Apache Spark ワーカーとユーザー定義関数のバイナリを展開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-104">This how-to provides general instructions on how to deploy .NET for Apache Spark worker and user-defined function binaries.</span></span> <span data-ttu-id="f2f15-105">設定する環境変数と、アプリケーションを `spark-submit` で起動するときによく使用されるパラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-105">You learn which Environment Variables to set up, as well as some commonly used parameters for launching applications with `spark-submit`.</span></span>

## <a name="configurations"></a><span data-ttu-id="f2f15-106">構成</span><span class="sxs-lookup"><span data-stu-id="f2f15-106">Configurations</span></span>
<span data-ttu-id="f2f15-107">構成では、.NET for Apache Spark ワーカーおよびユーザー定義関数のバイナリを展開する場合の一般的な環境変数とパラメーター設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-107">Configurations show the general environment variables and parameters settings in order to deploy .NET for Apache Spark worker and user-defined function binaries.</span></span>

### <a name="environment-variables"></a><span data-ttu-id="f2f15-108">環境変数</span><span class="sxs-lookup"><span data-stu-id="f2f15-108">Environment variables</span></span>
<span data-ttu-id="f2f15-109">ワーカーを展開して UDF を記述する場合、次のようないくつかの環境変数を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2f15-109">When deploying workers and writing UDFs, there are a few commonly used environment variables that you may need to set:</span></span> 

| <span data-ttu-id="f2f15-110">環境変数</span><span class="sxs-lookup"><span data-stu-id="f2f15-110">Environment Variable</span></span>         | <span data-ttu-id="f2f15-111">説明</span><span class="sxs-lookup"><span data-stu-id="f2f15-111">Description</span></span>
| :--------------------------- | :---------- 
| <span data-ttu-id="f2f15-112">DOTNET_WORKER_DIR</span><span class="sxs-lookup"><span data-stu-id="f2f15-112">DOTNET_WORKER_DIR</span></span>            | <span data-ttu-id="f2f15-113"><code>Microsoft.Spark.Worker</code> バイナリが生成されるパス。</span><span class="sxs-lookup"><span data-stu-id="f2f15-113">Path where the <code>Microsoft.Spark.Worker</code> binary has been generated.</span></span></br><span data-ttu-id="f2f15-114">これは Spark ドライバーによって使用され、Spark Executor に渡されます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-114">It's used by the Spark driver and will be passed to Spark executors.</span></span> <span data-ttu-id="f2f15-115">この変数を設定しないと、Spark Executor は <code>PATH</code> 環境変数から指定したパスを検索します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-115">If this variable is not set up, the Spark executors will search the path specified in the <code>PATH</code> environment variable.</span></span></br><span data-ttu-id="f2f15-116">_例:"C:\bin\Microsoft.Spark.Worker"_</span><span class="sxs-lookup"><span data-stu-id="f2f15-116">_e.g. "C:\bin\Microsoft.Spark.Worker"_</span></span>
| <span data-ttu-id="f2f15-117">DOTNET_ASSEMBLY_SEARCH_PATHS</span><span class="sxs-lookup"><span data-stu-id="f2f15-117">DOTNET_ASSEMBLY_SEARCH_PATHS</span></span> | <span data-ttu-id="f2f15-118"><code>Microsoft.Spark.Worker</code> がアセンブリを読み込むコンマ区切りのパス。</span><span class="sxs-lookup"><span data-stu-id="f2f15-118">Comma-separated paths where <code>Microsoft.Spark.Worker</code> will load assemblies.</span></span></br><span data-ttu-id="f2f15-119">パスが "." で始まる場合、作業ディレクトリが先頭に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-119">Note that if a path starts with ".", the working directory will be prepended.</span></span> <span data-ttu-id="f2f15-120">**yarn モード**の場合、"." はコンテナーの作業ディレクトリを表します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-120">If in **yarn mode**, "." would represent the container's working directory.</span></span></br><span data-ttu-id="f2f15-121">_例:"C:\Users\\&lt;ユーザー名&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;dotnet バージョン&gt;"_</span><span class="sxs-lookup"><span data-stu-id="f2f15-121">_e.g. "C:\Users\\&lt;user name&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;dotnet version&gt;"_</span></span>
| <span data-ttu-id="f2f15-122">DOTNET_WORKER_DEBUG</span><span class="sxs-lookup"><span data-stu-id="f2f15-122">DOTNET_WORKER_DEBUG</span></span>          | <span data-ttu-id="f2f15-123"><a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">UDF をデバッグしたい</a>場合、<code>spark-submit</code> の実行前にこの環境変数を <code>1</code> に設定します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-123">If you want to <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">debug a UDF</a>, then set this environment variable to <code>1</code> before running <code>spark-submit</code>.</span></span>

### <a name="parameter-options"></a><span data-ttu-id="f2f15-124">パラメーター オプション</span><span class="sxs-lookup"><span data-stu-id="f2f15-124">Parameter options</span></span>
<span data-ttu-id="f2f15-125">一度[バンドル](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)した Spark アプリケーションは、`spark-submit` を使用して起動できます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-125">Once the Spark application is [bundled](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies), you can launch it using `spark-submit`.</span></span> <span data-ttu-id="f2f15-126">一般的に使用されるオプションは、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f2f15-126">The following table shows some of the commonly used options:</span></span> 

| <span data-ttu-id="f2f15-127">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="f2f15-127">Parameter Name</span></span>        | <span data-ttu-id="f2f15-128">説明</span><span class="sxs-lookup"><span data-stu-id="f2f15-128">Description</span></span>
| :---------------------| :---------- 
| <span data-ttu-id="f2f15-129">--class</span><span class="sxs-lookup"><span data-stu-id="f2f15-129">--class</span></span>               | <span data-ttu-id="f2f15-130">お使いのアプリケーションのエントリ ポイント。</span><span class="sxs-lookup"><span data-stu-id="f2f15-130">The entry point for your application.</span></span></br><span data-ttu-id="f2f15-131">_例: org.apache.spark.deploy.dotnet.DotnetRunner_</span><span class="sxs-lookup"><span data-stu-id="f2f15-131">_e.g. org.apache.spark.deploy.dotnet.DotnetRunner_</span></span>
| <span data-ttu-id="f2f15-132">--master</span><span class="sxs-lookup"><span data-stu-id="f2f15-132">--master</span></span>              | <span data-ttu-id="f2f15-133">クラスターの<a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">マスター URL</a>。</span><span class="sxs-lookup"><span data-stu-id="f2f15-133">The <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">master URL</a> for the cluster.</span></span></br><span data-ttu-id="f2f15-134">_例: yarn_</span><span class="sxs-lookup"><span data-stu-id="f2f15-134">_e.g. yarn_</span></span>
| <span data-ttu-id="f2f15-135">--deploy-mode</span><span class="sxs-lookup"><span data-stu-id="f2f15-135">--deploy-mode</span></span>         | <span data-ttu-id="f2f15-136">ご自分のドライバーをワーカー ノードに展開 (<code>cluster</code>) するか、外部クライアントとしてローカルに展開 (<code>client</code>) するか。</span><span class="sxs-lookup"><span data-stu-id="f2f15-136">Whether to deploy your driver on the worker nodes (<code>cluster</code>) or locally as an external client (<code>client</code>).</span></span></br><span data-ttu-id="f2f15-137">既定値: <code>client</code></span><span class="sxs-lookup"><span data-stu-id="f2f15-137">Default: <code>client</code></span></span>
| <span data-ttu-id="f2f15-138">--conf</span><span class="sxs-lookup"><span data-stu-id="f2f15-138">--conf</span></span>                | <span data-ttu-id="f2f15-139">Spark の <code>key=value</code> 形式での任意の構成プロパティ。</span><span class="sxs-lookup"><span data-stu-id="f2f15-139">Arbitrary Spark configuration property in <code>key=value</code> format.</span></span></br><span data-ttu-id="f2f15-140">_例: spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=.\worker\Microsoft.Spark.Worker_</span><span class="sxs-lookup"><span data-stu-id="f2f15-140">_e.g. spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=.\worker\Microsoft.Spark.Worker_</span></span>
| <span data-ttu-id="f2f15-141">--files</span><span class="sxs-lookup"><span data-stu-id="f2f15-141">--files</span></span>               | <span data-ttu-id="f2f15-142">各 Executor の作業ディレクトリに展開されるファイルのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="f2f15-142">Comma-separated list of files to be placed in the working directory of each executor.</span></span><br/><ul><li><span data-ttu-id="f2f15-143">なお、このオプションは、yarn モードでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-143">Please note that this option is only applicable for yarn mode.</span></span></li><li><span data-ttu-id="f2f15-144">ファイル名は、Hadoop と同様 # を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-144">It supports specifying file names with # similar to Hadoop.</span></span></br></ul><span data-ttu-id="f2f15-145">_例: <code>myLocalSparkApp.dll#appSeen.dll</code>YARN で実行する場合、<code>myLocalSparkApp.dll</code> を参照するには、お使いのアプリケーションで <code>appSeen.dll</code> の名前を使用する必要があります。_</span><span class="sxs-lookup"><span data-stu-id="f2f15-145">_e.g. <code>myLocalSparkApp.dll#appSeen.dll</code>. Your application should use the name as <code>appSeen.dll</code> to reference <code>myLocalSparkApp.dll</code> when running on YARN._</span></span></li>
| <span data-ttu-id="f2f15-146">--archives</span><span class="sxs-lookup"><span data-stu-id="f2f15-146">--archives</span></span>          | <span data-ttu-id="f2f15-147">各 Executor の作業ディレクトリに抽出されるアーカイブのコンマ区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="f2f15-147">Comma-separated list of archives to be extracted into the working directory of each executor.</span></span></br><ul><li><span data-ttu-id="f2f15-148">なお、このオプションは、yarn モードでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-148">Please note that this option is only applicable for yarn mode.</span></span></li><li><span data-ttu-id="f2f15-149">ファイル名は、Hadoop と同様 # を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-149">It supports specifying file names with # similar to Hadoop.</span></span></br></ul><span data-ttu-id="f2f15-150">_例: <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>これで、この zip ファイルはコピーされ <code>worker</code> フォルダーに抽出されます。_</span><span class="sxs-lookup"><span data-stu-id="f2f15-150">_e.g. <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. This will copy and extract the zip file to <code>worker</code> folder._</span></span></li>
| <span data-ttu-id="f2f15-151">application-jar</span><span class="sxs-lookup"><span data-stu-id="f2f15-151">application-jar</span></span>       | <span data-ttu-id="f2f15-152">お使いのアプリケーションとすべての依存関係が含まれた、バンドルされている jar へのパス。</span><span class="sxs-lookup"><span data-stu-id="f2f15-152">Path to a bundled jar including your application and all dependencies.</span></span></br><span data-ttu-id="f2f15-153">_例: hdfs://&lt;お使いの jar へのパス&gt;/microsoft-spark-&lt;バージョン&gt;.jar_</span><span class="sxs-lookup"><span data-stu-id="f2f15-153">_e.g. hdfs://&lt;path to your jar&gt;/microsoft-spark-&lt;version&gt;.jar_</span></span>
| <span data-ttu-id="f2f15-154">application-arguments</span><span class="sxs-lookup"><span data-stu-id="f2f15-154">application-arguments</span></span> | <span data-ttu-id="f2f15-155">(存在する場合) お使いのメイン クラスのメイン メソッドに渡される引数。</span><span class="sxs-lookup"><span data-stu-id="f2f15-155">Arguments passed to the main method of your main class, if any.</span></span></br><span data-ttu-id="f2f15-156">_例: hdfs://&lt;お使いのアプリへのパス&gt;/&lt;お使いのアプリ&gt;.zip &lt;お使いのアプリ名&gt; &lt;アプリの引数&gt;_</span><span class="sxs-lookup"><span data-stu-id="f2f15-156">_e.g. hdfs://&lt;path to your app&gt;/&lt;your app&gt;.zip &lt;your app name&gt; &lt;app args&gt;_</span></span>

> [!NOTE]
> <span data-ttu-id="f2f15-157">`spark-submit` を使用してアプリケーションを起動する場合、`--options` はすべて `application-jar` の前に指定してください。そのようにしないと、それらは無視されます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-157">Specify all the `--options` before `application-jar` when launching applications with `spark-submit`, otherwise they will be ignored.</span></span> <span data-ttu-id="f2f15-158">詳細については、[`spark-submit` オプション](https://spark.apache.org/docs/latest/submitting-applications.html)に関するページと [YARN での spark の実行](https://spark.apache.org/docs/latest/running-on-yarn.html)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2f15-158">For more information, see [`spark-submit` options](https://spark.apache.org/docs/latest/submitting-applications.html) and [running spark on YARN details](https://spark.apache.org/docs/latest/running-on-yarn.html).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="f2f15-159">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="f2f15-159">Frequently asked questions</span></span>
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a><span data-ttu-id="f2f15-160">UDF で spark アプリを実行すると、\`FileNotFoundException' エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-160">When I run a spark app with UDFs, I get a \`FileNotFoundException' error.</span></span> <span data-ttu-id="f2f15-161">どうすればいいですか。</span><span class="sxs-lookup"><span data-stu-id="f2f15-161">What should I do?</span></span>
> <span data-ttu-id="f2f15-162">**エラー:** [エラー] [TaskRunner] [0] ProcessStream() が次の例外で失敗しました:System.IO.FileNotFoundException:Assembly 'mySparkApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' ファイルが見つかりません: 'mySparkApp.dll'</span><span class="sxs-lookup"><span data-stu-id="f2f15-162">**Error:** [Error] [TaskRunner] [0] ProcessStream() failed with exception: System.IO.FileNotFoundException: Assembly 'mySparkApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' file not found: 'mySparkApp.dll'</span></span>

<span data-ttu-id="f2f15-163">**回答:** `DOTNET_ASSEMBLY_SEARCH_PATHS` 環境変数の設定が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-163">**Answer:** Check that the `DOTNET_ASSEMBLY_SEARCH_PATHS` environment variable is set correctly.</span></span> <span data-ttu-id="f2f15-164">これは、お使いの `mySparkApp.dll` を含むパスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2f15-164">It should be the path that contains your `mySparkApp.dll`.</span></span>

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a><span data-ttu-id="f2f15-165">.NET for Apache Spark バージョンをアップグレードし、`DOTNET_WORKER_DIR` 環境変数をリセットした後も次の `IOException` エラーが表示されるのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="f2f15-165">After I upgraded my .NET for Apache Spark version and reset the `DOTNET_WORKER_DIR` environment variable, why do I still get the following `IOException` error?</span></span>
> <span data-ttu-id="f2f15-166">**エラー:** ステージ 11.0 でタスク 0.0 が失われました (TID 24, localhost, executor driver): java.io.IOException:"Microsoft.Spark.Worker.exe" プログラムを実行できません:CreateProcess error=2, システムに指定されたファイルが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f2f15-166">**Error:** Lost task 0.0 in stage 11.0 (TID 24, localhost, executor driver): java.io.IOException: Cannot run program "Microsoft.Spark.Worker.exe": CreateProcess error=2, The system cannot find the file specified.</span></span>

<span data-ttu-id="f2f15-167">**回答:** 最新の環境変数値が使用されるよう、まずはお使いの PowerShell ウィンドウ (またはその他のコマンド ウィンドウ) の再起動を試行してください。</span><span class="sxs-lookup"><span data-stu-id="f2f15-167">**Answer:** Try restarting your PowerShell window (or other command windows) first so that it can take the latest environment variable values.</span></span> <span data-ttu-id="f2f15-168">その後、お使いのプログラムを起動します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-168">Then start your program.</span></span>

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a><span data-ttu-id="f2f15-169">自分の Spark アプリケーションの送信後、エラー `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2f15-169">After submitting my Spark application, I get the error `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`.</span></span>
> <span data-ttu-id="f2f15-170">**エラー:** [エラー] [TaskRunner] [0] ProcessStream() が次の例外で失敗しました:System.TypeLoadException:型 'System.Runtime.Remoting.Contexts.Context' をアセンブリ 'mscorlib から読み込むことができませんでした, Version=4.0.0.0, Culture=neutral, PublicKeyToken=...'.</span><span class="sxs-lookup"><span data-stu-id="f2f15-170">**Error:** [Error] [TaskRunner] [0] ProcessStream() failed with exception: System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context' from assembly 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=...'.</span></span>

<span data-ttu-id="f2f15-171">**回答:** お使いの `Microsoft.Spark.Worker` のバージョンを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f2f15-171">**Answer:** Check the `Microsoft.Spark.Worker` version you are using.</span></span> <span data-ttu-id="f2f15-172">**.NET Framework 4.6.1** と **.NET Core 2.1.x** の 2 つのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="f2f15-172">There are two versions: **.NET Framework 4.6.1** and **.NET Core 2.1.x**.</span></span> <span data-ttu-id="f2f15-173">`System.Runtime.Remoting.Contexts.Context` は .NET Framework のみ用であるため、この場合は、([ダウンロード](https://github.com/dotnet/spark/releases)可能な) `Microsoft.Spark.Worker.net461.win-x64-<version>` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2f15-173">In this case, `Microsoft.Spark.Worker.net461.win-x64-<version>` (which you can [download](https://github.com/dotnet/spark/releases)) should be used since `System.Runtime.Remoting.Contexts.Context` is only for .NET Framework.</span></span>

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a><span data-ttu-id="f2f15-174">YARN 上の UDF で spark アプリケーションはどのように実行できますか。</span><span class="sxs-lookup"><span data-stu-id="f2f15-174">How do I run my spark application with UDFs on YARN?</span></span> <span data-ttu-id="f2f15-175">どの環境変数とパラメーターを使用すればよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="f2f15-175">Which environment variables and parameters should I use?</span></span>

<span data-ttu-id="f2f15-176">**回答:** YARN で spark アプリケーションを起動するには、`spark.yarn.appMasterEnv.[EnvironmentVariableName]` のように環境変数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2f15-176">**Answer:** To launch the spark application on YARN, the environment variables should be specified as `spark.yarn.appMasterEnv.[EnvironmentVariableName]`.</span></span> <span data-ttu-id="f2f15-177">`spark-submit` の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f2f15-177">Please see below as an example using `spark-submit`:</span></span>

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a><span data-ttu-id="f2f15-178">次の手順</span><span class="sxs-lookup"><span data-stu-id="f2f15-178">Next steps</span></span>

* [<span data-ttu-id="f2f15-179">.NET for Apache Spark の概要</span><span class="sxs-lookup"><span data-stu-id="f2f15-179">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="f2f15-180">Windows で .NET for Apache Spark アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="f2f15-180">Debug a .NET for Apache Spark application on Windows</span></span>](../how-to-guides/debug.md)