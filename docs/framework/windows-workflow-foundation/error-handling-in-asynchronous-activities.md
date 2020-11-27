---
title: 非同期アクティビティ内のエラー処理
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 2c214ce1d0f435cda79deb6976ca9196a5d7aee1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280261"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="eea85-102">非同期アクティビティ内のエラー処理</span><span class="sxs-lookup"><span data-stu-id="eea85-102">Error handling in asynchronous activities</span></span>

<span data-ttu-id="eea85-103"><xref:System.Activities.AsyncCodeActivity> でのエラー処理には、アクティビティのコールバック システムを使用したエラーの送信が含まれています。</span><span class="sxs-lookup"><span data-stu-id="eea85-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="eea85-104">このトピックでは、SendMail アクティビティのサンプルを使用してホストへ非同期操作でスローされるエラーを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eea85-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="eea85-105">非同期アクティビティでスローされたエラーをホストへ返す</span><span class="sxs-lookup"><span data-stu-id="eea85-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  

 <span data-ttu-id="eea85-106">SendMail アクティビティ サンプルでの、ホストに返される非同期操作でのエラーのルーティングの手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eea85-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="eea85-107">Exception プロパティを `SendMailAsyncResult` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="eea85-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="eea85-108">スローされたエラーを `SendCompleted` イベント ハンドラー内でそのプロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="eea85-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="eea85-109">`EndExecute` イベント ハンドラー内で例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="eea85-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="eea85-110">結果として得られるコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="eea85-110">The resulting code is as follows.</span></span>  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;
        }  
    }  
```
