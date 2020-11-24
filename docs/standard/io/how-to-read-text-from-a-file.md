---
title: '方法: ファイルのテキストの読み取り'
description: この記事では、.NET デスクトップ アプリの StreamReader クラスを使用して、テキスト ファイルから同期または非同期でテキストを読み取る方法の例を示します。
ms.date: 01/03/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 7c772ec1de41d0ba2b4ef0d924a252326ee6909e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823369"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="5faa5-103">方法: ファイルのテキストの読み取り</span><span class="sxs-lookup"><span data-stu-id="5faa5-103">How to: Read text from a file</span></span>

<span data-ttu-id="5faa5-104">次に、.NET デスクトップ アプリを使用してテキスト ファイルから同期でテキストを読み取る方法と非同期でテキストを読み取る方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="5faa5-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="5faa5-105">どちらの例でも、<xref:System.IO.StreamReader> クラスのインスタンスを作成する場合に、ファイルの相対パスまたは絶対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="5faa5-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5faa5-106">Windows ランタイムではファイルに対する読み取りと書き込みに別のストリーム型が用意されているため、これらのコード例はユニバーサル Windows プラットフォーム (UWP) アプリには適用されません。</span><span class="sxs-lookup"><span data-stu-id="5faa5-106">These code examples do not apply to Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="5faa5-107">UWP アプリのファイルからテキストを読み取る方法を示す例については、「[Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10))」 (クイック スタート: ファイルの読み取りと書き込み) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5faa5-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="5faa5-108">.NET Framework ストリームと Windows ランタイム ストリーム間で変換を行う方法を示す例については、「[方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う](how-to-convert-between-dotnet-streams-and-winrt-streams.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5faa5-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="5faa5-109">例:コンソール アプリの同期読み取り</span><span class="sxs-lookup"><span data-stu-id="5faa5-109">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="5faa5-110">次の例では、コンソール アプリ内での同期読み取り操作を示します。</span><span class="sxs-lookup"><span data-stu-id="5faa5-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="5faa5-111">この例では、ストリーム リーダーを使用してテキスト ファイルを開き、コンテンツが文字列にコピーされ、文字列がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="5faa5-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5faa5-112">サンプルでは、*TestFile.txt* という名前のファイルがアプリと同じフォルダーに入っていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="5faa5-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="5faa5-113">例:WPF アプリの非同期読み取り</span><span class="sxs-lookup"><span data-stu-id="5faa5-113">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="5faa5-114">次の例では、Windows Presentation Foundation (WPF) アプリ内での非同期読み取り操作を示します。</span><span class="sxs-lookup"><span data-stu-id="5faa5-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5faa5-115">サンプルでは、*TestFile.txt* という名前のファイルがアプリと同じフォルダーに入っていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="5faa5-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a><span data-ttu-id="5faa5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5faa5-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="5faa5-117">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="5faa5-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="5faa5-118">[方法: ディレクトリ一覧を作成する](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5faa5-118">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- <span data-ttu-id="5faa5-119">[クイック スタート:ファイルの読み書き](/previous-versions/windows/apps/hh758325(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="5faa5-119">[Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10))</span></span>  
- [<span data-ttu-id="5faa5-120">方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う</span><span class="sxs-lookup"><span data-stu-id="5faa5-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="5faa5-121">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="5faa5-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="5faa5-122">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="5faa5-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="5faa5-123">方法: テキストのファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="5faa5-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="5faa5-124">方法: 文字列からの文字の読み取り</span><span class="sxs-lookup"><span data-stu-id="5faa5-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="5faa5-125">方法: 文字列への文字の書き込み</span><span class="sxs-lookup"><span data-stu-id="5faa5-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="5faa5-126">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="5faa5-126">File and stream I/O</span></span>](index.md)
