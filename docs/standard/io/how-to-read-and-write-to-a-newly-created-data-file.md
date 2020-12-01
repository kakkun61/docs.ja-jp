---
title: '方法: 新しく作成されたデータ ファイルに対して読み書きする'
description: System.IO.BinaryReader クラスと System.IO.BinaryWriter クラスを使用して .NET で新しく作成されたデータ ファイルの読み取りと書き込みを行う方法について説明します。
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET], reading data
- I/O [.NET], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 8ec14ef560ddd69e8c9217298271b7ec715fcb9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734583"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="49b08-103">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="49b08-103">How to: Read and write to a newly created data file</span></span>

<span data-ttu-id="49b08-104"><xref:System.IO.BinaryWriter?displayProperty=nameWithType> クラスおよび <xref:System.IO.BinaryReader?displayProperty=nameWithType> クラスは、文字列ではない形式でデータを書き込んだり読み取ったりするために使用します。</span><span class="sxs-lookup"><span data-stu-id="49b08-104">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="49b08-105">次の例では、空のファイル ストリームを作成し、それにデータを書き込み、それからデータを読み取る方法を示します。</span><span class="sxs-lookup"><span data-stu-id="49b08-105">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="49b08-106">この例では、現在のディレクトリに *Test.data* という名前のデータ ファイルが作成され、関連する <xref:System.IO.BinaryWriter> オブジェクトと <xref:System.IO.BinaryReader> オブジェクトが作成され、<xref:System.IO.BinaryWriter> オブジェクトを使用し、0 から 10 までの整数が *Test.data* に書き込まれます。ファイル ポインターがファイルの末尾に残ります。</span><span class="sxs-lookup"><span data-stu-id="49b08-106">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="49b08-107">次に、<xref:System.IO.BinaryReader> オブジェクトによってファイル ポインターが起点に戻され、指定された内容が読み出されます。</span><span class="sxs-lookup"><span data-stu-id="49b08-107">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49b08-108">*Test.data* が既に現在のディレクトリに存在する場合は、<xref:System.IO.IOException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="49b08-108">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="49b08-109">例外をスローせず、常に新しいファイルを作成するには、ファイル モード オプションとして <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> ではなく <xref:System.IO.FileMode.Create?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="49b08-109">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49b08-110">例</span><span class="sxs-lookup"><span data-stu-id="49b08-110">Example</span></span>  

 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="49b08-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="49b08-111">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="49b08-112">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="49b08-112">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="49b08-113">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="49b08-113">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="49b08-114">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="49b08-114">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="49b08-115">方法: テキストのファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="49b08-115">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="49b08-116">方法: 文字列からの文字の読み取り</span><span class="sxs-lookup"><span data-stu-id="49b08-116">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="49b08-117">方法: 文字列への文字の書き込み</span><span class="sxs-lookup"><span data-stu-id="49b08-117">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="49b08-118">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="49b08-118">File and stream I/O</span></span>](index.md)
