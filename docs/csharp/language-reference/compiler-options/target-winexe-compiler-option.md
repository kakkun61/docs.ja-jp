---
description: -target:winexe (C# コンパイラ オプション)
title: -target:winexe (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 6e14a2aac427c7adfd69f66eaf624816b75f6ea2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91168934"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="4a40e-103">-target:winexe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4a40e-103">-target:winexe (C# Compiler Options)</span></span>

<span data-ttu-id="4a40e-104">**-target:winexe** オプションを使用すると、実行可能な (EXE) Windows プログラムがコンパイラによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="4a40e-104">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a40e-105">構文</span><span class="sxs-lookup"><span data-stu-id="4a40e-105">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="4a40e-106">解説</span><span class="sxs-lookup"><span data-stu-id="4a40e-106">Remarks</span></span>  

 <span data-ttu-id="4a40e-107">実行可能ファイルは、.exe という拡張子で作成されます。</span><span class="sxs-lookup"><span data-stu-id="4a40e-107">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="4a40e-108">Windows プログラムは、.NET ライブラリまたは Windows API のユーザー インターフェイスを提供するプログラムです。</span><span class="sxs-lookup"><span data-stu-id="4a40e-108">A Windows program is one that provides a user interface from either the .NET library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="4a40e-109">コンソール アプリケーションを作成するには、[-target:exe](./target-exe-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="4a40e-109">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="4a40e-110">[-out](./out-compiler-option.md) オプションで指定しない限り、出力ファイル名は [Main](../../programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="4a40e-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="4a40e-111">コマンド ラインで指定すると、次の **-out** オプションまたは [-target](./target-compiler-option.md) オプションまでのすべてのファイルが、Windows プログラムの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4a40e-111">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="4a40e-112">**Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内で 1 つだけ必要になります。</span><span class="sxs-lookup"><span data-stu-id="4a40e-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="4a40e-113">コードに **Main** メソッドを含むクラスが複数ある場合は、[-main](./main-compiler-option.md) オプションを使用して、**Main** メソッドを含めるクラスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4a40e-113">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4a40e-114">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="4a40e-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="4a40e-115">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="4a40e-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="4a40e-116">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a40e-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="4a40e-117">**[出力の種類]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="4a40e-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="4a40e-118">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a40e-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a40e-119">例</span><span class="sxs-lookup"><span data-stu-id="4a40e-119">Example</span></span>  

 <span data-ttu-id="4a40e-120">`in.cs` をコンパイルし、Windows プログラムを生成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4a40e-120">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a40e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a40e-121">See also</span></span>

- [<span data-ttu-id="4a40e-122">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4a40e-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="4a40e-123">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="4a40e-123">C# Compiler Options</span></span>](./index.md)
