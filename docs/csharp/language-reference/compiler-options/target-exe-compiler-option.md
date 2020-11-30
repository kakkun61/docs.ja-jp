---
description: -target:exe (C# コンパイラ オプション)
title: -target:exe (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: ae1706f1ecdd396e24711070d19420faa6d34761
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193764"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="d1a9b-103">-target:exe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="d1a9b-103">-target:exe (C# Compiler Options)</span></span>

<span data-ttu-id="d1a9b-104">**-target:exe** オプションを指定した場合、コンパイラは実行可能な (EXE) コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a9b-105">構文</span><span class="sxs-lookup"><span data-stu-id="d1a9b-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="d1a9b-106">解説</span><span class="sxs-lookup"><span data-stu-id="d1a9b-106">Remarks</span></span>  

 <span data-ttu-id="d1a9b-107">**-target:exe** オプションは既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="d1a9b-108">実行可能ファイルは、.exe という拡張子で作成されます。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="d1a9b-109">Windows プログラムの実行可能ファイルを作成する場合は、[-target:winexe](./target-winexe-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="d1a9b-110">[-out](./out-compiler-option.md) オプションで指定しない限り、出力ファイル名は [Main](../../programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="d1a9b-111">コマンド ラインで指定すると、次の **-out** または **-target:module** オプションまでのすべてのファイルが .exe ファイルを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="d1a9b-112">**Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内で 1 つだけ必要になります。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="d1a9b-113">コードに **Main** メソッドを含むクラスが複数ある場合は、[-main](./main-compiler-option.md) コンパイラ オプションを使用して、**Main** メソッドを含めるクラスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d1a9b-114">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="d1a9b-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d1a9b-115">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d1a9b-116">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="d1a9b-117">**[出力の種類]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="d1a9b-118">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1a9b-119">例</span><span class="sxs-lookup"><span data-stu-id="d1a9b-119">Example</span></span>  

 <span data-ttu-id="d1a9b-120">次のコマンド ラインのいずれかで `in.cs` がコンパイルされ、`in.exe` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="d1a9b-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1a9b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1a9b-121">See also</span></span>

- [<span data-ttu-id="d1a9b-122">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="d1a9b-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="d1a9b-123">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="d1a9b-123">C# Compiler Options</span></span>](./index.md)
