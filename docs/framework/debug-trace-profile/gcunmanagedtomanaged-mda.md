---
title: gcUnmanagedToManaged MDA
description: .NET の gcManagedToUnmanaged マネージデバッグアシスタントを確認します。 この MDA は、マネージコードへの遷移中にガベージヒープが破損したことが原因でアクティブになる場合があります。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: 61fbdbf0d3941aa3e876748ae4d76cd7ad0c0977
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244224"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="a779a-104">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="a779a-104">gcUnmanagedToManaged MDA</span></span>

<span data-ttu-id="a779a-105">`gcUnmanagedToManaged` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、スレッドがアンマネージド コードからマネージド コードに遷移する時に、毎回ガベージ コレクションが行われるようにします。</span><span class="sxs-lookup"><span data-stu-id="a779a-105">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a779a-106">現象</span><span class="sxs-lookup"><span data-stu-id="a779a-106">Symptoms</span></span>  

 <span data-ttu-id="a779a-107">COM およびプラットフォーム呼び出しを使用してアンマネージ ユーザー コンポーネントを実行中のアプリケーションによって、CLR で非確定的なアクセス違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="a779a-107">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a779a-108">原因</span><span class="sxs-lookup"><span data-stu-id="a779a-108">Cause</span></span>  

 <span data-ttu-id="a779a-109">アプリケーションがアンマネージ ユーザー コンポーネントを実行中の場合、それらのコンポーネントによって、ガベージ コレクトされたヒープが破損された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a779a-109">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="a779a-110">これが原因で、ガベージ コレクターがオブジェクト グラフをウォークしようとしたときに、CLR でアクセス違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="a779a-110">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a779a-111">解像度</span><span class="sxs-lookup"><span data-stu-id="a779a-111">Resolution</span></span>  

 <span data-ttu-id="a779a-112">このアシスタントを有効にすると、各マネージド遷移の前にガベージ コレクションが必ず行われるようになるため、アンマネージド コンポーネントがガベージ コレクトされたヒープを破損してから、アクセス違反が発生するまでの時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="a779a-112">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a779a-113">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="a779a-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="a779a-114">スレッドがアンマネージド コードからマネージド コードに遷移する時に、毎回ガベージ コレクションが行われるようになります。</span><span class="sxs-lookup"><span data-stu-id="a779a-114">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a779a-115">出力</span><span class="sxs-lookup"><span data-stu-id="a779a-115">Output</span></span>  

 <span data-ttu-id="a779a-116">この MDA は、出力を生成しません。</span><span class="sxs-lookup"><span data-stu-id="a779a-116">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a779a-117">構成</span><span class="sxs-lookup"><span data-stu-id="a779a-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a779a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a779a-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a779a-119">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a779a-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a779a-120">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="a779a-120">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="a779a-121">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="a779a-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
