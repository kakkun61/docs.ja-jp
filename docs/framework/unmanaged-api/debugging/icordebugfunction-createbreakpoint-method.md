---
title: ICorDebugFunction::CreateBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
ms.openlocfilehash: 2d1846acae51f416471404389dd1dbcfb2383760
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728174"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="200ec-102">ICorDebugFunction::CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="200ec-102">ICorDebugFunction::CreateBreakpoint Method</span></span>

<span data-ttu-id="200ec-103">この関数の先頭にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="200ec-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="200ec-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="200ec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="200ec-105">Parameters</span></span>  

 `ppBreakpoint`  
 <span data-ttu-id="200ec-106">入出力関数の新しいブレークポイントを表す、の新しいブレークポイントオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="200ec-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="200ec-107">要件</span><span class="sxs-lookup"><span data-stu-id="200ec-107">Requirements</span></span>  

 <span data-ttu-id="200ec-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="200ec-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="200ec-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="200ec-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="200ec-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="200ec-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="200ec-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="200ec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
