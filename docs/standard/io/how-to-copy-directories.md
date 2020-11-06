---
title: '方法: ディレクトリをコピーする'
description: 別の場所にディレクトリの内容を同期的にコピーする I/O クラスを使用してディレクトリをコピーする方法を参照します。
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET], copying directories
- subdirectory copying
- copying directories
- directories [.NET], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 476473d5c25ce29d070abbeef7fa29a7cb9621e1
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187984"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="c0435-103">方法: ディレクトリをコピーする</span><span class="sxs-lookup"><span data-stu-id="c0435-103">How to: Copy directories</span></span>

<span data-ttu-id="c0435-104">この記事では、I/O クラスを使用して、別の場所にディレクトリの内容を同期的にコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c0435-104">This article demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="c0435-105">ファイルを非同期的にコピーする例については、「[非同期ファイル I/O](asynchronous-file-i-o.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0435-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="c0435-106">この例では、`DirectoryCopy` メソッドの `copySubDirs` を `true` に設定することでサブディレクトリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="c0435-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="c0435-107">`DirectoryCopy` メソッドは各サブディレクトリでそれ自体を呼び出すことで、コピーするサブディレクトリがなくなるまでサブディレクトリを再帰的にコピーします。</span><span class="sxs-lookup"><span data-stu-id="c0435-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0435-108">例</span><span class="sxs-lookup"><span data-stu-id="c0435-108">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="c0435-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0435-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="c0435-110">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="c0435-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="c0435-111">共通 I/O タスク</span><span class="sxs-lookup"><span data-stu-id="c0435-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="c0435-112">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="c0435-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
