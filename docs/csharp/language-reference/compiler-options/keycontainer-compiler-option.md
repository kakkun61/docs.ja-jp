---
description: -keycontainer (C# コンパイラ オプション)
title: -keycontainer (C# コンパイラ オプション)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 93ee5cd755a4fd6918d2a5825b63151a201a8f6a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91152469"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="46f79-103">-keycontainer (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="46f79-103">-keycontainer (C# Compiler Options)</span></span>

<span data-ttu-id="46f79-104">暗号化キー コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="46f79-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f79-105">構文</span><span class="sxs-lookup"><span data-stu-id="46f79-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="46f79-106">引数</span><span class="sxs-lookup"><span data-stu-id="46f79-106">Arguments</span></span>  

 `string`  
 <span data-ttu-id="46f79-107">厳密な名前のキー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="46f79-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46f79-108">注釈</span><span class="sxs-lookup"><span data-stu-id="46f79-108">Remarks</span></span>  

 <span data-ttu-id="46f79-109">**-keycontainer** オプションを使うと、コンパイラは共有可能なコンポーネントを作成します。</span><span class="sxs-lookup"><span data-stu-id="46f79-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="46f79-110">コンパイラは、指定されたコンテナーからアセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。</span><span class="sxs-lookup"><span data-stu-id="46f79-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="46f79-111">キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="46f79-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="46f79-112">`sn -i` は、キー ペアをコンテナーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="46f79-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="46f79-113">コンパイラが CoreCLR 上で実行するときは、このオプションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="46f79-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="46f79-114">CoreCLR 上でビルドするときにアセンブリに署名するには、[-keyfile](keyfile-compiler-option.md) オプションを使います。</span><span class="sxs-lookup"><span data-stu-id="46f79-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="46f79-115">[-target:module](./target-module-compiler-option.md) を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、このモジュールを [-addmodule](./addmodule-compiler-option.md) でアセンブリにコンパイルするときに、アセンブリに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="46f79-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="46f79-116">このオプションは、任意の Microsoft Intermediate Language (MSIL) モジュールのソース コードで、カスタム属性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="46f79-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="46f79-117">また、暗号化情報を [-keyfile](./keyfile-compiler-option.md) でコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="46f79-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="46f79-118">公開キーをアセンブリ マニフェストに追加してだけおき、アセンブリの署名はテスト後まで待って行いたい場合は、[-delaysign](./delaysign-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="46f79-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="46f79-119">詳しくは、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」および「[アセンブリへの遅延署名](../../../standard/assembly/delay-sign.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46f79-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="46f79-120">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="46f79-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="46f79-121">このコンパイラ オプションは、Visual Studio 開発環境では使うことができません。</span><span class="sxs-lookup"><span data-stu-id="46f79-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="46f79-122">このコンパイラ オプションには、プログラムで <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> を使ってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="46f79-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f79-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="46f79-123">See also</span></span>

- [<span data-ttu-id="46f79-124">C# コンパイラの -keyfile オプション</span><span class="sxs-lookup"><span data-stu-id="46f79-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="46f79-125">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="46f79-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="46f79-126">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="46f79-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
