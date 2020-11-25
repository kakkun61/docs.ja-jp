---
title: IManagedObject::GetObjectIdentity メソッド
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
ms.openlocfilehash: fc74b84bccceb1772bf3642e51ec88c562ce5dce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730716"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="1b24d-102">IManagedObject::GetObjectIdentity メソッド</span><span class="sxs-lookup"><span data-stu-id="1b24d-102">IManagedObject::GetObjectIdentity Method</span></span>

<span data-ttu-id="1b24d-103">このマネージオブジェクトの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b24d-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b24d-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b24d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b24d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b24d-105">Parameters</span></span>  

 `pBSTRGUID`  
 <span data-ttu-id="1b24d-106">入出力オブジェクトが存在するプロセスの GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b24d-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="1b24d-107">入出力オブジェクトのアプリケーションドメインの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b24d-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="1b24d-108">入出力COM クラシック v テーブル内のオブジェクトのインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b24d-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b24d-109">注釈</span><span class="sxs-lookup"><span data-stu-id="1b24d-109">Remarks</span></span>  

 <span data-ttu-id="1b24d-110">マネージオブジェクトの id には、プロセス GUID、アプリケーションドメイン ID、および COM クラシック v テーブルのオブジェクトのインデックスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b24d-111">要件</span><span class="sxs-lookup"><span data-stu-id="1b24d-111">Requirements</span></span>  

 <span data-ttu-id="1b24d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b24d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b24d-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1b24d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b24d-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1b24d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b24d-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b24d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b24d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b24d-116">See also</span></span>

- [<span data-ttu-id="1b24d-117">IManagedObject インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b24d-117">IManagedObject Interface</span></span>](imanagedobject-interface.md)
