---
title: IActionOnCLREvent インターフェイス
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 8ca4bb1fe35451f95f752a4e71f5f0b541b55e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721778"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="455c6-102">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="455c6-102">IActionOnCLREvent Interface</span></span>

<span data-ttu-id="455c6-103">[Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md)メソッドを提供します。このメソッドは、 [ICLROnEventManager:: registeractiononevent](iclroneventmanager-registeractiononevent-method.md)メソッドの呼び出しを使用して登録されたイベントに対してコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="455c6-103">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="455c6-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="455c6-104">Methods</span></span>  
  
|<span data-ttu-id="455c6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="455c6-105">Method</span></span>|<span data-ttu-id="455c6-106">説明</span><span class="sxs-lookup"><span data-stu-id="455c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="455c6-107">OnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="455c6-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="455c6-108">登録されているイベントに対してコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="455c6-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="455c6-109">要件</span><span class="sxs-lookup"><span data-stu-id="455c6-109">Requirements</span></span>  

 <span data-ttu-id="455c6-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="455c6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="455c6-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="455c6-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="455c6-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="455c6-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="455c6-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="455c6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="455c6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="455c6-114">See also</span></span>

- [<span data-ttu-id="455c6-115">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="455c6-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="455c6-116">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="455c6-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="455c6-117">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="455c6-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="455c6-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="455c6-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
