---
title: ICorRuntimeHost::LocksHeldByLogicalThread メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: 16f34d91861f9fcae51691ab13549bdf1ef333a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671500"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="88a4e-102">ICorRuntimeHost::LocksHeldByLogicalThread メソッド</span><span class="sxs-lookup"><span data-stu-id="88a4e-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>

<span data-ttu-id="88a4e-103">現在のスレッドが保持しているロックの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="88a4e-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="88a4e-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="88a4e-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a4e-105">構文</span><span class="sxs-lookup"><span data-stu-id="88a4e-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88a4e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="88a4e-106">Parameters</span></span>  

 `pCount`  
 <span data-ttu-id="88a4e-107">入出力現在のスレッドが保持しているロックの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="88a4e-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a4e-108">要件</span><span class="sxs-lookup"><span data-stu-id="88a4e-108">Requirements</span></span>  

 <span data-ttu-id="88a4e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88a4e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88a4e-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="88a4e-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88a4e-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="88a4e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88a4e-112">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="88a4e-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a4e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="88a4e-113">See also</span></span>

- [<span data-ttu-id="88a4e-114">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="88a4e-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
