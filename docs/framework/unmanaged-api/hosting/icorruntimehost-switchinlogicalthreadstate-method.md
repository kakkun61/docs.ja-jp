---
title: ICorRuntimeHost::SwitchInLogicalThreadState メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: a4590bcd96226a713ff5535a8bc802c2116f862a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690136"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="d76f3-102">ICorRuntimeHost::SwitchInLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="d76f3-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>

<span data-ttu-id="d76f3-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="d76f3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d76f3-104">構文</span><span class="sxs-lookup"><span data-stu-id="d76f3-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d76f3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d76f3-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="d76f3-106">から使用するファイバーを示すクッキー。</span><span class="sxs-lookup"><span data-stu-id="d76f3-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d76f3-107">要件</span><span class="sxs-lookup"><span data-stu-id="d76f3-107">Requirements</span></span>  

 <span data-ttu-id="d76f3-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d76f3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d76f3-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d76f3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d76f3-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d76f3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d76f3-111">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="d76f3-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76f3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d76f3-112">See also</span></span>

- [<span data-ttu-id="d76f3-113">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d76f3-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
