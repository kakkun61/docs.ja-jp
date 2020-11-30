---
description: -moduleassemblyname (C# コンパイラ オプション)
title: -moduleassemblyname (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9131db17d767c76fe6a57f5d5353474153e0c269
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194090"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="d0ce0-103">-moduleassemblyname (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="d0ce0-103">-moduleassemblyname (C# Compiler Option)</span></span>

<span data-ttu-id="d0ce0-104">.netmodule がアクセスできる非パブリック型のアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-104">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ce0-105">構文</span><span class="sxs-lookup"><span data-stu-id="d0ce0-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="d0ce0-106">引数</span><span class="sxs-lookup"><span data-stu-id="d0ce0-106">Arguments</span></span>  

 `assembly_name`  
 <span data-ttu-id="d0ce0-107">.netmodule がアクセスできる非パブリック型のアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-107">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0ce0-108">注釈</span><span class="sxs-lookup"><span data-stu-id="d0ce0-108">Remarks</span></span>  

 <span data-ttu-id="d0ce0-109">**-moduleassemblyname** は、.netmodule をビルドする場合と、次の条件に当てはまる場合に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-109">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="d0ce0-110">.netmodule で、既存のアセンブリ内の非パブリック型へのアクセスが必要な場合。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-110">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="d0ce0-111">.netmodule をビルドするアセンブリの名前を把握していること。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-111">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="d0ce0-112">既存のアセンブリに、.netmodule をビルドするアセンブリへのフレンド アセンブリのアクセス権が付与されていること。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-112">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="d0ce0-113">.netmodule のビルドの詳細については、「[-target:module (C# コンパイラ オプション)](./target-module-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-113">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="d0ce0-114">フレンド アセンブリの詳細については、「[フレンド アセンブリ](../../../standard/assembly/friend.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-114">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="d0ce0-115">このオプションは、開発環境からは利用できません。これはコマンドラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-115">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="d0ce0-116">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-116">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ce0-117">例</span><span class="sxs-lookup"><span data-stu-id="d0ce0-117">Example</span></span>  

 <span data-ttu-id="d0ce0-118">このサンプルは、csman_an_assembly というアセンブリへのフレンド アセンブリのアクセス権を付与する、プライベート型のアセンブリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-118">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class
{  
    public void Test()
    {
        Console.WriteLine("An_Internal_Class.Test called");
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="d0ce0-119">例</span><span class="sxs-lookup"><span data-stu-id="d0ce0-119">Example</span></span>  

 <span data-ttu-id="d0ce0-120">このサンプルは、アセンブリ moduleassemblyname_1.dll 内の非パブリック型にアクセスする .netmodule をビルドします。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-120">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="d0ce0-121">この .netmodule が csman_an_assembly というアセンブリにビルドされることがわかっていれば、 **-moduleassemblyname** を指定して、csman_an_assembly へのフレンド アセンブリのアクセス権が付与されているアセンブリ内の非パブリック型へのアクセスを .netmodule に許可することができます。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-121">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="d0ce0-122">例</span><span class="sxs-lookup"><span data-stu-id="d0ce0-122">Example</span></span>  

 <span data-ttu-id="d0ce0-123">このコード サンプルは、既にビルドされたアセンブリと .netmodule を参照する、アセンブリ csman_an_assembly をビルドします。</span><span class="sxs-lookup"><span data-stu-id="d0ce0-123">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="d0ce0-124">**An_Internal_Class.Test called**</span><span class="sxs-lookup"><span data-stu-id="d0ce0-124">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="d0ce0-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0ce0-125">See also</span></span>

- [<span data-ttu-id="d0ce0-126">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="d0ce0-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d0ce0-127">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="d0ce0-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
