---
title: 非同期プログラミングのパターン
description: .NET のタスクベースの非同期パターン (TAP)、イベントベースの非同期パターン (EAP)、非同期プログラミング モデル (APM) について説明します。
ms.date: 10/16/2018
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: bc0e37c060ab6375f943b4b50053e3046c05a556
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830338"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="e9f5a-103">非同期プログラミングのパターン</span><span class="sxs-lookup"><span data-stu-id="e9f5a-103">Asynchronous programming patterns</span></span>

<span data-ttu-id="e9f5a-104">.NET には、非同期操作を実行するための 3 つのパターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-104">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="e9f5a-105">**タスク ベースの非同期パターン (TAP)** 。1 つのメソッドを使用して非同期操作の開始と完了を表します。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-105">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="e9f5a-106">TAP は .NET Framework 4 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-106">TAP was introduced in .NET Framework 4.</span></span> <span data-ttu-id="e9f5a-107">**.NET で非同期プログラミングを行う場合、これが推奨される方法となります。**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-107">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="e9f5a-108">C# の [async](../../csharp/language-reference/keywords/async.md) キーワードと [await](../../csharp/language-reference/operators/await.md) キーワード、および Visual Basic の [Async](../../visual-basic/language-reference/modifiers/async.md) 演算子と [Await](../../visual-basic/language-reference/operators/await-operator.md) 演算子により、TAP の言語サポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-108">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="e9f5a-109">詳細については、「[タスク ベースの非同期パターン (TAP)](task-based-asynchronous-pattern-tap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-109">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="e9f5a-110">**イベント ベースの非同期パターン (EAP)** は、非同期動作を提供するための、イベント ベースの従来のモデルです。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-110">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="e9f5a-111">これは、`Async` サフィックスを持つメソッドと、1 つ以上のイベント、イベント ハンドラー デリゲート型、および `EventArg` 派生型を必要とします。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-111">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="e9f5a-112">EAP は .NET Framework 2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-112">EAP was introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="e9f5a-113">新規の開発では推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-113">It's no longer recommended for new development.</span></span> <span data-ttu-id="e9f5a-114">詳細については、「[イベント ベースの非同期パターン (EAP)](event-based-asynchronous-pattern-eap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-114">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="e9f5a-115">**非同期プログラミング モデル (APM)** パターン (<xref:System.IAsyncResult> パターンとも呼ばれます) は、<xref:System.IAsyncResult> インターフェイスを使用して非同期動作を提供する従来のモデルです。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-115">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="e9f5a-116">このパターンでは、同期操作に `Begin` と `End` メソッドが必要になります (たとえば、非同期書き込み操作を実装するための `BeginWrite` と `EndWrite`)。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-116">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="e9f5a-117">このパターンは、新規の開発では推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-117">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="e9f5a-118">詳細については、「[非同期プログラミング モデル (APM)](asynchronous-programming-model-apm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-118">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="e9f5a-119">パターンの比較</span><span class="sxs-lookup"><span data-stu-id="e9f5a-119">Comparison of patterns</span></span>

<span data-ttu-id="e9f5a-120">3 つのパターンで非同期操作がどのようにモデリングされるかを簡単に比較するために、指定された量のデータを、指定のバッファーの指定されたオフセットに読み込む `Read` メソッドを考えます。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-120">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="e9f5a-121">TAP のこのメソッドに対応する部分では、次の単一の `ReadAsync` メソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-121">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="e9f5a-122">EAP の場合は次の型とメンバーのセットが公開されます。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-122">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="e9f5a-123">APM の対応する部分では `BeginRead` メソッドと `EndRead` メソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-123">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="e9f5a-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9f5a-124">See also</span></span>

- [<span data-ttu-id="e9f5a-125">非同期の詳細</span><span class="sxs-lookup"><span data-stu-id="e9f5a-125">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="e9f5a-126">C# の非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="e9f5a-126">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="e9f5a-127">F# の非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="e9f5a-127">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="e9f5a-128">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9f5a-128">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
