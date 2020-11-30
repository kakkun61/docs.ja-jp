---
title: '方法: 静的パーティション分割用にパーティショナーを実装する'
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 59a5519a8f129576c08604633cd3c411d3ca020e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734492"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="f5cca-102">方法: 静的パーティション分割用にパーティショナーを実装する</span><span class="sxs-lookup"><span data-stu-id="f5cca-102">How to: Implement a Partitioner for Static Partitioning</span></span>

<span data-ttu-id="f5cca-103">次の例は、静的なパーティション分割を行う PLINQ 用の単純なカスタム パーティショナーを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f5cca-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="f5cca-104">パーティショナーは動的なパーティションをサポートしていないため、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> からは利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f5cca-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5cca-105">この特定のパーティショナーは、各要素が大量の処理時間を必要とするデータ ソースで、既定の範囲のパーティショナーよりも処理速度を向上させることができる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5cca-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cca-106">例</span><span class="sxs-lookup"><span data-stu-id="f5cca-106">Example</span></span>  

 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="f5cca-107">この例のパーティションでは、各要素の処理時間が直線的に増加することが前提となっています。</span><span class="sxs-lookup"><span data-stu-id="f5cca-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="f5cca-108">実際には、この方法で処理時間を予測するのは難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5cca-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="f5cca-109">特定のデータ ソースで静的パーティショナーを使用している場合、ソースのパーティション分割の数式を最適化したり、負荷分散のロジックを追加したり、「[方法: 動的パーティションを実装する](how-to-implement-dynamic-partitions.md)」に示すチャンク パーティション分割の手法を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f5cca-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cca-110">参照</span><span class="sxs-lookup"><span data-stu-id="f5cca-110">See also</span></span>

- [<span data-ttu-id="f5cca-111">PLINQ および TPL 用のカスタム パーティショナー</span><span class="sxs-lookup"><span data-stu-id="f5cca-111">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
