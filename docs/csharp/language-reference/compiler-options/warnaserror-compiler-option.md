---
description: -warnaserror (C# コンパイラ オプション)
title: -warnaserror (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 9c3b307668968865b401aedc04c79f95d4f32513
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171339"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="61628-103">-warnaserror (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="61628-103">-warnaserror (C# Compiler Options)</span></span>

<span data-ttu-id="61628-104">**-warnaserror+** オプションは、すべての警告をエラーとして扱います</span><span class="sxs-lookup"><span data-stu-id="61628-104">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61628-105">構文</span><span class="sxs-lookup"><span data-stu-id="61628-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="61628-106">解説</span><span class="sxs-lookup"><span data-stu-id="61628-106">Remarks</span></span>  

 <span data-ttu-id="61628-107">通常は警告として報告されるすべてのメッセージが、代わりにエラーとして報告され、ビルド プロセスが停止します (出力ファイルはビルドされません)。</span><span class="sxs-lookup"><span data-stu-id="61628-107">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="61628-108">既定では、**-warnaserror-** が有効になっているため、警告により出力ファイルの生成が妨げられることはありません。</span><span class="sxs-lookup"><span data-stu-id="61628-108">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="61628-109">**-warnaserror** は **-warnaserror+** と同じで、警告がエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="61628-109">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="61628-110">必要に応じて、いくつかの特定の警告のみをエラーとして扱う場合は、エラーとして扱う警告番号のコンマ区切りのリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="61628-110">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="61628-111">**nullable** 短縮形を使用して、Null 値が許容されるすべての警告のセットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="61628-111">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="61628-112">コンパイラで表示する警告のレベルを指定するには、[-warn](./warn-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="61628-112">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="61628-113">特定の警告を無効にするには、[-nowarn](./nowarn-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="61628-113">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="61628-114">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="61628-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="61628-115">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="61628-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="61628-116">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61628-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="61628-117">**警告をエラーとして扱う** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="61628-117">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="61628-118">このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61628-118">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61628-119">例</span><span class="sxs-lookup"><span data-stu-id="61628-119">Example</span></span>  

 <span data-ttu-id="61628-120">`in.cs` をコンパイルして、コンパイラで警告を表示させないようにします。</span><span class="sxs-lookup"><span data-stu-id="61628-120">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="61628-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="61628-121">See also</span></span>

- [<span data-ttu-id="61628-122">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="61628-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="61628-123">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="61628-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
