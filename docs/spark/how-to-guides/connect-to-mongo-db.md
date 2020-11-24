---
title: .NET for Apache Spark を MongoDB に接続する
description: .NET for Apache Spark アプリケーションから MongoDB インスタンスに接続する方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 945e494e8a027d438bf4659d989da6033a13f6f0
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687604"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a><span data-ttu-id="bc698-103">.NET for Apache Spark を MongoDB に接続する</span><span class="sxs-lookup"><span data-stu-id="bc698-103">Connect .NET for Apache Spark to MongoDB</span></span>

<span data-ttu-id="bc698-104">この記事では、.NET for Apache Spark アプリケーションから MongoDB インスタンスに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc698-104">In this article, you learn how to connect to a MongoDB instance from your .NET for Apache Spark application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bc698-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="bc698-105">Prerequisites</span></span>

1. <span data-ttu-id="bc698-106">[データベースといくつかのコレクション](https://docs.mongodb.com/manual/core/databases-and-collections/)が追加された稼働中の MongoDB サーバー (ローカル サーバーの場合は[こちらのコミュニティ サーバー](https://www.mongodb.com/try/download/community)をダウンロードします。または、クラウド MongoDB サービスの場合は [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) を試すことができます)。</span><span class="sxs-lookup"><span data-stu-id="bc698-106">Have a MongoDB server up and running with a [database and some collection](https://docs.mongodb.com/manual/core/databases-and-collections/) added to it (Download [this community server](https://www.mongodb.com/try/download/community) for a local server or you can try [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for a cloud MongoDB service.)</span></span>

## <a name="set-up-your-mongodb-instance"></a><span data-ttu-id="bc698-107">MongoDB インスタンスを設定する</span><span class="sxs-lookup"><span data-stu-id="bc698-107">Set up your MongoDB instance</span></span>

<span data-ttu-id="bc698-108">.NET for Apache Spark が MongoDB インスタンスと通信できるようにするには、次の手順に従って、正しく設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc698-108">In order to get .NET for Apache Spark to talk to your MongoDB instance you need to make sure it is set up correctly by doing the following:</span></span>

1. <span data-ttu-id="bc698-109">アプリケーションで接続に使用されるユーザー名とパスワードを作成し、mongo シェルをから次のコマンドを使用してユーザーに必要なアクセス許可とロールを付与します。</span><span class="sxs-lookup"><span data-stu-id="bc698-109">Create a username and password for your application to connect through, and give the user the necessary permissions/roles using the following command through mongo shell:</span></span>

    ```bash
    use database
    db.createUser(
      {
        user: "mySparkUser",
        pwd: "<password>",
        roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
      }
    )
    ```

2. <span data-ttu-id="bc698-110">.NET for Apache Spark アプリケーションが実行されているマシンの IP アドレスが、MongoDB サーバーが接続できるようにホワイトリストに登録されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc698-110">Make sure the IP address of the machine your .NET for Apache Spark application is running on is whitelisted for the MongoDB server to be able to connect to.</span></span> <span data-ttu-id="bc698-111">その方法については、[こちらのガイド](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc698-111">You can refer to [this guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) to learn how to do that.</span></span>

## <a name="configure-your-net-for-apache-spark-application"></a><span data-ttu-id="bc698-112">.NET for Apache Spark アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="bc698-112">Configure your .NET for Apache Spark application</span></span>

1. <span data-ttu-id="bc698-113">次の変数を設定して、MongoDB インスタンスと通信し、コレクションから読み取るようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="bc698-113">Have the following variables set to configure your application to talk to the MongoDB instance and read from a collection.</span></span>
    1. <span data-ttu-id="bc698-114">**authURI**:"アプリケーションが必要な MongoDB インスタンスに接続することを承認する接続文字列"。</span><span class="sxs-lookup"><span data-stu-id="bc698-114">**authURI**: "Connection string authorizing your application to connect to the required MongoDB instance".</span></span> <span data-ttu-id="bc698-115">この形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bc698-115">The format for that is as follows:</span></span>

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. <span data-ttu-id="bc698-116">**username**:前のセクションの手順 1 で作成したアカウントのユーザー名</span><span class="sxs-lookup"><span data-stu-id="bc698-116">**username**: Username of the account you created in Step 1 of the previous section</span></span>
    3. <span data-ttu-id="bc698-117">**password**:作成したユーザー アカウントのパスワード</span><span class="sxs-lookup"><span data-stu-id="bc698-117">**password**: Password of the user account created</span></span>
    4. <span data-ttu-id="bc698-118">**cluster_address**: MongoDB クラスターのホスト名またはアドレス</span><span class="sxs-lookup"><span data-stu-id="bc698-118">**cluster_address**: hostname/address of your MongoDB cluster</span></span>
    5. <span data-ttu-id="bc698-119">**database**:接続先の MongoDB データベース</span><span class="sxs-lookup"><span data-stu-id="bc698-119">**database**: The MongoDB database you want to connect to</span></span>
    6. <span data-ttu-id="bc698-120">**collection**:読み取る MongoDB コレクション。</span><span class="sxs-lookup"><span data-stu-id="bc698-120">**collection**: The MongoDB collection you want to read.</span></span> <span data-ttu-id="bc698-121">(この例では、すべての Apache Spark インストールに用意されている標準の [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) サンプル ファイルを使用します)。</span><span class="sxs-lookup"><span data-stu-id="bc698-121">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.)</span></span>

2. <span data-ttu-id="bc698-122">次の簡単なコード スニペットに示すように、`com.mongodb.spark.sql.DefaultSource` 形式は `spark.Read()` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc698-122">Use the `com.mongodb.spark.sql.DefaultSource` format is `spark.Read()` as shown below in a simple code snippet:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            var authURI = "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>?retryWrites=true&w=majority";
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Connect to Mongo DB example")
                .Config("spark.mongodb.input.uri", authURI)
                .GetOrCreate();

            DataFrame df = spark.Read().Format("com.mongodb.spark.sql.DefaultSource").Load();
            df.PrintSchema();
            df.Show();
            spark.Stop();
        }
    }
    ```

## <a name="run-your-application"></a><span data-ttu-id="bc698-123">アプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="bc698-123">Run your application</span></span>

<span data-ttu-id="bc698-124">.NET for Apache Spark アプリケーションを実行するには、sbt プロジェクトの `build.sbt` で `libraryDependency` を使用して、Spark プロジェクトのビルド定義の一環として `mongo-spark-connector` モジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="bc698-124">In order to run your .NET for Apache Spark application, you should define the `mongo-spark-connector` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="bc698-125">`spark-submit` (または `spark-shell`) などの Spark 環境では、次のように `--packages` コマンドライン オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc698-125">For Spark environments such as `spark-submit` (or `spark-shell`) you should use the `--packages` command-line option like so:</span></span>

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar yourApp.exe
```

> [!NOTE]
> <span data-ttu-id="bc698-126">実行する Spark のバージョンに合わせて、パッケージのバージョンを必ず含めてください。</span><span class="sxs-lookup"><span data-stu-id="bc698-126">Make sure to include the package version in accordance with the version of Spark being run.</span></span>

<span data-ttu-id="bc698-127">表示される結果は、次のように DataFrame (`df`) です。</span><span class="sxs-lookup"><span data-stu-id="bc698-127">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
