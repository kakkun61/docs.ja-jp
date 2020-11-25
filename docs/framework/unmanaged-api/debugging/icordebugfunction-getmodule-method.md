---
title: ICorDebugFunction::GetModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: 5fad8b56b783748e23c8adc4aee0e1bf3450e243
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696129"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="4cc58-102">ICorDebugFunction::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="4cc58-102">ICorDebugFunction::GetModule Method</span></span>

<span data-ttu-id="4cc58-103">この関数が定義されているモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="4cc58-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc58-104">構文</span><span class="sxs-lookup"><span data-stu-id="4cc58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cc58-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4cc58-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="4cc58-106">入出力この関数が定義されているモジュールを表す、モジュールオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4cc58-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cc58-107">要件</span><span class="sxs-lookup"><span data-stu-id="4cc58-107">Requirements</span></span>  

 <span data-ttu-id="4cc58-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cc58-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cc58-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cc58-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cc58-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cc58-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cc58-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cc58-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
