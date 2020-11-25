---
title: IHostTaskManager::GetStackGuarantee メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
ms.openlocfilehash: 718e6f3f19a5c368091c8a8aad3bd1f6598228df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727280"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="46f88-102">IHostTaskManager::GetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="46f88-102">IHostTaskManager::GetStackGuarantee Method</span></span>

<span data-ttu-id="46f88-103">スタック操作が完了した後、プロセスが終了する前に使用可能であることが保証されているスタック領域の量を取得します。</span><span class="sxs-lookup"><span data-stu-id="46f88-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f88-104">構文</span><span class="sxs-lookup"><span data-stu-id="46f88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46f88-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="46f88-105">Parameters</span></span>  

 `pGuarantee`  
 <span data-ttu-id="46f88-106">入出力使用可能なバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="46f88-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46f88-107">要件</span><span class="sxs-lookup"><span data-stu-id="46f88-107">Requirements</span></span>  

 <span data-ttu-id="46f88-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46f88-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46f88-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="46f88-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46f88-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="46f88-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46f88-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46f88-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f88-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="46f88-112">See also</span></span>

- [<span data-ttu-id="46f88-113">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="46f88-113">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
