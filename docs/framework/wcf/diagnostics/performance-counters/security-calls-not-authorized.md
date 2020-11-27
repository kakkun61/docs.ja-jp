---
title: 承認されていないセキュリティ呼び出し
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 5575b108353e9c434ff01e76edc127e8691f0bf4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276127"
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="7049b-102">承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="7049b-102">Security Calls Not Authorized</span></span>

<span data-ttu-id="7049b-103">カウンター名 : 承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="7049b-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7049b-104">Description</span><span class="sxs-lookup"><span data-stu-id="7049b-104">Description</span></span>  

 <span data-ttu-id="7049b-105">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="7049b-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="7049b-106">受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="7049b-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
