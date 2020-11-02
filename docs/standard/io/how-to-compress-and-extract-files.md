---
title: '方法: ファイルを圧縮して抽出する'
description: System.IO.Compression を使用してファイルを圧縮して抽出します。 ZipFile、ZipArchive、ZipArchiveEntry、DeflateStream、GZipStream の使用例を参照します。
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
ms.openlocfilehash: ea078099aba3161818844d14af221eb582e7f11b
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188290"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="d6f58-104">方法: ファイルを圧縮して抽出する</span><span class="sxs-lookup"><span data-stu-id="d6f58-104">How to: Compress and extract files</span></span>

<span data-ttu-id="d6f58-105"><xref:System.IO.Compression> 名前空間には、ファイルおよびストリームを圧縮および展開するための次の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d6f58-105">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="d6f58-106">これらの型を使用して、圧縮ファイルの内容を読み取り、変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-106">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="d6f58-107">圧縮ファイルで実行できる操作の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-107">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="d6f58-108">これらの例では、プロジェクトに次の NuGet パッケージを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6f58-108">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="d6f58-109">System.IO.Compression</span><span class="sxs-lookup"><span data-stu-id="d6f58-109">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="d6f58-110">System.IO.Compression.ZipFile</span><span class="sxs-lookup"><span data-stu-id="d6f58-110">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="d6f58-111">.NET Framework を使用している場合は、プロジェクトにこれら 2 つのライブラリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-111">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="d6f58-112">例 1: .zip ファイルを作成して抽出する</span><span class="sxs-lookup"><span data-stu-id="d6f58-112">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="d6f58-113">次の例では、<xref:System.IO.Compression.ZipFile> クラスを使用して圧縮された *.zip* ファイルの作成と抽出を行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d6f58-113">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="d6f58-114">この例では、フォルダーの内容を新しい *.zip* ファイルに圧縮し、その zip を新しいフォルダーに抽出します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-114">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="d6f58-115">サンプルを実行するには、プログラムのフォルダーに *start* フォルダーを作成し、圧縮するファイルをそこに置きます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-115">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="d6f58-116">例 2:特定の拡張子のファイルを抽出する</span><span class="sxs-lookup"><span data-stu-id="d6f58-116">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="d6f58-117">次の例では、既存の *.zip* ファイルの内容を反復処理し、拡張子が *.txt* のファイルを抽出します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-117">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="d6f58-118"><xref:System.IO.Compression.ZipArchive> クラスを使用して zip にアクセスし、<xref:System.IO.Compression.ZipArchiveEntry> クラスを使用して個々のエントリを調べます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-118">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="d6f58-119"><xref:System.IO.Compression.ZipArchiveEntry> オブジェクトの拡張メソッド <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> は、<xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> クラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-119">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="d6f58-120">サンプルを実行するには、 *result.zip* という名前の *.zip* ファイルをプログラム フォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-120">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="d6f58-121">入力を求められたら、抽出先のフォルダー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-121">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6f58-122">ファイルを解凍する場合は、解凍先のディレクトリを回避する悪意のあるファイル パスを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6f58-122">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="d6f58-123">これは、パス トラバーサル攻撃と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-123">This is known as a path traversal attack.</span></span> <span data-ttu-id="d6f58-124">次の例では、悪意のあるファイル パスを確認して安全な解凍手段を提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-124">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="d6f58-125">例 3:既存の zip にファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="d6f58-125">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="d6f58-126">次の例では、<xref:System.IO.Compression.ZipArchive> クラスを使用して既存の *.zip* ファイルにアクセスし、ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-126">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="d6f58-127">新しいファイルは、既存の zip に追加するときに圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-127">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="d6f58-128">例 4:.gz ファイルを圧縮および展開する</span><span class="sxs-lookup"><span data-stu-id="d6f58-128">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="d6f58-129">また、<xref:System.IO.Compression.GZipStream> クラスと <xref:System.IO.Compression.DeflateStream> クラスを使用してデータを圧縮および展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-129">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="d6f58-130">圧縮と展開には同じ圧縮アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-130">They use the same compression algorithm.</span></span> <span data-ttu-id="d6f58-131">多くの一般的なツールを使用して、 *.gz* ファイルに書き込まれた <xref:System.IO.Compression.GZipStream> オブジェクトを展開できます。</span><span class="sxs-lookup"><span data-stu-id="d6f58-131">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="d6f58-132">次の例では、<xref:System.IO.Compression.GZipStream> クラスを使用してファイルのディレクトリを圧縮および展開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d6f58-132">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="d6f58-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6f58-133">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="d6f58-134">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="d6f58-134">File and stream I/O</span></span>](index.md)
