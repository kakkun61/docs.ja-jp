---
title: ICorDebugDataTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 14f0b247ded363dedce193886aab50538db3e6a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683681"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="f3005-102">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3005-102">ICorDebugDataTarget Interface</span></span>

<span data-ttu-id="f3005-103">特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f3005-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3005-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f3005-104">Methods</span></span>  
  
|<span data-ttu-id="f3005-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f3005-105">Method</span></span>|<span data-ttu-id="f3005-106">説明</span><span class="sxs-lookup"><span data-stu-id="f3005-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3005-107">GetPlatform メソッド</span><span class="sxs-lookup"><span data-stu-id="f3005-107">GetPlatform Method</span></span>](icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="f3005-108">ターゲットプロセスが実行されているプラットフォーム (プロセッサアーキテクチャやオペレーティングシステムなど) に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3005-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="f3005-109">ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="f3005-109">ReadVirtual Method</span></span>](icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="f3005-110">指定したアドレスを開始位置として連続したメモリのブロックを取得し、指定したバッファー内でそれを返します。</span><span class="sxs-lookup"><span data-stu-id="f3005-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="f3005-111">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="f3005-111">GetThreadContext Method</span></span>](icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="f3005-112">指定されたスレッドの現在のスレッドコンテキストを要求します。</span><span class="sxs-lookup"><span data-stu-id="f3005-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3005-113">注釈</span><span class="sxs-lookup"><span data-stu-id="f3005-113">Remarks</span></span>  

 <span data-ttu-id="f3005-114">`ICorDebugDataTarget` およびそのメソッドの特性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f3005-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="f3005-115">デバッグサービスは、このインターフェイスのメソッドを呼び出して、ターゲットプロセス内のメモリおよびその他のデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f3005-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="f3005-116">デバッガークライアントは、特定のターゲット (ライブプロセスやメモリダンプなど) に適した方法でこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3005-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="f3005-117">`ICorDebugDataTarget`メソッドを呼び出すことができるのは、他のインターフェイスで実装されているメソッド内からだけ `ICorDebug*` です。</span><span class="sxs-lookup"><span data-stu-id="f3005-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="f3005-118">これにより、デバッガークライアントは、呼び出されるスレッドとそのタイミングを制御できます。</span><span class="sxs-lookup"><span data-stu-id="f3005-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="f3005-119">実装では `ICorDebugDataTarget` 、常にターゲットに関する最新の情報を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3005-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="f3005-120">ターゲットプロセスは、 `ICorDebug*` インターフェイス (およびメソッド) が呼び出されている間は停止し、変更されないようにする必要があり `ICorDebugDataTarget` ます。</span><span class="sxs-lookup"><span data-stu-id="f3005-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="f3005-121">ターゲットがライブプロセスであり、その状態が変更された場合、 [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) メソッドを再度呼び出して、置換されたののインスタンスを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3005-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3005-122">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f3005-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3005-123">要件</span><span class="sxs-lookup"><span data-stu-id="f3005-123">Requirements</span></span>  

 <span data-ttu-id="f3005-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3005-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3005-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3005-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3005-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3005-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3005-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3005-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3005-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3005-128">See also</span></span>

- [<span data-ttu-id="f3005-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3005-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f3005-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f3005-130">Debugging</span></span>](index.md)
