---
title: クラスおよびオブジェクト - C# チュートリアルの概要
description: 初めての C# プログラムを作成し、オブジェクト指向の概念を確認します
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 0955b0ac33b346b9880c8af70bd73cb458120f35
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434898"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="116db-103">クラスおよびオブジェクトを使用したオブジェクト指向プログラミングについて確認します</span><span class="sxs-lookup"><span data-stu-id="116db-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="116db-104">このチュートリアルでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="116db-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="116db-105">Windows、Linux、または macOS 上でローカルの開発環境を設定する手順については、.NET チュートリアル [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) (10 分で Hello World) に記載されています。</span><span class="sxs-lookup"><span data-stu-id="116db-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="116db-106">使用するコマンドの概要については、詳細な情報へのリンクが掲載されている、[開発ツールに対する理解を深める](local-environment.md)方法に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="116db-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="116db-107">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="116db-107">Create your application</span></span>

<span data-ttu-id="116db-108">ターミナル ウィンドウで、「 *classes* 」という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="116db-108">Using a terminal window, create a directory named *classes* .</span></span> <span data-ttu-id="116db-109">ここにアプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="116db-109">You'll build your application there.</span></span> <span data-ttu-id="116db-110">このディレクトリに移動し、コンソール ウィンドウで「`dotnet new console`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="116db-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="116db-111">このコマンドにより、アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="116db-111">This command creates your application.</span></span> <span data-ttu-id="116db-112">*Program.cs* を開きます。</span><span class="sxs-lookup"><span data-stu-id="116db-112">Open *Program.cs* .</span></span> <span data-ttu-id="116db-113">内容は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="116db-113">It should look like this:</span></span>

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="116db-114">このチュートリアルでは、銀行口座を表す新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="116db-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="116db-115">通常、開発者は各クラスを別々のテキスト ファイルで定義します。</span><span class="sxs-lookup"><span data-stu-id="116db-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="116db-116">この方法なら、プログラムのサイズが大きくなっても管理が容易です。</span><span class="sxs-lookup"><span data-stu-id="116db-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="116db-117">*classes* ディレクトリに「 *BankAccount.cs* 」という名前の新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="116db-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="116db-118">このファイルには、" **銀行口座** " の定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="116db-118">This file will contain the definition of a \* **bank account** _.</span></span> <span data-ttu-id="116db-119">オブジェクト指向プログラミングにより、" _\*_クラス_\*_ " の形式で型が作成され、コードが整理されます。</span><span class="sxs-lookup"><span data-stu-id="116db-119">Object Oriented programming organizes code by creating types in the form of _*_classes_*_ .</span></span> <span data-ttu-id="116db-120">これらのクラスには、特定のエンティティを表すコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="116db-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="116db-121">`BankAccount` クラスは銀行口座を表します。</span><span class="sxs-lookup"><span data-stu-id="116db-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="116db-122">コードでは、メソッドとプロパティを使用した特定の操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="116db-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="116db-123">このチュートリアルでは、銀行口座は次の動作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="116db-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="116db-124">銀行口座を一意に特定する 10 桁の数字をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="116db-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="116db-125">口座の名前、または所有者の名前を格納する文字列をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="116db-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="116db-126">残高を取得できます。</span><span class="sxs-lookup"><span data-stu-id="116db-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="116db-127">預金を許可します。</span><span class="sxs-lookup"><span data-stu-id="116db-127">It accepts deposits.</span></span>
1. <span data-ttu-id="116db-128">引き出しを許可します。</span><span class="sxs-lookup"><span data-stu-id="116db-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="116db-129">初期残高は正の値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="116db-130">引き出しによって残高が負の値になることはありません。</span><span class="sxs-lookup"><span data-stu-id="116db-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="116db-131">銀行口座の型を定義する</span><span class="sxs-lookup"><span data-stu-id="116db-131">Define the bank account type</span></span>

