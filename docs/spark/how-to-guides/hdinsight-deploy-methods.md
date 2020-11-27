---
title: .NET for Apache Spark ジョブを Azure HDInsight に送信する
description: spark-submit と Apache Livy を使用して、.NET for Apache Spark ジョブを Azure HDInsight に送信する方法について説明します。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 74be4ecf33a9a881633da0630fa1c1a4bf0b19c6
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688164"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="24996-103">.NET for Apache Spark ジョブを Azure HDInsight に送信する</span><span class="sxs-lookup"><span data-stu-id="24996-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="24996-104">.NET for Apache Spark ジョブを HDInsight に展開するには、`spark-submit` と Apache Livy の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="24996-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="24996-105">spark-submit を使用して展開する</span><span class="sxs-lookup"><span data-stu-id="24996-105">Deploy using spark-submit</span></span>

<span data-ttu-id="24996-106">[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) コマンドを使用して、.NET for Apache Spark ジョブを Azure HDInsight に送信できます。</span><span class="sxs-lookup"><span data-stu-id="24996-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="24996-107">Azure portal の HDInsight Spark クラスターに移動し、 **[SSH およびクラスターのログイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="24996-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="24996-108">ssh ログイン情報をコピーし、ログインをターミナルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="24996-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="24996-109">クラスターの作成時に設定したパスワードを使用してクラスターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="24996-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="24996-110">Ubuntu および Spark のウェルカム メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="24996-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="24996-111">**spark-submit** コマンドを使用して、HDInsight クラスターでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="24996-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="24996-112">このスクリプト例の **mycontainer** と **mystorageaccount** を、実際の BLOB コンテナーの名前とストレージ アカウントに置き換えることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="24996-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="24996-113">また、microsoft-spark jar を、使用中の Spark および .NET for Apache Spark のバージョンに置き換えることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="24996-113">Also remember to replace the microsoft-spark jar with the version of Spark and .NET for Apache Spark being used.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="24996-114">Apache Livy を使用して展開する</span><span class="sxs-lookup"><span data-stu-id="24996-114">Deploy using Apache Livy</span></span>

<span data-ttu-id="24996-115">[Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) を使用して、.NET for Apache Spark ジョブを Azure HDInsight Spark クラスターに送信することができます。</span><span class="sxs-lookup"><span data-stu-id="24996-115">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="24996-116">詳細については、[Apache Livy を使用したリモート ジョブ](/azure/hdinsight/spark/apache-spark-livy-rest-interface) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="24996-116">For more information, see [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="24996-117">Linux では、`curl` を使用して次のコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="24996-117">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="24996-118">次の手順</span><span class="sxs-lookup"><span data-stu-id="24996-118">Next steps</span></span>

* [<span data-ttu-id="24996-119">.NET for Apache Spark の概要</span><span class="sxs-lookup"><span data-stu-id="24996-119">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="24996-120">.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする</span><span class="sxs-lookup"><span data-stu-id="24996-120">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="24996-121">HDInsight のドキュメント</span><span class="sxs-lookup"><span data-stu-id="24996-121">HDInsight Documentation</span></span>](/azure/hdinsight/)
