---
title: Single コンカレンシー モードでメッセージを順番に処理する
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: d70087a6dc1501f9a7f7ed057eae3dad181761ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248020"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="dbf1d-102">Single コンカレンシー モードでメッセージを順番に処理する</span><span class="sxs-lookup"><span data-stu-id="dbf1d-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>

<span data-ttu-id="dbf1d-103">基になるチャネルがセッションフルの場合を除き、WCF はメッセージの処理順序について一切保証しません。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="dbf1d-104">たとえば、セッションフルチャネルではなく MsmqInputChannel を使用する WCF サービスでは、メッセージを順番に処理することができません。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="dbf1d-105">場合によっては、開発者が注文処理の動作を必要としても、セッションを使用しないようにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="dbf1d-106">このトピックでは、サービスが Single コンカレンシー モードで実行されている場合にこの動作を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="dbf1d-107">順番に従ったメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="dbf1d-107">In-order Message Processing</span></span>  

 <span data-ttu-id="dbf1d-108"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> という名前の新しい属性が <xref:System.ServiceModel.ServiceBehaviorAttribute> に追加されました。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="dbf1d-109"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> を true に設定し、<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> を <xref:System.ServiceModel.ConcurrencyMode.Single> に設定すると、サービスに送信されたメッセージは順番に処理されます。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="dbf1d-110">次のコードは、これらの属性の設定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="dbf1d-111"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> をその他の値に設定すると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="dbf1d-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf1d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbf1d-112">See also</span></span>

- [<span data-ttu-id="dbf1d-113">セッション、インスタンス化、およびコンカレンシー</span><span class="sxs-lookup"><span data-stu-id="dbf1d-113">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="dbf1d-114">コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="dbf1d-114">Concurrency</span></span>](../samples/concurrency.md)
