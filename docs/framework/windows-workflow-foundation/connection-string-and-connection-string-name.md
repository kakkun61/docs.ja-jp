---
title: 接続文字列と接続文字列名
ms.date: 03/30/2017
ms.assetid: 473e7a3c-c88a-4a01-914a-bea82ba42866
ms.openlocfilehash: 5352dbac09565e872493581a2809409b156d1300
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248865"
---
# <a name="connection-string-and-connection-string-name"></a><span data-ttu-id="dd2dd-102">接続文字列と接続文字列名</span><span class="sxs-lookup"><span data-stu-id="dd2dd-102">Connection String and Connection String Name</span></span>

<span data-ttu-id="dd2dd-103">**接続文字列** プロパティは、SQL Workflow Instance Store が永続性データベースに接続するために使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd2dd-103">**Connection String** property specifies the connection string that the SQL Workflow Instance Store should use to connect to a persistence database.</span></span> <span data-ttu-id="dd2dd-104">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="dd2dd-104">This parameter is an optional parameter.</span></span> <span data-ttu-id="dd2dd-105">"**接続文字列名**" プロパティは、SQL Workflow Instance Store が永続性データベースに接続するために使用する名前付き接続文字列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd2dd-105">**Connection String Name** property specifies the name of the named connection string that the SQL Workflow Instance Store should use to connect to the persistence database.</span></span> <span data-ttu-id="dd2dd-106">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="dd2dd-106">This parameter is an optional parameter.</span></span> <span data-ttu-id="dd2dd-107">SQL Workflow Instance Store で既定の名前付き接続文字列 **DefaultSqlWorkflowInstanceStoreConnectionString** を使用しない場合は、"接続文字列名" プロパティまたは "接続文字列" プロパティの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd2dd-107">You should specify a value for the Connection String Name property or the Connection String property if you do not want the SQL Workflow Instance Store to use the default named connection string **DefaultSqlWorkflowInstanceStoreConnectionString**.</span></span>
