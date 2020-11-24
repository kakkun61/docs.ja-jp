---
title: '方法: テキストのファイルへの書き込み'
description: .NET アプリでファイルにテキストを書き込む方法、または追加する方法について説明します。 StreamWriter クラスまたは File クラスのメソッドを使用して、同期的または非同期的にテキストを書き込みます。
ms.date: 01/04/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: bd9abc2aac4b02f71e41f71e518a76b2477420da
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829714"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="098ac-104">方法: テキストのファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="098ac-104">How to: Write text to a file</span></span>

<span data-ttu-id="098ac-105">このトピックでは、.NET アプリ用のファイルにテキストを書き込むさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="098ac-105">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="098ac-106">テキストをファイルに書き込むには、一般に次のクラスおよびメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="098ac-106">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="098ac-107"><xref:System.IO.StreamWriter> には、同期的にファイルに書き込むメソッド (<xref:System.IO.StreamWriter.Write%2A> と <xref:System.IO.TextWriter.WriteLine%2A>) または非同期的に書き込むメソッド (<xref:System.IO.StreamWriter.WriteAsync%2A> と <xref:System.IO.StreamWriter.WriteLineAsync%2A>) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="098ac-107"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="098ac-108"><xref:System.IO.File> では、ファイルにテキストを書き込む静的メソッド (<xref:System.IO.File.WriteAllLines%2A>、<xref:System.IO.File.WriteAllText%2A> など)、またはファイルにテキストを追加する静的メソッド (<xref:System.IO.File.AppendAllLines%2A>、<xref:System.IO.File.AppendAllText%2A>、<xref:System.IO.File.AppendText%2A> など) が提供されています。</span><span class="sxs-lookup"><span data-stu-id="098ac-108"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="098ac-109"><xref:System.IO.Path> は、ファイルまたはディレクトリのパスの情報を含む文字列用です。</span><span class="sxs-lookup"><span data-stu-id="098ac-109"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="098ac-110">これには、<xref:System.IO.Path.Combine%2A> メソッドと、.NET Core 2.1 以降においてファイルまたはディレクトリのパスを作成するために文字列を連結できる <xref:System.IO.Path.Join%2A> および <xref:System.IO.Path.TryJoin%2A> メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="098ac-110">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="098ac-111">次の例では、最小限必要なコードのみを示します。</span><span class="sxs-lookup"><span data-stu-id="098ac-111">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="098ac-112">通常、実際のアプリではこれよりも信頼性の高いエラー チェックと例外処理を行います。</span><span class="sxs-lookup"><span data-stu-id="098ac-112">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="098ac-113">例:StreamWriter で同期的にテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="098ac-113">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="098ac-114">次の例では、<xref:System.IO.StreamWriter> クラスを使用して、新しいファイルにテキストを一度に 1 行ずつ同期的に書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="098ac-114">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="098ac-115"><xref:System.IO.StreamWriter> オブジェクトが宣言されていて、`using` ステートメントでインスタンス化されるため、<xref:System.IO.StreamWriter.Dispose%2A> メソッドが呼び出され、それによってストリームが自動的にフラッシュされて閉じられます。</span><span class="sxs-lookup"><span data-stu-id="098ac-115">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="098ac-116">例:StreamWriter で同期的にテキストを追加する</span><span class="sxs-lookup"><span data-stu-id="098ac-116">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="098ac-117">次の例では、<xref:System.IO.StreamWriter> クラスを使用して、最初の例で作成したテキスト ファイルにテキストを同期的に追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="098ac-117">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="098ac-118">例:StreamWriter で非同期的にテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="098ac-118">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="098ac-119">次の例に、 <xref:System.IO.StreamWriter> クラスを使用して、新しいファイルにテキストを非同期的に書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="098ac-119">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="098ac-120"><xref:System.IO.StreamWriter.WriteAsync%2A> メソッドを呼び出すには、`async` メソッド内で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="098ac-120">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="098ac-121">C# の例では、プログラム エントリ ポイントでの `async` 修飾子のサポートが追加されている C# 7.1 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="098ac-121">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="098ac-122">例:File クラスを使用してテキストの書き込みと追加を行う</span><span class="sxs-lookup"><span data-stu-id="098ac-122">Example: Write and append text with the File class</span></span>

<span data-ttu-id="098ac-123">次の例に、 <xref:System.IO.File> クラスを使用して、新しいファイルにテキストを書き込み、この同じファイルに新しいテキスト行を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="098ac-123">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="098ac-124"><xref:System.IO.File.WriteAllText%2A> および <xref:System.IO.File.AppendAllLines%2A> メソッドは、ファイルを自動的に開き、閉じます。</span><span class="sxs-lookup"><span data-stu-id="098ac-124">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="098ac-125"><xref:System.IO.File.WriteAllText%2A> メソッドに指定したパスが既に存在する場合、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="098ac-125">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="098ac-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="098ac-126">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="098ac-127">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="098ac-127">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="098ac-128">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="098ac-128">How to: Read and write to a newly-created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="098ac-129">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="098ac-129">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="098ac-130">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="098ac-130">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)
- [<span data-ttu-id="098ac-131">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="098ac-131">File and stream I/O</span></span>](index.md)
