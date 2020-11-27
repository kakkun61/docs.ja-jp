---
title: インスタンス エンコーディング オプション
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 416394eb346a7c82385da32a89bd54179b255cd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279897"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="b4b9d-102">インスタンス エンコーディング オプション</span><span class="sxs-lookup"><span data-stu-id="b4b9d-102">Instance Encoding Option</span></span>

<span data-ttu-id="b4b9d-103">SQL ワークフローインスタンスストアの **インスタンスエンコードオプション** プロパティを使用すると、永続性データベースに情報を保存する前に、sql 永続化プロバイダーで、GZip アルゴリズムを使用してワークフローインスタンスの状態情報を圧縮するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="b4b9d-104">このプロパティに使用できる値は GZip と None です。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="b4b9d-105">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-105">The default value is None.</span></span> <span data-ttu-id="b4b9d-106">これらのオプションを次の一覧で説明します。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-106">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="b4b9d-107">**GZip**。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-107">**GZip**.</span></span> <span data-ttu-id="b4b9d-108">永続化プロバイダーは、永続性データベースに状態情報を永続化する前に、GZip アルゴリズムを使用して状態情報をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="b4b9d-109">**なし**。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-109">**None**.</span></span> <span data-ttu-id="b4b9d-110">永続化プロバイダーは、永続性データベースに情報を保存する前は、状態情報をエンコードしません。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="b4b9d-111">GZip を使用してワークフロー インスタンスの状態情報をエンコードすると、SQL データベースのメモリ消費量が減ります。また、ワークフロー サービス ホストが実行されているコンピューターとは異なるコンピューターがネットワーク上にあり、そこにデータベースが配置されている場合、ネットワークの消費量も減ります。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="b4b9d-112">一般的なガイダンスとして、ワークフローインスタンスの状態が小さい場合は、 **インスタンスエンコーディングオプション** プロパティを **None** に設定します。</span><span class="sxs-lookup"><span data-stu-id="b4b9d-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