<span data-ttu-id="116db-132">動作を定義するクラスの基本を作成することから開始できます。</span><span class="sxs-lookup"><span data-stu-id="116db-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="116db-133">*File:New* コマンドを使用して、新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="116db-133">Create a new file using the _ *File:New* \* command.</span></span> <span data-ttu-id="116db-134">*BankAccount.cs* という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="116db-134">Name it *BankAccount.cs* .</span></span> <span data-ttu-id="116db-135">*BankAccount.cs* ファイルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-135">Add the following code to your *BankAccount.cs* file:</span></span>

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

<span data-ttu-id="116db-136">先に進む前に、構築したものを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="116db-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="116db-137">`namespace` 宣言は、コードを論理的に整理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="116db-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="116db-138">このチュートリアルで取り扱うコードは比較的小さいため、1 つの名前空間にすべてのコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="116db-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="116db-139">`public class BankAccount` は、これから作成するクラスまたは型を定義します。</span><span class="sxs-lookup"><span data-stu-id="116db-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="116db-140">クラス宣言のあとにある `{` と `}` の内側はすべて、クラスの状態と動作を定義しています。</span><span class="sxs-lookup"><span data-stu-id="116db-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="116db-141">`BankAccount` クラスには、5 つの " **メンバー** " があります。</span><span class="sxs-lookup"><span data-stu-id="116db-141">There are five \* **members** _ of the `BankAccount` class.</span></span> <span data-ttu-id="116db-142">最初の 3 つは " _\*_プロパティ_\*_ " です。</span><span class="sxs-lookup"><span data-stu-id="116db-142">The first three are _*_properties_*_ .</span></span> <span data-ttu-id="116db-143">プロパティはデータ要素であり、検証やその他の規則を適用するコードを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="116db-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="116db-144">最後の 2 つは " _\*_メソッド_\*_ " です。</span><span class="sxs-lookup"><span data-stu-id="116db-144">The last two are _*_methods_*_ .</span></span> <span data-ttu-id="116db-145">メソッドは 1 つの機能を実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="116db-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="116db-146">各メンバーの名前を確認すると、開発者がそのクラスの作用を把握するための十分な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="116db-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="116db-147">新しいアカウントを開く</span><span class="sxs-lookup"><span data-stu-id="116db-147">Open a new account</span></span>

