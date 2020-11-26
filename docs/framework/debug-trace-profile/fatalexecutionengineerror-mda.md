---
title: fatalExecutionEngineError MDA
description: .NET の fatalExecutionEngineError マネージデバッグアシスタント (MDA) を確認します。これは、予期しないプロセスの終了によってアクティブになる可能性があります。
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
ms.openlocfilehash: a9347338d53755b74b3ff291f75cb6b221134130
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244276"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="86afe-103">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="86afe-103">fatalExecutionEngineError MDA</span></span>

<span data-ttu-id="86afe-104">`fatalExecutionEngineError` マネージド デバッグ アシスタント (MDA) は、共通言語ランタイム (CLR) で致命的なエラーが検出されたときにアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="86afe-104">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="86afe-105">プロセスは終了されます。</span><span class="sxs-lookup"><span data-stu-id="86afe-105">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="86afe-106">現象</span><span class="sxs-lookup"><span data-stu-id="86afe-106">Symptoms</span></span>  

 <span data-ttu-id="86afe-107">予期せずにプロセスが終了します。</span><span class="sxs-lookup"><span data-stu-id="86afe-107">Unexpected process termination.</span></span> <span data-ttu-id="86afe-108">CLR エラーは、さまざまな理由により発生する可能性があるため、他の症状を特定できません。</span><span class="sxs-lookup"><span data-stu-id="86afe-108">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="86afe-109">原因</span><span class="sxs-lookup"><span data-stu-id="86afe-109">Cause</span></span>  

 <span data-ttu-id="86afe-110">CLR が致命的に破損しています。</span><span class="sxs-lookup"><span data-stu-id="86afe-110">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="86afe-111">これはほとんどの場合、データの破損により発生します。データの破損は、不正なプラットフォームの呼び出し関数への呼び出しや、CLR に無効なデータを渡すといった、多くの問題が原因で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86afe-111">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="86afe-112">解像度</span><span class="sxs-lookup"><span data-stu-id="86afe-112">Resolution</span></span>  

 <span data-ttu-id="86afe-113">追加の MDA を有効にすると、問題を特定するのに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="86afe-113">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="86afe-114">次の MDA は、問題を診断する際に特に有用です。</span><span class="sxs-lookup"><span data-stu-id="86afe-114">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="86afe-115">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="86afe-115">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="86afe-116">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="86afe-116">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="86afe-117">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="86afe-117">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="86afe-118">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="86afe-118">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="86afe-119">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="86afe-119">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="86afe-120">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="86afe-120">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="86afe-121">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="86afe-121">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="86afe-122">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="86afe-122">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="86afe-123">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="86afe-123">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="86afe-124">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="86afe-124">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="86afe-125">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="86afe-125">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="86afe-126">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="86afe-126">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="86afe-127">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="86afe-127">Effect on the Runtime</span></span>  

 <span data-ttu-id="86afe-128">この MDA は、ランタイムの動作への影響はありません。</span><span class="sxs-lookup"><span data-stu-id="86afe-128">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="86afe-129">出力</span><span class="sxs-lookup"><span data-stu-id="86afe-129">Output</span></span>  

 <span data-ttu-id="86afe-130">致命的なエラーの原因となった CLR 関数のアドレス、エラーが発生したスレッドの ID、およびエラー コード。</span><span class="sxs-lookup"><span data-stu-id="86afe-130">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="86afe-131">構成</span><span class="sxs-lookup"><span data-stu-id="86afe-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86afe-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="86afe-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="86afe-133">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="86afe-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
