---
title: イベントのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: d04ffd2cab21177f1342a13259a81df22b65723a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734414"
---
# <a name="event-design"></a><span data-ttu-id="18997-102">イベントのデザイン</span><span class="sxs-lookup"><span data-stu-id="18997-102">Event Design</span></span>

<span data-ttu-id="18997-103">イベントは、最も一般的に使用されるコールバックの形式です (フレームワークがユーザーコードを呼び出すことを許可するコンストラクト)。</span><span class="sxs-lookup"><span data-stu-id="18997-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="18997-104">その他のコールバックメカニズムには、デリゲート、仮想メンバー、およびインターフェイスベースのプラグインを受け取るメンバーが含まれます。ユーザビリティ研究からのデータは、開発者の大半が、他のコールバックメカニズムを使用しているよりも、イベントをより快適に使用できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="18997-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="18997-105">イベントは、Visual Studio と多くの言語に適切に統合されています。</span><span class="sxs-lookup"><span data-stu-id="18997-105">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="18997-106">イベントのグループは2つあることに注意してください。システムの状態が変更される前に発生するイベント (前のイベントと呼ばれます) と、状態の変更後に発生するイベント (ポストイベント) です。</span><span class="sxs-lookup"><span data-stu-id="18997-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="18997-107">前のイベントの例として `Form.Closing` 、フォームが閉じられる前にが発生します。</span><span class="sxs-lookup"><span data-stu-id="18997-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="18997-108">ポストイベントの例としては `Form.Closed` 、フォームが閉じられた後に発生するがあります。</span><span class="sxs-lookup"><span data-stu-id="18997-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="18997-109">✔️は、"火災" や "トリガー" ではなく、イベントに "raise" という用語を使用します。</span><span class="sxs-lookup"><span data-stu-id="18997-109">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="18997-110"><xref:System.EventHandler%601?displayProperty=nameWithType>イベントハンドラーとして使用する新しいデリゲートを手動で作成する代わりに、を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18997-110">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="18997-111">イベントがイベント処理メソッドにデータを渡す必要がないことが確実である場合を除き、のサブクラスをイベント引数として使用することを検討してください <xref:System.EventArgs> 。この場合、型を直接使用でき `EventArgs` ます。✔️</span><span class="sxs-lookup"><span data-stu-id="18997-111">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="18997-112">直接を使用して API を出荷する場合 `EventArgs` 、互換性を損なうことなく、イベントに含まれるデータを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="18997-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="18997-113">サブクラスを使用する場合、最初は完全に空であっても、必要に応じてサブクラスにプロパティを追加できます。</span><span class="sxs-lookup"><span data-stu-id="18997-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="18997-114">✔️、保護された仮想メソッドを使用して各イベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="18997-114">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="18997-115">これは、構造体、シールクラス、または静的イベントではなく、シールされていないクラスの非静的イベントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="18997-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="18997-116">メソッドの目的は、派生クラスがオーバーライドを使用してイベントを処理する方法を提供することです。</span><span class="sxs-lookup"><span data-stu-id="18997-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="18997-117">オーバーライドは、派生クラスの基底クラスのイベントを処理するための、より柔軟で高速で、より自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="18997-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="18997-118">慣例として、メソッドの名前は "On" で始まり、その後にイベントの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18997-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="18997-119">派生クラスは、オーバーライドでメソッドの基本実装を呼び出さないことを選択できます。</span><span class="sxs-lookup"><span data-stu-id="18997-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="18997-120">基底クラスが正常に動作するために必要なメソッドに処理を含めないで、これを準備してください。</span><span class="sxs-lookup"><span data-stu-id="18997-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="18997-121">✔️は、イベントを発生させるプロテクトメソッドに対して1つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="18997-121">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="18997-122">パラメーターにはという名前を付け、 `e` イベント引数クラスとして型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18997-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="18997-123">❌ 非静的イベントを発生させるときに、送信者として null を渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="18997-123">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="18997-124">静的なイベントを発生させるときに、送信者として null を渡す✔️ます。</span><span class="sxs-lookup"><span data-stu-id="18997-124">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="18997-125">❌ イベントの発生時には、イベントデータパラメーターとして null を渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="18997-125">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="18997-126">`EventArgs.Empty`イベント処理メソッドにデータを渡さない場合は、を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="18997-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="18997-127">開発者は、このパラメーターを null にすることを想定していません。</span><span class="sxs-lookup"><span data-stu-id="18997-127">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="18997-128">エンドユーザーがキャンセルできるイベントの発生を✔️検討します。</span><span class="sxs-lookup"><span data-stu-id="18997-128">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="18997-129">これは、前のイベントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="18997-129">This only applies to pre-events.</span></span>

 <span data-ttu-id="18997-130"><xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>またはそのサブクラスをイベント引数として使用し、エンドユーザーがイベントをキャンセルできるようにします。</span><span class="sxs-lookup"><span data-stu-id="18997-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="18997-131">カスタムイベントハンドラーのデザイン</span><span class="sxs-lookup"><span data-stu-id="18997-131">Custom Event Handler Design</span></span>

 <span data-ttu-id="18997-132">を使用できないケースがあります `EventHandler<T>` 。たとえば、フレームワークが以前のバージョンの CLR を使用する必要があり、そのためにジェネリックがサポートされていない場合などです。</span><span class="sxs-lookup"><span data-stu-id="18997-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="18997-133">このような場合は、カスタムイベントハンドラーデリゲートの設計と開発が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="18997-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="18997-134">✔️は、イベントハンドラーに戻り値の型 void を使用します。</span><span class="sxs-lookup"><span data-stu-id="18997-134">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="18997-135">イベントハンドラーは複数のイベント処理メソッド (場合によっては複数のオブジェクト) を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="18997-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="18997-136">イベント処理メソッドで値を返すことが許可された場合、イベントの呼び出しごとに複数の戻り値が返されます。</span><span class="sxs-lookup"><span data-stu-id="18997-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="18997-137">✔️は、 `object` イベントハンドラーの最初のパラメーターの型としてを使用し、それを呼び出し `sender` ます。</span><span class="sxs-lookup"><span data-stu-id="18997-137">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="18997-138"><xref:System.EventArgs?displayProperty=nameWithType>イベントハンドラーの2番目のパラメーターの型としてまたはそのサブクラスを使用✔️、それを呼び出し `e` ます。</span><span class="sxs-lookup"><span data-stu-id="18997-138">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="18997-139">❌ イベントハンドラーに2つ以上のパラメーターを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="18997-139">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="18997-140">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="18997-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="18997-141">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="18997-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="18997-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="18997-142">See also</span></span>

- [<span data-ttu-id="18997-143">メンバーデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="18997-143">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="18997-144">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="18997-144">Framework Design Guidelines</span></span>](index.md)
