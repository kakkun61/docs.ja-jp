---
title: ICorThreadpool::CorCreateTimer メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
ms.openlocfilehash: 3eac575e18c7371754401da6498d85ba7ed6c8cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717618"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="c100d-102">ICorThreadpool::CorCreateTimer メソッド</span><span class="sxs-lookup"><span data-stu-id="c100d-102">ICorThreadpool::CorCreateTimer Method</span></span>

<span data-ttu-id="c100d-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="c100d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c100d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c100d-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c100d-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="c100d-105">Requirements</span></span>  

 <span data-ttu-id="c100d-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c100d-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c100d-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c100d-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c100d-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c100d-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c100d-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c100d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c100d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c100d-110">See also</span></span>

- [<span data-ttu-id="c100d-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c100d-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
