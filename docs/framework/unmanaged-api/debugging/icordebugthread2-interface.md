---
title: ICorDebugThread2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: fd4ad536d7d3df2b8f91f206459122cf083c8b9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691137"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="6bc53-102">ICorDebugThread2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bc53-102">ICorDebugThread2 Interface</span></span>

<span data-ttu-id="6bc53-103">は、"、" スレッドインターフェイスの論理的な拡張として機能します。</span><span class="sxs-lookup"><span data-stu-id="6bc53-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bc53-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc53-104">Methods</span></span>  
  
|<span data-ttu-id="6bc53-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc53-105">Method</span></span>|<span data-ttu-id="6bc53-106">説明</span><span class="sxs-lookup"><span data-stu-id="6bc53-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bc53-107">GetActiveFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc53-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="6bc53-108">スレッドのフレーム内のアクティブな関数に関するデータを格納している COR_ACTIVE_FUNCTION インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="6bc53-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="6bc53-109">GetConnectionID メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc53-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="6bc53-110">このの接続識別子を取得し `ICorDebugThread2` ます。</span><span class="sxs-lookup"><span data-stu-id="6bc53-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="6bc53-111">GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc53-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="6bc53-112">こののタスク識別子を取得し `ICorDebugThread2` ます。</span><span class="sxs-lookup"><span data-stu-id="6bc53-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="6bc53-113">GetVolatileOSThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc53-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="6bc53-114">こののオペレーティングシステムスレッド識別子を取得し `ICorDebugThread2` ます。</span><span class="sxs-lookup"><span data-stu-id="6bc53-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="6bc53-115">InterceptCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc53-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="6bc53-116">デバッガーがスレッドの現在の例外をインターセプトできるようにします。</span><span class="sxs-lookup"><span data-stu-id="6bc53-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bc53-117">注釈</span><span class="sxs-lookup"><span data-stu-id="6bc53-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bc53-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6bc53-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bc53-119">要件</span><span class="sxs-lookup"><span data-stu-id="6bc53-119">Requirements</span></span>  

 <span data-ttu-id="6bc53-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bc53-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bc53-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bc53-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bc53-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bc53-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bc53-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bc53-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc53-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bc53-124">See also</span></span>

- [<span data-ttu-id="6bc53-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bc53-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
