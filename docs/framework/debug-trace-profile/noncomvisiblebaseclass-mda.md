---
title: nonComVisibleBaseClass MDA
description: COR_E_INVALIDOPERATION で失敗したネイティブコードからの QueryInterface 呼び出しに対して呼び出される、nonComVisibleBaseClass managed デバッグアシスタント (MDA) を参照してください。
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
ms.openlocfilehash: c13d05d04c75d6b4f1be4a5f338fd7246fed8db4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254572"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="e25b8-103">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="e25b8-103">nonComVisibleBaseClass MDA</span></span>

<span data-ttu-id="e25b8-104">`nonComVisibleBaseClass` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、COM 参照可能ではない基本クラスから派生した COM 参照可能マネージド クラスの COM 呼び出し可能ラッパー (CCW: COM Callable Wrapper) で、ネイティブ コードまたはアンマネージド コードによって `QueryInterface` 呼び出しがなされるとアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="e25b8-104">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="e25b8-105">`QueryInterface` 呼び出しによって MDA がアクティブになるのは、COM 参照可能マネージド クラスのクラス インターフェイスまたは既定の `IDispatch` が呼び出しによって要求された場合のみです。</span><span class="sxs-lookup"><span data-stu-id="e25b8-105">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="e25b8-106">`QueryInterface` 呼び出しが、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性が適用され、COM 参照可能クラスによって明示的に実装された明示的なインターフェイスに対する呼び出しである場合、この MDA はアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="e25b8-106">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e25b8-107">現象</span><span class="sxs-lookup"><span data-stu-id="e25b8-107">Symptoms</span></span>  

 <span data-ttu-id="e25b8-108">ネイティブ コードからなされた `QueryInterface` 呼び出しが COR_E_INVALIDOPERATION HRESULT により失敗します。</span><span class="sxs-lookup"><span data-stu-id="e25b8-108">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="e25b8-109">HRESULT は、この MDA をアクティブにする `QueryInterface` 呼び出しをランタイムが許可しないことによって発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="e25b8-109">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e25b8-110">原因</span><span class="sxs-lookup"><span data-stu-id="e25b8-110">Cause</span></span>  

 <span data-ttu-id="e25b8-111">ランタイムは、COM 参照可能ではないクラスから派生した COM 参照可能クラスのクラス インターフェイスまたは既定の `IDispatch` インターフェイスに対する `QueryInterface` 呼び出しを許可できません。これは、バージョン管理に関係する問題が発生する可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="e25b8-111">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="e25b8-112">たとえば、COM 参照可能でない基本クラスにパブリック メンバーを追加した場合、基本クラス メンバーを含む派生クラスの vtable がこの変更によって変更されるため、派生クラスを使用する既存の COM クライアントが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e25b8-112">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="e25b8-113">COM に公開されている明示的なインターフェイスの場合は、インターフェイスの基本メンバーが vtable に含まれないため、この問題は発生しません。</span><span class="sxs-lookup"><span data-stu-id="e25b8-113">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e25b8-114">解像度</span><span class="sxs-lookup"><span data-stu-id="e25b8-114">Resolution</span></span>  

 <span data-ttu-id="e25b8-115">クラス インターフェイスを公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="e25b8-115">Do not expose the class interface.</span></span> <span data-ttu-id="e25b8-116">明示的なインターフェイスを定義し、それに <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="e25b8-116">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e25b8-117">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="e25b8-117">Effect on the Runtime</span></span>  

 <span data-ttu-id="e25b8-118">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="e25b8-118">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e25b8-119">出力</span><span class="sxs-lookup"><span data-stu-id="e25b8-119">Output</span></span>  

 <span data-ttu-id="e25b8-120">非 COM 参照可能クラス `Base` から派生した COM 参照可能クラス `Derived` で `QueryInterface` 呼び出しを実行した場合のメッセージ例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e25b8-120">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a><span data-ttu-id="e25b8-121">構成</span><span class="sxs-lookup"><span data-stu-id="e25b8-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e25b8-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e25b8-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e25b8-123">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="e25b8-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e25b8-124">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="e25b8-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
