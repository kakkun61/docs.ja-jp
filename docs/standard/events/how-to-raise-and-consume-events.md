---
title: '方法: イベントを発生させる/処理する'
description: .NET でイベントを発生させ、使用します。 EventHandler デリゲート、EventHandler<TEventArgs> デリゲート、カスタム デリゲートを使用する例を参照します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET], raising
- raising events
- events [.NET], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 9d068981694c212c5cb29a67ccd2fcb19dcc907b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828297"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="164c2-104">方法: イベントを発生させる/処理する</span><span class="sxs-lookup"><span data-stu-id="164c2-104">How to: Raise and Consume Events</span></span>
<span data-ttu-id="164c2-105">このトピックの例では、イベントを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="164c2-105">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="164c2-106">ここでは、<xref:System.EventHandler> デリゲートと <xref:System.EventHandler%601> デリゲート、およびカスタム デリゲートの例を使用して、データを持つイベントと持たないイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="164c2-106">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="164c2-107">この例では、「[イベント](index.md)」で説明されている概念を使用します。</span><span class="sxs-lookup"><span data-stu-id="164c2-107">The examples use concepts described in the [Events](index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="164c2-108">例</span><span class="sxs-lookup"><span data-stu-id="164c2-108">Example</span></span>  
 <span data-ttu-id="164c2-109">最初の例は、データを持たないイベントを発生させて処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="164c2-109">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="164c2-110">この例には、`Counter` という名前のイベントを持つ、`ThresholdReached` という名前のクラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="164c2-110">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="164c2-111">このイベントは、カウンター値がしきい値と等しいか、またはそれを超えた場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="164c2-111">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="164c2-112">イベントのデータが指定されていないため、<xref:System.EventHandler> デリゲートはイベントに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="164c2-112">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="164c2-113">例</span><span class="sxs-lookup"><span data-stu-id="164c2-113">Example</span></span>  
 <span data-ttu-id="164c2-114">次の例は、データを持つイベントを発生させて処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="164c2-114">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="164c2-115"><xref:System.EventHandler%601> デリゲートはイベントに関連付けられ、カスタム イベント データ オブジェクトのインスタンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="164c2-115">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="164c2-116">例</span><span class="sxs-lookup"><span data-stu-id="164c2-116">Example</span></span>  
 <span data-ttu-id="164c2-117">次の例は、イベントのデリゲートを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="164c2-117">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="164c2-118">デリゲートの名前は `ThresholdReachedEventHandler` です。</span><span class="sxs-lookup"><span data-stu-id="164c2-118">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="164c2-119">これはあくまでも一例です。</span><span class="sxs-lookup"><span data-stu-id="164c2-119">This is just an illustration.</span></span> <span data-ttu-id="164c2-120">通常は、<xref:System.EventHandler> デリゲートまたは <xref:System.EventHandler%601> デリゲートを使用できるため、イベントのデリゲートを宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="164c2-120">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="164c2-121">ジェネリックを使用できないレガシ コードでクラスを使用できるようにするなど、ごくまれに、デリゲートの宣言が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="164c2-121">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="164c2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="164c2-122">See also</span></span>

- [<span data-ttu-id="164c2-123">イベント</span><span class="sxs-lookup"><span data-stu-id="164c2-123">Events</span></span>](index.md)
