---
title: 'サービス : 承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
ms.openlocfilehash: 32b0a62ecf9364270f5580787b7e129af5ac80b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236911"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="6ff2b-102">サービス : 承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="6ff2b-102">Service: Security Calls Not Authorized</span></span>

<span data-ttu-id="6ff2b-103">カウンター名 : 承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="6ff2b-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6ff2b-104">Description</span><span class="sxs-lookup"><span data-stu-id="6ff2b-104">Description</span></span>  

 <span data-ttu-id="6ff2b-105">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="6ff2b-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="6ff2b-106">受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="6ff2b-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
