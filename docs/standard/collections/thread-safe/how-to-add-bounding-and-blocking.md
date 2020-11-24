---
title: '方法: 境界ブロッキング機能をコレクションに追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 52ba264c5a0fc9cfffb00ee30b50f6b89dc1e660
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825040"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="e42a4-102">方法: 境界ブロッキング機能をコレクションに追加する</span><span class="sxs-lookup"><span data-stu-id="e42a4-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="e42a4-103">この例では、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> インターフェイスをクラスに実装し、クラスのインスタンスを <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> の内部ストレージ メカニズムとして使用することによって、カスタム コレクション クラスに境界ブロッキング機能を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e42a4-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e42a4-104">境界ブロッキングの詳細については、「[BlockingCollection の概要](blockingcollection-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e42a4-104">For more information about bounding and blocking, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e42a4-105">例</span><span class="sxs-lookup"><span data-stu-id="e42a4-105">Example</span></span>  
 <span data-ttu-id="e42a4-106">カスタム コレクション クラスは基本優先度キューであり、優先度レベルは <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> オブジェクトの配列として表されます。</span><span class="sxs-lookup"><span data-stu-id="e42a4-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="e42a4-107">各キュー内で他の順序付けは行われません。</span><span class="sxs-lookup"><span data-stu-id="e42a4-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="e42a4-108">クライアント コードでは、3 つのタスクが開始されます。</span><span class="sxs-lookup"><span data-stu-id="e42a4-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="e42a4-109">1 番目のタスクはキーボード入力のポーリングだけを行い、実行中にいつでもキャンセルできるようにします。</span><span class="sxs-lookup"><span data-stu-id="e42a4-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="e42a4-110">2 番目のタスクはプロデューサー スレッドであり、ブロッキング コレクションに新しい項目を追加し、ランダムな値に基づく優先度を各項目に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e42a4-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="e42a4-111">3 番目のタスクは、利用可能になった項目をコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="e42a4-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="e42a4-112">1 つのスレッドが他より速く実行されるようにすることで、アプリケーションの動作を調整できます。</span><span class="sxs-lookup"><span data-stu-id="e42a4-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="e42a4-113">プロデューサーが高速に実行されると、コンストラクターで指定されている数の項目がコレクションに既に含まれる場合はブロッキング コレクションが項目の追加を防ぐので、境界機能が目立つようになります。</span><span class="sxs-lookup"><span data-stu-id="e42a4-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="e42a4-114">コンシューマーが高速に実行されると、コンシューマーは新しい項目が追加されるのを待機するので、ブロッキング機能が目立つようになります。</span><span class="sxs-lookup"><span data-stu-id="e42a4-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="e42a4-115">既定では、<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> の記憶域は <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="e42a4-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42a4-116">参照</span><span class="sxs-lookup"><span data-stu-id="e42a4-116">See also</span></span>

- [<span data-ttu-id="e42a4-117">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="e42a4-117">Thread-Safe Collections</span></span>](index.md)
