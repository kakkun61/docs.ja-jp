---
title: 単体テストを記述するためのベスト プラクティス
description: .NET Core プロジェクトと .NET Standard プロジェクトのコードの品質と回復性を向上させる単体テストを記述するためのベスト プラクティスについて説明します。
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 56f51cde0e52a9e6a38e5291c81470beee61adef
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678115"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="2157e-103">.NET Core と .NET Standard での単体テストのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="2157e-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="2157e-104">単体テストの記述には多大な利点があります。回帰の防止に役立ち、ドキュメントを提供して、優れた設計を容易に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2157e-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="2157e-105">ただし、読みにくくて不安定な単体テストは、コード ベースに打撃を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="2157e-106">この記事では、.NET Core プロジェクトと .NET Standard プロジェクトの単体テストの設計に関するベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2157e-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="2157e-107">このガイドでは、テストの回復性とわかりやすさを維持するよう単体テストを記述する際のいくつかのベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2157e-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="2157e-108">著者: [John Reese](https://reese.dev)、協力者: [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="2157e-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="2157e-109">単体テストを記述する理由</span><span class="sxs-lookup"><span data-stu-id="2157e-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="2157e-110">機能テストの実行時間を短縮</span><span class="sxs-lookup"><span data-stu-id="2157e-110">Less time performing functional tests</span></span>

<span data-ttu-id="2157e-111">機能テストはコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="2157e-111">Functional tests are expensive.</span></span> <span data-ttu-id="2157e-112">通常、これらのテストでは、アプリケーションを開き、想定される動作を検証するためにお客様 (または他のだれか) が従う必要のある一連の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2157e-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="2157e-113">テスト担当者は、これらの手順を必ずしもが把握しているとは限りません。つまり、テストを実行するために、その領域に精通している他者に支援を求める必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="2157e-114">テスト自体は、小さな変更の場合は数秒かかり、大きな変更の場合は数分かかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="2157e-115">最後に、システムで変更を行うたびにこのプロセスを繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="2157e-116">一方、単体テストは数ミリ秒しかかからず、ボタンを押すだけで実行でき、概してシステムの知識は必ずしも必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2157e-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button, and don't necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="2157e-117">テストに合格するか失敗するかは、個人ではなくテスト ランナーの責任となります。</span><span class="sxs-lookup"><span data-stu-id="2157e-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="2157e-118">回帰の防止</span><span class="sxs-lookup"><span data-stu-id="2157e-118">Protection against regression</span></span>

<span data-ttu-id="2157e-119">回帰問題は、アプリケーションに変更が行われると発生する欠陥です。</span><span class="sxs-lookup"><span data-stu-id="2157e-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="2157e-120">一般的にテスト担当者は、新しい機能をテストするだけでなく、以前に実装されていた機能が今も想定どおりに機能していることを確認するために、事前に存在していた機能もテストします。</span><span class="sxs-lookup"><span data-stu-id="2157e-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="2157e-121">単体テストでは、ビルドを行うたびに、さらにはコード行を変更するたびに、テストのスイート全体を再実行できます。</span><span class="sxs-lookup"><span data-stu-id="2157e-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="2157e-122">これにより、新しいコードが既存の機能を損なわないことを確信できます。</span><span class="sxs-lookup"><span data-stu-id="2157e-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="2157e-123">実行可能なドキュメント</span><span class="sxs-lookup"><span data-stu-id="2157e-123">Executable documentation</span></span>

<span data-ttu-id="2157e-124">特定の入力によって、特定のメソッドが何を実行するか、またはそのメソッドがどのように動作するかは、必ずしも明らかではありません。</span><span class="sxs-lookup"><span data-stu-id="2157e-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="2157e-125">空の文字列や Null を渡した場合にこのメソッドがどのように動作するか、自分自身わからないことが</span><span class="sxs-lookup"><span data-stu-id="2157e-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="2157e-126">あります。</span><span class="sxs-lookup"><span data-stu-id="2157e-126">Null?</span></span>

<span data-ttu-id="2157e-127">適切な名前の単体テストのスイートがある場合、各テストは、特定の入力に対して想定される出力を明確に説明できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="2157e-128">さらに、実際に動作することを確認できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="2157e-129">疎結合コード</span><span class="sxs-lookup"><span data-stu-id="2157e-129">Less coupled code</span></span>

<span data-ttu-id="2157e-130">コードが密結合されている場合、単体テストは難しくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="2157e-131">記述しているコードに対して単体テストを作成しないと、結合を明確に認識できません。</span><span class="sxs-lookup"><span data-stu-id="2157e-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="2157e-132">したがって、コードに対するテストを記述する際には、必然的にコードを分離します。そうしないと、テストが困難になるからです。</span><span class="sxs-lookup"><span data-stu-id="2157e-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="2157e-133">適切な単体テストの特性</span><span class="sxs-lookup"><span data-stu-id="2157e-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="2157e-134">**高速**。</span><span class="sxs-lookup"><span data-stu-id="2157e-134">**Fast**.</span></span> <span data-ttu-id="2157e-135">完成度の高いプロジェクトに数千もの単体テストが含まれることは、珍しくありません。</span><span class="sxs-lookup"><span data-stu-id="2157e-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="2157e-136">単体テストの実行にかかる時間はごくわずかで、</span><span class="sxs-lookup"><span data-stu-id="2157e-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="2157e-137">数ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="2157e-137">Milliseconds.</span></span>
- <span data-ttu-id="2157e-138">**独立性**。</span><span class="sxs-lookup"><span data-stu-id="2157e-138">**Isolated**.</span></span> <span data-ttu-id="2157e-139">単体テストはスタンドアロンであり、独立して実行でき、ファイル システムやデータベースなどの外部要因に対する依存関係がありません。</span><span class="sxs-lookup"><span data-stu-id="2157e-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="2157e-140">**反復可能**。</span><span class="sxs-lookup"><span data-stu-id="2157e-140">**Repeatable**.</span></span> <span data-ttu-id="2157e-141">単体テストの実行では、その結果に一貫性がある必要があります。つまり、実行と実行の間で何も変更しない場合、常に同じ結果を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="2157e-142">**自己チェック**。</span><span class="sxs-lookup"><span data-stu-id="2157e-142">**Self-Checking**.</span></span> <span data-ttu-id="2157e-143">テストは人の介入なしに、合格したか失敗したかを自動的に検出できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="2157e-144">**タイムリー**。</span><span class="sxs-lookup"><span data-stu-id="2157e-144">**Timely**.</span></span> <span data-ttu-id="2157e-145">単体テストは、テスト対象のコードの記述と比較して時間がかかりすぎないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="2157e-146">コードの記述と比較してコードのテストに時間がかかりすぎる場合は、よりテストしやすい設計を検討してください。</span><span class="sxs-lookup"><span data-stu-id="2157e-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="code-coverage"></a><span data-ttu-id="2157e-147">コード カバレッジ</span><span class="sxs-lookup"><span data-stu-id="2157e-147">Code coverage</span></span>

<span data-ttu-id="2157e-148">コード カバレッジのパーセンテージの高さは多くの場合、コードの品質の高さに関連します。</span><span class="sxs-lookup"><span data-stu-id="2157e-148">A high code coverage percentage is often associated with a higher quality of code.</span></span> <span data-ttu-id="2157e-149">ただし、測定自体でコードの品質を判断することは "*できません*"。</span><span class="sxs-lookup"><span data-stu-id="2157e-149">However, the measurement itself *cannot* determine the quality of code.</span></span> <span data-ttu-id="2157e-150">コード カバレッジのパーセンテージ目標を過度に大きく設定すると、逆効果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="2157e-150">Setting an overly ambitious code coverage percentage goal can be counterproductive.</span></span> <span data-ttu-id="2157e-151">条件分岐が大量にある複雑なプロジェクトを想像してください。また、コード カバレッジ目標を 95% に設定することを想像してください。</span><span class="sxs-lookup"><span data-stu-id="2157e-151">Imagine a complex project with thousands of conditional branches, and imagine that you set a goal of 95% code coverage.</span></span> <span data-ttu-id="2157e-152">現在、このプロジェクトは 90% のコード カバレッジを維持しています。</span><span class="sxs-lookup"><span data-stu-id="2157e-152">Currently the project maintains 90% code coverage.</span></span> <span data-ttu-id="2157e-153">残り 5% の極端な状況をすべて考慮するために膨大な時間が必要になる可能性があり、提案された価値がすぐに減少します。</span><span class="sxs-lookup"><span data-stu-id="2157e-153">The amount of time it takes to account for all of the edge cases in the remaining 5% could be a massive undertaking, and the value proposition quickly diminishes.</span></span>

<span data-ttu-id="2157e-154">コード カバレッジのパーセンテージの高さは成功を示すものではありません。コードの品質の高さを暗に示すものでもありません。</span><span class="sxs-lookup"><span data-stu-id="2157e-154">A high code coverage percentage is not an indicator of success, nor does it imply high code quality.</span></span> <span data-ttu-id="2157e-155">単体テストの対象となるコードの量を表すだけです。</span><span class="sxs-lookup"><span data-stu-id="2157e-155">It just represents the amount of code that is covered by unit tests.</span></span> <span data-ttu-id="2157e-156">詳細については、[単体テストのコード カバレッジ](unit-testing-code-coverage.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2157e-156">For more information, see [unit testing code coverage](unit-testing-code-coverage.md).</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="2157e-157">用語を統一する</span><span class="sxs-lookup"><span data-stu-id="2157e-157">Let's speak the same language</span></span>

<span data-ttu-id="2157e-158">テストに関して、"*モック*" という用語は残念ながら誤用されることがしばしばあります。</span><span class="sxs-lookup"><span data-stu-id="2157e-158">The term *mock* is unfortunately often misused when talking about testing.</span></span> <span data-ttu-id="2157e-159">単体テストの記述時における最も一般的な種類の "*フェイク*" を定義するポイントを以下に挙げます。</span><span class="sxs-lookup"><span data-stu-id="2157e-159">The following points define the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="2157e-160">"*フェイク*" - フェイクは、スタブまたはモック オブジェクトのいずれかを示すのに使用できる汎用的な用語です。</span><span class="sxs-lookup"><span data-stu-id="2157e-160">*Fake* - A fake is a generic term that can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="2157e-161">スタブとモックのどちらであるかは、使用されているコンテキストによって決まります。</span><span class="sxs-lookup"><span data-stu-id="2157e-161">Whether it's a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="2157e-162">つまり、フェイクはスタブとモックのどちらにもなりえます。</span><span class="sxs-lookup"><span data-stu-id="2157e-162">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="2157e-163">*モック* - モック オブジェクトは、単体テストに合格したか失敗したかを判断する、システム内のフェイク オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="2157e-163">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="2157e-164">モックは、アサートされるまでフェイクとして開始します。</span><span class="sxs-lookup"><span data-stu-id="2157e-164">A mock starts out as a Fake until it's asserted against.</span></span>

<span data-ttu-id="2157e-165">*スタブ* - スタブは、システム内の既存の依存関係 (コラボレーター) の制御可能な置換です。</span><span class="sxs-lookup"><span data-stu-id="2157e-165">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="2157e-166">スタブを使用すると、依存関係を直接処理することなく、コードをテストできます。</span><span class="sxs-lookup"><span data-stu-id="2157e-166">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="2157e-167">既定では、スタブはフェイクとして開始します。</span><span class="sxs-lookup"><span data-stu-id="2157e-167">By default, a stub starts out as a fake.</span></span>

<span data-ttu-id="2157e-168">次のコード スニペットを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="2157e-168">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="2157e-169">これは、モックとして参照されるスタブの例です。</span><span class="sxs-lookup"><span data-stu-id="2157e-169">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="2157e-170">ここでは、実際にはスタブです。</span><span class="sxs-lookup"><span data-stu-id="2157e-170">In this case, it is a stub.</span></span> <span data-ttu-id="2157e-171">`Purchase` (テスト対象のシステム) をインスタンス化する手段として、Order を渡しているだけです。</span><span class="sxs-lookup"><span data-stu-id="2157e-171">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="2157e-172">Order はモックでないので、名前 `MockOrder` も紛らわしいものです。</span><span class="sxs-lookup"><span data-stu-id="2157e-172">The name `MockOrder` is also misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="2157e-173">より適切なアプローチを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="2157e-173">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="2157e-174">クラスの名前を `FakeOrder` に変更して、クラスをより汎用的な名前にし、クラスをモックまたはスタブとして使用できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="2157e-174">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="2157e-175">テスト ケースに適切な方をどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="2157e-175">Whichever is better for the test case.</span></span> <span data-ttu-id="2157e-176">上記の例では、`FakeOrder` はスタブとして使用されています。</span><span class="sxs-lookup"><span data-stu-id="2157e-176">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="2157e-177">アサート時には、どのような形状または形式でも `FakeOrder` を使用していません。</span><span class="sxs-lookup"><span data-stu-id="2157e-177">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="2157e-178">`FakeOrder` は、コンストラクターの要件を満たすためだけに `Purchase` クラスに渡されました。</span><span class="sxs-lookup"><span data-stu-id="2157e-178">`FakeOrder` was passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="2157e-179">これをモックとして使用するには、たとえば次のようにします。</span><span class="sxs-lookup"><span data-stu-id="2157e-179">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="2157e-180">この場合は、フェイクのプロパティをチェック (フェイクに対してアサート) しているので、上記のコード スニペット内で `mockOrder` はモックです。</span><span class="sxs-lookup"><span data-stu-id="2157e-180">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2157e-181">この用語を正確に理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="2157e-181">It's important to get this terminology correct.</span></span> <span data-ttu-id="2157e-182">スタブを "モック" と名付けた場合、他の開発者はあなたの意図を誤って解釈してしまいます。</span><span class="sxs-lookup"><span data-stu-id="2157e-182">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="2157e-183">モックとスタブに関する重要な留意点として、モックとスタブはよく似ていますが、モック オブジェクトに対してはアサートを行うのに対し、スタブに対してはアサートを行いません。</span><span class="sxs-lookup"><span data-stu-id="2157e-183">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="2157e-184">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="2157e-184">Best practices</span></span>

<span data-ttu-id="2157e-185">単体テストを記述するときは、インフラストラクチャに対する依存関係を設けようとしないでください。</span><span class="sxs-lookup"><span data-stu-id="2157e-185">Try not to introduce dependencies on infrastructure when writing unit tests.</span></span> <span data-ttu-id="2157e-186">テストが低速で不安定になるため、これは統合テストで行います。</span><span class="sxs-lookup"><span data-stu-id="2157e-186">These make the tests slow and brittle and should be reserved for integration tests.</span></span> <span data-ttu-id="2157e-187">アプリケーションでこれらの依存関係を回避するには、[明示的な依存関係の原則](https://deviq.com/explicit-dependencies-principle)に従い、[依存関係の挿入](../extensions/dependency-injection.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="2157e-187">You can avoid these dependencies in your application by following the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle) and using [Dependency Injection](../extensions/dependency-injection.md).</span></span> <span data-ttu-id="2157e-188">個別のプロジェクトの単体テストを統合テストと区別することもできます。</span><span class="sxs-lookup"><span data-stu-id="2157e-188">You can also keep your unit tests in a separate project from your integration tests.</span></span> <span data-ttu-id="2157e-189">これにより、単体テスト プロジェクトとインフラストラクチャ パッケージの間に参照や依存関係がなくなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-189">This ensures your unit test project doesn't have references to or dependencies on infrastructure packages.</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="2157e-190">テストの名前付け</span><span class="sxs-lookup"><span data-stu-id="2157e-190">Naming your tests</span></span>

<span data-ttu-id="2157e-191">テストの名前は、次の 3 つの部分で構成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-191">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="2157e-192">テスト対象のメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2157e-192">The name of the method being tested.</span></span>
- <span data-ttu-id="2157e-193">それがテストされるシナリオ。</span><span class="sxs-lookup"><span data-stu-id="2157e-193">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="2157e-194">シナリオが呼び出されたときに想定される動作。</span><span class="sxs-lookup"><span data-stu-id="2157e-194">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="2157e-195">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-195">Why?</span></span>

- <span data-ttu-id="2157e-196">名前付け規則は、テストの目的を明示的に表すので重要です。</span><span class="sxs-lookup"><span data-stu-id="2157e-196">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="2157e-197">テストは、コードが機能することを確認するだけでなく、ドキュメントも提供します。</span><span class="sxs-lookup"><span data-stu-id="2157e-197">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="2157e-198">単体テストのスイートを見るだけで、コード自体を見なくても、コードの動作を推測できます。</span><span class="sxs-lookup"><span data-stu-id="2157e-198">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="2157e-199">さらに、テストが失敗した際には、どのシナリオが想定を満たしていないかを正確に判断できます。</span><span class="sxs-lookup"><span data-stu-id="2157e-199">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="2157e-200">不適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-200">Bad:</span></span>

[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="2157e-201">より適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-201">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="2157e-202">テストの配置</span><span class="sxs-lookup"><span data-stu-id="2157e-202">Arranging your tests</span></span>

<span data-ttu-id="2157e-203">**Arrange、Act、Assert** は、単体テスト時に共通するパターンです。</span><span class="sxs-lookup"><span data-stu-id="2157e-203">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="2157e-204">名前が示すように、これは次の 3 つの主なアクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2157e-204">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="2157e-205">オブジェクトを *配置 (Arrange)* し、必要に応じて作成および設定します。</span><span class="sxs-lookup"><span data-stu-id="2157e-205">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="2157e-206">オブジェクトを *操作 (Act)* します。</span><span class="sxs-lookup"><span data-stu-id="2157e-206">*Act* on an object.</span></span>
- <span data-ttu-id="2157e-207">何かが想定どおりであることを *アサート (Assert)* します。</span><span class="sxs-lookup"><span data-stu-id="2157e-207">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="2157e-208">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-208">Why?</span></span>

- <span data-ttu-id="2157e-209">*配置* と *アサート* の手順で、テストする対象を明確に区別します。</span><span class="sxs-lookup"><span data-stu-id="2157e-209">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="2157e-210">"Act" コードにより、アサーションが混合される可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-210">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="2157e-211">読みやすさは、テストの作成時において最も重要な側面の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2157e-211">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="2157e-212">テスト内でこれらの各アクションを分離することで、コードの呼び出しに必要な依存関係、コードを呼び出す方法、および何をアサートしようとしているかが明確に区別されます。</span><span class="sxs-lookup"><span data-stu-id="2157e-212">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="2157e-213">いくつかの手順を結合し、テストのサイズを小さくすることは可能ですが、主な目的はテストをできるだけ読みやすくすることにあります。</span><span class="sxs-lookup"><span data-stu-id="2157e-213">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="2157e-214">不適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-214">Bad:</span></span>

[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="2157e-215">より適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-215">Better:</span></span>

[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="2157e-216">最小限の情報で合格するテストを記述する</span><span class="sxs-lookup"><span data-stu-id="2157e-216">Write minimally passing tests</span></span>

<span data-ttu-id="2157e-217">単体テストで使用する入力は、現在テストしている動作を検証するために、できる限り単純である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-217">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="2157e-218">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-218">Why?</span></span>

- <span data-ttu-id="2157e-219">コードベースでの今後の変更に対して、テストの回復力が高くなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-219">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="2157e-220">実装よりもテストの動作に的が絞られます。</span><span class="sxs-lookup"><span data-stu-id="2157e-220">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="2157e-221">テストに合格するために必要以上の情報を含むテストは、テストでエラーが発生する可能性が高く、テストの目的が不明確になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-221">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="2157e-222">テストの記述時には、動作に的を絞る必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-222">When writing tests, you want to focus on the behavior.</span></span> <span data-ttu-id="2157e-223">モデルに追加のプロパティを設定したり、不要な場合に 0 以外の値を使用すると、証明しようとしている内容が不明瞭になるだけです。</span><span class="sxs-lookup"><span data-stu-id="2157e-223">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="2157e-224">不適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-224">Bad:</span></span>

[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="2157e-225">より適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-225">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="2157e-226">マジック文字列を回避する</span><span class="sxs-lookup"><span data-stu-id="2157e-226">Avoid magic strings</span></span>

<span data-ttu-id="2157e-227">単体テストにおける変数の名前付けは、より重要というわけではなくとも、運用コードにおける変数の名前付けと同等に重要です。</span><span class="sxs-lookup"><span data-stu-id="2157e-227">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="2157e-228">単体テストにマジック文字列を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="2157e-228">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="2157e-229">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-229">Why?</span></span>

- <span data-ttu-id="2157e-230">特殊な値となっている原因を特定するために、テストを読む人が運用コードを調べる必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-230">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="2157e-231">*実現* しようとしている内容ではなく *証明* しようとしている内容が明示的に示されます。</span><span class="sxs-lookup"><span data-stu-id="2157e-231">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="2157e-232">マジック文字列は、テストを読む人に混乱をきたす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-232">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="2157e-233">文字列が通常からかけ離れて見えれば、パラメーターや戻り値としてその特定の値がなぜ選択されたかが気になります。</span><span class="sxs-lookup"><span data-stu-id="2157e-233">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="2157e-234">そのような場合、テストに集中するのではなく、実装の詳細を調べようとします。</span><span class="sxs-lookup"><span data-stu-id="2157e-234">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="2157e-235">テストの記述時には、その意図をできる限り表現することを目指す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-235">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="2157e-236">マジック文字列の場合の適切なアプローチとしては、これらの値を定数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2157e-236">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="2157e-237">不適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-237">Bad:</span></span>

[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="2157e-238">より適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-238">Better:</span></span>

[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="2157e-239">テストで論理を回避する</span><span class="sxs-lookup"><span data-stu-id="2157e-239">Avoid logic in tests</span></span>

<span data-ttu-id="2157e-240">単体テストの記述時には、手動による文字列の連結、および `if`、`while`、`for`、`switch` などの論理条件を回避します。</span><span class="sxs-lookup"><span data-stu-id="2157e-240">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="2157e-241">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-241">Why?</span></span>

- <span data-ttu-id="2157e-242">テスト内にバグが発生する可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-242">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="2157e-243">実装の詳細ではなく、最終的な結果に的が絞られます。</span><span class="sxs-lookup"><span data-stu-id="2157e-243">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="2157e-244">テスト スイートに論理を導入すると、バグが発生する可能性が著しく高まります。</span><span class="sxs-lookup"><span data-stu-id="2157e-244">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="2157e-245">テスト スイート内でバグが発見されることは避けなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2157e-245">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="2157e-246">テストが機能するという高レベルの確信が持てる必要があります。そうでなければ、テストを信頼することはできません。</span><span class="sxs-lookup"><span data-stu-id="2157e-246">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="2157e-247">信頼できないテストは、何の値も提供しません。</span><span class="sxs-lookup"><span data-stu-id="2157e-247">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="2157e-248">テストが失敗した場合は、コードに実際に問題があり、無視できないことを実感できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-248">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="2157e-249">テスト内の論理を避けられない場合は、テストを 2 つ以上の別々のテストに分割することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2157e-249">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="2157e-250">不適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-250">Bad:</span></span>

[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="2157e-251">より適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-251">Better:</span></span>

[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="2157e-252">設定と破棄よりもヘルパー メソッドを優先する</span><span class="sxs-lookup"><span data-stu-id="2157e-252">Prefer helper methods to setup and teardown</span></span>

<span data-ttu-id="2157e-253">テストに同様のオブジェクトまたは状態が必要な場合は、`Setup` 属性と `Teardown` 属性を利用する (存在する場合) より、ヘルパー メソッドを優先します。</span><span class="sxs-lookup"><span data-stu-id="2157e-253">If you require a similar object or state for your tests, prefer a helper method than leveraging `Setup` and `Teardown` attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="2157e-254">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-254">Why?</span></span>

- <span data-ttu-id="2157e-255">各テスト内からコード全体を見ることができるので、テストを読むときに混乱が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-255">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="2157e-256">特定のテストに対する設定が多すぎたり少なすぎたりする可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-256">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="2157e-257">テスト間で状態を共有して、テスト間に不要な依存関係が生じる可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="2157e-257">Less chance of sharing state between tests, which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="2157e-258">単体テスト フレームワークでは、テスト スイート内のすべての各単体テスト前に `Setup` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2157e-258">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="2157e-259">これは便利なツールとして見なされる場合もありますが、通常はテストが膨張して読みづらくなってしまいます。</span><span class="sxs-lookup"><span data-stu-id="2157e-259">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="2157e-260">各テストには、テストが稼働するためにさまざまな要件があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-260">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="2157e-261">しかし、`Setup` は各テストに対してまったく同じ要件を使用することを強制します。</span><span class="sxs-lookup"><span data-stu-id="2157e-261">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="2157e-262">xUnit では、バージョン 2.x の時点で SetUp と TearDown の両方が削除されています。</span><span class="sxs-lookup"><span data-stu-id="2157e-262">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="2157e-263">不適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-263">Bad:</span></span>

[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="2157e-264">より適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-264">Better:</span></span>

[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="2157e-265">複数のアサートを回避する</span><span class="sxs-lookup"><span data-stu-id="2157e-265">Avoid multiple asserts</span></span>

<span data-ttu-id="2157e-266">テストを記述する際には、テストごとにアサートを 1 つだけ含めるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="2157e-266">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="2157e-267">アサートを 1 つだけ使用する一般的なアプローチには、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="2157e-267">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="2157e-268">アサートごとに別々のテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="2157e-268">Create a separate test for each assert.</span></span>
- <span data-ttu-id="2157e-269">パラメーター化されたテストを使用します。</span><span class="sxs-lookup"><span data-stu-id="2157e-269">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="2157e-270">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-270">Why?</span></span>

- <span data-ttu-id="2157e-271">1 つのアサートに失敗した場合、後続のアサートは評価されません。</span><span class="sxs-lookup"><span data-stu-id="2157e-271">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="2157e-272">テストで複数のケースをアサートしないようにします。</span><span class="sxs-lookup"><span data-stu-id="2157e-272">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="2157e-273">テストが失敗した理由に関する全体像をとらえることができます。</span><span class="sxs-lookup"><span data-stu-id="2157e-273">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="2157e-274">テスト ケースに複数のアサートを導入した場合、すべてのアサートが実行されることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="2157e-274">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="2157e-275">ほとんどの単体テスト フレームワークでは、単体テストでアサーションが失敗すると、続行中のテストは自動的に失敗と見なされます。</span><span class="sxs-lookup"><span data-stu-id="2157e-275">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="2157e-276">この際、実際には動作している機能が失敗として示されるので、混乱を招きます。</span><span class="sxs-lookup"><span data-stu-id="2157e-276">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="2157e-277">この規則の一般的な例外は、オブジェクトに対してアサートを行う場合です。</span><span class="sxs-lookup"><span data-stu-id="2157e-277">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="2157e-278">この場合、オブジェクトが想定どおりの状態にあること保証するために、通常は各プロパティに対して複数のアサートを使用することが許容されます。</span><span class="sxs-lookup"><span data-stu-id="2157e-278">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="2157e-279">不適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-279">Bad:</span></span>

[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="2157e-280">より適切な例:</span><span class="sxs-lookup"><span data-stu-id="2157e-280">Better:</span></span>

[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="2157e-281">パブリック メソッドの単体テストを行うことでプライベート メソッドを検証する</span><span class="sxs-lookup"><span data-stu-id="2157e-281">Validate private methods by unit testing public methods</span></span>

<span data-ttu-id="2157e-282">ほとんどの場合、プライベート メソッドをテストする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2157e-282">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="2157e-283">プライベート メソッドは実装の詳細です。</span><span class="sxs-lookup"><span data-stu-id="2157e-283">Private methods are an implementation detail.</span></span> <span data-ttu-id="2157e-284">プライベート メソッドは独立して存在することはない、と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="2157e-284">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="2157e-285">いずれかの時点で、実装の一部としてプライベート メソッドを呼び出す、パブリックに公開されたメソッドが存在することになります。</span><span class="sxs-lookup"><span data-stu-id="2157e-285">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="2157e-286">鍵となるのは、プライベート メソッドを呼び出すパブリック メソッドの最終結果です。</span><span class="sxs-lookup"><span data-stu-id="2157e-286">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="2157e-287">次のケースを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="2157e-287">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="2157e-288">メソッドが想定どおりに動作していることを確認する必要があるので、まずは、`TrimInput` に対してテストを記述しようと考えるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="2157e-288">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="2157e-289">しかし、想定外の方法で `ParseLogLine` が `sanitizedInput` を操作し、`TrimInput` に対するテストが無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-289">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="2157e-290">実際のテストは、パブリックに公開された `ParseLogLine` メソッドに対して行う必要があります。最終的にはこのメソッドが鍵となるためです。</span><span class="sxs-lookup"><span data-stu-id="2157e-290">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_StartsAndEndsWithSpace_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="2157e-291">この観点で、プライベート メソッドがある場合は、パブリック メソッドを見つけて、そのメソッドに対してテストを記述します。</span><span class="sxs-lookup"><span data-stu-id="2157e-291">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="2157e-292">プライベート メソッドが想定どおりの結果を返すからといって、最終的にプライベート メソッドを呼び出すシステムが、結果を正しく使用するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="2157e-292">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="2157e-293">スタブの静的参照</span><span class="sxs-lookup"><span data-stu-id="2157e-293">Stub static references</span></span>

<span data-ttu-id="2157e-294">単体テストの原則の 1 つは、テスト対象システムに対してフル コントロールを持つ必要があることです。</span><span class="sxs-lookup"><span data-stu-id="2157e-294">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="2157e-295">このことは、運用コードに静的参照への呼び出しが含まれる場合に問題となります (例: `DateTime.Now`)。</span><span class="sxs-lookup"><span data-stu-id="2157e-295">This can be problematic when production code includes calls to static references (for example, `DateTime.Now`).</span></span> <span data-ttu-id="2157e-296">次のコードを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="2157e-296">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if (DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="2157e-297">このコードに対して単体テストを行うには、どのようにすればよいでしょうでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2157e-297">How can this code possibly be unit tested?</span></span> <span data-ttu-id="2157e-298">次のようなアプローチを試してみることができます。</span><span class="sxs-lookup"><span data-stu-id="2157e-298">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="2157e-299">ただし、このテストにはいくつかの問題があることがすぐにわかります。</span><span class="sxs-lookup"><span data-stu-id="2157e-299">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="2157e-300">テスト スイートが火曜日に実行される場合、2 番目のテストには合格しますが、最初のテストには失敗します。</span><span class="sxs-lookup"><span data-stu-id="2157e-300">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="2157e-301">テスト スイートが他のいずれかの曜日に実行される場合、最初のテストには合格しますが、2 番目のテストには失敗します。</span><span class="sxs-lookup"><span data-stu-id="2157e-301">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="2157e-302">こうした問題を解決するには、運用コードに *シーム* を導入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2157e-302">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="2157e-303">1 つのアプローチとしては、インターフェイス内で制御する必要のあるコードをラップし、運用コードがそのインターフェイスに依存するようにします。</span><span class="sxs-lookup"><span data-stu-id="2157e-303">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if (dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="2157e-304">この時点で、テスト スイートは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2157e-304">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="2157e-305">これで、テスト スイートは `DateTime.Now` に対してフル コントロールを持ち、メソッドを呼び出すときに任意の値をスタブできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2157e-305">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
