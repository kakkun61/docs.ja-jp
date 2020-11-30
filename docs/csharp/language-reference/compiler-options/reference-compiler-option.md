---
description: -reference (C# コンパイラ オプション)
title: -reference (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: cd7346ae4094a84a398306394f771e040dd7b72f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193791"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="4bed0-103">-reference (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4bed0-103">-reference (C# Compiler Options)</span></span>

<span data-ttu-id="4bed0-104">**-reference** オプションを指定すると、コンパイラは指定されたファイルの [public](../keywords/public.md) 型の情報を現在のプロジェクトにインポートし、指定されたアセンブリ ファイルからメタデータを参照できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4bed0-104">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bed0-105">構文</span><span class="sxs-lookup"><span data-stu-id="4bed0-105">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="4bed0-106">引数</span><span class="sxs-lookup"><span data-stu-id="4bed0-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="4bed0-107">アセンブリ マニフェストを含むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="4bed0-107">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="4bed0-108">複数のファイルをインポートするには、ファイルごとに個別に **-reference** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bed0-108">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="4bed0-109">アセンブリ内のすべての名前空間を格納するルート名前空間を表す有効な C# 識別子。</span><span class="sxs-lookup"><span data-stu-id="4bed0-109">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bed0-110">注釈</span><span class="sxs-lookup"><span data-stu-id="4bed0-110">Remarks</span></span>  

 <span data-ttu-id="4bed0-111">複数のファイルからインポートするには、ファイルごとに **-reference** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bed0-111">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="4bed0-112">インポートするファイルは、マニフェストが含まれている必要があります。出力ファイルは、[-target:module](./target-module-compiler-option.md) 以外のいずれかの [-target](./target-compiler-option.md) オプションでコンパイルされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bed0-112">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4bed0-113">**-r** は **-reference** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="4bed0-113">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="4bed0-114">アセンブリ マニフェストを含まない出力ファイルからメタデータをインポートするには、[-addmodule](./addmodule-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="4bed0-114">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="4bed0-115">あるアセンブリ (アセンブリ A) を参照していて、そのアセンブリが別のアセンブリ (アセンブリ B) を参照している場合は、以下の条件が当てはまる場合はアセンブリ B を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bed0-115">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="4bed0-116">アセンブリ A から使う型がアセンブリ B の型から継承されているか、アセンブリ B からインターフェイスを実装している。</span><span class="sxs-lookup"><span data-stu-id="4bed0-116">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="4bed0-117">アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="4bed0-117">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="4bed0-118">アセンブリ参照が存在するディレクトリを指定するには、[-lib](./lib-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="4bed0-118">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="4bed0-119">**-lib** のトピックでは、コンパイラがアセンブリを検索するディレクトリについても説明されています。</span><span class="sxs-lookup"><span data-stu-id="4bed0-119">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="4bed0-120">モジュールではなくアセンブリ内の型をコンパイラで認識するには、型の解決を強制する必要があります。そのためには、型のインスタンスを定義します。</span><span class="sxs-lookup"><span data-stu-id="4bed0-120">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="4bed0-121">アセンブリの型名を解決する方法は他にもあります。たとえば、アセンブリの型を継承すると、コンパイラで型名が認識されます。</span><span class="sxs-lookup"><span data-stu-id="4bed0-121">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="4bed0-122">1 つのアセンブリ内から、同じコンポーネントの 2 つの異なるバージョンを参照することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4bed0-122">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="4bed0-123">そのためには、ファイルごとに **-reference** スイッチの alias サブオブションを使って、2 つのファイルを区別します。</span><span class="sxs-lookup"><span data-stu-id="4bed0-123">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="4bed0-124">この別名は、コンポーネント名の修飾子として使われ、いずれかのファイルのコンポーネントに解決されます。</span><span class="sxs-lookup"><span data-stu-id="4bed0-124">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="4bed0-125">既定では、よく使われる .NET Framework アセンブリを参照する csc 応答 (.rsp) ファイルが使われます。</span><span class="sxs-lookup"><span data-stu-id="4bed0-125">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="4bed0-126">コンパイラが csc.rsp を使わないようにする場合は、[-noconfig](./noconfig-compiler-option.md) を指定します。</span><span class="sxs-lookup"><span data-stu-id="4bed0-126">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bed0-127">Visual Studio では、**[参照の追加]** ダイアログ ボックスを使います。</span><span class="sxs-lookup"><span data-stu-id="4bed0-127">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="4bed0-128">詳細については、「[方法: 参照マネージャーを使用して参照を追加または削除する](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bed0-128">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="4bed0-129">`-reference` を使った場合と **[参照の追加]** ダイアログ ボックスを使った場合で、参照の追加の動作が同じになるようにするには、追加するアセンブリの **[相互運用型の埋め込み]** プロパティを **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="4bed0-129">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="4bed0-130">このプロパティの既定値は **[True]** です。</span><span class="sxs-lookup"><span data-stu-id="4bed0-130">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bed0-131">例</span><span class="sxs-lookup"><span data-stu-id="4bed0-131">Example</span></span>  

 <span data-ttu-id="4bed0-132">この例では、[extern alias](../keywords/extern-alias.md) 機能を使う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4bed0-132">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="4bed0-133">ソース ファイルをコンパイルし、`grid.dll` と `grid20.dll` からメタデータをインポートします。これらは事前にコンパイルしておきます。</span><span class="sxs-lookup"><span data-stu-id="4bed0-133">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="4bed0-134">2 つの DLL には同じコンポーネントの異なるバージョンが含まれており、ソース ファイルをコンパイルするには 2 つの **-reference** と別名オプションを使います。</span><span class="sxs-lookup"><span data-stu-id="4bed0-134">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="4bed0-135">オプションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4bed0-135">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="4bed0-136">これは、外部別名 `GridV1` と `GridV2` を設定します。プログラムではこれらを `extern` ステートメントで使います。</span><span class="sxs-lookup"><span data-stu-id="4bed0-136">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="4bed0-137">このようにすると、コントロール名にプレフィックス `GridV1` を付けることで、`grid.dll` のグリッド コントロールを参照できます。次に示すのはその例です。</span><span class="sxs-lookup"><span data-stu-id="4bed0-137">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="4bed0-138">さらに、コントロール名にプレフィックス `GridV2` を付けることで、`grid20.dll` のグリッド コントロールを参照できます。次に示すのはその例です。</span><span class="sxs-lookup"><span data-stu-id="4bed0-138">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="4bed0-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bed0-139">See also</span></span>

- [<span data-ttu-id="4bed0-140">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="4bed0-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4bed0-141">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="4bed0-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
