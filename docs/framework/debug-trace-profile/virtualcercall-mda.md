---
title: virtualCERCall MDA
description: VirtualCERCall マネージデバッグアシスタント (MDA) を確認します。これは、CER に自動的に準備できない仮想メソッドの呼び出しが含まれている場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: c3e8060702239c6f87659f48658160e46491542f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257094"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="1a8c2-103">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="1a8c2-103">virtualCERCall MDA</span></span>

<span data-ttu-id="1a8c2-104">`virtualCERCall` マネージド デバッグ アシスタント (MDA) は、制約された実行領域 (CER) 呼び出し先の呼び出しサイトが、仮想ターゲット (つまり、インターフェイスを使用した最終ではない仮想メソッドまたは呼び出しの仮想呼び出し) を参照していることを示す警告としてアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-104">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="1a8c2-105">共通言語ランタイム (CLR) は、中間言語およびメタデータの分析だけでは、これらの呼び出しの呼び出し先メソッドを予測できません。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-105">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="1a8c2-106">その結果、CER グラフの一部としてコール ツリーを準備できません。また、そのサブツリー内のスレッドの中止を自動的にブロックできません。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-106">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="1a8c2-107">呼び出し対象の計算に必要な追加情報が実行時に判明すると、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> メソッドの明示的な呼び出しを使用して CER の拡張が必要な可能性がある場合に、この MDA は警告します。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-107">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1a8c2-108">現象</span><span class="sxs-lookup"><span data-stu-id="1a8c2-108">Symptoms</span></span>  

 <span data-ttu-id="1a8c2-109">スレッドが中止されたとき、またはアプリケーション ドメインがアンロードされたときに CER が実行されません。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-109">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1a8c2-110">原因</span><span class="sxs-lookup"><span data-stu-id="1a8c2-110">Cause</span></span>  

 <span data-ttu-id="1a8c2-111">CER に、自動的に準備できない仮想メソッドの呼び出しが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-111">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1a8c2-112">解像度</span><span class="sxs-lookup"><span data-stu-id="1a8c2-112">Resolution</span></span>  

 <span data-ttu-id="1a8c2-113">仮想メソッドの <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-113">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1a8c2-114">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="1a8c2-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="1a8c2-115">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="1a8c2-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1a8c2-116">出力</span><span class="sxs-lookup"><span data-stu-id="1a8c2-116">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="1a8c2-117">構成</span><span class="sxs-lookup"><span data-stu-id="1a8c2-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="1a8c2-118">例</span><span class="sxs-lookup"><span data-stu-id="1a8c2-118">Example</span></span>  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a8c2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a8c2-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1a8c2-120">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="1a8c2-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1a8c2-121">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="1a8c2-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
