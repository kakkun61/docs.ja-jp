---
title: ICorDebugAppDomain::GetId メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
ms.openlocfilehash: 88866d75cc97d40c827359450e8e7bdbe13ef3ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715889"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="3cabb-102">ICorDebugAppDomain::GetId メソッド</span><span class="sxs-lookup"><span data-stu-id="3cabb-102">ICorDebugAppDomain::GetId Method</span></span>

<span data-ttu-id="3cabb-103">アプリケーションドメインの一意の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="3cabb-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cabb-104">構文</span><span class="sxs-lookup"><span data-stu-id="3cabb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cabb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cabb-105">Parameters</span></span>  

 `pId`  
 <span data-ttu-id="3cabb-106">入出力アプリケーションドメインの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="3cabb-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cabb-107">注釈</span><span class="sxs-lookup"><span data-stu-id="3cabb-107">Remarks</span></span>  

 <span data-ttu-id="3cabb-108">アプリケーションドメインの識別子は、含まれているプロセス内で一意です。</span><span class="sxs-lookup"><span data-stu-id="3cabb-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cabb-109">要件</span><span class="sxs-lookup"><span data-stu-id="3cabb-109">Requirements</span></span>  

 <span data-ttu-id="3cabb-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cabb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cabb-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3cabb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cabb-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cabb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cabb-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cabb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
