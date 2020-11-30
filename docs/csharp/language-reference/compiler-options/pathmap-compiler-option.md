---
description: -pathmap (C# コンパイラ オプション)
title: -pathmap (C# コンパイラ オプション)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 707a37c6946cfcaf429552f0aeece6b87f3ad71d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125008"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="7acb8-103">-pathmap (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="7acb8-103">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="7acb8-104">**-pathmap** コンパイラ オプションは、コンパイラによるソース パス名出力への物理パスのマップ方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="7acb8-104">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="7acb8-105">構文</span><span class="sxs-lookup"><span data-stu-id="7acb8-105">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="7acb8-106">引数</span><span class="sxs-lookup"><span data-stu-id="7acb8-106">Arguments</span></span>

 <span data-ttu-id="7acb8-107">`path1` 現在の環境でのソース ファイルへの完全なパス</span><span class="sxs-lookup"><span data-stu-id="7acb8-107">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="7acb8-108">`sourcePath1` 出力ファイルにおいて `path1` の代わりに使用されるソース パス。</span><span class="sxs-lookup"><span data-stu-id="7acb8-108">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="7acb8-109">複数のマップされるソース パスを指定するには、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="7acb8-109">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="7acb8-110">注釈</span><span class="sxs-lookup"><span data-stu-id="7acb8-110">Remarks</span></span>

<span data-ttu-id="7acb8-111">コンパイラは、次の理由でその出力にソース パスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7acb8-111">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="7acb8-112"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute> が省略可能なパラメーターに適用される場合、引数はソース パスに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="7acb8-112">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="7acb8-113">ソース パスは、PDB ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="7acb8-113">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="7acb8-114">PDB ファイルのパスは、PE (ポータブル実行可能) ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="7acb8-114">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="7acb8-115">このオプションは、コンパイラが実行されるコンピューター上の各物理パスを、出力ファイルに書き込まれる必要がある対応するパスにマップします。</span><span class="sxs-lookup"><span data-stu-id="7acb8-115">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="7acb8-116">例</span><span class="sxs-lookup"><span data-stu-id="7acb8-116">Example</span></span>

<span data-ttu-id="7acb8-117">ディレクトリ **C:\\work\\tests** 内の `t.cs` をコンパイルし、出力ではそのディレクトリを **\publish** にマップします。</span><span class="sxs-lookup"><span data-stu-id="7acb8-117">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="7acb8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7acb8-118">See also</span></span>

- [<span data-ttu-id="7acb8-119">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="7acb8-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7acb8-120">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="7acb8-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
