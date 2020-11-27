---
title: SqlClient による LocalDB のサポート
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 55ab1346de6f5c14f15d01344a984c18edf30e02
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824481"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="19d08-102">SqlClient による LocalDB のサポート</span><span class="sxs-lookup"><span data-stu-id="19d08-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="19d08-103">この記事では、LocalDB データベースに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19d08-103">This article discusses how to connect to a LocalDB database.</span></span> <span data-ttu-id="19d08-104">LocalDB は SQL Server の軽量バージョンです。</span><span class="sxs-lookup"><span data-stu-id="19d08-104">LocalDB is a lightweight version of SQL Server.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="19d08-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="19d08-105">Remarks</span></span>
  
 <span data-ttu-id="19d08-106">LocalDB で実行できる操作の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19d08-106">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="19d08-107">sqllocaldb.exe または app.config ファイルを使用して LocalDB インスタンスを作成および開始する。</span><span class="sxs-lookup"><span data-stu-id="19d08-107">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="19d08-108">sqlcmd.exe を使用して LocalDB インスタンスにデータベースを追加および変更する。</span><span class="sxs-lookup"><span data-stu-id="19d08-108">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="19d08-109">たとえば、 `sqlcmd -S (localdb)\myinst`のようにします。</span><span class="sxs-lookup"><span data-stu-id="19d08-109">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="19d08-110">`AttachDBFilename` 接続文字列キーワードを使用して LocalDB インスタンスにデータベースを追加する。</span><span class="sxs-lookup"><span data-stu-id="19d08-110">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="19d08-111">`AttachDBFilename`を使用していて、 `Database` 接続文字列キーワードでデータベースの名前を指定しない場合、アプリケーションを閉じると、データベースは LocalDB インスタンスから削除されます。</span><span class="sxs-lookup"><span data-stu-id="19d08-111">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="19d08-112">接続文字列に LocalDB インスタンスを指定する。</span><span class="sxs-lookup"><span data-stu-id="19d08-112">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="19d08-113">たとえば、インスタンス名が `myInstance`の場合、接続文字列には次の行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="19d08-113">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="19d08-114">`User Instance=True` は LocalDB データベースに接続するときに使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="19d08-114">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
<span data-ttu-id="19d08-115">LocalDB のインストールの詳細については、「[SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19d08-115">For information about installing LocalDB, see [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span></span>
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="19d08-116">名前付きインスタンスをプログラムによって作成する</span><span class="sxs-lookup"><span data-stu-id="19d08-116">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="19d08-117">アプリケーションは、次のように名前付きインスタンスを作成してデータベースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="19d08-117">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="19d08-118">app.config ファイルに作成するための LocalDB インスタンスを次のように指定する。</span><span class="sxs-lookup"><span data-stu-id="19d08-118">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="19d08-119">インスタンスのバージョン番号は LocalDB インストールのバージョン番号と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="19d08-119">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- <span data-ttu-id="19d08-120">`server` 接続文字列キーワードを使用してインスタンス名を指定する。</span><span class="sxs-lookup"><span data-stu-id="19d08-120">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="19d08-121">`server` 接続文字列キーワードで指定されたインスタンス名は app.config ファイルで指定された名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19d08-121">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="19d08-122">.MDF ファイルを指定するには、 `AttachDBFilename` 接続文字列キーワードを使用する。</span><span class="sxs-lookup"><span data-stu-id="19d08-122">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d08-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="19d08-123">See also</span></span>

- [<span data-ttu-id="19d08-124">SQL Server の機能と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19d08-124">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="19d08-125">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="19d08-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
