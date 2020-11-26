---
title: HTTP、TCP、または名前付きパイプを使用した非同期シナリオ
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 00213c8d117f4319d7e29312dd0b9805d916231a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244146"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="62e94-102">HTTP、TCP、または名前付きパイプを使用した非同期シナリオ</span><span class="sxs-lookup"><span data-stu-id="62e94-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>

<span data-ttu-id="62e94-103">ここでは、マルチスレッド要求で HTTP、TCP、または名前付きパイプを使用したときの、さまざまな非同期要求/応答シナリオでのアクティビティおよび転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="62e94-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="62e94-104">エラーを伴わない非同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="62e94-104">Asynchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="62e94-105">ここでは、マルチスレッド クライアントを使用したときの、非同期要求/応答シナリオでのアクティビティおよび転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="62e94-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="62e94-106">呼び出し元アクティビティは、`beginCall` が返され、`endCall` が返されると終了します。</span><span class="sxs-lookup"><span data-stu-id="62e94-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="62e94-107">コールバックが呼び出されたときは、そのコールバックが返されます。</span><span class="sxs-lookup"><span data-stu-id="62e94-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="62e94-108">呼び出されたアクティビティは、`beginCall` が返され、`endCall` が返されると終了します。または、そのアクティビティからコールバックが呼び出された場合は、コールバックが返されると終了します。</span><span class="sxs-lookup"><span data-stu-id="62e94-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="62e94-109">コールバックを伴わない非同期クライアント</span><span class="sxs-lookup"><span data-stu-id="62e94-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="62e94-110">HTTP を使用して、両方の側で伝達が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="62e94-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  

 ![コールバックのない非同期クライアント。両側で propagateActivity が true に設定されています。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="62e94-112">`propagateActivity=true`の場合、"メッセージは、転送先の ProcessAction アクティビティを示します。</span><span class="sxs-lookup"><span data-stu-id="62e94-112">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="62e94-113">HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="62e94-113">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="62e94-114">HTTP を使用して、両方の側で伝達が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="62e94-114">Propagation is Disabled on Either Sides, using HTTP</span></span>  

 <span data-ttu-id="62e94-115">`propagateActivity=false`どちらの側でも、"メッセージは、転送先の ProcessAction アクティビティを示しません。</span><span class="sxs-lookup"><span data-stu-id="62e94-115">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="62e94-116">したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="62e94-116">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="62e94-117">非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。</span><span class="sxs-lookup"><span data-stu-id="62e94-117">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="62e94-118">その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。</span><span class="sxs-lookup"><span data-stu-id="62e94-118">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![いずれかの側で propagateActivity が false に設定されているコールバックのない非同期クライアント。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="62e94-120">HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="62e94-120">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="62e94-121">プロセスアクションアクティビティは、 `propagateActivity=false` 呼び出し元または呼び出し先の場合、および応答メッセージに Action ヘッダーが含まれていない場合に、非同期クライアントで作成されます。</span><span class="sxs-lookup"><span data-stu-id="62e94-121">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="62e94-122">TCP または名前付きパイプを使用して、両方の側で伝達が有効になっている場合</span><span class="sxs-lookup"><span data-stu-id="62e94-122">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  

 ![コールバックのない非同期クライアント。両側と名前付きパイプ/TCP で propagateActivity が true に設定されています。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="62e94-124">名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="62e94-124">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="62e94-125">最初のイメージに似て `propagateActivity=true` います。の場合、"メッセージは、転送先の ProcessAction アクティビティを示します。</span><span class="sxs-lookup"><span data-stu-id="62e94-125">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="62e94-126">TCP または名前付きパイプを使用して、両方の側で伝達が無効になっている場合</span><span class="sxs-lookup"><span data-stu-id="62e94-126">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  

 <span data-ttu-id="62e94-127">名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。</span><span class="sxs-lookup"><span data-stu-id="62e94-127">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="62e94-128">2番目のイメージに似て `propagateActivity=false` いますが、どちらの側でも、"メッセージは、転送先の ProcessAction アクティビティを示していません。</span><span class="sxs-lookup"><span data-stu-id="62e94-128">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="62e94-129">したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="62e94-129">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="62e94-130">非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。</span><span class="sxs-lookup"><span data-stu-id="62e94-130">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="62e94-131">その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。</span><span class="sxs-lookup"><span data-stu-id="62e94-131">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![コールバックのない非同期クライアント (サイドと名前付きパイプ/TCP で propagateActivity が false に設定されている場合)。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="62e94-133">コールバックを伴う非同期クライアント</span><span class="sxs-lookup"><span data-stu-id="62e94-133">Asynchronous client with Callback</span></span>  

 <span data-ttu-id="62e94-134">このシナリオでは、コールバックと `endCall` に対するアクティビティ G と A’、およびその転送 (送受信) が追加されています。</span><span class="sxs-lookup"><span data-stu-id="62e94-134">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="62e94-135">このセクションでは、で HTTP を使用する方法のみを示し `propagateActivity` = `true` ます。</span><span class="sxs-lookup"><span data-stu-id="62e94-135">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="62e94-136">ただし、追加のアクティビティと転送も、他のケース (つまり、 `propagateActivity` = `false` TCP または名前付きパイプを使用) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="62e94-136">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="62e94-137">クライアントがユーザー コードを呼び出して結果の準備が完了したことを通知すると、コールバックは新しいアクティビティ (G) を作成します。</span><span class="sxs-lookup"><span data-stu-id="62e94-137">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="62e94-138">ユーザー コードは、次に、コールバック内 (図 5 を参照) またはコールバック外 (図 6 を参照) で `endCall` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="62e94-138">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="62e94-139">どのユーザーアクティビティが呼び出されているかが不明であるため `endCall` 、このアクティビティにはというラベルが付けられ `A’` ます。</span><span class="sxs-lookup"><span data-stu-id="62e94-139">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="62e94-140">A’ と A が同じである場合もありますし、異なる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="62e94-140">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![コールバックのコールバックがある非同期クライアントを表示します。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![コールバックの外部のコールバックを持つ非同期クライアントを表示します。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="62e94-143">コールバックを伴う非同期サーバー</span><span class="sxs-lookup"><span data-stu-id="62e94-143">Asynchronous Server with Callback</span></span>  

 ![コールバックがある非同期サーバーを表示します。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="62e94-145">チャネル スタックは、"メッセージを受信" でクライアントをコールバックします。この処理のトレースは、"要求を処理" アクティビティ自体で出力されます。</span><span class="sxs-lookup"><span data-stu-id="62e94-145">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="62e94-146">エラーを伴う非同期要求/応答</span><span class="sxs-lookup"><span data-stu-id="62e94-146">Asynchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="62e94-147">エラー メッセージは、`endCall` 中に受信されます。</span><span class="sxs-lookup"><span data-stu-id="62e94-147">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="62e94-148">この点を除き、アクティビティおよび転送は前のシナリオと同様です。</span><span class="sxs-lookup"><span data-stu-id="62e94-148">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="62e94-149">エラーを伴う/伴わない非同期一方向要求/応答</span><span class="sxs-lookup"><span data-stu-id="62e94-149">Asynchronous One-Way with or without Errors</span></span>  

 <span data-ttu-id="62e94-150">クライアントに返される応答やエラーはありません。</span><span class="sxs-lookup"><span data-stu-id="62e94-150">No response or fault is returned to the client.</span></span>
