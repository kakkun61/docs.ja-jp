---
title: ICorDebugFunction::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
ms.openlocfilehash: 40cb59a2ad0539764702369b13d632eddbab8174
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728161"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="69c50-102">ICorDebugFunction::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="69c50-102">ICorDebugFunction::GetClass Method</span></span>

<span data-ttu-id="69c50-103">この関数がメンバーとなっているクラスを表す、のオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="69c50-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c50-104">構文</span><span class="sxs-lookup"><span data-stu-id="69c50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69c50-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69c50-105">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="69c50-106">入出力クラスを表すオブジェクトのアドレスへのポインター `ICorDebugClass` 。この関数がクラスのメンバーでない場合は null。</span><span class="sxs-lookup"><span data-stu-id="69c50-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c50-107">要件</span><span class="sxs-lookup"><span data-stu-id="69c50-107">Requirements</span></span>  

 <span data-ttu-id="69c50-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69c50-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69c50-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69c50-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69c50-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69c50-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69c50-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69c50-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
