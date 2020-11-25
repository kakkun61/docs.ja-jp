---
title: ICorThreadpool::CorRegisterWaitForSingleObject メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorRegisterWaitForSingleObject
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegisterWaitForSingleObject
helpviewer_keywords:
- ICorThreadpool::CorRegisterWaitForSingleObject method [.NET Framework hosting]
- CorRegisterWaitForSingleObject method [.NET Framework hosting]
ms.assetid: cade1feb-71d2-43ed-85ca-7b2e9da12994
topic_type:
- apiref
ms.openlocfilehash: 9f555d3119ede5eabe61467aa81d35aa5c354751
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727849"
---
# <a name="icorthreadpoolcorregisterwaitforsingleobject-method"></a><span data-ttu-id="4bd22-102">ICorThreadpool::CorRegisterWaitForSingleObject メソッド</span><span class="sxs-lookup"><span data-stu-id="4bd22-102">ICorThreadpool::CorRegisterWaitForSingleObject Method</span></span>

<span data-ttu-id="4bd22-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="4bd22-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd22-104">構文</span><span class="sxs-lookup"><span data-stu-id="4bd22-104">Syntax</span></span>  
  
```cpp  
HRESULT CorRegisterWaitForSingleObject (  
    [in]  HANDLE*             phNewWaitObject,  
    [in]  HANDLE              hWaitObject,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Context,  
    [in]  ULONG               timeout,  
    [in]  BOOL                executeOnlyOnce,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4bd22-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="4bd22-105">Requirements</span></span>  

 <span data-ttu-id="4bd22-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bd22-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bd22-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4bd22-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bd22-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4bd22-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bd22-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bd22-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd22-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bd22-110">See also</span></span>

- [<span data-ttu-id="4bd22-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bd22-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
