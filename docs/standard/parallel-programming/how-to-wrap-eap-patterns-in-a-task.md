---
title: '方法: タスクに EAP パターンをラップする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: 667de563a53695f7b8f4782a2bdd5b753673b4e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728213"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="3b9a5-102">方法: タスクに EAP パターンをラップする</span><span class="sxs-lookup"><span data-stu-id="3b9a5-102">How to: Wrap EAP Patterns in a Task</span></span>

<span data-ttu-id="3b9a5-103">次の例では、<xref:System.Threading.Tasks.TaskCompletionSource%601> を使用して、任意のシーケンスのイベント ベースの非同期パターン (EAP) 操作を公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3b9a5-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="3b9a5-104">また、この例は <xref:System.Threading.CancellationToken> を使用して、<xref:System.Net.WebClient> オブジェクトの組み込みキャンセル メソッドを呼び出す方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="3b9a5-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b9a5-105">例</span><span class="sxs-lookup"><span data-stu-id="3b9a5-105">Example</span></span>  

 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="3b9a5-106">参照</span><span class="sxs-lookup"><span data-stu-id="3b9a5-106">See also</span></span>

- [<span data-ttu-id="3b9a5-107">TPL と従来の .NET 非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="3b9a5-107">TPL and Traditional .NET Asynchronous Programming</span></span>](tpl-and-traditional-async-programming.md)
