---
title: '方法: オブザーバーを実装する'
description: .NET でオブザーバーを実装します。 オブザーバー デザイン パターンでは、通知を登録するオブザーバーと、プロバイダーを分ける必要があります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET], observer design pattern
- observer design pattern [.NET], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: bfd595cec8e499b760f75f614bd0a61b031eb207
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828336"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="eaaff-104">方法: オブザーバーを実装する</span><span class="sxs-lookup"><span data-stu-id="eaaff-104">How to: Implement an Observer</span></span>
<span data-ttu-id="eaaff-105">オブザーバー デザイン パターンでは、通知を登録するオブザーバーと、データを監視して 1 人以上のオブザーバーに通知を送信するプロバイダーを分ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaaff-105">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="eaaff-106">このトピックでは、オブザーバーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eaaff-106">This topic discusses how to create an observer.</span></span> <span data-ttu-id="eaaff-107">プロバイダーの作成方法については、関連トピックの「[方法:プロバイダーを実装する](how-to-implement-a-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaaff-107">A related topic, [How to: Implement a Provider](how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="eaaff-108">オブザーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="eaaff-108">To create an observer</span></span>  
  
1. <span data-ttu-id="eaaff-109">オブザーバーを定義します。これは <xref:System.IObserver%601?displayProperty=nameWithType> インターフェイスを実装する型です。</span><span class="sxs-lookup"><span data-stu-id="eaaff-109">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="eaaff-110">たとえば、次のコードでは、`TemperatureReporter` という型が定義されています。これは、ジェネリック型引数の <xref:System.IObserver%601?displayProperty=nameWithType> を使用して構築された `Temperature` の実装です。</span><span class="sxs-lookup"><span data-stu-id="eaaff-110">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. <span data-ttu-id="eaaff-111">プロバイダーが <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> の実装を呼び出す前にオブザーバーが通知の受信を停止できる場合は、プロバイダーの <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> メソッドから返される <xref:System.IDisposable> の実装を保持するプライベート変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="eaaff-111">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="eaaff-112">また、プロバイダーの <xref:System.IObservable%601.Subscribe%2A> メソッドを呼び出し、返された <xref:System.IDisposable> オブジェクトを格納するサブスクリプション メソッドも定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaaff-112">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="eaaff-113">たとえば、次のコードでは `unsubscriber` というプライベート変数を定義し、プロバイダーの <xref:System.IObservable%601.Subscribe%2A> メソッドを呼び出し、返されたオブジェクトを `unsubscriber` 変数に割り当てる `Subscribe` メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="eaaff-113">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. <span data-ttu-id="eaaff-114">この機能が必要な場合は、プロバイダーが <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> の実装を呼び出す前に、オブザーバーが通知の受信を停止できるようにするメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="eaaff-114">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="eaaff-115">次の例では、`Unsubscribe` メソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="eaaff-115">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <span data-ttu-id="eaaff-116"><xref:System.IObserver%601> インターフェイスに定義されている 3 つのメソッド <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、<xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>、および <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> の実装を用意します。</span><span class="sxs-lookup"><span data-stu-id="eaaff-116">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eaaff-117">プロバイダーとアプリケーションのニーズに応じて、<xref:System.IObserver%601.OnError%2A> メソッドと <xref:System.IObserver%601.OnCompleted%2A> メソッドをスタブ実装にすることができます。</span><span class="sxs-lookup"><span data-stu-id="eaaff-117">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="eaaff-118"><xref:System.IObserver%601.OnError%2A> メソッドが渡された <xref:System.Exception> オブジェクトを例外として処理しない点と、<xref:System.IObserver%601.OnCompleted%2A> メソッドはプロバイダーの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を自由に呼び出すことができる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="eaaff-118">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="eaaff-119">次の例は、`TemperatureReporter` クラスの <xref:System.IObserver%601> の実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="eaaff-119">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="eaaff-120">例</span><span class="sxs-lookup"><span data-stu-id="eaaff-120">Example</span></span>  
 <span data-ttu-id="eaaff-121">次の例には、`TemperatureReporter` クラスの完全なソース コードが含まれています。これは、温度監視アプリケーション向けに <xref:System.IObserver%601> の実装を提供するクラスです。</span><span class="sxs-lookup"><span data-stu-id="eaaff-121">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="eaaff-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="eaaff-122">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="eaaff-123">オブサーバー デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="eaaff-123">Observer Design Pattern</span></span>](observer-design-pattern.md)
- [<span data-ttu-id="eaaff-124">方法: プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="eaaff-124">How to: Implement a Provider</span></span>](how-to-implement-a-provider.md)
- [<span data-ttu-id="eaaff-125">オブザーバー デザイン パターンのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="eaaff-125">Observer Design Pattern Best Practices</span></span>](observer-design-pattern-best-practices.md)
