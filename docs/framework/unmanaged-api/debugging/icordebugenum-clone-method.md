---
title: ICorDebugEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 28e0cded33b49e3aadc0564bae3a60bee76c4396
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677389"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="5cbed-102">ICorDebugEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="5cbed-102">ICorDebugEnum::Clone Method</span></span>

<span data-ttu-id="5cbed-103">この ICorDebugEnum オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5cbed-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cbed-104">構文</span><span class="sxs-lookup"><span data-stu-id="5cbed-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cbed-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5cbed-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="5cbed-106">入出力 `ICorDebugEnum` このオブジェクトのコピーであるオブジェクトのアドレスへのポインター `ICorDebugEnum` 。</span><span class="sxs-lookup"><span data-stu-id="5cbed-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cbed-107">要件</span><span class="sxs-lookup"><span data-stu-id="5cbed-107">Requirements</span></span>  

 <span data-ttu-id="5cbed-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cbed-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cbed-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cbed-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cbed-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cbed-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cbed-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cbed-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
