---
title: overlappedFreeError MDA
description: .NET の overlappedFreeError マネージデバッグアシスタント (MDA) を確認します。これにより、アクセス違反またはガベージコレクトされたヒープの破損に対してアクティブ化される場合があります。
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 1bedb8ad3b9801f0d235371a397c8951ff8723b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254533"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="61694-103">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="61694-103">overlappedFreeError MDA</span></span>

<span data-ttu-id="61694-104">オーバーラップされた操作が完了する前に <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> メソッドが呼び出されると、`overlappedFreeError` マネージド デバッグ アシスタント (MDA) がアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="61694-104">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="61694-105">現象</span><span class="sxs-lookup"><span data-stu-id="61694-105">Symptoms</span></span>  

 <span data-ttu-id="61694-106">アクセス違反またはガベージ コレクションされたヒープの破損。</span><span class="sxs-lookup"><span data-stu-id="61694-106">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="61694-107">原因</span><span class="sxs-lookup"><span data-stu-id="61694-107">Cause</span></span>  

 <span data-ttu-id="61694-108">操作が完了する前に、オーバーラップされた構造が解放されました。</span><span class="sxs-lookup"><span data-stu-id="61694-108">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="61694-109">オーバーラップされたポインターを使用する関数は、解放された後に構造に書き込む可能性があります。</span><span class="sxs-lookup"><span data-stu-id="61694-109">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="61694-110">その場合、現時点で別のオブジェクトがその領域を占有していることによってヒープが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="61694-110">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="61694-111">オーバーラップされた操作が正常に起動しなかった場合、この MDA はエラーを発生しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="61694-111">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="61694-112">解像度</span><span class="sxs-lookup"><span data-stu-id="61694-112">Resolution</span></span>  

 <span data-ttu-id="61694-113"><xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> メソッドを呼び出す前に、オーバーラップされた構造を使用している I/O 操作が必ず完了するようにします。</span><span class="sxs-lookup"><span data-stu-id="61694-113">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="61694-114">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="61694-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="61694-115">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="61694-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="61694-116">出力</span><span class="sxs-lookup"><span data-stu-id="61694-116">Output</span></span>  

 <span data-ttu-id="61694-117">この MDA のサンプル出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="61694-117">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="61694-118">構成</span><span class="sxs-lookup"><span data-stu-id="61694-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61694-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="61694-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="61694-120">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="61694-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="61694-121">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="61694-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
