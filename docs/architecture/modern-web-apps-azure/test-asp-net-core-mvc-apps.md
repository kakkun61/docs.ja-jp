---
title: ASP.NET Core MVC アプリのテスト
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | ASP.NET Core MVC アプリのテスト
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
ms.openlocfilehash: b253cfb90487cc462b0f3b8a7564c97ad403aa06
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851400"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="9a2a4-103">ASP.NET Core MVC アプリのテスト</span><span class="sxs-lookup"><span data-stu-id="9a2a4-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="9a2a4-104">*"あなたが製品の単体テストを好まないと、あなたの顧客もテストを望まないでしょう。"*</span><span class="sxs-lookup"><span data-stu-id="9a2a4-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="9a2a4-105">\_- 匿名 -</span><span class="sxs-lookup"><span data-stu-id="9a2a4-105">\_- Anonymous-</span></span>

<span data-ttu-id="9a2a4-106">変更に対応するとき、複雑なソフトウェアには予想外のエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="9a2a4-107">そのため、ほとんどの些細な (少なくとも重要性が最も低い) アプリケーションを除くすべてのアプリケーションで変更後のテストが必須となります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="9a2a4-108">手動テストはソフトウェアのテスト方法として最も遅く、信頼性がなく、高額です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="9a2a4-109">残念ながら、アプリケーションにテスト機能が付いていない場合、手動テストが唯一の手段になることがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="9a2a4-110">[第 4 章](architectural-principles.md)に記載されているアーキテクチャの原則に従って作成されたアプリケーションは、単体テストが可能になります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="9a2a4-111">ASP.NET Core アプリケーションでは、統合テストと機能テストの自動化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="9a2a4-112">自動テストの種類</span><span class="sxs-lookup"><span data-stu-id="9a2a4-112">Kinds of automated tests</span></span>

<span data-ttu-id="9a2a4-113">ソフトウェア アプリケーションでは、さまざまな種類のテストが自動化されています。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="9a2a4-114">最も単純でレベルの低いテストが単体テストです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="9a2a4-115">少し高いレベルに、統合テストや機能テストがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="9a2a4-116">他の種類のテスト (UI テスト、ロード テスト、ストレス テスト、スモーク テストなど) は、このドキュメントでは扱いません。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="9a2a4-117">単体テスト</span><span class="sxs-lookup"><span data-stu-id="9a2a4-117">Unit tests</span></span>

<span data-ttu-id="9a2a4-118">単体テストでは、アプリケーションのロジックの 1 つの部分をテストします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="9a2a4-119">単体テストに含まれない内容を列挙するして単体テストをさらに説明できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="9a2a4-120">単体テストでは、依存関係やインフラストラクチャとのコードの連動をテストしません。それは統合テストの対象です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="9a2a4-121">単体テストでは、コード記述の基礎となるフレームワークをテストしません。フレームワークは動作すると想定してください。動作しないことが判明した場合、バグを提出するか、回避策となるコードを記述してください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="9a2a4-122">単体テストは、メモリとプロセスの中で完全に実行されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="9a2a4-123">ファイル システム、ネットワーク、データベースとは通信しません。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="9a2a4-124">単体テストはコードのみをテストします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="9a2a4-125">単体テストはコードの 1 単位のみをテストし、外部の依存関係が関与しないため、極めて短時間で実行されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely fast.</span></span> <span data-ttu-id="9a2a4-126">そのため、何百という単体テストからなるテスト スイートを数秒で実行できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="9a2a4-127">単体テストは頻繁に実行してください。共有ソース管理リポジトリにプッシュするたびに実行するのが理想です。ビルド サーバーで自動化ビルドを実行したときには、もちろん毎回実行してください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="9a2a4-128">統合テスト</span><span class="sxs-lookup"><span data-stu-id="9a2a4-128">Integration tests</span></span>

