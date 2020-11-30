---
description: -doc (C# コンパイラ オプション)
title: -doc (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: b1d7fbbe98aaad16454fdd71c161f2a17a2f4f2e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173257"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="18a31-103">-doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="18a31-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="18a31-104">**-doc** オプションを使用すると、XML ファイル内にドキュメント コメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="18a31-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18a31-105">構文</span><span class="sxs-lookup"><span data-stu-id="18a31-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="18a31-106">引数</span><span class="sxs-lookup"><span data-stu-id="18a31-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="18a31-107">XML の出力ファイル。コンパイルのソース コード ファイルのコメントが入力されます。</span><span class="sxs-lookup"><span data-stu-id="18a31-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18a31-108">注釈</span><span class="sxs-lookup"><span data-stu-id="18a31-108">Remarks</span></span>  

 <span data-ttu-id="18a31-109">ソース コード ファイルで、次の項目の前にあるドキュメント コメントを処理し、XML ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="18a31-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="18a31-110">[クラス](../keywords/class.md)、[デリゲート](../builtin-types/reference-types.md#the-delegate-type)、[インターフェイス](../keywords/interface.md)などのユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="18a31-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="18a31-111">フィールド、[イベント](../keywords/event.md)、[プロパティ](../../programming-guide/classes-and-structs/using-properties.md)、メソッドなどのメンバー</span><span class="sxs-lookup"><span data-stu-id="18a31-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="18a31-112">Main を含むソース コード ファイルが最初に XML に出力されます。</span><span class="sxs-lookup"><span data-stu-id="18a31-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="18a31-113">生成された .xml ファイルで [IntelliSense](/visualstudio/ide/using-intellisense) 機能を使用するには、サポートするアセンブリの名前と .xml ファイル名を同じにして、その .xml ファイルをアセンブリと同じディレクトリに置きます。</span><span class="sxs-lookup"><span data-stu-id="18a31-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="18a31-114">これで、アセンブリが Visual Studio プロジェクトで参照されると、.xml ファイルも同様に検出されます。</span><span class="sxs-lookup"><span data-stu-id="18a31-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="18a31-115">詳細については、[コード コメントの追加](/visualstudio/ide/reference/generate-xml-documentation-comments)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="18a31-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="18a31-116">[-target:module](./target-module-compiler-option.md) でコンパイルしない限り、`file` には \<assembly>\</assembly> タグが追加されます。これにより、コンパイルの出力ファイルのアセンブリ マニフェストを含むファイルの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="18a31-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18a31-117">-doc オプションは、すべての入力ファイル (プロジェクトの設定で設定された場合、そのプロジェクト内のすべてのファイル) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="18a31-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="18a31-118">特定のファイルまたはコードの特定のセクションについて、ドキュメントのコメントに関する警告を無効にするには、[#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="18a31-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="18a31-119">コードのコメントからドキュメントを生成する方法については、「[ドキュメント コメント用の推奨タグ](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18a31-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="18a31-120">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="18a31-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="18a31-121">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="18a31-121">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="18a31-122">**[ビルド]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18a31-122">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="18a31-123">**[XML ドキュメント ファイル]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="18a31-123">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="18a31-124">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18a31-124">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a31-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="18a31-125">See also</span></span>

- [<span data-ttu-id="18a31-126">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="18a31-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="18a31-127">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="18a31-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
