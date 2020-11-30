---
title: '方法: パイプラインでブロッキング コレクションの配列を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 55dc3e9934efa153c61322f63b7dde8077442fd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733465"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="56618-102">方法: パイプラインでブロッキング コレクションの配列を使用する</span><span class="sxs-lookup"><span data-stu-id="56618-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>

<span data-ttu-id="56618-103">次の例は、<xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> や <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> などの静的メソッドで <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> オブジェクトの配列を使用し、コンポーネント間の高速で柔軟なデータ転送を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="56618-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56618-104">例</span><span class="sxs-lookup"><span data-stu-id="56618-104">Example</span></span>  

 <span data-ttu-id="56618-105">次の例では、各オブジェクトが同時にデータを入力コレクションから取得し、変換して、出力コレクションに渡す、基本的なパイプラインの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="56618-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="56618-106">参照</span><span class="sxs-lookup"><span data-stu-id="56618-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="56618-107">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="56618-107">Thread-Safe Collections</span></span>](index.md)
