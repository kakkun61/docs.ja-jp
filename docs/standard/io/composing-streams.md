---
title: ストリームの作成
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
ms.openlocfilehash: c50a372ee3434fcd7f72ad707ca82c5c9ad8a5c8
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823382"
---
# <a name="compose-streams"></a><span data-ttu-id="63d4a-102">ストリームの作成</span><span class="sxs-lookup"><span data-stu-id="63d4a-102">Compose streams</span></span>
<span data-ttu-id="63d4a-103">*バッキング ストア* は、ディスクやメモリなどの記憶域メディアです。</span><span class="sxs-lookup"><span data-stu-id="63d4a-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="63d4a-104">さまざまなバッキング ストアが <xref:System.IO.Stream> クラスの実装としてそれぞれ独自のストリームを実装しています。</span><span class="sxs-lookup"><span data-stu-id="63d4a-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="63d4a-105">各ストリームの種類は、指定されたバッキング ストアとの間でバイトの読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="63d4a-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="63d4a-106">バッキング ストアに接続するストリームは、*基本ストリーム* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="63d4a-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="63d4a-107">基本ストリームにはコンストラクターがあり、ストリームをバッキング ストアに接続するために必要なパラメーターがそれに指定されます。</span><span class="sxs-lookup"><span data-stu-id="63d4a-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="63d4a-108">たとえば、<xref:System.IO.FileStream> には、プロセスでファイルを共有する方法を指定する path パラメーターを指定するコンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="63d4a-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="63d4a-109"><xref:System.IO> クラスは、簡易なストリーム構成で設計されています。</span><span class="sxs-lookup"><span data-stu-id="63d4a-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="63d4a-110">必要な機能を提供する 1 つ以上のパススルー ストリームに基本ストリームをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="63d4a-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="63d4a-111">好みの種類の読み取りまたは書き込みを簡単に実行できるように、チェーンの末端に閲覧者またはライターをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="63d4a-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="63d4a-112">次のコード例では、*MyFile.txt* をバッファーするために既存の *MyFile.txt* を中心にして **FileStream** を作成します。</span><span class="sxs-lookup"><span data-stu-id="63d4a-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="63d4a-113">**FileStreams** は既定でバッファーされます。</span><span class="sxs-lookup"><span data-stu-id="63d4a-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="63d4a-114">サンプルでは、*MyFile.txt* という名前のファイルがアプリと同じフォルダーに入っていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="63d4a-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="63d4a-115">例:StreamReader を使用する</span><span class="sxs-lookup"><span data-stu-id="63d4a-115">Example: Use StreamReader</span></span>
<span data-ttu-id="63d4a-116">次の例では、**FileStream** から文字を読み取る <xref:System.IO.StreamReader> が作成されます。これはコンストラクター引数として **StreamReader** に渡されます。</span><span class="sxs-lookup"><span data-stu-id="63d4a-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="63d4a-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> は、<xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> によって文字が検出されなくなるまで読み取りを行います。</span><span class="sxs-lookup"><span data-stu-id="63d4a-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="63d4a-118">例:BinaryReader を使用する</span><span class="sxs-lookup"><span data-stu-id="63d4a-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="63d4a-119">次の例では、**FileStream** からバイト数を読み取る <xref:System.IO.BinaryReader> が作成されます。これはコンストラクター引数として **BinaryReader** に渡されます。</span><span class="sxs-lookup"><span data-stu-id="63d4a-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="63d4a-120"><xref:System.IO.BinaryReader.ReadByte%2A> は、<xref:System.IO.BinaryReader.PeekChar%2A> によってバイトが検出されなくなるまで読み取りを行います。</span><span class="sxs-lookup"><span data-stu-id="63d4a-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="63d4a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="63d4a-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
