---
description: -pdb (C# コンパイラ オプション)
title: -pdb (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: ced1ee1f4f079830a032a628da96a389ba27da90
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193856"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="9996d-103">-pdb (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="9996d-103">-pdb (C# Compiler Options)</span></span>

<span data-ttu-id="9996d-104">**-pdb** コンパイラ オプションは、デバッグ シンボル ファイルの場所と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9996d-104">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9996d-105">構文</span><span class="sxs-lookup"><span data-stu-id="9996d-105">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9996d-106">引数</span><span class="sxs-lookup"><span data-stu-id="9996d-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="9996d-107">デバッグ シンボル ファイルの名前と場所です。</span><span class="sxs-lookup"><span data-stu-id="9996d-107">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9996d-108">注釈</span><span class="sxs-lookup"><span data-stu-id="9996d-108">Remarks</span></span>  

 <span data-ttu-id="9996d-109">[-debug (C# コンパイラ オプション)](./debug-compiler-option.md) を指定すると、コンパイラは、コンパイラが出力ファイル (.exe または .dll) を作成するのと同じディレクトリに、出力ファイルと同じ名前のファイル名で .pdb ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9996d-109">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="9996d-110">**-pdb** では、.pdb ファイルに対し、既定以外のファイル名と場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="9996d-110">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="9996d-111">このコンパイラ オプションは、Visual Studio 開発環境で設定することはできません。また、プログラムで変更することもできません。</span><span class="sxs-lookup"><span data-stu-id="9996d-111">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9996d-112">例</span><span class="sxs-lookup"><span data-stu-id="9996d-112">Example</span></span>  

 <span data-ttu-id="9996d-113">`t.cs` をコンパイルして、tt.pdb と呼ばれる .pdb ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9996d-113">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9996d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9996d-114">See also</span></span>

- [<span data-ttu-id="9996d-115">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="9996d-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9996d-116">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="9996d-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
