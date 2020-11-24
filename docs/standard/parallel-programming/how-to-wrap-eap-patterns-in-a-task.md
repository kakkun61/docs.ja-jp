---
title: '方法: タスクに EAP パターンをラップする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: 2d6788634fe03bed7a380184c0e954954e224aec
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826685"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="5984a-102">方法: タスクに EAP パターンをラップする</span><span class="sxs-lookup"><span data-stu-id="5984a-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="5984a-103">次の例では、<xref:System.Threading.Tasks.TaskCompletionSource%601> を使用して、任意のシーケンスのイベント ベースの非同期パターン (EAP) 操作を公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5984a-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="5984a-104">また、この例は <xref:System.Threading.CancellationToken> を使用して、<xref:System.Net.WebClient> オブジェクトの組み込みキャンセル メソッドを呼び出す方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="5984a-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5984a-105">例</span><span class="sxs-lookup"><span data-stu-id="5984a-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="5984a-106">参照</span><span class="sxs-lookup"><span data-stu-id="5984a-106">See also</span></span>

- [<span data-ttu-id="5984a-107">TPL と従来の .NET 非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="5984a-107">TPL and Traditional .NET Asynchronous Programming</span></span>](tpl-and-traditional-async-programming.md)
