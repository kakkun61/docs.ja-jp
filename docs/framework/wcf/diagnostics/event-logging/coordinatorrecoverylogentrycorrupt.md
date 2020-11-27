---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: c3174e70d42385923674a3db5f696a0f64eda29f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295362"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="b9777-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="b9777-102">CoordinatorRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="b9777-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="b9777-103">Id: 139</span></span>  
  
 <span data-ttu-id="b9777-104">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="b9777-104">Severity: Error</span></span>  
  
 <span data-ttu-id="b9777-105">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="b9777-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="b9777-106">Description</span><span class="sxs-lookup"><span data-stu-id="b9777-106">Description</span></span>  

 <span data-ttu-id="b9777-107">このイベントは、コーディネーターの回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="b9777-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="b9777-108">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="b9777-108">Data loss may result from this error.</span></span> <span data-ttu-id="b9777-109">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9777-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9777-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9777-110">See also</span></span>

- [<span data-ttu-id="b9777-111">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="b9777-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="b9777-112">イベント一覧</span><span class="sxs-lookup"><span data-stu-id="b9777-112">Events General Reference</span></span>](events-general-reference.md)
