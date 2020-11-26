---
title: jitCompilationStart マネージデバッグアシスタント (MDA)
description: JitCompilationStart managed デバッグアシスタント (MDA) は、just-in-time (JIT) コンパイラが .NET 関数のコンパイルを開始したときに報告します。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 228226d90e70d296681e48ffe85dada8eb18209a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247370"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="15fb5-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="15fb5-103">jitCompilationStart MDA</span></span>

<span data-ttu-id="15fb5-104">`jitCompilationStart` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) が起動すると、Just-In-Time (JIT) コンパイラが関数のコンパイルを開始した時刻が報告されます。</span><span class="sxs-lookup"><span data-stu-id="15fb5-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="15fb5-105">現象</span><span class="sxs-lookup"><span data-stu-id="15fb5-105">Symptoms</span></span>  

 <span data-ttu-id="15fb5-106">mscorjit.dll がプロセスに読み込まれるため、既にネイティブイメージ形式のプログラムでワーキングセットサイズが増加します。</span><span class="sxs-lookup"><span data-stu-id="15fb5-106">The working set size increases for a program that's already in native image format, because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="15fb5-107">原因</span><span class="sxs-lookup"><span data-stu-id="15fb5-107">Cause</span></span>  

<span data-ttu-id="15fb5-108">プログラムが依存しているアセンブリがネイティブ形式で生成されていないか、アセンブリが正しく登録されていません。</span><span class="sxs-lookup"><span data-stu-id="15fb5-108">Not all the assemblies the program depends on have been generated into native format, or an assembly is not registered correctly.</span></span>  

## <a name="resolution"></a><span data-ttu-id="15fb5-109">解像度</span><span class="sxs-lookup"><span data-stu-id="15fb5-109">Resolution</span></span>  

 <span data-ttu-id="15fb5-110">この MDA を有効にすると、どの関数が JIT コンパイルされているかを識別できます。</span><span class="sxs-lookup"><span data-stu-id="15fb5-110">Enabling this MDA allows you to identify which function is being JIT-compiled.</span></span> <span data-ttu-id="15fb5-111">関数を含むアセンブリが、ネイティブ形式に生成され、適切に登録されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="15fb5-111">Make sure that the assembly that contains the function is generated to native format and properly registered.</span></span>
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="15fb5-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="15fb5-112">Effect on the runtime</span></span>  

 <span data-ttu-id="15fb5-113">この MDA は、メソッドが JIT コンパイルされる前にメッセージをログに記録します。そのため、この MDA を有効にすると、パフォーマンスに大きな影響が出ます。</span><span class="sxs-lookup"><span data-stu-id="15fb5-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="15fb5-114">メソッドがインラインである場合、この MDA は別のメッセージを生成しません。</span><span class="sxs-lookup"><span data-stu-id="15fb5-114">If a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="15fb5-115">出力</span><span class="sxs-lookup"><span data-stu-id="15fb5-115">Output</span></span>  

 <span data-ttu-id="15fb5-116">次のコード サンプルでは、サンプル出力を確認できます。</span><span class="sxs-lookup"><span data-stu-id="15fb5-116">The following code sample shows sample output.</span></span> <span data-ttu-id="15fb5-117">この場合、出力には、アセンブリテストで、クラス "ns2.CO" のメソッド "m" が JIT でコンパイルされたことが示されています。</span><span class="sxs-lookup"><span data-stu-id="15fb5-117">In this case, the output shows that, in assembly Test, the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="15fb5-118">構成</span><span class="sxs-lookup"><span data-stu-id="15fb5-118">Configuration</span></span>  

 <span data-ttu-id="15fb5-119">次の構成ファイルでは、最初に JIT コンパイルされたときに報告されるメソッドを絞り込むためのさまざまなフィルターを確認できます。</span><span class="sxs-lookup"><span data-stu-id="15fb5-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="15fb5-120">Name 属性の値をに設定することによって、すべてのメソッドを報告するように指定でき \* ます。</span><span class="sxs-lookup"><span data-stu-id="15fb5-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="15fb5-121">例</span><span class="sxs-lookup"><span data-stu-id="15fb5-121">Example</span></span>  

 <span data-ttu-id="15fb5-122">次のコード サンプルは、先の構成ファイルとの併用を意図しています。</span><span class="sxs-lookup"><span data-stu-id="15fb5-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="15fb5-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="15fb5-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="15fb5-124">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="15fb5-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="15fb5-125">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="15fb5-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
