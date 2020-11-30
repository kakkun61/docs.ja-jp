---
description: -nowarn (C# コンパイラ オプション)
title: -nowarn (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194025"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="85338-103">-nowarn (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="85338-103">-nowarn (C# Compiler Options)</span></span>

<span data-ttu-id="85338-104">**-nowarn** オプションを使用すると、コンパイラから警告が出力されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="85338-104">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="85338-105">警告番号が複数ある場合は、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="85338-105">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85338-106">構文</span><span class="sxs-lookup"><span data-stu-id="85338-106">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="85338-107">引数</span><span class="sxs-lookup"><span data-stu-id="85338-107">Arguments</span></span>  

 <span data-ttu-id="85338-108">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="85338-108">`number1`, `number2`</span></span>  
 <span data-ttu-id="85338-109">コンパイラで表示しないようにする警告番号。</span><span class="sxs-lookup"><span data-stu-id="85338-109">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85338-110">注釈</span><span class="sxs-lookup"><span data-stu-id="85338-110">Remarks</span></span>  

 <span data-ttu-id="85338-111">警告 ID の数値だけを指定します。</span><span class="sxs-lookup"><span data-stu-id="85338-111">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="85338-112">たとえば、CS0028 を抑制する場合は、`-nowarn:28` と指定します。</span><span class="sxs-lookup"><span data-stu-id="85338-112">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="85338-113">`-nowarn` に渡された警告番号が以前のリリースでは有効であったが、今はコンパイラから削除されている場合、コンパイラはその番号を自動的に無視します。</span><span class="sxs-lookup"><span data-stu-id="85338-113">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="85338-114">たとえば、CS0679 は Visual Studio .NET 2002 のコンパイラでは有効でしたが、その後削除されました。</span><span class="sxs-lookup"><span data-stu-id="85338-114">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="85338-115">`-nowarn` オプションでは、次の警告は抑制されません。</span><span class="sxs-lookup"><span data-stu-id="85338-115">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="85338-116">コンパイラの警告 (レベル 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="85338-116">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="85338-117">コンパイラの警告 (レベル 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="85338-117">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="85338-118">コンパイラの警告 (レベル 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="85338-118">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="85338-119">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="85338-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="85338-120">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="85338-120">Open the **Properties** page for the project.</span></span> <span data-ttu-id="85338-121">詳細については、「[[ビルド] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85338-121">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="85338-122">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="85338-122">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="85338-123">[**警告の表示なし**] プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="85338-123">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="85338-124">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85338-124">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85338-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="85338-125">See also</span></span>

- [<span data-ttu-id="85338-126">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="85338-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="85338-127">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="85338-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="85338-128">C# コンパイラ エラー</span><span class="sxs-lookup"><span data-stu-id="85338-128">C# Compiler Errors</span></span>](../compiler-messages/index.md)
