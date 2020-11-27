---
title: セキュリティ ネゴシエーションとタイムアウト
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 4ccc7e5539b1a772be6f9edb5a4cb4d94a8d1c1b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275984"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="cce38-102">セキュリティ ネゴシエーションとタイムアウト</span><span class="sxs-lookup"><span data-stu-id="cce38-102">Security Negotiation and Timeouts</span></span>

<span data-ttu-id="cce38-103">クライアントとサービスが認証されると、Windows Communication Foundation (WCF) は、認証の一部としてサービス資格情報がネゴシエートされるモードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cce38-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="cce38-104">このようなシナリオでは、サービス資格情報をクライアントに反映させるために、クライアントとサービスの間でマルチレッグ交換が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cce38-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="cce38-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> プロパティは、マルチレッグ交換の完了に要する時間を制御します。</span><span class="sxs-lookup"><span data-stu-id="cce38-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="cce38-106">ただし、このタイムアウトは、実際に、単一の要求 - 応答よりも長い時間が交換にかかる場合のみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cce38-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="cce38-107">単一のラウンド トリップでネゴシエーションが完了する場合、このタイムアウトは適用されません。</span><span class="sxs-lookup"><span data-stu-id="cce38-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce38-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="cce38-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="cce38-109">方法: 時刻のずれの最大値を設定する</span><span class="sxs-lookup"><span data-stu-id="cce38-109">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)
