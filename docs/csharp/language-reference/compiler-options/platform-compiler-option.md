---
description: -platform (C# コンパイラ オプション)
title: -platform (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 3fdb030dfc141b011f5faa827a4e4bb45ae38d19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "89466015"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="b9b13-103">-platform (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="b9b13-103">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="b9b13-104">アセンブリを実行できる共通言語ランタイム (CLR) のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9b13-104">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9b13-105">構文</span><span class="sxs-lookup"><span data-stu-id="b9b13-105">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="b9b13-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9b13-106">Parameters</span></span>

`string` \
<span data-ttu-id="b9b13-107">anycpu (既定値)、anycpu32bitpreferred、ARM、x64、x86、または Itanium。</span><span class="sxs-lookup"><span data-stu-id="b9b13-107">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9b13-108">注釈</span><span class="sxs-lookup"><span data-stu-id="b9b13-108">Remarks</span></span>

- <span data-ttu-id="b9b13-109">**anycpu** (既定) は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-109">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="b9b13-110">可能な場合は、アプリケーションを 64 ビット プロセスとして実行し、32 ビット モードしか使用できない場合は、32 ビットにフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-110">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="b9b13-111">**anycpu32bitpreferred** は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-111">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="b9b13-112">64 ビットと 32 ビットの両方のアプリケーションをサポートするシステムで、32 ビット モードでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="b9b13-112">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="b9b13-113">このオプションは、.NET Framework 4.5 以降を対象とするプロジェクトに対してのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="b9b13-113">You can specify this option only for projects that target .NET Framework 4.5 or later.</span></span>

- <span data-ttu-id="b9b13-114">**ARM** は、Advanced RISC Machine (ARM) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-114">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="b9b13-115">**ARM64** では、A64 命令セットをサポートする Advanced RISC Machine (ARM) プロセッサが搭載されたコンピューター上で 64 ビット CLR によって実行されるように、アセンブリがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="b9b13-115">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="b9b13-116">**x64** は AMD64 または EM64T 命令セットをサポートするコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-116">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="b9b13-117">**x86** は 32 ビット x86 互換 CLR で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-117">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="b9b13-118">**Itanium** は、Itanium プロセッサ搭載のコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-118">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="b9b13-119">64 ビット Windows オペレーティング システムの場合:</span><span class="sxs-lookup"><span data-stu-id="b9b13-119">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="b9b13-120">**-platform:x86** でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b9b13-120">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="b9b13-121">**-platform:anycpu** でコンパイルでされた DLL は、ロード先のプロセスと同じ CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b9b13-121">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="b9b13-122">**-platform:anycpu** でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b9b13-122">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="b9b13-123">**-platform:anycpu32bitpreferred** でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b9b13-123">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="b9b13-124">**anycpu32bitpreferred** 設定は、実行可能 (.EXE) ファイルに対してのみ有効であり、.NET Framework 4.5 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9b13-124">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires .NET Framework 4.5 or later.</span></span>

<span data-ttu-id="b9b13-125">Windows 64 ビット オペレーティング システムで実行するアプリケーションの開発に関する詳細は、「[64 ビット アプリケーション](../../../framework/64-bit-apps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b13-125">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b9b13-126">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="b9b13-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="b9b13-127">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9b13-127">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="b9b13-128">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-128">Click the **Build** property page.</span></span>

3. <span data-ttu-id="b9b13-129">**プラットフォーム ターゲット** プロパティを変更します。.NET Framework 4.5 以降を対象とするプロジェクトでは、 **[32 ビットを優先]** チェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="b9b13-129">Modify the **Platform target** property and, for projects that target .NET Framework 4.5 or later, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="b9b13-130">`-platform` は、Visual C# Express では開発環境で使用できません。</span><span class="sxs-lookup"><span data-stu-id="b9b13-130">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="b9b13-131">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b13-131">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="b9b13-132">例</span><span class="sxs-lookup"><span data-stu-id="b9b13-132">Example</span></span>

<span data-ttu-id="b9b13-133">次の例では、**-platform** オプションを使用して、Windows 64 ビット オペレーティング システムで 64 ビット CLR によりアプリケーションを実行することを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9b13-133">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="b9b13-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9b13-134">See also</span></span>

- [<span data-ttu-id="b9b13-135">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="b9b13-135">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="b9b13-136">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="b9b13-136">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
