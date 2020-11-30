---
description: -resource (C# コンパイラ オプション)
title: -resource (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 6f90ce6c1590784cefbd5f15ca8a36941aad77ed
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193778"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="79cae-103">-resource (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="79cae-103">-resource (C# Compiler Options)</span></span>

<span data-ttu-id="79cae-104">指定されたリソースを出力ファイルに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="79cae-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79cae-105">構文</span><span class="sxs-lookup"><span data-stu-id="79cae-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="79cae-106">引数</span><span class="sxs-lookup"><span data-stu-id="79cae-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="79cae-107">出力ファイルに埋め込む .NET リソース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="79cae-107">The .NET resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="79cae-108">`identifier` (省略可)</span><span class="sxs-lookup"><span data-stu-id="79cae-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="79cae-109">リソースの論理名。リソースを読み込むために使われる名前です。</span><span class="sxs-lookup"><span data-stu-id="79cae-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="79cae-110">既定値はファイル名です。</span><span class="sxs-lookup"><span data-stu-id="79cae-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="79cae-111">`accessibility-modifier` (省略可)</span><span class="sxs-lookup"><span data-stu-id="79cae-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="79cae-112">リソースのアクセシビリティ。パブリックまたはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="79cae-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="79cae-113">既定値はパブリックです。</span><span class="sxs-lookup"><span data-stu-id="79cae-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79cae-114">注釈</span><span class="sxs-lookup"><span data-stu-id="79cae-114">Remarks</span></span>  

 <span data-ttu-id="79cae-115">[-linkresource](./linkresource-compiler-option.md) を使用すると、リソースがアセンブリにリンクされ、リソース ファイルは出力ファイルに追加されません。</span><span class="sxs-lookup"><span data-stu-id="79cae-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="79cae-116">既定では、リソースは、C# コンパイラを使用して作成されるときにアセンブリ内でパブリックになります。</span><span class="sxs-lookup"><span data-stu-id="79cae-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="79cae-117">リソースをプライベートにするには、アクセシビリティ修飾子として `private` を指定します。</span><span class="sxs-lookup"><span data-stu-id="79cae-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="79cae-118">`public` と `private` 以外のアクセシビリティは使用できません。</span><span class="sxs-lookup"><span data-stu-id="79cae-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="79cae-119">`filename` が、たとえば [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) によって作成されたり、開発環境で作成されたりした .NET リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使ってそのファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="79cae-119">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="79cae-120">詳細については、「<xref:System.Resources.ResourceManager?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79cae-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="79cae-121">それ以外のすべてのリソースに対しては、<xref:System.Reflection.Assembly> クラスの `GetManifestResource` メソッドを使用して、実行時にリソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="79cae-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="79cae-122">**-res** は **-resource** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="79cae-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="79cae-123">出力ファイルにおけるリソースの順序は、コマンド ラインでの指定順序に基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="79cae-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="79cae-124">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="79cae-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="79cae-125">プロジェクトにリソース ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="79cae-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="79cae-126">**ソリューション エクスプローラー** で、埋め込むファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="79cae-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="79cae-127">選択したファイルの **[プロパティ]** ウィンドウで、**[ビルド アクション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="79cae-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="79cae-128">**[ビルド アクション]** を **[埋め込まれたリソース]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="79cae-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="79cae-129">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.FileProperties2.BuildAction%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79cae-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79cae-130">例</span><span class="sxs-lookup"><span data-stu-id="79cae-130">Example</span></span>  

 <span data-ttu-id="79cae-131">`in.cs` をコンパイルし、リソース ファイル `rf.resource` をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="79cae-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="79cae-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="79cae-132">See also</span></span>

- [<span data-ttu-id="79cae-133">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="79cae-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="79cae-134">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="79cae-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
