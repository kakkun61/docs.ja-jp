---
title: 共通言語ランタイムでの型の転送
description: 型の転送を使用すると、別の .NET アセンブリに型を移動する際に、元のアセンブリを使用するアプリケーションを再コンパイルする必要がありません。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687673"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="7d874-103">共通言語ランタイムでの型の転送</span><span class="sxs-lookup"><span data-stu-id="7d874-103">Type forwarding in the common language runtime</span></span>

<span data-ttu-id="7d874-104">型の転送を使用すると、別のアセンブリに型を移動する際に、元のアセンブリを使用するアプリケーションを再コンパイルする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="7d874-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="7d874-105">たとえば、 *Utility.dll* というアセンブリ内の `Example` クラスをアプリケーションが使用しているとします。</span><span class="sxs-lookup"><span data-stu-id="7d874-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="7d874-106">その場合、 *Utility.dll* の開発者がアセンブリをリファクタリングすることになった際には、その過程で `Example` クラスが別のアセンブリに移動される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d874-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="7d874-107">*Utility.dll* の旧バージョンが *Utility.dll* の新バージョンとそのコンパニオン アセンブリに置き換えられると、`Example` クラスを使用するアプリケーションは、新しいバージョンの *Utility.dll* で `Example` クラスを見つけられないために失敗します。</span><span class="sxs-lookup"><span data-stu-id="7d874-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="7d874-108">*Utility.dll* の開発者は、<xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 属性を使用して、`Example` クラスの要求を転送することで、この問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="7d874-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="7d874-109">この属性が新バージョンの *Utility.dll* に適用されている場合、`Example` クラスに対する要求は、現在このクラスを含んでいるアセンブリに転送されます。</span><span class="sxs-lookup"><span data-stu-id="7d874-109">If the attribute has been applied to the new version of *Utility.dll* , requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="7d874-110">既存のアプリケーションは、再コンパイルを必要とすることなく正常に機能し続けます。</span><span class="sxs-lookup"><span data-stu-id="7d874-110">The existing application continues to function normally, without recompilation.</span></span>

## <a name="forward-a-type"></a><span data-ttu-id="7d874-111">型の転送</span><span class="sxs-lookup"><span data-stu-id="7d874-111">Forward a type</span></span>

 <span data-ttu-id="7d874-112">型の転送は 4 つの手順で行います。</span><span class="sxs-lookup"><span data-stu-id="7d874-112">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="7d874-113">型のソース コードを、元のアセンブリから転送先のアセンブリに移動します。</span><span class="sxs-lookup"><span data-stu-id="7d874-113">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="7d874-114">配置に使用される型のアセンブリで、移動された型の <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> を追加します。</span><span class="sxs-lookup"><span data-stu-id="7d874-114">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="7d874-115">次のコードは、移動された `Example` という型の属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="7d874-115">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="7d874-116">型の現在の場所であるアセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7d874-116">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="7d874-117">型の現在の場所であるアセンブリへの参照を指定して、型の元の場所であるアセンブリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7d874-117">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="7d874-118">たとえば、C# ファイルをコマンド ラインからコンパイルする場合は、[-reference (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) オプションを使用して、型の現在の場所であるアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7d874-118">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="7d874-119">C++ では、ソース ファイルで [#using](/cpp/preprocessor/hash-using-directive-cpp) ディレクティブを使用して、型の現在の場所であるアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="7d874-119">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d874-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d874-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="7d874-121">型の転送 (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="7d874-121">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="7d874-122">#using ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="7d874-122">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
