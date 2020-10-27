---
title: .NET for Apache Spark でブロードキャスト変数を使用する
description: .NET for Apache Spark アプリケーションでブロードキャスト変数を使用する方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 55a52754439020bd2a925aa3e987fb4ad99c9c3d
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223996"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a><span data-ttu-id="978c4-103">.NET for Apache Spark でブロードキャスト変数を使用する</span><span class="sxs-lookup"><span data-stu-id="978c4-103">Use broadcast variables in .NET for Apache Spark</span></span>

<span data-ttu-id="978c4-104">この記事では、.NET for Apache Spark でブロードキャスト変数を使用する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="978c4-104">In this article, you learn how to use broadcast variables in .NET for Apache Spark.</span></span> <span data-ttu-id="978c4-105">[Apache Spark のブロードキャスト変数](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables)は、読み取り専用であることを意図した、Executor で変数を共有するためのメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="978c4-105">[Broadcast variables in Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) are mechanisms for sharing variables across executors that are meant to be read-only.</span></span> <span data-ttu-id="978c4-106">ブロードキャスト変数を使用すると、読み取り専用の変数をコピーしたものをタスクと共に送るのではなく、各マシンにキャッシュしたままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="978c4-106">Broadcast variables allow you to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.</span></span> <span data-ttu-id="978c4-107">ブロードキャスト変数を使用すると、すべてのノードに大きな入力データセットのコピーを効率的な方法で渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="978c4-107">You can use broadcast variables to give every node a copy of a large input dataset in an efficient manner.</span></span>

