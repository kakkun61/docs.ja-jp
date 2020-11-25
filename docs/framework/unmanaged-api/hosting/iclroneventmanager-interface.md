---
title: ICLROnEventManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 1948075d87b5a44397a1eaab3adb4edbc96d7143
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725635"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="a81fa-102">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a81fa-102">ICLROnEventManager Interface</span></span>

<span data-ttu-id="a81fa-103">ホストが共通言語ランタイム (CLR) イベントのコールバックを登録および登録解除できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a81fa-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a81fa-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a81fa-104">Methods</span></span>  
  
|<span data-ttu-id="a81fa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a81fa-105">Method</span></span>|<span data-ttu-id="a81fa-106">説明</span><span class="sxs-lookup"><span data-stu-id="a81fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a81fa-107">RegisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="a81fa-107">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="a81fa-108">指定されたイベントのコールバックポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="a81fa-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="a81fa-109">UnregisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="a81fa-109">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="a81fa-110">指定されたイベントに対して、以前に登録されたコールバックポインターの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="a81fa-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a81fa-111">注釈</span><span class="sxs-lookup"><span data-stu-id="a81fa-111">Remarks</span></span>  

 <span data-ttu-id="a81fa-112">イベントコールバックの登録と登録解除を行うために、ホストは `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) メソッドを呼び出すことによってへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="a81fa-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a81fa-113">[Eclrevent](eclrevent-enumeration.md)によって説明されているイベントは、異なるスレッドから、または CLR のアンロードまたは無効化を通知するために、複数回発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a81fa-113">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a81fa-114">要件</span><span class="sxs-lookup"><span data-stu-id="a81fa-114">Requirements</span></span>  

 <span data-ttu-id="a81fa-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a81fa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a81fa-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a81fa-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a81fa-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a81fa-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a81fa-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a81fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a81fa-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a81fa-119">See also</span></span>

- [<span data-ttu-id="a81fa-120">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="a81fa-120">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="a81fa-121">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a81fa-121">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="a81fa-122">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a81fa-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a81fa-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a81fa-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
