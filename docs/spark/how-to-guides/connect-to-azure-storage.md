---
title: ローカル コンピューターからリモート ストレージに接続する
description: ローカル コンピューターから .NET for Apache Spark を使用して Azure Storage アカウントに接続します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dc0c3b44279756596f3d456616821e690710ae04
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224014"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a><span data-ttu-id="39a91-103">Azure Data Lake Storage Gen 2 または WASB アカウントに接続する</span><span class="sxs-lookup"><span data-stu-id="39a91-103">Connect to Azure Data Lake Storage Gen 2 or WASB account</span></span>

<span data-ttu-id="39a91-104">この記事では、Windows マシン上のローカルで実行されている [.NET for Apache Spark](https://github.com/dotnet/spark) のインスタンスを介して、Azure Data Lake Storage (ADLS) Gen 2 または Windows Azure Storage Blob (WASB) アカウントに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39a91-104">In this article, you learn how to connect to an Azure Data Lake Storage (ADLS) Gen 2 or Windows Azure Storage Blob (WASB) account through an instance of [.NET for Apache Spark](https://github.com/dotnet/spark) running locally on your Windows machine.</span></span>

## <a name="set-up-the-environment"></a><span data-ttu-id="39a91-105">環境を設定する</span><span class="sxs-lookup"><span data-stu-id="39a91-105">Set up the environment</span></span>

1. <span data-ttu-id="39a91-106">Hadoop を使用せずにビルドされた Apache Spark ディストリビューションを[公式 Web サイト](https://archive.apache.org/dist/spark/) ([.NET for Apache Spark でサポートされている](https://github.com/dotnet/spark#supported-apache-spark)バージョンを選択してください) からダウンロードし、ディレクトリに展開します。</span><span class="sxs-lookup"><span data-stu-id="39a91-106">Download the Apache Spark distribution built without Hadoop from [official website](https://archive.apache.org/dist/spark/) (choose a version [supported by .NET for Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)), and extract it to a directory.</span></span> <span data-ttu-id="39a91-107">このディレクトリに環境変数 `SPARK_HOME` を設定します。</span><span class="sxs-lookup"><span data-stu-id="39a91-107">Set the environment variable `SPARK_HOME` to this directory.</span></span>
2. <span data-ttu-id="39a91-108">[こちら](http://hadoop.apache.org/releases.html)から Apache Hadoop バイナリをダウンロードしてフォルダーに展開し、このフォルダーに `HADOOP_HOME` 環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="39a91-108">Download the Apache Hadoop binary from [here](http://hadoop.apache.org/releases.html) and extract to a folder, and set your `HADOOP_HOME` environment variable to this folder.</span></span>
3. <span data-ttu-id="39a91-109">[こちらの場所](https://github.com/cdarlint/winutils) (前の手順でインストールした Hadoop のバージョンに応じて異なります) から `winutils.exe` と `hadoop.dll` のファイルをダウンロードし、お使いの Hadoop の bin フォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="39a91-109">Download the `winutils.exe` and `hadoop.dll` files from [this location](https://github.com/cdarlint/winutils) (depending on the version of Hadoop installed in the previous step) and put them in the bin folder of your Hadoop.</span></span> <span data-ttu-id="39a91-110">すべての設定を正しく行うには、これらのバイナリが Windows 上に必要です (この詳細については、[こちらの Apache wiki](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems) を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="39a91-110">These binaries are needed on Windows in order to get everything setup correctly (this is explained in detail in the [Apache wiki here](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).</span></span>
4. <span data-ttu-id="39a91-111">`%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` ファイルに次の変更を加えて、Hadoop のインストールを構成します。</span><span class="sxs-lookup"><span data-stu-id="39a91-111">Configure your Hadoop installation by making the following changes to your `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` file:</span></span>
    1. <span data-ttu-id="39a91-112">DOS パスを使用して `JAVA_HOME` プロパティを設定します (Hadoop では `JAVA_HOME` 内のスペースが推奨されないため)。</span><span class="sxs-lookup"><span data-stu-id="39a91-112">Set the `JAVA_HOME` property using the DOS path (since Hadoop doesn't like spaces in `JAVA_HOME`).</span></span> <span data-ttu-id="39a91-113">これで次のようになります。`C:\Progra~1\Java\jdk1.8.0_241` (ローカル コンピューターにインストールされている任意のバージョンの Java を指します)。</span><span class="sxs-lookup"><span data-stu-id="39a91-113">This should look something like this: `C:\Progra~1\Java\jdk1.8.0_241` (Pointing to whatever version of Java you have installed on your local machine).</span></span>
    2. <span data-ttu-id="39a91-114">`%HADOOP_HOME%\share\hadoop\tools\lib\*` を `HADOOP_CLASSPATH` に追加します。</span><span class="sxs-lookup"><span data-stu-id="39a91-114">Append `%HADOOP_HOME%\share\hadoop\tools\lib\*` to `HADOOP_CLASSPATH`.</span></span>
    <span data-ttu-id="39a91-115">最終的な `hadoop-env.cmd` ファイルは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="39a91-115">Your final `hadoop-env.cmd` file should look something like this:</span></span>

    ![最終的な hadoop-env.cmd ファイル](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a><span data-ttu-id="39a91-117">Hadoop でストレージ アカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="39a91-117">Configure your storage account in Hadoop</span></span>

1. <span data-ttu-id="39a91-118">[Azure portal](https://portal.azure.com) を介して接続する ADLS Gen 2 または WASB ストレージ アカウントを開き、 **[設定]** ブレードの下にある **[アクセス キー]** パネルを開き、key1 の **[キー]** の値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="39a91-118">Open the ADLS Gen 2 or WASB storage account you want to connect to through the [Azure portal](https://portal.azure.com) and open the **Access keys** panel under the **Settings** blade and copy the value of **Key** from under key1.</span></span>
2. <span data-ttu-id="39a91-119">ここで、ADLS Gen2 アカウントにアクセスするように Hadoop を構成するには、クラスター全体の構成を含む `core-site.xml` (`%HADOOP_HOME%\etc\hadoop\` 内にあります) ファイルを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a91-119">Now in order to configure Hadoop to access your ADLS Gen2 account you would have to edit your `core-site.xml` (located in `%HADOOP_HOME%\etc\hadoop\` ) file which contains cluster-wide configuration.</span></span> <span data-ttu-id="39a91-120">このファイルの `<configuration>` タグ内に次のプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="39a91-120">Add the following properties inside the `<configuration>` tags in this file:</span></span>

    ```xml
    <configuration>
      <property>
        <name>fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>SharedKey</value>
        <description></description>
      </property>
      <property>
        <name>fs.azure.account.key.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>YOUR ACCESS KEY (copied from Step 1)</value>
        <description>The secret password. Never share these.</description>
      </property>
    </configuration>
    ```

    <span data-ttu-id="39a91-121">WASB アカウントに接続しようとしている場合は、プロパティ名の `dfs` を `blob` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="39a91-121">If you are trying to connect to a WASB account, replace `dfs` with `blob` in the property names.</span></span> <span data-ttu-id="39a91-122">たとえば、「 `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="39a91-122">For example, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span></span>
3. <span data-ttu-id="39a91-123">`%HADOOP_HOME%` ディレクトリから次のコマンドを実行することで、Hadoop からストレージ アカウントへの接続をテストできます。</span><span class="sxs-lookup"><span data-stu-id="39a91-123">You can test the connectivity to your Storage Account from Hadoop by running the following command from your `%HADOOP_HOME%` directory:</span></span>

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

<span data-ttu-id="39a91-124">これにより、URI に指定されたパスにあるすべてのファイルおよびフォルダーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39a91-124">This should display a list of all files/folders in the path provided by your URI.</span></span>

> [!NOTE]
> <span data-ttu-id="39a91-125">ストレージ アカウントに URI を派生させる形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="39a91-125">The format to derive the URI to your Storage account is as follows:</span></span>
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a><span data-ttu-id="39a91-126">ストレージ アカウントに接続する</span><span class="sxs-lookup"><span data-stu-id="39a91-126">Connect to your storage account</span></span>

1. <span data-ttu-id="39a91-127">上記のコマンドが動作した場合は、Spark を介してこのストレージ アカウントへのアクセスに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="39a91-127">If the above command worked, you can now move on to accessing this storage account through Spark.</span></span> <span data-ttu-id="39a91-128">まず、`%HADOOP_HOME%` 内のコマンドラインからコマンド `hadoop classpath` を実行し、出力をコピーします。</span><span class="sxs-lookup"><span data-stu-id="39a91-128">First run the command `hadoop classpath` from the commandline inside `%HADOOP_HOME%` and copy the output.</span></span>
2. <span data-ttu-id="39a91-129">手順 1 で実行したコマンドの出力を環境変数 `SPARK_DIST_CLASSPATH` の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="39a91-129">Set the output of the command run in Step 1 to the value of environment variable `SPARK_DIST_CLASSPATH`.</span></span>
3. <span data-ttu-id="39a91-130">これで、次の簡単な例に示すように、abfs URI を使用して Spark .NET を介して ADLS または WASB ストレージ アカウントにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="39a91-130">Now you should be able to access your ADLS or WASB storage account through Spark .NET using the abfs URI as shown in the simple example below.</span></span> <span data-ttu-id="39a91-131">(この例では、すべての Apache Spark インストールに用意されている標準の [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) サンプル ファイルを使用します。):</span><span class="sxs-lookup"><span data-stu-id="39a91-131">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.):</span></span>

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    <span data-ttu-id="39a91-132">表示される結果は、次のように DataFrame (`df`) です。</span><span class="sxs-lookup"><span data-stu-id="39a91-132">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
