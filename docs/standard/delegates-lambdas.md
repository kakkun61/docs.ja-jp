---
title: デリゲートとラムダ
description: 特定のメソッド シグネチャを指定する型をデリゲートで定義する方法について説明します。このようなメソッドは、直接呼び出すか、別のメソッドに渡して呼び出すことができます。
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 9be4fcdc29eac433dc7416578acbc664ac2e431c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821685"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="96154-103">デリゲートとラムダ</span><span class="sxs-lookup"><span data-stu-id="96154-103">Delegates and lambdas</span></span>

<span data-ttu-id="96154-104">デリゲートは、特定のメソッド シグネチャを指定する型を定義します。</span><span class="sxs-lookup"><span data-stu-id="96154-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="96154-105">このシグネチャを満たすメソッド (静的またはインスタンス) は、その型の変数に代入し、(適切な引数を使用して) 直接呼び出したり、別のメソッドに引数そのものとして渡してから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="96154-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="96154-106">次の例は、デリゲートの使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="96154-106">The following example demonstrates delegate use.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* <span data-ttu-id="96154-107">`public delegate string Reverse(string s);` の行で特定のシグネチャのデリゲート型が作成されています。この場合、文字列パラメーターを取ってから文字列パラメーターを返すメソッドです。</span><span class="sxs-lookup"><span data-stu-id="96154-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="96154-108">`static string ReverseString(string s)` メソッド (定義済みのデリゲート型とまったく同じシグネチャを持つ) では、デリゲートが実装されます。</span><span class="sxs-lookup"><span data-stu-id="96154-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="96154-109">`Reverse rev = ReverseString;` 行では、対応するデリゲート型の変数にメソッドを割り当てることができることを示しています。</span><span class="sxs-lookup"><span data-stu-id="96154-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="96154-110">`Console.WriteLine(rev("a string"));` 行では、デリゲート型の変数を使用してデリゲートを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="96154-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="96154-111">開発プロセスを効率化するため、.NET にはプログラマが再利用できるデリゲート型のセットが含まれているため、新しい型を作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="96154-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="96154-112">これらの型は `Func<>`、`Action<>` および `Predicate<>` であり、新しいデリゲート型を定義しなくても使用できます。</span><span class="sxs-lookup"><span data-stu-id="96154-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="96154-113">使用を意図した方法で実行する必要がある 3 つの型には、いくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="96154-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="96154-114">`Action<>` は、デリゲートの引数を使用してアクションを実行する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="96154-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="96154-115">カプセル化されるメソッドは、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="96154-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="96154-116">`Func<>` は、通常、変換が手元にあるときに使用されます。つまり、デリゲートの引数を異なる結果に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96154-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="96154-117">予測が良い例です。</span><span class="sxs-lookup"><span data-stu-id="96154-117">Projections are a good example.</span></span> <span data-ttu-id="96154-118">カプセル化されるメソッドは、指定された値を返します。</span><span class="sxs-lookup"><span data-stu-id="96154-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="96154-119">`Predicate<>` は、引数がデリゲートの条件を満たすかどうかを判断する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="96154-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="96154-120">また、`Func<T, bool>` として書き込むこともできます。これは、メソッドがブール値を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="96154-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="96154-121">ここで、上記の例を使用して、カスタム型の代わりに `Func<>` デリゲートを使用して書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="96154-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="96154-122">プログラムは引き続きまったく同じに実行されます。</span><span class="sxs-lookup"><span data-stu-id="96154-122">The program will continue running exactly the same.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

<span data-ttu-id="96154-123">このシンプルな例では、`Main` メソッドの外部にメソッドを定義することは、少し余分なようです。</span><span class="sxs-lookup"><span data-stu-id="96154-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="96154-124">.NET Framework 2.0 では、*匿名デリゲート* の概念が導入されました。これにより、追加の型やメソッドを指定しなくても "インライン" デリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="96154-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="96154-125">次の例では、匿名デリゲートによってリストが偶数だけにフィルター処理され、コンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="96154-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="96154-126">ご覧のように、デリゲートの本体は、他のデリゲートと同じく、単なる式のセットです。</span><span class="sxs-lookup"><span data-stu-id="96154-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="96154-127">しかし、それを別の定義にする代わりに、<xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> メソッドへの呼び出しでそれを _アド ホック_ で導入しました。</span><span class="sxs-lookup"><span data-stu-id="96154-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="96154-128">ただし、この方法でも、破棄できる多くのコードがまだ残ります。</span><span class="sxs-lookup"><span data-stu-id="96154-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="96154-129">このような場合に *ラムダ式* が機能します。</span><span class="sxs-lookup"><span data-stu-id="96154-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="96154-130">ラムダ式 (または略して単に "ラムダ") は、C# 3.0 で統合言語クエリ (LINQ) のコア ビルディング ブロックの 1 つとして導入されました。</span><span class="sxs-lookup"><span data-stu-id="96154-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="96154-131">これらは、デリゲートの使用の利便性を高める構文です。</span><span class="sxs-lookup"><span data-stu-id="96154-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="96154-132">これらは、シグネチャとメソッド本体を宣言しますが、デリゲートに割り当てられない限り、独自の正式な ID を持ちません。</span><span class="sxs-lookup"><span data-stu-id="96154-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="96154-133">デリゲートの場合とは異なり、これらをイベント登録の右側として、またはさまざまな LINQ 句およびメソッド内に、直接割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="96154-133">Unlike delegates, they can be directly assigned as the right-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="96154-134">ラムダ式はデリゲートを指定するもう 1 つの方法であるため、上記のサンプルを匿名デリゲートの代わりにラムダ式を使用するように書き換えることができるようになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="96154-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="96154-135">上の例で、使用されているラムダ式は `i => i % 2 == 0` です。</span><span class="sxs-lookup"><span data-stu-id="96154-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="96154-136">これも、デリゲートの使用の利便性を高める構文にすぎません。</span><span class="sxs-lookup"><span data-stu-id="96154-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="96154-137">内部で行われる処理は、匿名デリゲートの場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="96154-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="96154-138">ここでも、ラムダは単なるデリゲートです。つまり、次のコード スニペットに示すように、ラムダは問題なくイベント ハンドラーとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="96154-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

<span data-ttu-id="96154-139">このコンテキストでの `+=` 演算子は、[イベント](../csharp/language-reference/keywords/event.md)をサブスクライブするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="96154-139">The `+=` operator in this context is used to subscribe to an [event](../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="96154-140">詳細については、「[イベントのサブスクリプションとサブスクリプション解除を行う方法](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96154-140">For more information, see [How to subscribe to and unsubscribe from events](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="96154-141">参考資料とリソース</span><span class="sxs-lookup"><span data-stu-id="96154-141">Further reading and resources</span></span>

* [<span data-ttu-id="96154-142">デリゲート</span><span class="sxs-lookup"><span data-stu-id="96154-142">Delegates</span></span>](../csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="96154-143">匿名関数</span><span class="sxs-lookup"><span data-stu-id="96154-143">Anonymous Functions</span></span>](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="96154-144">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="96154-144">Lambda expressions</span></span>](../csharp/language-reference/operators/lambda-expressions.md)
