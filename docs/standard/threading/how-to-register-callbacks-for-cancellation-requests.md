---
title: キャンセル要求のコールバックを登録する
ms.date: 08/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: f551055fc6e5e4565329201e9e0be6e4a83487a1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826405"
---
# <a name="register-callbacks-for-cancellation-requests"></a><span data-ttu-id="4f2c4-102">キャンセル要求のコールバックを登録する</span><span class="sxs-lookup"><span data-stu-id="4f2c4-102">Register callbacks for cancellation requests</span></span>

<span data-ttu-id="4f2c4-103"><xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティが true になったときに呼び出されるデリゲートを登録する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-103">Learn how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true.</span></span> <span data-ttu-id="4f2c4-104">この値は、トークンを作成したオブジェクトが <xref:System.Threading.CancellationTokenSource.Cancel%2A> を呼び出したときに、false から true に変更されます。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-104">The value changes from false to true when a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token is made.</span></span> <span data-ttu-id="4f2c4-105">この方法は、統合キャンセル フレームワークをネイティブにはサポートしていない非同期操作を取り消す場合や、非同期操作の終了を待機している可能性のあるメソッドのブロックを解除する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-105">Use this technique for canceling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="4f2c4-106">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="4f2c4-107">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-107">This error is benign.</span></span> <span data-ttu-id="4f2c4-108"><kbd>F5</kbd> キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-108">You can press <kbd>F5</kbd> to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="4f2c4-109">Visual Studio による処理が最初のエラーで中断しないようにするには、 **[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>

## <a name="example"></a><span data-ttu-id="4f2c4-110">例</span><span class="sxs-lookup"><span data-stu-id="4f2c4-110">Example</span></span>

<span data-ttu-id="4f2c4-111">次の例では、<xref:System.Net.WebClient.CancelAsync%2A> メソッドを、キャンセル トークンを通じてキャンセルが要求されたときに呼び出されるメソッドとして登録します。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-111">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

<span data-ttu-id="4f2c4-112">コールバックを登録するときにキャンセルが既に要求されていても、コールバックは必ず呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-112">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="4f2c4-113">このような場合、進行中の非同期操作がないと <xref:System.Net.WebClient.CancelAsync%2A> メソッドは何も実行しないので、このメソッドの呼び出しは常に安全です。</span><span class="sxs-lookup"><span data-stu-id="4f2c4-113">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f2c4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f2c4-114">See also</span></span>

- [<span data-ttu-id="4f2c4-115">マネージド スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="4f2c4-115">Cancellation in managed threads</span></span>](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
