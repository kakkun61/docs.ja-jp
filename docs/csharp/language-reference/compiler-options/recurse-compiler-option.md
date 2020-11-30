---
description: -recurse (C# コンパイラ オプション)
title: -recurse (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 9e84ff95f7f0addac1c2c2d79af0ab53572da27f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193804"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="84b58-103">-recurse (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="84b58-103">-recurse (C# Compiler Options)</span></span>

<span data-ttu-id="84b58-104">-recurse オプションを使用すると、指定のディレクトリ (dir) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="84b58-104">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b58-105">構文</span><span class="sxs-lookup"><span data-stu-id="84b58-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="84b58-106">引数</span><span class="sxs-lookup"><span data-stu-id="84b58-106">Arguments</span></span>  

 <span data-ttu-id="84b58-107">`dir` (省略可)</span><span class="sxs-lookup"><span data-stu-id="84b58-107">`dir` (optional)</span></span>  
 <span data-ttu-id="84b58-108">検索を開始するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="84b58-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="84b58-109">指定しない場合は、プロジェクト ディレクトリから検索されます。</span><span class="sxs-lookup"><span data-stu-id="84b58-109">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="84b58-110">検索するファイル。</span><span class="sxs-lookup"><span data-stu-id="84b58-110">The file(s) to search for.</span></span> <span data-ttu-id="84b58-111">ワイルドカード文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="84b58-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84b58-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="84b58-112">Remarks</span></span>  

 <span data-ttu-id="84b58-113">**-recurse** オプションを使用すると、指定のディレクトリ (`dir`) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="84b58-113">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="84b58-114">**-recurse** を使用しなくても、ファイル名にワイルドカードを使用すると、プロジェクト ディレクトリ内で一致するすべてのファイルをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="84b58-114">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="84b58-115">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="84b58-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84b58-116">例</span><span class="sxs-lookup"><span data-stu-id="84b58-116">Example</span></span>  

 <span data-ttu-id="84b58-117">現在のディレクトリ内のすべての C# ファイルをコンパイルするには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="84b58-117">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="84b58-118">dir1\dir2 ディレクトリおよびそのディレクトリの下の全ディレクトリ内の C# ファイルすべてをコンパイルし、dir2.dll を生成するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="84b58-118">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="84b58-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="84b58-119">See also</span></span>

- [<span data-ttu-id="84b58-120">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="84b58-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="84b58-121">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="84b58-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
