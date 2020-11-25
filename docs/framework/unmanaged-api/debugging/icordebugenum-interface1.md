---
title: ICorDebugEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: b208444de3b427329988f27b9d252b54143b7240
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698794"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="7c458-102">ICorDebugEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c458-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="7c458-103">デバッグアプリケーションで使用される列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="7c458-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c458-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c458-104">Methods</span></span>  
  
|<span data-ttu-id="7c458-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c458-105">Method</span></span>|<span data-ttu-id="7c458-106">説明</span><span class="sxs-lookup"><span data-stu-id="7c458-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c458-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="7c458-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="7c458-108">この `ICorDebugEnum` オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7c458-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="7c458-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="7c458-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="7c458-110">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c458-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="7c458-111">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="7c458-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="7c458-112">カーソルを列挙体の先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="7c458-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="7c458-113">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="7c458-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="7c458-114">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="7c458-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c458-115">注釈</span><span class="sxs-lookup"><span data-stu-id="7c458-115">Remarks</span></span>  

 <span data-ttu-id="7c458-116">次の列挙子は、から派生し `ICorDebugEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="7c458-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="7c458-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="7c458-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="7c458-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="7c458-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="7c458-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="7c458-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="7c458-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="7c458-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="7c458-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="7c458-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="7c458-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="7c458-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="7c458-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="7c458-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="7c458-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="7c458-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="7c458-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="7c458-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="7c458-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="7c458-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="7c458-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="7c458-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="7c458-138">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7c458-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c458-139">要件</span><span class="sxs-lookup"><span data-stu-id="7c458-139">Requirements</span></span>  

 <span data-ttu-id="7c458-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c458-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c458-141">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c458-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c458-142">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c458-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c458-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c458-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c458-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c458-144">See also</span></span>

- [<span data-ttu-id="7c458-145">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c458-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
