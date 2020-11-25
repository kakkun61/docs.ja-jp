---
title: ICorConfiguration::SetGCHostControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 4824fcfc53bae6c81760a23f76e83fb8ae7efd79
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715811"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="96f59-102">ICorConfiguration::SetGCHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="96f59-102">ICorConfiguration::SetGCHostControl Method</span></span>

<span data-ttu-id="96f59-103">仮想メモリの制限を変更するようにホストに要求するために、ガベージコレクターによって使用されるコールバックインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="96f59-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f59-104">構文</span><span class="sxs-lookup"><span data-stu-id="96f59-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96f59-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96f59-105">Parameters</span></span>  

 `pGCHostControl`  
 <span data-ttu-id="96f59-106">からガベージコレクターが仮想メモリの制限を変更するようにホストに要求できるようにする、 [igている Stcontrol](igchostcontrol-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="96f59-106">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96f59-107">要件</span><span class="sxs-lookup"><span data-stu-id="96f59-107">Requirements</span></span>  

 <span data-ttu-id="96f59-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96f59-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96f59-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="96f59-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96f59-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="96f59-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96f59-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96f59-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f59-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="96f59-112">See also</span></span>

- [<span data-ttu-id="96f59-113">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96f59-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
