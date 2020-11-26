---
title: loadFromContext MDA
description: .NET の loadFromContext マネージデバッグアシスタント (MDA) について説明します。これは、アセンブリが LoadFrom コンテキストに読み込まれた場合にアクティブ化されます。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 631939b38ace4d26d0deb5b104cc5de0df3d9f3a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247357"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="2d801-103">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="2d801-103">loadFromContext MDA</span></span>

<span data-ttu-id="2d801-104">アセンブリが `LoadFrom` コンテキストに読み込まれると、`loadFromContext` マネージド デバッグ アシスタント (MDA) がアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="2d801-104">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="2d801-105">このような状況は、<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> または他の同様のメソッドを呼び出した結果として発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d801-105">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2d801-106">現象</span><span class="sxs-lookup"><span data-stu-id="2d801-106">Symptoms</span></span>  

 <span data-ttu-id="2d801-107">一部のローダー メソッドは、使用すると、`LoadFrom` コンテキストでアセンブリが呼び出される結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d801-107">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="2d801-108">このコンテキストを使用すると、シリアル化、キャスティング、依存関係の解決について予期しない結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d801-108">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="2d801-109">一般的に、このような問題を回避するために、アセンブリを `Load` コンテキストに読み込むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2d801-109">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="2d801-110">この MDA を使用せずに、アセンブリが読み込まれたコンテキストを判断することは困難です。</span><span class="sxs-lookup"><span data-stu-id="2d801-110">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2d801-111">原因</span><span class="sxs-lookup"><span data-stu-id="2d801-111">Cause</span></span>  

 <span data-ttu-id="2d801-112">一般的に、アセンブリは `Load` コンテキスト以外のパス (グローバル アセンブリ キャッシュや <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> プロパティなど) から読み込まれた場合、`LoadFrom` コンテキストに読み込まれていました。</span><span class="sxs-lookup"><span data-stu-id="2d801-112">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2d801-113">解像度</span><span class="sxs-lookup"><span data-stu-id="2d801-113">Resolution</span></span>  

 <span data-ttu-id="2d801-114"><xref:System.Reflection.Assembly.LoadFrom%2A> の呼び出しが不要になるようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="2d801-114">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="2d801-115">そのためには、次の手法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d801-115">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="2d801-116">グローバル アセンブリ キャッシュにアセンブリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2d801-116">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="2d801-117">アセンブリを <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="2d801-117">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="2d801-118">既定のドメインの場合、<xref:System.AppDomainSetup.ApplicationBase%2A> ディレクトリは、プロセスを開始した実行可能ファイルを含むディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="2d801-118">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="2d801-119">また、アセンブリを移動したくない場合は、必要に応じて新しい <xref:System.AppDomain> を作成します。</span><span class="sxs-lookup"><span data-stu-id="2d801-119">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="2d801-120">依存するアセンブリが、実行可能ファイルの相対的な子ディレクトリ内にある場合、アプリケーション構成 (.config) ファイルまたはセカンダリ アプリケーション ドメインのプローブ パスを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d801-120">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="2d801-121">いずれの場合でも、<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドを使用するようにコードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2d801-121">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2d801-122">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="2d801-122">Effect on the Runtime</span></span>  

 <span data-ttu-id="2d801-123">MDA は、CLR にまったく影響がありません。</span><span class="sxs-lookup"><span data-stu-id="2d801-123">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="2d801-124">MDA では、読み込み要求の結果として使用されたコンテキストが報告されます。</span><span class="sxs-lookup"><span data-stu-id="2d801-124">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2d801-125">出力</span><span class="sxs-lookup"><span data-stu-id="2d801-125">Output</span></span>  

 <span data-ttu-id="2d801-126">MDA では、アセンブリが `LoadFrom` コンテキストに読み込まれたことが報告されます。</span><span class="sxs-lookup"><span data-stu-id="2d801-126">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="2d801-127">また、アセンブリの簡易名とパスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="2d801-127">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="2d801-128">`LoadFrom` コンテキストの使用を回避する軽減策も提案されます。</span><span class="sxs-lookup"><span data-stu-id="2d801-128">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2d801-129">構成</span><span class="sxs-lookup"><span data-stu-id="2d801-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2d801-130">例</span><span class="sxs-lookup"><span data-stu-id="2d801-130">Example</span></span>  

 <span data-ttu-id="2d801-131">次のコードの例は、この MDA がアクティブ化されることのある状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="2d801-131">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is
            // located outside of the Load context probing path.
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d801-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d801-132">See also</span></span>

- [<span data-ttu-id="2d801-133">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="2d801-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
