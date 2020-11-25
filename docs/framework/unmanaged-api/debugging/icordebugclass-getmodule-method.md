---
title: ICorDebugClass::GetModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: e95d10512da73d9f483b87557fd7cd4574503c70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728460"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="e444a-102">ICorDebugClass::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="e444a-102">ICorDebugClass::GetModule Method</span></span>

<span data-ttu-id="e444a-103">このクラスを定義するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="e444a-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e444a-104">構文</span><span class="sxs-lookup"><span data-stu-id="e444a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e444a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e444a-105">Parameters</span></span>  

 `pModule`  
 <span data-ttu-id="e444a-106">入出力このクラスが定義されているモジュールを表す、モジュールオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e444a-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e444a-107">要件</span><span class="sxs-lookup"><span data-stu-id="e444a-107">Requirements</span></span>  

 <span data-ttu-id="e444a-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e444a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e444a-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e444a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e444a-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e444a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e444a-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e444a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