<span data-ttu-id="116db-148">実装する最初の機能は、銀行口座を開く機能です。</span><span class="sxs-lookup"><span data-stu-id="116db-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="116db-149">顧客が口座を開く場合、初期残高や口座の (1 名または複数名の) 所有者の情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="116db-150">`BankAccount` 型の新しいオブジェクトを作成することは、これらの値を割り当てる " _\*_コンストラクター_\*_ " を定義することを意味します。</span><span class="sxs-lookup"><span data-stu-id="116db-150">Creating a new object of the `BankAccount` type means defining a _*_constructor_*_ that assigns those values.</span></span> <span data-ttu-id="116db-151">" _\*_コンストラクター_\*_ " はクラスと同じ名前のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="116db-151">A _*_constructor_*_ is a member that has the same name as the class.</span></span> <span data-ttu-id="116db-152">これは、そのクラス型のオブジェクトを初期化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="116db-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="116db-153">`BankAccount` 型に次のコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="116db-154">`MakeDeposit` クラス宣言の上に次のコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="116db-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="116db-155">[`new`](../../language-reference/operators/new-operator.md) を使用してオブジェクトを作成すると、コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="116db-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="116db-156">"Program.cs" の `Console.WriteLine("Hello World!");` の行を次のコードに置き換えます (`<name>` は自分の名前に置き換えます)。</span><span class="sxs-lookup"><span data-stu-id="116db-156">Replace the line `Console.WriteLine("Hello World!");` in _Program.cs\* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="116db-157">これまでに構築したものを実行してみましょう。</span><span class="sxs-lookup"><span data-stu-id="116db-157">Let's run what you've built so far.</span></span> <span data-ttu-id="116db-158">Visual Studio を使用している場合は、 **[実行]** メニューから **[デバッグなしで開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="116db-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="116db-159">コマンド ラインを使用している場合は、プロジェクトを作成したディレクトリで `dotnet run` を入力します。</span><span class="sxs-lookup"><span data-stu-id="116db-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="116db-160">口座番号が空であることに気付かれましたか?</span><span class="sxs-lookup"><span data-stu-id="116db-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="116db-161">次にこの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="116db-161">It's time to fix that.</span></span> <span data-ttu-id="116db-162">口座番号はオブジェクトが作成されるときに割り当てられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="116db-163">しかし、それを作成する責任を呼び出し元に負わせるべきではありません。</span><span class="sxs-lookup"><span data-stu-id="116db-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="116db-164">`BankAccount` クラスのコードは、新しい口座番号の割り当て方を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="116db-165">そのための簡単な方法は、10 桁の数字で始めることです。</span><span class="sxs-lookup"><span data-stu-id="116db-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="116db-166">そして、新しい口座番号が作成されるごとに値を 1 増加します。</span><span class="sxs-lookup"><span data-stu-id="116db-166">Increment it when each new account is created.</span></span> <span data-ttu-id="116db-167">最後に、オブジェクトが作成されるときに現在の口座番号を格納します。</span><span class="sxs-lookup"><span data-stu-id="116db-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="116db-168">`BankAccount`クラスにメンバーの宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="116db-169">`BankAccount` クラスの先頭の左中かっこ `{` の後に、次のコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="116db-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="116db-170">これがデータ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="116db-170">This is a data member.</span></span> <span data-ttu-id="116db-171">これは `private` であり、`BankAccount` クラス内のコードのみがこれにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="116db-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="116db-172">この方法により、プライベートな実装 (口座番号の生成方法) から (口座番号を持つなどの) パブリックな責任を分離できます。</span><span class="sxs-lookup"><span data-stu-id="116db-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="116db-173">`static` でもあるため、すべての `BankAccount` オブジェクトによって共有されます。</span><span class="sxs-lookup"><span data-stu-id="116db-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="116db-174">静的でない変数の値は `BankAccount` オブジェクトのインスタンスごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="116db-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="116db-175">次の 2 行をコンストラクターに追加して、口座番号を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="116db-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="116db-176">それらは `this.Balance = initialBalance` という行の後に配置します。</span><span class="sxs-lookup"><span data-stu-id="116db-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="116db-177">「`dotnet run`」と入力して結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="116db-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="116db-178">預金と引き出しを作成する</span><span class="sxs-lookup"><span data-stu-id="116db-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="116db-179">銀行口座クラスは、預金と引き出しを許可して正しく動作するようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="116db-180">口座のすべてのトランザクションを記録する履歴を作成して、預金と引き出しを実装しましょう。</span><span class="sxs-lookup"><span data-stu-id="116db-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="116db-181">これには、単純にトランザクションごとに残高を更新する方法に比べていくつかのメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="116db-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="116db-182">履歴は、すべてのトランザクションを監査して毎日の残高を管理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="116db-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="116db-183">必要に応じてすべてのトランザクションの履歴から残高を計算することにより、1 つのトランザクションの中で修正されたすべてのエラーが正しく残高に反映されて次の計算に使用されます。</span><span class="sxs-lookup"><span data-stu-id="116db-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="116db-184">トランザクションを表す新しい型を作成するところから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="116db-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="116db-185">これは一切の責任を持たない単純型です。</span><span class="sxs-lookup"><span data-stu-id="116db-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="116db-186">いくつかのプロパティが必要になります。</span><span class="sxs-lookup"><span data-stu-id="116db-186">It needs a few properties.</span></span> <span data-ttu-id="116db-187">「 *Transaction.cs* 」という名前の新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="116db-187">Create a new file named *Transaction.cs* .</span></span> <span data-ttu-id="116db-188">これに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="116db-189">`BankAccount` クラスに `Transaction` オブジェクトの <xref:System.Collections.Generic.List%601> を追加しましょう。</span><span class="sxs-lookup"><span data-stu-id="116db-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="116db-190">*BankAccount.cs* ファイルのコンストラクターの後に次の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="116db-191"><xref:System.Collections.Generic.List%601> クラスでは、別の名前空間をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="116db-192">*BankAccount.cs* の最初に次を追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-192">Add the following at the beginning of *BankAccount.cs* :</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="116db-193">それでは、`Balance` を正しく計算しましょう。</span><span class="sxs-lookup"><span data-stu-id="116db-193">Now, let's correctly compute the `Balance`.</span></span> <span data-ttu-id="116db-194">現在の残高は、すべての取引の値を合計することによって確認できます。</span><span class="sxs-lookup"><span data-stu-id="116db-194">The current balance can be found by summing the values of all transactions.</span></span> <span data-ttu-id="116db-195">現在、このコードで取得できるのは口座の初期残高のみであるため、`Balance` プロパティを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-195">As the code is currently, you can only get the initial balance of the account, so you'll have to update the `Balance` property.</span></span> <span data-ttu-id="116db-196">*BankAccount.cs* の `public decimal Balance { get; }` の行を、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="116db-196">Replace the line `public decimal Balance { get; }` in *BankAccount.cs* with the following code:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="116db-197">この例は、" **プロパティ** " の重要な側面を示しています。</span><span class="sxs-lookup"><span data-stu-id="116db-197">This example shows an important aspect of \* **properties** _.</span></span> <span data-ttu-id="116db-198">これで、別のプログラマーが値を要求したときに残高が計算されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="116db-198">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="116db-199">この計算処理は、すべてのトランザクションを列挙して、その合計値を現在の残高として提供します。</span><span class="sxs-lookup"><span data-stu-id="116db-199">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="116db-200">次に `MakeDeposit` メソッドと `MakeWithdrawal` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="116db-200">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="116db-201">これらのメソッドは、初期残高が正の値でなければならず、引き出し後の残高が負の値になってはいけない、という最後の 2 つの規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="116db-201">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="116db-202">これにより、" _\*_例外_\*_ " の概念が導入されます。</span><span class="sxs-lookup"><span data-stu-id="116db-202">This introduces the concept of _*_exceptions_*_ .</span></span> <span data-ttu-id="116db-203">メソッドが作業を正常に完了できないことを示す標準的な方法は、例外をスローすることです。</span><span class="sxs-lookup"><span data-stu-id="116db-203">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="116db-204">例外の型とそれに関連付けられたメッセージがエラーを説明します。</span><span class="sxs-lookup"><span data-stu-id="116db-204">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="116db-205">`MakeDeposit` メソッドは、預金額が負の値になる場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="116db-205">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="116db-206">`MakeWithdrawal` メソッドは、引き出し額が負の値になる場合、または引き出しを適用した結果、残高が負の値になる場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="116db-206">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="116db-207">`allTransactions` リストの宣言の後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-207">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="116db-208">[`throw`](../../language-reference/keywords/throw.md) ステートメントで例外が " *スロー* " されます。</span><span class="sxs-lookup"><span data-stu-id="116db-208">The [`throw`](../../language-reference/keywords/throw.md) statement _ *throws* \* an exception.</span></span> <span data-ttu-id="116db-209">現在のブロックの実行が終了し、コントロールによってコール スタックで最初に一致した `catch` ブロックに転送されます。</span><span class="sxs-lookup"><span data-stu-id="116db-209">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="116db-210">あとで `catch` ブロックを追加してこのコードをテストします。</span><span class="sxs-lookup"><span data-stu-id="116db-210">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="116db-211">残高を直接更新するのではなく、最初のトランザクションを追加するようにするため、コンストラクターを 1 か所変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="116db-211">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="116db-212">既に `MakeDeposit` メソッドは記述したので、このメソッドをコンストラクターから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="116db-212">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="116db-213">完成したコンストラクターは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="116db-213">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="116db-214"><xref:System.DateTime.Now?displayProperty=nameWithType> は、現在の日付と時刻を返すプロパティです。</span><span class="sxs-lookup"><span data-stu-id="116db-214"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="116db-215">新しい `BankAccount` を作成するコードの後で、`Main` メソッドにいくつかの預金と引き出しを追加することで、これをテストします。</span><span class="sxs-lookup"><span data-stu-id="116db-215">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="116db-216">次に、残高が負の値になっている口座を作成してみることで、エラー条件のキャッチをテストします。</span><span class="sxs-lookup"><span data-stu-id="116db-216">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="116db-217">追加したコードの後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-217">Add the following code after the preceding code you just added:</span></span>

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="116db-218">[`try` と `catch` のステートメント](../../language-reference/keywords/try-catch.md)を使用して、例外をスローする可能性のあるコード ブロックをマークし、想定したエラーをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="116db-218">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="116db-219">同じ方法で、残高が負の値になっている場合に例外をスローするコードをテストします。</span><span class="sxs-lookup"><span data-stu-id="116db-219">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="116db-220">`Main` メソッドの末尾に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-220">Add the following code at the end of your `Main` method:</span></span>

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="116db-221">ファイルを保存し、「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="116db-221">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="116db-222">課題 - すべてのトランザクションをログに記録する</span><span class="sxs-lookup"><span data-stu-id="116db-222">Challenge - log all transactions</span></span>

<span data-ttu-id="116db-223">このチュートリアルを完了すると、トランザクション履歴の `string` を作成する `GetAccountHistory` メソッドを記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="116db-223">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="116db-224">このメソッドを `BankAccount` 型に追加します。</span><span class="sxs-lookup"><span data-stu-id="116db-224">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="116db-225">これは、<xref:System.Text.StringBuilder> クラスを使用して、各トランザクションを 1 行で表す文を含んだ文字列をフォーマットします。</span><span class="sxs-lookup"><span data-stu-id="116db-225">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="116db-226">文字列をフォーマットするコードについては、このチュートリアルで先述しました。</span><span class="sxs-lookup"><span data-stu-id="116db-226">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="116db-227">新しい文字の 1 つは `\t` です。</span><span class="sxs-lookup"><span data-stu-id="116db-227">One new character is `\t`.</span></span> <span data-ttu-id="116db-228">これはタブを挿入して出力をフォーマットします。</span><span class="sxs-lookup"><span data-stu-id="116db-228">That inserts a tab to format the output.</span></span>

<span data-ttu-id="116db-229">次の行を追加して、 *Program.cs* でテストします。</span><span class="sxs-lookup"><span data-stu-id="116db-229">Add this line to test it in *Program.cs* :</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="116db-230">プログラムを実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="116db-230">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="116db-231">次の手順</span><span class="sxs-lookup"><span data-stu-id="116db-231">Next steps</span></span>

<span data-ttu-id="116db-232">うまくいかない場合は、このチュートリアルのソースを [GitHub リポジトリ](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="116db-232">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="116db-233">[オブジェクト指向プログラミング](object-oriented-programming.md)のチュートリアルに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="116db-233">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="116db-234">次の記事でこれらの概念の詳細を学習できます。</span><span class="sxs-lookup"><span data-stu-id="116db-234">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="116db-235">if と else ステートメント</span><span class="sxs-lookup"><span data-stu-id="116db-235">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="116db-236">while ステートメント</span><span class="sxs-lookup"><span data-stu-id="116db-236">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="116db-237">do ステートメント</span><span class="sxs-lookup"><span data-stu-id="116db-237">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="116db-238">for ステートメント</span><span class="sxs-lookup"><span data-stu-id="116db-238">For statement</span></span>](../../language-reference/keywords/for.md)