<span data-ttu-id="9a2a4-129">データベースやファイル システムなど、インフラストラクチャとやり取りするコードをカプセル化することは良い考えですが、それでもカプセル化されないコードが残るので、それをテストすることになります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="9a2a4-130">また、アプリケーションの依存関係が完全に解決されるとき、コードの層が予想どおりにやり取りすることを検証してください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="9a2a4-131">この機能は統合テストの担当です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-131">This functionality is the responsibility of integration tests.</span></span> <span data-ttu-id="9a2a4-132">統合テストには、単体テストより時間がかかり、設定が難しくなる傾向があります。外部の依存関係やインフラストラクチャに依存することが多いためです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="9a2a4-133">そのため、統合テストでは、単体テストでテストできるようなことはテストしないでください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="9a2a4-134">所与のシナリオを単体テストでテストできる場合、単体テストでテストしてください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="9a2a4-135">単体テストでテストできない場合、統合テストの利用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="9a2a4-136">統合テストは多くの場合、セットアップと破棄のプロシージャが単体テストより複雑です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="9a2a4-137">たとえば、実際のデータベースに対して統合テストを行うとき、データベースをテスト実行前の既知の状態に戻す方法が必要になります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="9a2a4-138">新しいテストが追加され、運用データベース スキーマが拡大するにつれ、テスト スクリプトのサイズが増加し、より複雑になります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="9a2a4-139">大規模なシステムの多くでは、共有ソース管理の変更を調べる前に、開発者ワークステーションで完全な統合テスト スイートを実行することは実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="9a2a4-140">そのような場合、ビルド サーバーで統合テストを実行できることがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="9a2a4-141">機能テスト</span><span class="sxs-lookup"><span data-stu-id="9a2a4-141">Functional tests</span></span>

<span data-ttu-id="9a2a4-142">システムの一部のコンポーネントが正しく連動することを確認する目的で、統合テストは開発者の視点から記述されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="9a2a4-143">機能テストはユーザーの視点から記述され、その要件に基づき、システムの正確性を検証します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="9a2a4-144">機能テストとは何か、単体テストとの比較で考えるとき、次の抜粋が類推として役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="9a2a4-145">"多くの場合、システムの開発は家の建築に例えられます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="9a2a4-146">この類推はまったく正しいというわけではありませんが、単体テストと機能テストの違いを理解する目的で拡大解釈できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="9a2a4-147">単体テストは、建築調査官が家の建築現場を訪問する行為に似ています。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="9a2a4-148">調査官は家のさまざまな内部システム、土台、骨組み、電気、配管を重点的に調べ、</span><span class="sxs-lookup"><span data-stu-id="9a2a4-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="9a2a4-149">家の各部分が正しく安全に機能すること、つまり、建築法規に準拠していることを確認 (テスト) します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="9a2a4-150">このシナリオにおける機能テストは、家主がこの同じ建築現場を訪問する行為に似ています。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="9a2a4-151">家主は、内部システムが適切に動作し、建築調査官がその仕事を遂行しているものと想定し、</span><span class="sxs-lookup"><span data-stu-id="9a2a4-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="9a2a4-152">その家で生活することはどのような感じになるのかを重点的に確認します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="9a2a4-153">家はどのように見えるか、各部屋の大きさはちょうど良いか、家は家族の希望に合っているか、朝日を取り入れる場所に窓が取り付けられているかが重要となります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="9a2a4-154">家主は家に機能テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="9a2a4-155">家主の視点はユーザーの視点です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-155">He has the user's perspective.</span></span> <span data-ttu-id="9a2a4-156">建築調査官は家に単体テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="9a2a4-157">調査官の視点は開発者の視点です。"</span><span class="sxs-lookup"><span data-stu-id="9a2a4-157">He has the builder's perspective."</span></span>

