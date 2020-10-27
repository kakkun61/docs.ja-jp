---
title: .NET for Apache Spark を SQL Server に接続する
description: .NET for Apache Spark アプリケーションから SQL Server インスタンスに接続する方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: b20710000d8717b5df238aa9a782371fbe586037
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224034"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a><span data-ttu-id="e4dcb-103">.NET for Apache Spark を SQL Server に接続する</span><span class="sxs-lookup"><span data-stu-id="e4dcb-103">Connect .NET for Apache Spark to SQL Server</span></span>

<span data-ttu-id="e4dcb-104">この記事では、[.NET for Apache Spark](https://github.com/dotnet/spark) アプリケーションから SQL Server インスタンスに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-104">In this article, you learn how to connect to an SQL server instance from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

## <a name="configure-sql-server-to-grant-your-application-access"></a><span data-ttu-id="e4dcb-105">アプリケーションへのアクセスを許可するように SQL Server を構成する</span><span class="sxs-lookup"><span data-stu-id="e4dcb-105">Configure SQL Server to grant your application access</span></span>

1. <span data-ttu-id="e4dcb-106">SQL Server 認証を選択して、ログイン ユーザーとパスワードを SQL Server インスタンスに追加します。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-106">Add a login user and password choosing SQL Server authentication to your SQL Server instance.</span></span>
2. <span data-ttu-id="e4dcb-107">次に示すように、該当するデータベース レベルでログイン ユーザーに必要な権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-107">Give that login user necessary permissions at the relevant database level as shown below:</span></span>

    ![SQL Server 権限](./media/connect-external-sources/SqlServerAuth.png)

3. <span data-ttu-id="e4dcb-109">SQL Server の既定のポート `1433` がファイアウォールを通過できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-109">Make sure the default port for SQL Server `1433` is allowed through the firewall.</span></span>
4. <span data-ttu-id="e4dcb-110">次に示すように、SQL 構成マネージャーを開いて、ネットワーク構成で TCP/IP を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-110">Open SQL configure manager to enable TCP/IP through the network configuration as shown below:</span></span>

    ![SQL Server TCP/IP の有効化](./media/connect-external-sources/SqlServerTCPIP.png)

    <span data-ttu-id="e4dcb-112">また、上の **[プロトコル]** タブの下にあるの **[すべて受信待ち]** の値にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-112">Also note the value of **Listen All** in above tab under **Protocol** .</span></span>

5. <span data-ttu-id="e4dcb-113">`Listen All` が `No` に設定されている場合は、必要なすべての IP アドレスに対して TCP/IP ポートを 1433 に構成します。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-113">Configure the TCP/IP port to 1433 for all required IP addresses if the `Listen All` is set to `No`.</span></span> <span data-ttu-id="e4dcb-114">それ以外の場合は、[IPAll] の [TCP ポート] を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-114">Otherwise, set the TCP Port in IPAll.</span></span>

    ![SQL Server TCP/IP ポート](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a><span data-ttu-id="e4dcb-116">アプリケーションから SQL Server に接続する</span><span class="sxs-lookup"><span data-stu-id="e4dcb-116">Connect to SQL Server from your application</span></span>

1. <span data-ttu-id="e4dcb-117">ご使用のアプリケーションを介してデータベース接続を提供するには、Microsoft JDBC Driver for SQL Server を使用します ([この公式 Web サイト](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)からダウンロードしてください)。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-117">Use the Microsoft JDBC Driver for SQL Server to provide database connectivity through your application (download from [this official website](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)).</span></span>
2. <span data-ttu-id="e4dcb-118">ご使用のアプリケーションから SQL Server インスタンスとデータベースに接続するには、次の構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-118">Set the following configurations to connect to the SQL server instance and database from your application:</span></span>
    1. <span data-ttu-id="e4dcb-119">**connection_url** : これは、SQL Server インスタンスまたはデータベースへの接続に使用される URL です。形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-119">**connection_url** : This is the URL used to connect to the SQL server instance/database and has the following format:</span></span>

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. <span data-ttu-id="e4dcb-120">**dbtable** : アクセスされているテーブルの名前。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-120">**dbtable** : Name of table being accessed.</span></span>
    3. <span data-ttu-id="e4dcb-121">**user** : SQL Server の構成の手順 1 で設定したログイン ユーザー。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-121">**user** : Login user set up in Step 1 of configuring the SQL server.</span></span>
    4. <span data-ttu-id="e4dcb-122">**password** : SQL Server の構成の手順 1 で設定したパスワード。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-122">**password** : Password of user set up in Step 1 of configuring the SQL server.</span></span>
3. <span data-ttu-id="e4dcb-123">次に示すように、上記の構成をご使用のアプリケーション コードで使用して、テーブルからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e4dcb-123">Use the above configuration in your application code to read the data from a table as shown below:</span></span>

    ```csharp
    static void Main()
    {
        SparkSession spark = SparkSession
            .Builder()
            .AppName("Connect to SQL Server")
            .GetOrCreate();

        string connection_url = "<URL to connect to SQL server instance>";
        string dbtable = "<database table to access>";
        string user = "<Login user name>";
        string password = "<Login user password>";

        DataFrame jdbcDF = spark.Read()
            .Format("jdbc")
            .Option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
            .Option("url", connection_url)
            .Option("dbtable", dbtable)
            .Option("user", user)
            .Option("password", password).Load();
        jdbcDF.Show(); // Displays the content of the SQL table as a DataFrame
    }
    ```
