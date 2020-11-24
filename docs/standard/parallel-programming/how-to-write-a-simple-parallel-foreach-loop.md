---
title: Parallel.ForEach を使用して単純な並列プログラムを記述する
description: この記事では、.NET でデータの並列処理を有効にする方法について説明します。 任意の IEnumerable または IEnumerable<T> データ ソースに対して、Parallel.ForEach ループを記述します。
ms.date: 02/14/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: e4f67f6fbe5a79e925ecd6aaec3f833704cda38c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825417"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="f9e50-104">方法: 単純な Parallel.ForEach ループを記述する</span><span class="sxs-lookup"><span data-stu-id="f9e50-104">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="f9e50-105">この例は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ループを使用して、<xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> データ ソースでのデータの並列処理を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f9e50-105">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="f9e50-106">ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="f9e50-106">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="f9e50-107">C# または Visual Basic のラムダ式についての情報が必要な場合は、「[PLINQ および TPL のラムダ式](lambda-expressions-in-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e50-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="f9e50-108">例</span><span class="sxs-lookup"><span data-stu-id="f9e50-108">Example</span></span>

<span data-ttu-id="f9e50-109">この例では、*C:\Users\Public\Pictures\Sample Pictures* フォルダーにいくつかの .jpg ファイルがあることを想定し、*Modified* という名前の新しいサブフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f9e50-109">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="f9e50-110">例を実行すると、*Sample Pictures* のそれぞれの .jpg 画像が回転して、*Modified* に保存されます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-110">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="f9e50-111">2 つのパスは必要に応じて変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-111">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="f9e50-112"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ループは <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ループのように動作します。</span><span class="sxs-lookup"><span data-stu-id="f9e50-112">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="f9e50-113">ループによってソース コレクションがパーティション分割され、作業はシステム環境に基づいて複数のスレッドでスケジューリングされます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-113">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="f9e50-114">システムのプロセッサの数が多いほど、並列メソッドの実行が速くなります。</span><span class="sxs-lookup"><span data-stu-id="f9e50-114">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="f9e50-115">一部のソース コレクションでは、ソースのサイズやループで実行される作業の種類に応じて、順次ループがより高速になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f9e50-115">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="f9e50-116">パフォーマンスの詳細については、「[データとタスクの並列化における注意点](potential-pitfalls-in-data-and-task-parallelism.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e50-116">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="f9e50-117">並列ループの詳細については、「[方法: 単純な Parallel.For ループを記述する](how-to-write-a-simple-parallel-for-loop.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e50-117">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="f9e50-118">非ジェネリック コレクションで <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> を使用する場合は、次の例に示すように、<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> 拡張メソッドを使用して、コレクションをジェネリック コレクションに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-118">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="f9e50-119">また、Parallel LINQ (PLINQ) を使用して、<xref:System.Collections.Generic.IEnumerable%601> データ ソースの処理を並列化することもできます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-119">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="f9e50-120">PLINQ では、宣言型のクエリ構文を使用して、ループの動作を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-120">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="f9e50-121">詳細については、「[Parallel LINQ (PLINQ)](introduction-to-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e50-121">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="f9e50-122">コードをコンパイルして実行する</span><span class="sxs-lookup"><span data-stu-id="f9e50-122">Compile and run the code</span></span>

<span data-ttu-id="f9e50-123">コードは .NET Framework のコンソール アプリケーションまたは .NET Core のコンソール アプリケーションとしてコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-123">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="f9e50-124">Visual Studio には、Windows デスクトップと .NET Core 向けに、Visual Basic と C# のコンソール アプリケーション テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="f9e50-124">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="f9e50-125">コマンド ラインから .NET Core CLI コマンド (`dotnet new console` や `dotnet new console -lang vb` など) を使用するか、またはファイルを作成して .NET Framework アプリケーション用のコマンド ライン コンパイラを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-125">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="f9e50-126">.NET Core プロジェクトの場合は、**System.Drawing.Common** NuGet パッケージを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e50-126">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="f9e50-127">Visual Studio ではパッケージのインストールに NuGet パッケージ マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e50-127">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="f9e50-128">または、\*.csproj または \*.vbproj ファイルにパッケージへの参照を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="f9e50-128">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="f9e50-129">コマンド ラインから .NET Core コンソール アプリケーションを実行するには、アプリケーションが含まれるフォルダーから `dotnet run` を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e50-129">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="f9e50-130">Visual Studio からコンソール アプリケーションを実行するには、**F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f9e50-130">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9e50-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9e50-131">See also</span></span>

- [<span data-ttu-id="f9e50-132">データの並列化</span><span class="sxs-lookup"><span data-stu-id="f9e50-132">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="f9e50-133">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="f9e50-133">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="f9e50-134">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f9e50-134">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
