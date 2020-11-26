---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 7ef31a188e1564da47ea1e7323cdd4cd5ef5be60
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236677"
---
# <a name="msmq"></a><span data-ttu-id="64cd0-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="64cd0-102">MSMQ</span></span>

<span data-ttu-id="64cd0-103">MSMQ アプリケーションでは、キューに置かれたチャネルから MSMQに、および MSMQ からキューに置かれたチャネルに追加アクティビティは転送されません。</span><span class="sxs-lookup"><span data-stu-id="64cd0-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="64cd0-104">さらに、MSMQ メッセージ ID と SOAP メッセージ ID (および、存在する場合はアクティビティ ID) は、キューに置かれたチャネルのトレースの一部として送信操作を追跡されます。</span><span class="sxs-lookup"><span data-stu-id="64cd0-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="64cd0-105">MSMQ メッセージ ID と SOAP メッセージ ID (および、存在する場合はアクティビティ ID) は、キューに置かれたチャネルのトレースの一部として受信操作を追跡されます。</span><span class="sxs-lookup"><span data-stu-id="64cd0-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="64cd0-106">受信操作で必要な転送については、他のトランスポートと同様に実行されます (受信バイト->プロセス メッセージ-> 操作)。</span><span class="sxs-lookup"><span data-stu-id="64cd0-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
