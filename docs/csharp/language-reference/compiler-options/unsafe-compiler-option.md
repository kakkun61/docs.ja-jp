---
description: -unsafe (C# コンパイラ オプション)
title: -unsafe (C# コンパイラ オプション)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "89140842"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="d0d73-103">-unsafe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="d0d73-103">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="d0d73-104">**-unsafe** コンパイラ オプションは、[unsafe](../keywords/unsafe.md) キーワードを使用するコードをコンパイルできるようにします。</span><span class="sxs-lookup"><span data-stu-id="d0d73-104">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d73-105">構文</span><span class="sxs-lookup"><span data-stu-id="d0d73-105">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="d0d73-106">解説</span><span class="sxs-lookup"><span data-stu-id="d0d73-106">Remarks</span></span>

<span data-ttu-id="d0d73-107">アンセーフ コードの詳細については、「[アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0d73-107">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d0d73-108">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="d0d73-108">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d0d73-109">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0d73-109">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d0d73-110">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0d73-110">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="d0d73-111">**[アンセーフ コードの許可]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d0d73-111">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="d0d73-112">このオプションを csproj ファイルに追加するには</span><span class="sxs-lookup"><span data-stu-id="d0d73-112">To add this option in a csproj file</span></span>

<span data-ttu-id="d0d73-113">プロジェクトの .csproj ファイルを開き、次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="d0d73-113">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="d0d73-114">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0d73-114">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0d73-115">例</span><span class="sxs-lookup"><span data-stu-id="d0d73-115">Example</span></span>

<span data-ttu-id="d0d73-116">unsafe モードで `in.cs` をコンパイルする場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0d73-116">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0d73-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0d73-117">See also</span></span>

- [<span data-ttu-id="d0d73-118">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="d0d73-118">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="d0d73-119">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="d0d73-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
