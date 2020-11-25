---
title: 例外のスロー
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: d41467b971e43ca9b22c59e3b64bdd45d16c740b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734401"
---
# <a name="exception-throwing"></a><span data-ttu-id="2bf49-102">例外のスロー</span><span class="sxs-lookup"><span data-stu-id="2bf49-102">Exception Throwing</span></span>

<span data-ttu-id="2bf49-103">このセクションで説明する例外をスローするガイドラインでは、実行エラーの意味を適切に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bf49-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="2bf49-104">実行エラーは、メンバーが実行するように設計された処理を実行できない場合 (メンバー名が示すもの) に発生します。</span><span class="sxs-lookup"><span data-stu-id="2bf49-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="2bf49-105">たとえば、 `OpenFile` メソッドが開いているファイルハンドルを呼び出し元に返すことができない場合、実行エラーと見なされます。</span><span class="sxs-lookup"><span data-stu-id="2bf49-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="2bf49-106">ほとんどの開発者は、0または null 参照による除算などの使用エラーに対して、例外を使用することに慣れています。</span><span class="sxs-lookup"><span data-stu-id="2bf49-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="2bf49-107">フレームワークでは、実行エラーを含むすべてのエラー条件に対して例外が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2bf49-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="2bf49-108">❌ エラーコードを返しません。</span><span class="sxs-lookup"><span data-stu-id="2bf49-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="2bf49-109">例外は、フレームワークでエラーを報告するための主な手段です。</span><span class="sxs-lookup"><span data-stu-id="2bf49-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="2bf49-110">✔️、例外をスローして実行エラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="2bf49-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="2bf49-111">✔️は、 `System.Environment.FailFast` コードにより実行が安全でないという状況が発生した場合に例外をスローするのではなく、(.NET Framework 2.0 機能) を呼び出してプロセスを終了することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2bf49-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="2bf49-112">❌ 可能であれば、通常の制御フローには例外を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="2bf49-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="2bf49-113">システムエラーや潜在的な競合状態による操作を除き、フレームワークデザイナーは、ユーザーが例外をスローしないコードを記述できるように Api を設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bf49-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="2bf49-114">たとえば、例外をスローしないコードをユーザーが記述できるように、メンバーを呼び出す前に事前条件を確認する方法を提供できます。</span><span class="sxs-lookup"><span data-stu-id="2bf49-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="2bf49-115">別のメンバーの事前条件を確認するために使用されるメンバーは、テスト担当者と呼ばれることもあり、実際に作業を行うメンバーは doer と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2bf49-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="2bf49-116">Tester-Doer パターンでは、許容できないパフォーマンスのオーバーヘッドが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2bf49-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="2bf49-117">このような場合は、いわゆる Try-Parse パターンを考慮する必要があります (詳細については、「 [例外とパフォーマンス](exceptions-and-performance.md) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="2bf49-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="2bf49-118">✔️例外をスローした場合のパフォーマンスへの影響を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="2bf49-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="2bf49-119">1秒あたり100を超えるレートをスローすると、ほとんどのアプリケーションのパフォーマンスが著しく低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2bf49-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="2bf49-120">✔️は、(システム障害ではなく) メンバーコントラクトの違反が原因で、パブリック呼び出し可能メンバーによってスローされたすべての例外をドキュメント化し、コントラクトの一部として処理します。</span><span class="sxs-lookup"><span data-stu-id="2bf49-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="2bf49-121">コントラクトの一部である例外は、あるバージョンから次のバージョンに変更することはできません (つまり、例外の種類を変更することはできません。また、新しい例外は追加しないでください)。</span><span class="sxs-lookup"><span data-stu-id="2bf49-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="2bf49-122">❌ 何らかのオプションに基づいてスローするかどうかを指定できるパブリックメンバーは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="2bf49-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="2bf49-123">❌ 戻り値またはパラメーターとして例外を返すパブリックメンバーを指定しないでください `out` 。</span><span class="sxs-lookup"><span data-stu-id="2bf49-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="2bf49-124">例外をスローするのではなくパブリック Api から例外を返すと、例外ベースのエラー報告の多くの利点が損なわれます。</span><span class="sxs-lookup"><span data-stu-id="2bf49-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="2bf49-125">✔️例外ビルダーメソッドを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2bf49-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="2bf49-126">さまざまな場所から同じ例外をスローするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="2bf49-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="2bf49-127">コードの肥大化を回避するには、例外を作成してプロパティを初期化するヘルパーメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2bf49-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="2bf49-128">また、例外をスローするメンバーはインライン展開されません。</span><span class="sxs-lookup"><span data-stu-id="2bf49-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="2bf49-129">ビルダー内で throw ステートメントを移動すると、メンバーをインライン化できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2bf49-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="2bf49-130">❌ 例外フィルターブロックから例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="2bf49-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="2bf49-131">例外フィルターによって例外が発生した場合、CLR によって例外がキャッチされ、フィルターは false を返します。</span><span class="sxs-lookup"><span data-stu-id="2bf49-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="2bf49-132">この動作は、実行中のフィルターと区別できないため、明示的に false を返すため、デバッグが非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="2bf49-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="2bf49-133">❌ Finally ブロックから明示的に例外をスローしないようにします。</span><span class="sxs-lookup"><span data-stu-id="2bf49-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="2bf49-134">暗黙的にスローされた例外は、スローするメソッドの呼び出しによって返されます。</span><span class="sxs-lookup"><span data-stu-id="2bf49-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="2bf49-135">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="2bf49-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2bf49-136">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="2bf49-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2bf49-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bf49-137">See also</span></span>

- [<span data-ttu-id="2bf49-138">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="2bf49-138">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="2bf49-139">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="2bf49-139">Design Guidelines for Exceptions</span></span>](exceptions.md)
