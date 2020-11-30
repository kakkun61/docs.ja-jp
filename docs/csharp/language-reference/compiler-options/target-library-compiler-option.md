---
description: -target:library (C# コンパイラ オプション)
title: -target:library (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0f5b1e1bec8fd601bf111e1c2c64adf22d0a064e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193726"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="8fc78-103">-target:library (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="8fc78-103">-target:library (C# Compiler Options)</span></span>

<span data-ttu-id="8fc78-104">**-target:library** オプションを指定した場合、コンパイラは実行可能ファイル (EXE) ではなく、ダイナミック リンク ライブラリ (DLL) を作成します。</span><span class="sxs-lookup"><span data-stu-id="8fc78-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc78-105">構文</span><span class="sxs-lookup"><span data-stu-id="8fc78-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="8fc78-106">解説</span><span class="sxs-lookup"><span data-stu-id="8fc78-106">Remarks</span></span>  

 <span data-ttu-id="8fc78-107">.dll 拡張子の DLL が作成されます。</span><span class="sxs-lookup"><span data-stu-id="8fc78-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="8fc78-108">[-out](./out-compiler-option.md) オプションを特に指定しない限り、出力ファイル名は最初の入力ファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="8fc78-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="8fc78-109">コマンド ラインで指定すると、次の **-out** または **-target:module** オプションまでのすべてのファイルが .dll ファイルを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8fc78-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="8fc78-110">.dll ファイルを作成する際に、[Main](../../programming-guide/main-and-command-args/index.md)メソッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8fc78-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8fc78-111">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="8fc78-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="8fc78-112">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="8fc78-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="8fc78-113">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fc78-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="8fc78-114">**[出力の種類]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="8fc78-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="8fc78-115">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fc78-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc78-116">例</span><span class="sxs-lookup"><span data-stu-id="8fc78-116">Example</span></span>  

 <span data-ttu-id="8fc78-117">`in.cs` をコンパイルし、`in.dll` を作成するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="8fc78-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fc78-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fc78-118">See also</span></span>

- [<span data-ttu-id="8fc78-119">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="8fc78-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="8fc78-120">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="8fc78-120">C# Compiler Options</span></span>](./index.md)
