---
title: IAssemblyName::Clone メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
ms.openlocfilehash: ca528bdbd9662db373d1beeece803d6c43728f2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698612"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="0cf40-102">IAssemblyName::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="0cf40-102">IAssemblyName::Clone Method</span></span>

<span data-ttu-id="0cf40-103">この [IAssemblyName](iassemblyname-interface.md) オブジェクトの簡易コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0cf40-103">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cf40-104">構文</span><span class="sxs-lookup"><span data-stu-id="0cf40-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cf40-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0cf40-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="0cf40-106">入出力このオブジェクトの返されたコピー `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="0cf40-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cf40-107">要件</span><span class="sxs-lookup"><span data-stu-id="0cf40-107">Requirements</span></span>  

 <span data-ttu-id="0cf40-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cf40-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cf40-109">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0cf40-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0cf40-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf40-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf40-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cf40-111">See also</span></span>

- [<span data-ttu-id="0cf40-112">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0cf40-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
