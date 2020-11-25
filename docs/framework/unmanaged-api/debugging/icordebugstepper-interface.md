---
title: ICorDebugStepper インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: 8b5bbb65034e5b715532397c9ecc650da9aee912
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718294"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="5955a-102">ICorDebugStepper インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5955a-102">ICorDebugStepper Interface</span></span>

<span data-ttu-id="5955a-103">デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="5955a-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5955a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-104">Methods</span></span>  
  
|<span data-ttu-id="5955a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-105">Method</span></span>|<span data-ttu-id="5955a-106">説明</span><span class="sxs-lookup"><span data-stu-id="5955a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5955a-107">Deactivate メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-107">Deactivate Method</span></span>](icordebugstepper-deactivate-method.md)|<span data-ttu-id="5955a-108">これにより、 `ICorDebugStepper` 受信した最後のステップコマンドがキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="5955a-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="5955a-109">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-109">IsActive Method</span></span>](icordebugstepper-isactive-method.md)|<span data-ttu-id="5955a-110">この `ICorDebugStepper` が現在ステップを実行しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="5955a-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="5955a-111">SetInterceptMask メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-111">SetInterceptMask Method</span></span>](icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="5955a-112">ステップインするコードの種類を指定する CorDebugIntercept 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5955a-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="5955a-113">SetRangeIL メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-113">SetRangeIL Method</span></span>](icordebugstepper-setrangeil-method.md)|<span data-ttu-id="5955a-114">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md)を呼び出すかどうかを示す値を設定します。これは、ネイティブコードまたはステップスルー中のメソッドの Microsoft 中間言語 (MSIL) コードを基準として、引数の値を渡します。</span><span class="sxs-lookup"><span data-stu-id="5955a-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="5955a-115">SetUnmappedStopMask メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-115">SetUnmappedStopMask Method</span></span>](icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="5955a-116">実行が停止するマップされていないコードの種類を指定する CorDebugUnmappedStop 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5955a-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="5955a-117">Step メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-117">Step Method</span></span>](icordebugstepper-step-method.md)|<span data-ttu-id="5955a-118">これにより、このが格納している `ICorDebugStepper` スレッドを1ステップずつ実行します。また、必要に応じて、スレッド内で呼び出される関数を使用したシングルステップ実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="5955a-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="5955a-119">StepOut メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-119">StepOut Method</span></span>](icordebugstepper-stepout-method.md)|<span data-ttu-id="5955a-120">これにより、この `ICorDebugStepper` が格納しているスレッドを1ステップずつ実行し、現在のフレームが呼び出し元のフレームに制御を返すときに完了します。</span><span class="sxs-lookup"><span data-stu-id="5955a-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="5955a-121">StepRange メソッド</span><span class="sxs-lookup"><span data-stu-id="5955a-121">StepRange Method</span></span>](icordebugstepper-steprange-method.md)|<span data-ttu-id="5955a-122">これにより、このが `ICorDebugStepper` 格納しているスレッドを1ステップずつ実行し、指定した範囲の最後のコードに到達したときにを返します。</span><span class="sxs-lookup"><span data-stu-id="5955a-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5955a-123">注釈</span><span class="sxs-lookup"><span data-stu-id="5955a-123">Remarks</span></span>  

 <span data-ttu-id="5955a-124">この `ICorDebugStepper` インターフェイスは、次の目的で機能します。</span><span class="sxs-lookup"><span data-stu-id="5955a-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="5955a-125">発行されたステップコマンドとそのコマンドの完了の間の識別子として機能します。</span><span class="sxs-lookup"><span data-stu-id="5955a-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="5955a-126">これは、実行可能なすべてのステップをカプセル化するための中心的なインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5955a-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="5955a-127">これにより、ステップ実行操作を途中で取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="5955a-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="5955a-128">スレッドごとに複数のステッパが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5955a-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="5955a-129">たとえば、関数をステップオーバーしている間にブレークポイントがヒットし、ユーザーがその関数内で新しいステップ実行操作を開始する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5955a-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="5955a-130">この状況をどのように処理するかは、デバッガーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="5955a-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="5955a-131">デバッガーでは、元のステップ実行操作をキャンセルするか、2つの操作を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5955a-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="5955a-132">インターフェイスでは、 `ICorDebugStepper` 両方の選択肢がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5955a-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="5955a-133">共通言語ランタイム (CLR) がクロススレッドでマーシャリングされた呼び出しを行う場合、ステッパはスレッド間で移行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5955a-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5955a-134">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5955a-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5955a-135">要件</span><span class="sxs-lookup"><span data-stu-id="5955a-135">Requirements</span></span>  

 <span data-ttu-id="5955a-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5955a-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5955a-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5955a-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5955a-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5955a-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5955a-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5955a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5955a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="5955a-140">See also</span></span>

- [<span data-ttu-id="5955a-141">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5955a-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
