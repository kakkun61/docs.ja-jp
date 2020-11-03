---
title: '方法: 文字列からの文字の読み取り'
description: .Net で文字列から文字を読み取る方法について学習します。 同期的および非同期的に文字を読み取る方法の例を参照してください。
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: c613f8170655601b72b87de4a20c295b1054bd1a
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189343"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="948bf-104">方法: 文字列からの文字の読み取り</span><span class="sxs-lookup"><span data-stu-id="948bf-104">How to: Read characters from a string</span></span>

<span data-ttu-id="948bf-105">次のコード例は、文字列から同期的または非同期的に文字を読み取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="948bf-105">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="948bf-106">例:同期的に文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="948bf-106">Example: Read characters synchronously</span></span>
 <span data-ttu-id="948bf-107">この例では、文字列から同期的に 13 文字を読み取り、配列に格納し、これらを表示します。</span><span class="sxs-lookup"><span data-stu-id="948bf-107">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="948bf-108">次に、この例では、文字列の残りの文字を読み取り、6 番目の要素で始まる配列に格納し、配列の内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="948bf-108">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="948bf-109">例:非同期的に文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="948bf-109">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="948bf-110">次の例は WPF アプリの裏側にあるコードです。</span><span class="sxs-lookup"><span data-stu-id="948bf-110">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="948bf-111">ウィンドウを読み込むと、<xref:System.Windows.Controls.TextBox> コントロールから非同期的にすべての文字を読み取り、配列に格納します。</span><span class="sxs-lookup"><span data-stu-id="948bf-111">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="948bf-112">次に、<xref:System.Windows.Controls.TextBlock> コントロールの個別の行に各文字または空白文字が非同期で書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="948bf-112">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="948bf-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="948bf-113">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="948bf-114">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="948bf-114">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="948bf-115">[方法: ディレクトリ一覧を作成する](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="948bf-115">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="948bf-116">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="948bf-116">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="948bf-117">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="948bf-117">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="948bf-118">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="948bf-118">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="948bf-119">方法: テキストのファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="948bf-119">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="948bf-120">方法: 文字列への文字の書き込み</span><span class="sxs-lookup"><span data-stu-id="948bf-120">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="948bf-121">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="948bf-121">File and stream I/O</span></span>](index.md)
