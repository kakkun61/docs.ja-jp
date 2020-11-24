---
title: 非同期ファイル I/O
description: .NET での非同期ファイル I/O について確認します。 ReadAsync、WriteAsync などの非同期操作を簡略化する非同期メソッドについて学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: aaf722c4af1598b639ffc56e30639e93dbc8a514
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823460"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="e0aa2-104">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="e0aa2-104">Asynchronous File I/O</span></span>

<span data-ttu-id="e0aa2-105">非同期操作では、メイン スレッドをブロックすることなくリソース使用量の多い I/O 操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-105">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="e0aa2-106">このパフォーマンスに関する考慮事項は、時間のかかるストリーム操作によって UI スレッドがブロックされ、アプリが動作していないと見なされる可能性がある Windows 8.x Store アプリまたはデスクトップ アプリで特に重要です。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-106">This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="e0aa2-107">.NET Framework 4.5 以降の I/O 型には非同期操作を単純化する非同期メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-107">Starting with .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="e0aa2-108">非同期のメソッドの名前には `Async` が含まれます ( <xref:System.IO.Stream.ReadAsync%2A>、 <xref:System.IO.Stream.WriteAsync%2A>、 <xref:System.IO.Stream.CopyToAsync%2A>、 <xref:System.IO.Stream.FlushAsync%2A>、 <xref:System.IO.TextReader.ReadLineAsync%2A>、 <xref:System.IO.TextReader.ReadToEndAsync%2A>など)。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-108">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="e0aa2-109">これらの非同期のメソッドは、 <xref:System.IO.Stream>、 <xref:System.IO.FileStream>、 <xref:System.IO.MemoryStream>などのストリーム クラスと、 <xref:System.IO.TextReader> 、 <xref:System.IO.TextWriter>などのストリームとの間の読み取り/書き込みに使用されるクラスに実装されます。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-109">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="e0aa2-110">.NET Framework 4 およびそれ以前のバージョンで非同期 I/O 操作を実装するには、<xref:System.IO.Stream.BeginRead%2A>、<xref:System.IO.Stream.EndRead%2A> などのメソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-110">In .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="e0aa2-111">これらのメソッドは、レガシ コードをサポートするために現行の .NET バージョンでも使用できますが、非同期 I/O 操作は非同期のメソッドを使用して実装する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-111">These methods are still available in current .NET versions to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="e0aa2-112">C# と Visual Basic には、非同期プログラミング用のキーワードがそれぞれ 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-112">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="e0aa2-113">`Async` (Visual Basic) 修飾子または `async` (C#) 修飾子。非同期操作を含むメソッドをマークするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-113">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="e0aa2-114">`Await` (Visual Basic) 演算子または `await` (C#) 演算子。非同期のメソッドの結果に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-114">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="e0aa2-115">非同期 I/O 操作を実装するには、これらのキーワードを非同期のメソッドと組み合わせて使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-115">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="e0aa2-116">詳細については、「[Async および Await を使用した非同期プログラミング (C#)](../../csharp/programming-guide/concepts/async/index.md)」または「[Async および Await を使用した非同期プログラミング (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-116">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="e0aa2-117">次の例では、2 つの <xref:System.IO.FileStream> オブジェクトを使用して、ファイルをディレクトリ間で非同期にコピーする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-117">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="e0aa2-118">非同期のメソッドを呼び出すので、 <xref:System.Web.UI.WebControls.Button.Click> コントロールの <xref:System.Windows.Controls.Button> イベント ハンドラーは `async` 修飾子でマークされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-118">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="e0aa2-119">次の例は前述の例と似ていますが、 <xref:System.IO.StreamReader> オブジェクトと <xref:System.IO.StreamWriter> オブジェクトを使用して、テキスト ファイルの内容の読み取り/書き込みを非同期で行います。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-119">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="e0aa2-120">次の例では、分離コード ファイルと XAML ファイルを使用して Windows 8.x Store アプリでファイルを <xref:System.IO.Stream> として開き、<xref:System.IO.StreamReader> クラスのインスタンスを使用してその内容を読み取る方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-120">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="e0aa2-121">ここでは、非同期のメソッドを使用して、ファイルをストリームとして開き、ファイルの内容を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e0aa2-121">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="e0aa2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0aa2-122">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="e0aa2-123">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="e0aa2-123">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="e0aa2-124">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="e0aa2-124">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="e0aa2-125">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0aa2-125">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
