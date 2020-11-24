---
title: ICorRuntimeHost::SwitchOutLogicalThreadState メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
ms.openlocfilehash: e41ead54b50b8b28ebd9ee9c97d15ca6c71e7313
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690123"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="20211-102">ICorRuntimeHost::SwitchOutLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="20211-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>

<span data-ttu-id="20211-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="20211-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20211-104">構文</span><span class="sxs-lookup"><span data-stu-id="20211-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20211-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20211-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="20211-106">入出力スイッチアウトされるファイバーを示すクッキー。</span><span class="sxs-lookup"><span data-stu-id="20211-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20211-107">要件</span><span class="sxs-lookup"><span data-stu-id="20211-107">Requirements</span></span>  

 <span data-ttu-id="20211-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20211-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20211-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="20211-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20211-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="20211-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20211-111">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="20211-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20211-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="20211-112">See also</span></span>

- [<span data-ttu-id="20211-113">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20211-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
