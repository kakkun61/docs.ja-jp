---
title: '方法: チャネル ファクトリを作成および使用して、チャネルを作成および管理する'
ms.date: 03/30/2017
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
ms.openlocfilehash: 44b0f45d1a340b8e8229ded827ad3ded738ae677
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256782"
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a><span data-ttu-id="0c500-102">方法: チャネル ファクトリを作成および使用して、チャネルを作成および管理する</span><span class="sxs-lookup"><span data-stu-id="0c500-102">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>

<span data-ttu-id="0c500-103"><xref:System.ServiceModel.DuplexChannelFactory%601> クラスは、クライアントがサービス エンドポイントとの間でメッセージを送受信するために使用する、さまざまな種類の双方向チャネルを作成したり、管理したりする手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="0c500-103">The <xref:System.ServiceModel.DuplexChannelFactory%601> class provides the means to create and manage duplex channels of different types that clients use to send and receive messages to and from service endpoints.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c500-104">例</span><span class="sxs-lookup"><span data-stu-id="0c500-104">Example</span></span>  

 <span data-ttu-id="0c500-105">次のコードは、チャネル ファクトリを作成および使用して、チャネルを作成および管理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0c500-105">The following code shows how to create a channel factory and use it to create and manage channels.</span></span>  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0c500-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c500-106">See also</span></span>

- <xref:System.ServiceModel.DuplexChannelFactory%601>
