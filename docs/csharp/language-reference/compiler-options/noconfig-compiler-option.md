---
description: -noconfig (C# コンパイラ オプション)
title: -noconfig (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: d62f16a3926aaa78e79c25b1c9b8d84e4401795a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194077"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="6d1ae-103">-noconfig (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="6d1ae-103">-noconfig (C# Compiler Options)</span></span>

<span data-ttu-id="6d1ae-104">**-noconfig** オプションは、csc.exe ファイルと同じディレクトリにあり、このディレクトリから読み込まれた csc.rsp ファイルでコンパイルしないようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="6d1ae-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d1ae-106">解説</span><span class="sxs-lookup"><span data-stu-id="6d1ae-106">Remarks</span></span>  

 <span data-ttu-id="6d1ae-107">csc.rsp ファイルは、.NET Framework に付属するすべてのアセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-107">The csc.rsp file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="6d1ae-108">Visual Studio .NET 開発環境に含まれる実際の参照は、プロジェクトの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="6d1ae-109">csc.rsp ファイルを変更し、csc.exe 使ってコマンドラインからすべてのコンパイルに含める必要がある追加のコンパイラ オプションを指定できます ( **-noconfig** オプションを除きます)。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="6d1ae-110">コンパイラは **csc** コマンドに最後に渡されるオプションを処理します。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="6d1ae-111">そのため、コマンドラインで指定した任意のオプションが、csc.rsp ファイル内の同じオプションの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="6d1ae-112">コンパイラで csc.rsp ファイル内の設定を検索して使用しない場合は、**-noconfig** を指定します。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="6d1ae-113">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="6d1ae-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1ae-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d1ae-114">See also</span></span>

- [<span data-ttu-id="6d1ae-115">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="6d1ae-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6d1ae-116">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="6d1ae-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
