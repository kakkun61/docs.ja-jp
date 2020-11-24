---
title: ICorThreadpool::CorChangeTimer メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
ms.openlocfilehash: 3d119c8355f5b58a05f1ea1695969b2e98682c72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690240"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="40d1f-102">ICorThreadpool::CorChangeTimer メソッド</span><span class="sxs-lookup"><span data-stu-id="40d1f-102">ICorThreadpool::CorChangeTimer Method</span></span>

<span data-ttu-id="40d1f-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="40d1f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d1f-104">構文</span><span class="sxs-lookup"><span data-stu-id="40d1f-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="40d1f-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="40d1f-105">Requirements</span></span>  

 <span data-ttu-id="40d1f-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40d1f-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40d1f-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="40d1f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40d1f-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="40d1f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40d1f-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40d1f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d1f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="40d1f-110">See also</span></span>

- [<span data-ttu-id="40d1f-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40d1f-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
