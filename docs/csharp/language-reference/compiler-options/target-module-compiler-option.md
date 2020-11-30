---
description: -target:module (C# コンパイラ オプション)
title: -target:module (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d8691e5e4477dbbe989344469b44382d5e0e7c8b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193609"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="ef523-103">-target:module (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="ef523-103">-target:module (C# Compiler Options)</span></span>

<span data-ttu-id="ef523-104">このオプションでは、コンパイラはアセンブリ マニフェストを生成しません。</span><span class="sxs-lookup"><span data-stu-id="ef523-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef523-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef523-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="ef523-106">解説</span><span class="sxs-lookup"><span data-stu-id="ef523-106">Remarks</span></span>  

 <span data-ttu-id="ef523-107">既定では、このオプションを使用してコンパイルすることによって作成された出力ファイルに、.netmodule という拡張子が付きます。</span><span class="sxs-lookup"><span data-stu-id="ef523-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="ef523-108">アセンブリ マニフェストのないファイルは、.NET ランタイムによって読み込むことができません。</span><span class="sxs-lookup"><span data-stu-id="ef523-108">A file that does not have an assembly manifest cannot be loaded by the .NET runtime.</span></span> <span data-ttu-id="ef523-109">ただし、このようなファイルは、[-addmodule](./addmodule-compiler-option.md) を使用して、アセンブリのアセンブリ マニフェストに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef523-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="ef523-110">複数のモジュールが 1 回のコンパイルで作成される場合、あるモジュールの [internal](../keywords/internal.md) 型をコンパイル中に別のモジュールで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ef523-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="ef523-111">あるモジュールのコードが別のモジュールの `internal` 型を参照する場合は、**-addmodule** を使用して、両方のモジュールをアセンブリ マニフェストに組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef523-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="ef523-112">Visual Studio 開発環境では、モジュールの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ef523-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="ef523-113">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef523-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef523-114">例</span><span class="sxs-lookup"><span data-stu-id="ef523-114">Example</span></span>  

 <span data-ttu-id="ef523-115">`in.cs` をコンパイルし、`in.netmodule` を作成するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ef523-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef523-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef523-116">See also</span></span>

- [<span data-ttu-id="ef523-117">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="ef523-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="ef523-118">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="ef523-118">C# Compiler Options</span></span>](./index.md)
