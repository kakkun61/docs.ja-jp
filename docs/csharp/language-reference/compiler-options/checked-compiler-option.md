---
description: -checked (C# コンパイラ オプション)
title: -checked (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: c92ad61b2f482631230e0e6aeb0af5716a4fcb61
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91196833"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="273e6-103">-checked (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="273e6-103">-checked (C# Compiler Options)</span></span>

<span data-ttu-id="273e6-104">**-checked** オプションは、データ型の範囲外の値になる整数の算術ステートメントと、[checked](../keywords/checked.md) または [unchecked](../keywords/unchecked.md) キーワードのスコープ内に含まれない整数の算術ステートメントで、ランタイム例外が発生するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="273e6-104">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="273e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="273e6-105">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="273e6-106">解説</span><span class="sxs-lookup"><span data-stu-id="273e6-106">Remarks</span></span>  

 <span data-ttu-id="273e6-107">`checked` または `unchecked` キーワードのスコープ内に含まれる整数の算術ステートメントは、**-checked** オプションの作用の対象になりません。</span><span class="sxs-lookup"><span data-stu-id="273e6-107">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="273e6-108">`checked` または `unchecked` キーワードのスコープ内に含まれない整数の算術ステートメントがデータ型の範囲外の値になり、**-checked+** (または **-checked**) がコンパイル時に使用されている場合は、そのステートメントでランタイム例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="273e6-108">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="273e6-109">**-checked-** がコンパイル時に使用された場合、そのステートメントでランタイム例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="273e6-109">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="273e6-110">このオプションの既定値は **-checked-** です。オーバーフロー チェックは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="273e6-110">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="273e6-111">場合によっては、大規模アプリケーションの構築に使用される自動化ツールによって -checked が + に設定されます。</span><span class="sxs-lookup"><span data-stu-id="273e6-111">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="273e6-112">-checked- を使用する場合のシナリオの 1 つは、-checked- を指定してツールのグローバルな既定値をオーバーライドすることです。</span><span class="sxs-lookup"><span data-stu-id="273e6-112">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="273e6-113">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="273e6-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="273e6-114">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="273e6-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="273e6-115">詳細については、「[Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」([ビルド] ページ (プロジェクト デザイナー) (C#)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="273e6-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="273e6-116">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="273e6-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="273e6-117">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="273e6-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="273e6-118">**[演算のオーバーフローのチェック]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="273e6-118">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="273e6-119">プログラムによってこのコンパイラ オプションにアクセスする方法については、<xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A> に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="273e6-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="273e6-120">例</span><span class="sxs-lookup"><span data-stu-id="273e6-120">Example</span></span>  

 <span data-ttu-id="273e6-121">次のコマンドは `t2.cs` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="273e6-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="273e6-122">コマンドで使用されている `-checked` は、ファイル内の整数の算術ステートメントのうち、`checked` または `unchecked` キーワードのスコープ内に含まれず、データ型の範囲外の値になるステートメントで、ランタイム例外が発生することを指定します。</span><span class="sxs-lookup"><span data-stu-id="273e6-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="273e6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="273e6-123">See also</span></span>

- [<span data-ttu-id="273e6-124">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="273e6-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="273e6-125">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="273e6-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
