---
title: .NET でのテスト
description: この記事では、.NET でのテストにおけるテストの概念、用語、ツールについて簡単に説明します。
author: IEvangelist
ms.author: dapine
ms.date: 10/19/2020
ms.openlocfilehash: 137a8f4e3bc9e3be529d5034c233d283cf158b31
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824858"
---
# <a name="testing-in-net"></a><span data-ttu-id="b0bbb-103">.NET でのテスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-103">Testing in .NET</span></span>

<span data-ttu-id="b0bbb-104">この記事では、テストの概念と、コードの検証に使用できるさまざまな種類のテストについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-104">This article introduces the concept of testing, and illustrates how different kinds of tests can be used to validate code.</span></span> <span data-ttu-id="b0bbb-105">.NET アプリケーションのテストには、[.NET CLI](#net-cli) や[統合開発環境 (IDE)](#ide) など、さまざまなツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-105">There are various tools available for testing .NET applications, such as the [.NET CLI](#net-cli) or [Integrated Development Environments (IDEs)](#ide).</span></span>

## <a name="test-types"></a><span data-ttu-id="b0bbb-106">テストの種類</span><span class="sxs-lookup"><span data-stu-id="b0bbb-106">Test types</span></span>

<span data-ttu-id="b0bbb-107">アプリケーション コードが作成者の意図どおりに動作するように自動テストを行うのは、最良の方法です。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-107">Having automated tests is a great way to ensure that application code does what its authors intend it to do.</span></span> <span data-ttu-id="b0bbb-108">この記事では、単体テスト、統合テスト、およびロード テストについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-108">This article covers unit tests, integration tests, and load tests.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="b0bbb-109">単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-109">Unit tests</span></span>

<span data-ttu-id="b0bbb-110">"*単体テスト*" とは、"作業単位" とも呼ばれるソフトウェアの個々のコンポーネントまたはメソッドを動かすテストです。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-110">A *unit test* is a test that exercises individual software components or methods, also known as "unit of work".</span></span> <span data-ttu-id="b0bbb-111">単体テストでは、開発者の管理下でのみ、コードをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-111">Unit tests should only test code within the developer's control.</span></span> <span data-ttu-id="b0bbb-112">インフラストラクチャに対する懸念はテストしません。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-112">They do not test infrastructure concerns.</span></span> <span data-ttu-id="b0bbb-113">インフラストラクチャに対する懸念とは、データベース、ファイル システム、ネットワーク リソースなどとのやりとりです。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-113">Infrastructure concerns include interacting with databases, file systems, and network resources.</span></span>

<span data-ttu-id="b0bbb-114">単体テストの作成の詳細については、[テスト ツール](#testing-tools)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-114">For more information on creating unit tests, see [Testing tools](#testing-tools).</span></span>

### <a name="integration-tests"></a><span data-ttu-id="b0bbb-115">統合テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-115">Integration tests</span></span>

<span data-ttu-id="b0bbb-116">"*統合テスト*" とは、2 つ以上のソフトウェア コンポーネントの連携機能、つまりそれらの "統合" を動かすという点で単体テストとは異なります。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-116">An *integration test* differs from a unit test in that it exercises two or more software components' ability to function together, also known as their "integration."</span></span> <span data-ttu-id="b0bbb-117">単体テストでは個々のコンポーネントに着目するのに対し、これらのテストでは、テスト対象のシステムの広範な部分を動作させます。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-117">These tests operate on a broader spectrum of the system under test, whereas unit tests focus on individual components.</span></span> <span data-ttu-id="b0bbb-118">多くの場合、統合テストにはインフラストラクチャに対する懸念も含まれます。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-118">Often, integration tests do include infrastructure concerns.</span></span>

### <a name="load-tests"></a><span data-ttu-id="b0bbb-119">ロード テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-119">Load tests</span></span>

<span data-ttu-id="b0bbb-120">"*ロード テスト*" では、アプリケーションを使用する同時ユーザー数や、やりとりに対するアプリの即時応答性など、システムが指定の負荷を処理できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-120">A *load test* aims to determine whether or not a system can handle a specified load, for example, the number of concurrent users using an application and the app's ability to handle interactions responsively.</span></span> <span data-ttu-id="b0bbb-121">Web アプリケーションのロード テストの詳細については、「[ASP.NET Core のロード テスト/ストレス テスト](/aspnet/core/test/load-tests)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-121">For more information on load testing of web applications, see [ASP.NET Core load/stress testing](/aspnet/core/test/load-tests).</span></span>

## <a name="test-considerations"></a><span data-ttu-id="b0bbb-122">テストに関する留意点</span><span class="sxs-lookup"><span data-stu-id="b0bbb-122">Test considerations</span></span>

<span data-ttu-id="b0bbb-123">テストの記述には、[ベスト プラクティス](unit-testing-best-practices.md)があります。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-123">Keep in mind there are [best practices](unit-testing-best-practices.md) for writing tests.</span></span> <span data-ttu-id="b0bbb-124">たとえば、[テスト駆動開発 (TDD)](https://deviq.com/test-driven-development) では、単体テストを記述してからチェック対象のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-124">For example, [Test Driven Development (TDD)](https://deviq.com/test-driven-development) is when a unit test is written before the code it's meant to check.</span></span> <span data-ttu-id="b0bbb-125">TDD は、本を書く前にアウトラインを作成するのと似ています。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-125">TDD is like creating an outline for a book before you write it.</span></span> <span data-ttu-id="b0bbb-126">開発者が簡潔で読みやすく、効率的なコードを記述できるように支援します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-126">It is meant to help developers write simpler, more readable, and efficient code.</span></span>

## <a name="testing-tools"></a><span data-ttu-id="b0bbb-127">テスト ツール</span><span class="sxs-lookup"><span data-stu-id="b0bbb-127">Testing tools</span></span>

<span data-ttu-id="b0bbb-128">.NET は、複数の言語を使用できる開発プラットフォームであり、[C#](../../csharp/index.yml)、[F#](../../fsharp/index.yml)、[Visual Basic](../../visual-basic/index.yml) 向けのさまざまな種類のテストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-128">.NET is a multi-language development platform, and you can write various test types for [C#](../../csharp/index.yml), [F#](../../fsharp/index.yml), and [Visual Basic](../../visual-basic/index.yml).</span></span> <span data-ttu-id="b0bbb-129">これら各言語に、いくつかのテスト フレームワークを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-129">For each of these languages, you can choose between several test frameworks.</span></span>

### <a name="xunit"></a><span data-ttu-id="b0bbb-130">xUnit</span><span class="sxs-lookup"><span data-stu-id="b0bbb-130">xUnit</span></span>

<span data-ttu-id="b0bbb-131">[xUnit](https://xunit.net) は、.NET 用の無料のオープン ソースのコミュニティ向け単体テスト ツールです。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-131">[xUnit](https://xunit.net) is a free, open source, community-focused unit testing tool for .NET.</span></span> <span data-ttu-id="b0bbb-132">xUnit.net は、NUnit v2 の最初の発明者によって記述された、.NET アプリを単体テストする最新のテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-132">Written by the original inventor of NUnit v2, xUnit.net is the latest technology for unit testing .NET apps.</span></span> <span data-ttu-id="b0bbb-133">xUnit.net は、ReSharper、CodeRush、TestDriven.NET および [Xamarin](https://dotnet.microsoft.com/apps/xamarin) と共に動作します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-133">xUnit.net works with ReSharper, CodeRush, TestDriven.NET, and [Xamarin](https://dotnet.microsoft.com/apps/xamarin).</span></span> <span data-ttu-id="b0bbb-134">これは、[.NET Foundation](https://dotnetfoundation.org) のプロジェクトであり、その行動規範の下で動作します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-134">It is a project of the [.NET Foundation](https://dotnetfoundation.org) and operates under their code of conduct.</span></span>

<span data-ttu-id="b0bbb-135">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-135">For more information, see the following resources:</span></span>

- [<span data-ttu-id="b0bbb-136">C# を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-136">Unit testing with C#</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="b0bbb-137">F# を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-137">Unit testing with F#</span></span>](unit-testing-fsharp-with-dotnet-test.md)
- [<span data-ttu-id="b0bbb-138">Visual Basic を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-138">Unit testing with Visual Basic</span></span>](unit-testing-visual-basic-with-dotnet-test.md)

### <a name="nunit"></a><span data-ttu-id="b0bbb-139">NUnit</span><span class="sxs-lookup"><span data-stu-id="b0bbb-139">NUnit</span></span>

<span data-ttu-id="b0bbb-140">[NUnit](https://nunit.org) は、.NET の全言語で使用できる単体テスト フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-140">[NUnit](https://nunit.org) is a unit-testing framework for all .NET languages.</span></span> <span data-ttu-id="b0bbb-141">最初に JUnit から移植された現在の運用リリースは、さまざまな .NET プラットフォーム向けの多数の新機能とサポートで書き換えられています。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-141">Initially ported from JUnit, the current production release has been rewritten with many new features and support for a wide range of .NET platforms.</span></span> <span data-ttu-id="b0bbb-142">これは、[.NET Foundation](https://dotnetfoundation.org) のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-142">It is a project of the [.NET Foundation](https://dotnetfoundation.org).</span></span>

<span data-ttu-id="b0bbb-143">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-143">For more information, see the following resources:</span></span>

- [<span data-ttu-id="b0bbb-144">C# を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-144">Unit testing with C#</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="b0bbb-145">F# を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-145">Unit testing with F#</span></span>](unit-testing-fsharp-with-nunit.md)
- [<span data-ttu-id="b0bbb-146">Visual Basic を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-146">Unit testing with Visual Basic</span></span>](unit-testing-visual-basic-with-nunit.md)

### <a name="mstest"></a><span data-ttu-id="b0bbb-147">MSTest</span><span class="sxs-lookup"><span data-stu-id="b0bbb-147">MSTest</span></span>

<span data-ttu-id="b0bbb-148">[MSTest](https://github.com/Microsoft/testfx-docs) は、.NET の全言語で使用できる Microsoft のテスト フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-148">[MSTest](https://github.com/Microsoft/testfx-docs) is the Microsoft test framework for all .NET languages.</span></span> <span data-ttu-id="b0bbb-149">これは拡張可能で、.NET CLI でも Visual Studio でも動作します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-149">It's extensible and works with both .NET CLI and Visual Studio.</span></span> <span data-ttu-id="b0bbb-150">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-150">For more information, see the following resources:</span></span>

- [<span data-ttu-id="b0bbb-151">C# を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-151">Unit testing with C#</span></span>](unit-testing-with-mstest.md)
- [<span data-ttu-id="b0bbb-152">F# を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-152">Unit testing with F#</span></span>](unit-testing-fsharp-with-mstest.md)
- [<span data-ttu-id="b0bbb-153">Visual Basic を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-153">Unit testing with Visual Basic</span></span>](unit-testing-visual-basic-with-mstest.md)

### <a name="net-cli"></a><span data-ttu-id="b0bbb-154">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b0bbb-154">.NET CLI</span></span>

<span data-ttu-id="b0bbb-155">[.NET CLI](../tools/index.md) からソリューションの単体テストを実行するには、[dotnet test](../tools/dotnet-test.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-155">You can run a solutions unit tests from the [.NET CLI](../tools/index.md), with the [dotnet test](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="b0bbb-156">.NET CLI では、[統合開発環境 (IDE)](#ide) からユーザー インターフェイスで使用できる機能の大部分が公開されています。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-156">The .NET CLI exposes a majority of the functionality that [Integrated Development Environments (IDEs)](#ide) make available through user interfaces.</span></span> <span data-ttu-id="b0bbb-157">.NET CLI はクロスプラットフォームであり、継続的インテグレーションおよび配信パイプラインの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-157">The .NET CLI is cross-platform and available to use as part of continuous integration and delivery pipelines.</span></span> <span data-ttu-id="b0bbb-158">.NET CLI は、一般的なタスクを自動化するスクリプト化されたプロセスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-158">The .NET CLI is used with scripted processes to automate common tasks.</span></span>

### <a name="ide"></a><span data-ttu-id="b0bbb-159">IDE</span><span class="sxs-lookup"><span data-stu-id="b0bbb-159">IDE</span></span>

<span data-ttu-id="b0bbb-160">Visual Studio、Visual Studio for Mac、Visual Studio Code のどれを使用していても、機能のテストには、グラフィカル ユーザー インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-160">Whether you're using Visual Studio, Visual Studio for Mac, or Visual Studio Code, there are graphical user interfaces for testing functionality.</span></span> <span data-ttu-id="b0bbb-161">IDE には CLI よりも、[Live Unit Testing](/visualstudio/test/live-unit-testing) など多くの機能があります。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-161">There are more features available to IDEs than the CLI, for example [Live Unit Testing](/visualstudio/test/live-unit-testing).</span></span> <span data-ttu-id="b0bbb-162">詳細については、[Visual Studio でのテストの追加と除外](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-162">For more information, see [Including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0bbb-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0bbb-163">See also</span></span>

<span data-ttu-id="b0bbb-164">詳細については、以下の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0bbb-164">For more information, see the following articles:</span></span>

- [<span data-ttu-id="b0bbb-165">.NET での単体テストのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="b0bbb-165">Unit testing best practices with .NET</span></span>](unit-testing-best-practices.md)
- [<span data-ttu-id="b0bbb-166">ASP.NET Core での統合テスト</span><span class="sxs-lookup"><span data-stu-id="b0bbb-166">Integration tests in ASP.NET Core</span></span>](/aspnet/core/test/integration-tests#test-app-prerequisites)
- [<span data-ttu-id="b0bbb-167">選択的単体テストの実行</span><span class="sxs-lookup"><span data-stu-id="b0bbb-167">Running selective unit tests</span></span>](selective-unit-tests.md)
- [<span data-ttu-id="b0bbb-168">単体テストにコードカバレッジを使用する</span><span class="sxs-lookup"><span data-stu-id="b0bbb-168">Use code coverage for unit testing</span></span>](unit-testing-code-coverage.md)
