---
description: -define (C# コンパイラ オプション)
title: -define (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 74c9a23cd1b3a691063c2976a593c9b3a63ca618
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173270"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="92044-103">-define (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="92044-103">-define (C# Compiler Options)</span></span>

<span data-ttu-id="92044-104">**-define** オプションは、`name` をプログラムのすべてのソース コード ファイル内のシンボルとして定義します。</span><span class="sxs-lookup"><span data-stu-id="92044-104">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92044-105">構文</span><span class="sxs-lookup"><span data-stu-id="92044-105">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="92044-106">引数</span><span class="sxs-lookup"><span data-stu-id="92044-106">Arguments</span></span>  

 <span data-ttu-id="92044-107">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="92044-107">`name`, `name2`</span></span>  
 <span data-ttu-id="92044-108">定義する 1 つまたは複数のシンボルの名前。</span><span class="sxs-lookup"><span data-stu-id="92044-108">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92044-109">注釈</span><span class="sxs-lookup"><span data-stu-id="92044-109">Remarks</span></span>  

 <span data-ttu-id="92044-110">**-define** オプションには、[#define](../preprocessor-directives/preprocessor-define.md) プリプロセッサ ディレクティブを使うのと同じ効果があります。ただし、コンパイラ オプションはプロジェクト内のすべてのファイルに対して有効である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="92044-110">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="92044-111">ソース ファイルの [#undef](../preprocessor-directives/preprocessor-undef.md) ディレクティブがこの定義を削除するまで、シンボルはソース ファイルで定義されたままになります。</span><span class="sxs-lookup"><span data-stu-id="92044-111">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="92044-112">-define オプションを使うと、あるファイルで指定されている `#undef` ディレクティブは、プロジェクト内の他のソース コード ファイルには影響しません。</span><span class="sxs-lookup"><span data-stu-id="92044-112">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="92044-113">このオプションで作成されるシンボルを [#if](../preprocessor-directives/preprocessor-if.md)、[#else](../preprocessor-directives/preprocessor-else.md)、[#elif](../preprocessor-directives/preprocessor-elif.md)、および [#endif](../preprocessor-directives/preprocessor-endif.md) で使う、ソース ファイルを条件付きでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="92044-113">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="92044-114">**-d** は **-define** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="92044-114">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="92044-115">**-define** では、シンボル名をセミコロンまたはコンマで区切ることにより、複数のシンボルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="92044-115">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="92044-116">たとえば、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="92044-116">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="92044-117">C# コンパイラ自体では、ソース コードで使うことができるシンボルやマクロは定義されません。すべてのシンボル定義はユーザーが定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92044-117">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92044-118">C++ などの言語とは異なり、C# の `#define` では、シンボルに値を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="92044-118">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="92044-119">たとえば、マクロの作成や定数の定義に `#define` を使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="92044-119">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="92044-120">定数を定義する必要がある場合は、`enum` 変数を使います。</span><span class="sxs-lookup"><span data-stu-id="92044-120">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="92044-121">C++ スタイルのマクロを作成する場合は、ジェネリックなどで代用してください。</span><span class="sxs-lookup"><span data-stu-id="92044-121">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="92044-122">マクロはエラーを招きやすいため、C# では、マクロの使用は禁止され、代わりに、より安全な方法が提供されています。</span><span class="sxs-lookup"><span data-stu-id="92044-122">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="92044-123">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="92044-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="92044-124">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="92044-124">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="92044-125">**[ビルド]** タブで、**[条件付きコンパイル シンボル]** ボックスに、定義するシンボルを入力します。</span><span class="sxs-lookup"><span data-stu-id="92044-125">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="92044-126">たとえば、次のコード例を使っている場合は、テキスト ボックスに「`xx`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="92044-126">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="92044-127">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92044-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92044-128">例</span><span class="sxs-lookup"><span data-stu-id="92044-128">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="92044-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="92044-129">See also</span></span>

- [<span data-ttu-id="92044-130">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="92044-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="92044-131">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="92044-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
