---
title: '方法 : 分離ストレージ内でファイルおよびディレクトリを検索する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: ebd2ae6684e7b3390b29aeebeb2552b4616a69f3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830728"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="521e6-102">方法 : 分離ストレージ内でファイルおよびディレクトリを検索する</span><span class="sxs-lookup"><span data-stu-id="521e6-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="521e6-103">分離ストレージ内のディレクトリを検索するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="521e6-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="521e6-104">このメソッドは、検索パターンを表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="521e6-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="521e6-105">検索パターンでは、1 文字を表すワイルドカード文字 (?) と複数の文字を表すワイルドカード文字 (\*) の両方を使用できます。しかし、これらのワイルドカード文字は、名前の最後の部分で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="521e6-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="521e6-106">たとえば、`directory1/*ect*` は有効な検索文字列ですが、`*ect*/directory2` は無効です。</span><span class="sxs-lookup"><span data-stu-id="521e6-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="521e6-107">ファイルを検索するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="521e6-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="521e6-108"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> に適用される、検索文字列内のワイルドカード文字の制約と同じ制約が <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="521e6-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="521e6-109">これらはいずれも再帰的メソッドではありません。つまり、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> には、ストア内のすべてのディレクトリまたはファイルを一覧表示するためのメソッドは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="521e6-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="521e6-110">ただし、次のコード例には、再帰的メソッドの例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="521e6-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="521e6-111">例</span><span class="sxs-lookup"><span data-stu-id="521e6-111">Example</span></span>  
 <span data-ttu-id="521e6-112">分離ストア内にファイルおよびディレクトリを作成する方法を次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="521e6-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="521e6-113">最初に、ユーザー、ドメイン、アセンブリ別に分離されたストアを取得し、`isoStore` 変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="521e6-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="521e6-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> メソッドは複数の異なるディレクトリをセットアップするために使用され、<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> コンストラクターではそれらのディレクトリ内にいくつかのファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="521e6-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="521e6-115">次に、`GetAllDirectories` メソッドの結果内をループします。</span><span class="sxs-lookup"><span data-stu-id="521e6-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="521e6-116">このメソッドは、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> を使用して現在のディレクトリ内のすべてのディレクトリ名を検索します。</span><span class="sxs-lookup"><span data-stu-id="521e6-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="521e6-117">これらのディレクトリ名は配列で格納されているので、`GetAllDirectories` は自分自身を呼び出し、検出したそれぞれのディレクトリを渡します。</span><span class="sxs-lookup"><span data-stu-id="521e6-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="521e6-118">結果として、すべてのディレクトリ名が配列に返されます。</span><span class="sxs-lookup"><span data-stu-id="521e6-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="521e6-119">次に、`GetAllFiles` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="521e6-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="521e6-120">このメソッドは、`GetAllDirectories` を呼び出してすべてのディレクトリの名前を検索した後、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> メソッドを使用して、各ディレクトリにファイルが存在するかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="521e6-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="521e6-121">結果は、表示のために配列で返されます。</span><span class="sxs-lookup"><span data-stu-id="521e6-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="521e6-122">参照</span><span class="sxs-lookup"><span data-stu-id="521e6-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="521e6-123">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="521e6-123">Isolated Storage</span></span>](isolated-storage.md)