<span data-ttu-id="978c4-108">データは 1 回しか送信されないため、タスクごとに Executor に送られるローカル変数と比較した場合、ブロードキャスト変数の方がパフォーマンスが優れています。</span><span class="sxs-lookup"><span data-stu-id="978c4-108">Because the data is sent only once, broadcast variables have performance benefits when compared to local variables that are shipped to the executors with each task.</span></span> <span data-ttu-id="978c4-109">ブロードキャスト変数とそれらが使用される理由について理解を深めるには、[ブロードキャスト変数の公式ドキュメント](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="978c4-109">Refer to the [official broadcast variable documentation](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) to get a deeper understanding of broadcast variables and why they are used.</span></span>

## <a name="create-broadcast-variables"></a><span data-ttu-id="978c4-110">ブロードキャスト変数を作成する</span><span class="sxs-lookup"><span data-stu-id="978c4-110">Create broadcast variables</span></span>

<span data-ttu-id="978c4-111">ブロードキャスト変数を作成するには、任意の変数 `v` に対して `SparkContext.Broadcast(v)` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="978c4-111">To create a broadcast variable, call `SparkContext.Broadcast(v)` for any variable `v`.</span></span> <span data-ttu-id="978c4-112">ブロードキャスト変数は、変数 `v` のラッパーであり、`Value()` メソッドを呼び出すとその値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="978c4-112">The broadcast variable is a wrapper around the variable `v`, and its value can be accessed by calling the `Value()` method.</span></span>

<span data-ttu-id="978c4-113">次のコード スニペットでは文字列変数 `v` が作成され、`SparkContext.Broadcast(v)` が呼び出されたときに、ブロードキャスト変数 `bv` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="978c4-113">In the following code snippet, a string variable `v` is created, and a broadcast variable `bv` is created when `SparkContext.Broadcast(v)`is called.</span></span> <span data-ttu-id="978c4-114">`Broadcast` の型パラメーター string が、ブロードキャストされている変数の型と一致していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="978c4-114">Notice the type parameter for `Broadcast`, string, matches the type of the variable being broadcasted.</span></span> <span data-ttu-id="978c4-115">ユーザー定義関数 (UDF) により、`bv` の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="978c4-115">The user-defined function (UDF) returns the value of `bv`.</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a><span data-ttu-id="978c4-116">ブロードキャスト変数を削除する</span><span class="sxs-lookup"><span data-stu-id="978c4-116">Delete broadcast variables</span></span>

<span data-ttu-id="978c4-117">ブロードキャスト変数は、`Destroy()` メソッドを呼び出すと、すべての Executor から削除することができます。</span><span class="sxs-lookup"><span data-stu-id="978c4-117">The broadcast variable can be deleted from all executors by calling the `Destroy()` method.</span></span>

```csharp
bv.Destroy();
```

<span data-ttu-id="978c4-118">`Destroy()` によって、ブロードキャスト変数に関連するすべてのデータとメタデータが削除されるため、注意して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="978c4-118">`Destroy()` deletes all data and metadata related to the broadcast variable and should be used with caution.</span></span> <span data-ttu-id="978c4-119">ブロードキャスト変数が一度破棄されると、再度使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="978c4-119">Once a broadcast variable is destroyed, it can't be used again.</span></span>

## <a name="limit-broadcast-variable-scope-in-udfs"></a><span data-ttu-id="978c4-120">UDF のブロードキャスト変数のスコープを制限する</span><span class="sxs-lookup"><span data-stu-id="978c4-120">Limit broadcast variable scope in UDFs</span></span>

<span data-ttu-id="978c4-121">UDF でブロードキャスト変数を使用する場合は、変数を参照している UDF のみに変数のスコープを制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="978c4-121">When you use broadcast variables in UDFs, you need to limit the scope of the variable to only the UDF that is referencing the variable.</span></span> <span data-ttu-id="978c4-122">この事象については、[UDF の使用に関するガイド](udf-guide.md)で詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="978c4-122">The [guide to using UDFs](udf-guide.md) describes this phenomenon in detail.</span></span> <span data-ttu-id="978c4-123">スコープは、ブロードキャスト変数に対して `Destroy()` を呼び出すときに特に重要です。</span><span class="sxs-lookup"><span data-stu-id="978c4-123">Scope is especially crucial when you call `Destroy()` on the broadcast variable.</span></span>

<span data-ttu-id="978c4-124">破棄されたブロードキャスト変数が他の UDF から参照できる場合、またはアクセスできる場合は、それが参照されていない場合でも、そのすべての UDF がシリアル化の対象として選択されます。</span><span class="sxs-lookup"><span data-stu-id="978c4-124">If the broadcast variable that has been destroyed is visible to or accessible from other UDFs, it gets picked up for serialization by all of the UDFs, even if it is not being referenced by them.</span></span> <span data-ttu-id="978c4-125">.NET for Apache Spark では、破棄されたブロードキャスト変数をシリアル化できないため、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="978c4-125">.NET for Apache Spark is unable to serialize the destroyed broadcast variable, which results in an error.</span></span> <span data-ttu-id="978c4-126">次のコード スニペットは、このエラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="978c4-126">The following code snippet demonstrates this error:</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

// Using the broadcast variable in a UDF:
Func<Column, Column> udf1 = Udf<string, string>(
    str => $"{str}: {bv.Value()}");

// Destroying bv
bv.Destroy();

// Calling udf1 after destroying bv throws the following expected exception:
// org.apache.spark.SparkException: Attempted to use Broadcast(0) after it was destroyed
df.Select(udf1(df["_1"])).Show();

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 throws the following (unexpected) exception:
// [Error] [JvmBridge] org.apache.spark.SparkException: Task not serializable
df.Select(udf2(df["_1"])).Show();
```

<span data-ttu-id="978c4-127">次のコード スニペットは、予期しないシリアル化の動作により、`bv` の破棄が確実に `udf2` に影響しないようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="978c4-127">The following code snippet demonstrates how to ensure that destroying `bv` doesn't affect `udf2` because of an unexpected serialization behavior:</span></span>

```csharp
string v = "Variable to be broadcasted";
// Restricting the visibility of bv to only the UDF referencing it
{
    Broadcast<string> bv = SparkContext.Broadcast(v);

    // Using the broadcast variable in a UDF:
    Func<Column, Column> udf1 = Udf<string, string>(
        str => $"{str}: {bv.Value()}");

    // Destroying bv
    bv.Destroy();
}

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 works fine as expected
df.Select(udf2(df["_1"])).Show();
```

## <a name="next-steps"></a><span data-ttu-id="978c4-128">次の手順</span><span class="sxs-lookup"><span data-stu-id="978c4-128">Next steps</span></span>

* [<span data-ttu-id="978c4-129">.NET for Apache Spark の概要</span><span class="sxs-lookup"><span data-stu-id="978c4-129">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="978c4-130">Windows で .NET for Apache Spark アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="978c4-130">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
* [<span data-ttu-id="978c4-131">.NET for Apache Spark ワーカーとユーザー定義関数のバイナリを展開する</span><span class="sxs-lookup"><span data-stu-id="978c4-131">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>](deploy-worker-udf-binaries.md)
