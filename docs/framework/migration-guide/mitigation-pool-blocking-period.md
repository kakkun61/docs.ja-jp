---
title: '軽減策: プールのロック期間'
description: Azure SQL データベースへの接続について、接続プールのブロック期間が削除されたことによって引き起こされた問題を軽減する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 270a71790f7a602df003415e9dc6dbf784cffdd7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276569"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="8b9e7-103">軽減策:プールのロック期間</span><span class="sxs-lookup"><span data-stu-id="8b9e7-103">Mitigation: Pool Blocking Period</span></span>

<span data-ttu-id="8b9e7-104">Azure SQL データベースへの接続に関して、接続プールのブロック期間が削除されました。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-104">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="8b9e7-105">その他の説明</span><span class="sxs-lookup"><span data-stu-id="8b9e7-105">Additional description</span></span>  

 <span data-ttu-id="8b9e7-106">.NET Framework 4.6.1 以前のバージョンでは、データベースへの接続時にアプリで一時的な接続エラーが発生した場合、接続はすぐに再試行されません。接続プールがエラーをキャッシュし、5 秒間から 1 分間エラーを再スローするためです。詳細については、「[SQL Server の接続プール (ADO.NET)](../data/adonet/sql-server-connection-pooling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-106">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="8b9e7-107">この動作は、Azure SQL データベースへの接続時に問題となります。多くの場合、一時的なエラーが発生し、通常数秒内に回復します。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-107">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="8b9e7-108">接続プールのブロック機能を使用すると、データベースが使用可能な場合でも、長い期間にわたってアプリがデータベースに接続できなくなるということです。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-108">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="8b9e7-109">この動作が特に問題となるのは、Azure SQL データベースに接続し、数秒内でレンダリングする必要がある Web アプリの場合です。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-109">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="8b9e7-110">.NET Framework 4.6.2 以降では、既知の Azure SQL データベースへの接続確立要求 (\*.database.windows.net、\*.database.chinacloudapi.cn、\*.database.usgovcloudapi.net、\*.database.cloudapi.de) の場合、接続確立のエラーはキャッシュされません。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-110">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="8b9e7-111">他のすべての接続を試みる場合は、接続プールのブロック期間が引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-111">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="8b9e7-112">影響</span><span class="sxs-lookup"><span data-stu-id="8b9e7-112">Impact</span></span>  

 <span data-ttu-id="8b9e7-113">この変更により、Azure SQL データベースへの接続確立がすぐに再試行するされるため、クラウド対応アプリケーションのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-113">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="8b9e7-114">軽減策</span><span class="sxs-lookup"><span data-stu-id="8b9e7-114">Mitigation</span></span>  

 <span data-ttu-id="8b9e7-115">この変更から悪影響を受けるアプリの場合、新しい <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> プロパティを設定することで、接続プールのブロック期間を構成できます。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-115">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="8b9e7-116">プロパティ値が <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> 列挙型のメンバーである場合、次の 3 つの値のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-116">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="8b9e7-117"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> プロパティを <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> に設定して、以前の動作を復元することができます。</span><span class="sxs-lookup"><span data-stu-id="8b9e7-117">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b9e7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b9e7-118">See also</span></span>

- [<span data-ttu-id="8b9e7-119">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="8b9e7-119">Application compatibility</span></span>](application-compatibility.md)
