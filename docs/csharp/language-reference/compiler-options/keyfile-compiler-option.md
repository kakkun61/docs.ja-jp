---
description: -keyfile (C# コンパイラ オプション)
title: -keyfile (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 5af40da18895d47933cb809d710e31a40f14513b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91152430"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="f82d3-103">-keyfile (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="f82d3-103">-keyfile (C# Compiler Options)</span></span>

<span data-ttu-id="f82d3-104">暗号化キーを格納するファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f82d3-104">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82d3-105">構文</span><span class="sxs-lookup"><span data-stu-id="f82d3-105">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f82d3-106">引数</span><span class="sxs-lookup"><span data-stu-id="f82d3-106">Arguments</span></span>  
  
|<span data-ttu-id="f82d3-107">期間</span><span class="sxs-lookup"><span data-stu-id="f82d3-107">Term</span></span>|<span data-ttu-id="f82d3-108">定義</span><span class="sxs-lookup"><span data-stu-id="f82d3-108">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="f82d3-109">厳密な名前のキーを格納するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="f82d3-109">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f82d3-110">注釈</span><span class="sxs-lookup"><span data-stu-id="f82d3-110">Remarks</span></span>  

 <span data-ttu-id="f82d3-111">このオプションを指定すると、コンパイラは、指定したファイルからアセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。</span><span class="sxs-lookup"><span data-stu-id="f82d3-111">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="f82d3-112">キー ファイルを生成するには、コマンド ラインで「sn -k `file`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f82d3-112">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="f82d3-113">**-target:module** を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、[-addmodule](./addmodule-compiler-option.md) でアセンブリをコンパイルすると作成されるアセンブリに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f82d3-113">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="f82d3-114">また、暗号化情報を [-keycontainer](./keycontainer-compiler-option.md) でコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f82d3-114">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="f82d3-115">部分的に署名されたアセンブリを作成する場合は、[-delaysign](./delaysign-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="f82d3-115">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="f82d3-116">同じコンパイルで (コマンド ライン オプションまたはカスタム属性によって) -keyfile と -keycontainer を両方とも指定すると、コンパイラは最初にキー コンテナーを試します。</span><span class="sxs-lookup"><span data-stu-id="f82d3-116">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="f82d3-117">それが成功すると、アセンブリはキー コンテナーの情報で署名されます。</span><span class="sxs-lookup"><span data-stu-id="f82d3-117">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="f82d3-118">キー コンテナーが見つからない場合、コンパイラは -keyfile で指定されたファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="f82d3-118">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="f82d3-119">ファイルが検出された場合、アセンブリはキー ファイルの情報で署名され、キー情報はキー コンテナーにインストールされるため (sn -i と同様)、次のコンパイル時にはキー コンテナーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="f82d3-119">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="f82d3-120">キー ファイルには公開キーだけが含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f82d3-120">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="f82d3-121">詳しくは、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」および「[アセンブリへの遅延署名](../../../standard/assembly/delay-sign.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f82d3-121">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f82d3-122">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="f82d3-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f82d3-123">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="f82d3-123">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="f82d3-124">**[署名]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f82d3-124">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="f82d3-125">**[厳密な名前のキー ファイルを選択してください]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="f82d3-125">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="f82d3-126">このコンパイラ オプションには、プログラムで <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> を使ってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f82d3-126">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82d3-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="f82d3-127">See also</span></span>

- [<span data-ttu-id="f82d3-128">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="f82d3-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f82d3-129">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="f82d3-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
