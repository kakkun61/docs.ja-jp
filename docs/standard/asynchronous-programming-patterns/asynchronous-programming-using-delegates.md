---
title: デリゲートを使用した非同期プログラミング
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: 05e574536abe4eac823b7b74369f5b191724e5b5
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889258"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="b6e82-102">デリゲートを使用した非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="b6e82-102">Asynchronous Programming Using Delegates</span></span>

<span data-ttu-id="b6e82-103">デリゲートを使用すると、同期メソッドを非同期的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="b6e82-104">デリゲートを同期的に呼び出すと、`Invoke` メソッドによって対象メソッドが現在のスレッドで直接呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="b6e82-105">`BeginInvoke` メソッドが呼び出されると、共通言語ランタイム (CLR) は要求をキューに置き、すぐに呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="b6e82-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="b6e82-106">対象メソッドは、スレッド プールのスレッドで非同期的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="b6e82-107">要求を送信した元のスレッドは、対象メソッドと並行して継続実行できます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="b6e82-108">`BeginInvoke` メソッドの呼び出しにコールバック メソッドを指定した場合、対象メソッドの終了時に、そのコールバック メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="b6e82-109">コールバック メソッドでは、`EndInvoke` メソッドを使用して、戻り値と、入出力パラメーターまたは出力専用パラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b6e82-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="b6e82-110">`BeginInvoke` の呼び出しにコールバック メソッドを指定しなかった場合は、`BeginInvoke` を呼び出したスレッドから `EndInvoke` を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b6e82-111">コンパイラは、ユーザーが指定したデリゲート シグネチャを使用して、`Invoke`、`BeginInvoke`、`EndInvoke` の各メソッドを持つデリゲート クラスを出力します。</span><span class="sxs-lookup"><span data-stu-id="b6e82-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="b6e82-112">`BeginInvoke` メソッドと `EndInvoke` メソッドは、ネイティブとして修飾されます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="b6e82-113">これら 2 つのメソッドはネイティブとしてマークされるため、クラスの読み込み時には、CLR によって自動的にメソッドが実装されます。</span><span class="sxs-lookup"><span data-stu-id="b6e82-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="b6e82-114">ローダーは、これらのメソッドがオーバーライドされないことを保証します。</span><span class="sxs-lookup"><span data-stu-id="b6e82-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6e82-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b6e82-115">In This Section</span></span>  
 [<span data-ttu-id="b6e82-116">同期メソッドの非同期呼び出し</span><span class="sxs-lookup"><span data-stu-id="b6e82-116">Calling Synchronous Methods Asynchronously</span></span>](calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="b6e82-117">デリゲートを使用した通常のメソッドの非同期呼び出しについて説明すると共に、簡単なコード例を示して、非同期呼び出しが戻るのを待機する 4 つの方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="b6e82-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b6e82-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6e82-118">Related Sections</span></span>  
 [<span data-ttu-id="b6e82-119">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="b6e82-119">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="b6e82-120">.NET での非同期プログラミングについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="b6e82-120">Describes asynchronous programming in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e82-121">参照</span><span class="sxs-lookup"><span data-stu-id="b6e82-121">See also</span></span>

- <xref:System.Delegate>