<span data-ttu-id="9a2a4-158">ソース:[Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (単体テストと機能テストの比較)</span><span class="sxs-lookup"><span data-stu-id="9a2a4-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="9a2a4-159">"開発者は 2 通りの失敗をします。間違った方法で開発することと間違ったものを開発することです。" というのは私の好きな表現です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="9a2a4-160">単体テストでは、正しい方法で開発していることを確認します。機能テストでは、正しいものを開発していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="9a2a4-161">機能テストはシステム レベルで動作するため、ある程度の UI 自動化が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="9a2a4-162">統合テストと同様に、通常、ある種のテスト インフラストラクチャとも連動します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="9a2a4-163">このアクティビティにより、単体テストや統合テストより遅くなり、不安定になります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-163">This activity makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="9a2a4-164">機能テストは、システムがユーザーの期待どおりに動作すると確信できるために必要な数だけ行ってください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="9a2a4-165">テストのピラミッド</span><span class="sxs-lookup"><span data-stu-id="9a2a4-165">Testing Pyramid</span></span>

<span data-ttu-id="9a2a4-166">Martin Fowler がテストをピラミッド図にしました。図 9-1 がその例です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![テストのピラミッド](./media/image9-1.png)

<span data-ttu-id="9a2a4-168">**図 9-1**</span><span class="sxs-lookup"><span data-stu-id="9a2a4-168">**Figure 9-1**.</span></span> <span data-ttu-id="9a2a4-169">テストのピラミッド</span><span class="sxs-lookup"><span data-stu-id="9a2a4-169">Testing Pyramid</span></span>

<span data-ttu-id="9a2a4-170">ピラミッドの各層はテストの種類を表し、その相対的な大きさはアプリケーションのために記述すべきテストの数を表します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="9a2a4-171">ご覧のように、単体テストの土台を大きくし、それより小さい統合テスト層が続き、さらに小さい機能テスト層が続くという構成が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="9a2a4-172">各層には、理想的には、それより下の層では適切に実行できないテストのみを含めます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="9a2a4-173">特定のシナリオで必要とするテストの種類を決定するとき、このピラミッドを念頭に置いてください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="9a2a4-174">テストの内容</span><span class="sxs-lookup"><span data-stu-id="9a2a4-174">What to test</span></span>

<span data-ttu-id="9a2a4-175">自動化テストの記述経験がない開発者にとっては、何をテストするのかが共通の問題です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="9a2a4-176">理想的な出発点は条件ロジックをテストすることです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="9a2a4-177">条件付きステートメント (if-else、switch など) に基づいて動作が変わるメソッドを使用している場所では、特定の条件に対する正しい動作を確認するためのテストを、少なくとも 2、3 個思い付くはずです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="9a2a4-178">コードの条件に間違いがある場合、(エラーのない) コード経由で "Happy Path" のテストを少なくとも 1 つ記述し、(エラーがあるか、結果が不規則な) "Sad Path" のテストを少なくとも 1 つ記述し、エラーに直面したときにアプリケーションが予想どおりに動作することを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="9a2a4-179">最後に、コード カバレッジなどの指標ではなく、エラーが起こりうるものに対するテストに集中的に取り組みます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="9a2a4-180">一般的に、カバレッジは少ないよりも多い方が良いとされます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="9a2a4-181">ただし、複雑でビジネスに不可欠なメソッド用にさらにいくつかのテストを記述することは、通常、テストのコード カバレッジ メトリックを改善するためだけに自動プロパティのテストを記述するよりも優れた時間の使い方です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="9a2a4-182">テスト プロジェクトを整理する</span><span class="sxs-lookup"><span data-stu-id="9a2a4-182">Organizing test projects</span></span>

<span data-ttu-id="9a2a4-183">テスト プロジェクトは、自分にとって最適に機能するように整理できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="9a2a4-184">種類 (単体テストや統合テスト) やテスト内容 (プロジェクトや名前空間) に基づいてテストを分類することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="9a2a4-185">その分類が 1 つのテスト プロジェクト内のフォルダーで構成されるのか、複数のテスト プロジェクト内のフォルダーで構成されるのかは設計上の決定事項の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="9a2a4-186">プロジェクトが 1 つであれば最も単純に整理されますが、大型のプロジェクトでさまざまなテストが含まれる場合、あるいはさまざまなテスト セットをより簡単に実行するには、複数のテスト プロジェクトが必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="9a2a4-187">多くのチームは、自分たちがテストしているプロジェクトに基づいてプロジェクトを整理します。アプリケーションに相当な数のプロジェクトが含まれるとき、テスト プロジェクトが大量になります。各プロジェクトに含まれるテストの種類に基づいてさらに細分化される場合は特に大量になります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="9a2a4-188">妥協案としては、テストの種類あたり、アプリケーションあたりプロジェクトを 1 つとし、テスト プロジェクトの中にフォルダーを置き、テスト対象のプロジェクト (とクラス) を示します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="9a2a4-189">一般的な方法は、'src' フォルダーの下でアプリケーション プロジェクトを整理し、並列する 'tests' フォルダーの下でアプリケーションのテスト プロジェクトを整理することです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="9a2a4-190">この整理方法が有効な場合、Visual Studio でこれに合ったソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![ソリューション内のテストの整理](./media/image9-2.png)

<span data-ttu-id="9a2a4-192">**図 9-2**</span><span class="sxs-lookup"><span data-stu-id="9a2a4-192">**Figure 9-2**.</span></span> <span data-ttu-id="9a2a4-193">ソリューション内のテストの整理</span><span class="sxs-lookup"><span data-stu-id="9a2a4-193">Test organization in your solution</span></span>

<span data-ttu-id="9a2a4-194">好きな方のテスト フレームワークを利用できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="9a2a4-195">xUnit フレームワークは良好に動作し、ASP.NET Core と EF Core テストはすべてこれで記述されています。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="9a2a4-196">図 9-3 のテンプレートを使用するか、CLI から `dotnet new xunit` を使用して、Visual Studio で xUnit テスト プロジェクトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![Visual Studio で xUnit テスト プロジェクトを追加する](./media/image9-3.png)

<span data-ttu-id="9a2a4-198">**図 9-3**</span><span class="sxs-lookup"><span data-stu-id="9a2a4-198">**Figure 9-3**.</span></span> <span data-ttu-id="9a2a4-199">Visual Studio で xUnit テスト プロジェクトを追加する</span><span class="sxs-lookup"><span data-stu-id="9a2a4-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="9a2a4-200">テストの命名規則</span><span class="sxs-lookup"><span data-stu-id="9a2a4-200">Test naming</span></span>

<span data-ttu-id="9a2a4-201">テストには一貫性のある名前を付けてください。各テストの内容を示す名前にします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="9a2a4-202">テストするクラスやメソッドに基づいてテスト クラスに名前を付けるという方法でうまく行ったことがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="9a2a4-203">このアプローチの結果、小さなテスト クラスが多く作られますが、それぞれのテストが担当する内容がとても明確になります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-203">This approach results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="9a2a4-204">テストするクラスやメソッドを識別するためにテスト クラスの名前を設定すると、テスト メソッド名を利用し、テストする動作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-204">With the test class name set up, to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="9a2a4-205">この名前には、想定される動作と、その動作をもたらす入力や前提を含めるようにします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-205">This name should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="9a2a4-206">テスト名の例:</span><span class="sxs-lookup"><span data-stu-id="9a2a4-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="9a2a4-207">この方法のバリエーションとしては、それぞれのテスト クラスの名前の末尾を "Should" にして時制を少し変えます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="9a2a4-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="9a2a4-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="9a2a4-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="9a2a4-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="9a2a4-210">少しばかり冗長ですが、2 つ目の命名規則の方がわかりやすいと感じるチームもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="9a2a4-211">いずれにせよ、テストの動作がわかる命名規則を利用してください。テストが失敗したとき、何が失敗したのか名前から判断できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="9a2a4-212">ControllerTests.Test1 のような曖昧な名前をテストに付けないでください。テスト結果に表示されるときに、これらの名前に何の価値もなくなります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these names offer no value when you see them in test results.</span></span>

<span data-ttu-id="9a2a4-213">小さなテスト クラスをたくさん生成する上記のような命名規則に従う場合、フォルダーや名前空間を利用し、テストをさらに整理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="9a2a4-214">図 9-4 では、テスト プロジェクト内のフォルダー別にテストを整理している手法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![テストされるクラスに基づき、テスト クラスをフォルダーで分けて整理する](./media/image9-4.png)

<span data-ttu-id="9a2a4-216">**図 9-4**</span><span class="sxs-lookup"><span data-stu-id="9a2a4-216">**Figure 9-4.**</span></span> <span data-ttu-id="9a2a4-217">テストされるクラスに基づき、テスト クラスをフォルダーで分けて整理します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="9a2a4-218">特定のアプリケーション クラスにテスト対象メソッドが多数ある (したがってテスト クラスも多数ある) 場合は、そのアプリケーション クラスに対応するフォルダーにこれらのクラスを配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these classes in a folder corresponding to the application class.</span></span> <span data-ttu-id="9a2a4-219">その整理方法では、ファイルをどこか他の場所のフォルダーに入れて整理する場合と変わりません。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="9a2a4-220">1 つのフォルダーの中に関連ファイルが 3 つもしくは 4 つ以上存在するとき、それぞれの下位フォルダーに移動させると便利なことがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="9a2a4-221">ASP.NET Core アプリを単体テストする</span><span class="sxs-lookup"><span data-stu-id="9a2a4-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="9a2a4-222">うまく設計された ASP.NET Core アプリケーションでは、ビジネス エンティティやさまざまなサービスにほとんどの複雑性やビジネス ロジックがカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="9a2a4-223">ASP.NET Core MVC アプリ自体とそのコントローラー、ビューモデル、ビューには単体テストはほとんど必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require few unit tests.</span></span> <span data-ttu-id="9a2a4-224">アクションの機能性の多くは、アクション メソッド自体の外にあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="9a2a4-225">ルーティングやグローバル エラーの処理が正しく行われているかどうかのテストを単体テストで実施することは、効果的ではありません。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-225">Testing whether routing or global error handling work correctly cannot be done effectively with a unit test.</span></span> <span data-ttu-id="9a2a4-226">同様に、モデル検証、認証、許可のフィルターを含むすべてのフィルターも、コントローラーのアクション メソッドをターゲットとするテストによって単体テストを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="9a2a4-227">動作の源がなければ、ほとんどのアクション メソッドは取るに足りないほど小さくなります。動作の源を利用するコントローラーに関係なくテストできるサービスに作業の大部分が委任されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="9a2a4-228">場合によっては、単体テストする目的で、コードを改良する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="9a2a4-229">多くの場合、このアクティビティでは、インフラストラクチャに対して直接コーディングするのではなく、抽象化を識別し、依存関係の挿入を使用して、テストするコードの抽象化にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-229">Frequently this activity involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="9a2a4-230">たとえば、次の例をご覧ください。これは画像を表示する簡単なアクション メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-230">For example, consider this easy action method for displaying images:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

<span data-ttu-id="9a2a4-231">このメソッドの単体テストは、ファイル システムからの読み取りに使われている `System.IO.File` に直接依存することで難しくなります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="9a2a4-232">この動作をテストし、予想どおり動くことを確認できますが、実際のファイルでそれをするのは統合テストです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="9a2a4-233">このメソッドのルートに対して単体テストを実施できない点に注目してください &mdash; この後すぐに、機能テストでこのテストを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-233">It's worth noting you can't unit test this method's route&mdash;you'll see how to do this testing with a functional test shortly.</span></span>

<span data-ttu-id="9a2a4-234">ファイル システムの動作の単体テストが直接実行できないために、ルートをテストできない場合、どのようなテストが残されているのでしょうか?</span><span class="sxs-lookup"><span data-stu-id="9a2a4-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="9a2a4-235">改良して単体テストを可能にすると、テスト ケースや、エラー処理など、足りない動作が見つかることがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="9a2a4-236">ファイルが見つからないとき、メトリックは何を行うのでしょうか?</span><span class="sxs-lookup"><span data-stu-id="9a2a4-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="9a2a4-237">何をすべきでしょうか?</span><span class="sxs-lookup"><span data-stu-id="9a2a4-237">What should it do?</span></span> <span data-ttu-id="9a2a4-238">この例では、改良後のメソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-238">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

<span data-ttu-id="9a2a4-239">`_logger` と `_imageService` は、両方とも依存関係として注入されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="9a2a4-240">これで、アクション メソッドに渡されるのと同じ ID が `_imageService` に渡されることと、生成されるバイトが FileResult の一部として返されることをテストできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="9a2a4-241">また、エラー ログが予想どおり行われることと、画像が見つからない場合に `NotFound` 結果が返されることもテストできます (この動作が重要なアプリケーション動作である (つまり、問題を診断するために開発者が追加した一時的なコードではない) ことを前提とします)。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this behavior is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="9a2a4-242">実際のファイル ロジックは別個の実装サービスに移動しており、ファイルが足りない場合にアプリケーション固有の例外を返すように拡大されています。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="9a2a4-243">統合テストを利用して、この実装を非依存でテストできます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="9a2a4-244">ほとんどの場合、コントローラーにグローバルの例外ハンドラーを使用します。それにより、コントローラーのロジック量が最小限に抑えられ、単体テストの必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="9a2a4-245">コントローラー アクションのテストのほとんどは、機能テストと下記の `TestServer` クラスを使用して実行してください。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="9a2a4-246">ASP.NET Core Apps を統合テストする</span><span class="sxs-lookup"><span data-stu-id="9a2a4-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="9a2a4-247">ASP.NET Core アプリのほとんどの統合テストで、インフラストラクチャ プロジェクトに定義されているサービスとその他の種類の実装をテストします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="9a2a4-248">たとえば、Infrastructure プロジェクト内に存在するデータ アクセス クラスから [EF Core が期待されるデータを正常に更新および取得したことをテストする](/ef/core/miscellaneous/testing/)ことができます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="9a2a4-249">ASP.NET Core MVC プロジェクトが正しく動作していることをテストする最良の方法は、テスト ホストで実行されているアプリに対して機能テストを実行することです。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="9a2a4-250">ASP.NET Core アプリを機能テストする</span><span class="sxs-lookup"><span data-stu-id="9a2a4-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="9a2a4-251">ASP.NET Core アプリケーションの場合、`TestServer` クラスを利用すると、機能テストをとても簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="9a2a4-252">`TestServer` を `WebHostBuilder` (または `HostBuilder`) を使用するように直接構成する (アプリケーションに対して通常実行するのと同じ)、または `WebApplicationFactory` 型 (バージョン 2.1 以降で使用可能) で構成します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="9a2a4-253">テスト ホストを運用ホストとできる限り一致させるようにしてください。これにより、運用環境でのアプリの動作と同様の動作がテストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="9a2a4-254">`WebApplicationFactory` クラスは、ビューなどの静的リソースを検索するために ASP.NET Core によって使用される、TestServer の ContentRoot を構成するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="9a2a4-255">`TEntry` が Web アプリケーションの `Startup` クラスである、`IClassFixture\<WebApplicationFactory\<TEntry>>` を実装するテスト クラスを作成することによって、シンプルな機能テストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-255">You can create simple functional tests by creating a test class that implements `IClassFixture\<WebApplicationFactory\<TEntry>>`, where `TEntry` is your web application's `Startup` class.</span></span> <span data-ttu-id="9a2a4-256">このインターフェイスを組み込むと、ファクトリの `CreateClient` メソッドを使用して、テスト フィクスチャでクライアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-256">With this interface in place, your test fixture can create a client using the factory's `CreateClient` method:</span></span>

```csharp
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BasicWebTests(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="9a2a4-257">アプリケーションをメモリ データ ストアで使用するように構成し、テスト データを使ってアプリケーションをシードするなど、各テストを実行する前に、ご利用のサイトの追加の構成を実行する必要があることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in-memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="9a2a4-258">この機能を実現するには、`WebApplicationFactory\<TEntry>` の独自のサブクラスを作成し、その `ConfigureWebHost` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-258">To achieve this functionality, create your own subclass of `WebApplicationFactory\<TEntry>` and override its `ConfigureWebHost` method.</span></span> <span data-ttu-id="9a2a4-259">以下の例は、eShopOnWeb FunctionalTests プロジェクトからのもので、メインの Web アプリケーション上でのテストの一部として使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

<span data-ttu-id="9a2a4-260">テストでは、クライアントを作成するために使用し、このクライアント インスタンスを使用してアプリケーションに要求を出すことによって、このカスタム WebApplicationFactory を活用できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="9a2a4-261">アプリケーションには、テストのアサーションの一部として使用できる、シードされたデータがあります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="9a2a4-262">次のテストは、eShopOnWeb アプリケーションのホーム ページが正しく読み込まれることを検証し、シード データの一部としてアプリケーションに追加された製品の一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```csharp
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="9a2a4-263">この機能テストでは、配置されているあらゆるミドルウェア、フィルター、バインダーなど、完全な ASP.NET Core MVC / Razor Pages アプリケーション スタックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, and binders that may be in place.</span></span> <span data-ttu-id="9a2a4-264">特定のルート ("/") が想定される正常な状態コードと HTML 出力を返すことを検証します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="9a2a4-265">これは、実際の Web サーバーを設定せずに行われます。また、実際の Web サーバーをテスト目的で使用した場合に経験する脆弱性 (ファイアウォール設定の問題など)、をほぼ回避できます。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-265">It does so without setting up a real web server, and avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="9a2a4-266">TestServer に対して実行される機能テストは通常、統合テストや単体テストより遅くなりますが、テスト Web サーバーのネットワークで実行されるテストよりはるかに速くなります。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="9a2a4-267">アプリケーションのフロント エンドのスタックが想定どおりに確実に動作するようにするため、機能テストを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="9a2a4-268">これらのテストは、コントローラーやページに重複があり、フィルターを追加して重複に対処するときに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="9a2a4-269">このリファクタリングではアプリケーションの動作を変更せずに、機能テストのスイートによってこの状況を検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="9a2a4-270">リファレンス – ASP.NET Core MVC アプリのテスト</span><span class="sxs-lookup"><span data-stu-id="9a2a4-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="9a2a4-271">**ASP.NET Core でのテスト** </span><span class="sxs-lookup"><span data-stu-id="9a2a4-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="9a2a4-272">**単体テストの名前付け規則** </span><span class="sxs-lookup"><span data-stu-id="9a2a4-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="9a2a4-273">**EF Core のテスト** </span><span class="sxs-lookup"><span data-stu-id="9a2a4-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="9a2a4-274">**ASP.NET Core での統合テスト** </span><span class="sxs-lookup"><span data-stu-id="9a2a4-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="9a2a4-275">[前へ](work-with-data-in-asp-net-core-apps.md)
>[次へ](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="9a2a4-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
