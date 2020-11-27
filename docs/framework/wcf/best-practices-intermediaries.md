---
title: ベスト プラクティス:中継局
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 57be78681147dfc5bc37701a76c1347040f5da1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96277895"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="3f22c-102">ベスト プラクティス:中継局</span><span class="sxs-lookup"><span data-stu-id="3f22c-102">Best Practices: Intermediaries</span></span>

<span data-ttu-id="3f22c-103">中継局のサービス側のチャネルが適切に閉じられていることを確認するために中継局を呼び出すときは、エラーが正しく処理されるよう注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f22c-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="3f22c-104">次のシナリオで考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="3f22c-104">Consider the following scenario.</span></span> <span data-ttu-id="3f22c-105">クライアントが中継局を呼び出すと、中継局はバックエンド サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3f22c-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="3f22c-106">バックエンド サービスはエラー コントラクトを定義しないので、そのサービスからスローされるエラーはすべて型指定されていないエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="3f22c-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="3f22c-107">バックエンドサービスが <xref:System.ApplicationException> をスローし、WCF がサービス側チャネルを正しく中止します。</span><span class="sxs-lookup"><span data-stu-id="3f22c-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="3f22c-108"><xref:System.ApplicationException> が <xref:System.ServiceModel.FaultException> として中継局にスローされます。</span><span class="sxs-lookup"><span data-stu-id="3f22c-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="3f22c-109">中継局は <xref:System.ApplicationException> を再スローします。</span><span class="sxs-lookup"><span data-stu-id="3f22c-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="3f22c-110">WCF はこれを中継局からの型指定されていないエラーとして解釈し、クライアントに転送します。</span><span class="sxs-lookup"><span data-stu-id="3f22c-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="3f22c-111">エラーを受け取ると、中継局とクライアントのクライアント側チャネルはエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="3f22c-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="3f22c-112">ただし、WCF にはエラーが致命的であることが通知されていないため、中継局のサービス側チャネルは開いたままです。</span><span class="sxs-lookup"><span data-stu-id="3f22c-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="3f22c-113">このシナリオのベスト プラクティスとしては、次のコード スニペットに示すように、サービスからスローされたエラーが致命的かどうかを検出し、致命的である場合は、中継局のサービス側チャネルでエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="3f22c-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f22c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f22c-114">See also</span></span>

- [<span data-ttu-id="3f22c-115">WCF エラー処理</span><span class="sxs-lookup"><span data-stu-id="3f22c-115">WCF Error Handling</span></span>](wcf-error-handling.md)
- [<span data-ttu-id="3f22c-116">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="3f22c-116">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
