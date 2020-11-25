---
title: ICLRTaskManager::GetCurrentTaskType メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 684b94471c53701c5ebe1dc7e7593eae16ad50fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728785"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="ae34c-102">ICLRTaskManager::GetCurrentTaskType メソッド</span><span class="sxs-lookup"><span data-stu-id="ae34c-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="ae34c-103">現在実行中のタスクの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="ae34c-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae34c-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae34c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae34c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae34c-105">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="ae34c-106">入出力現在実行中のタスクの種類を示す [Etasktype](etasktype-enumeration.md) 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae34c-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae34c-107">要件</span><span class="sxs-lookup"><span data-stu-id="ae34c-107">Requirements</span></span>  

 <span data-ttu-id="ae34c-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae34c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae34c-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ae34c-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae34c-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ae34c-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae34c-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae34c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae34c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae34c-112">See also</span></span>

- [<span data-ttu-id="ae34c-113">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae34c-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
