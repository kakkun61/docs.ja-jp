---
title: ICorDebugEval::GetResult メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 86c017f581c7b980b8b0cb8bd7bdc1b0aa439afe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705825"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="bea4a-102">ICorDebugEval::GetResult メソッド</span><span class="sxs-lookup"><span data-stu-id="bea4a-102">ICorDebugEval::GetResult Method</span></span>

<span data-ttu-id="bea4a-103">この評価の結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="bea4a-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea4a-104">構文</span><span class="sxs-lookup"><span data-stu-id="bea4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bea4a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bea4a-105">Parameters</span></span>  

 `ppResult`  
 <span data-ttu-id="bea4a-106">入出力評価が正常に完了した場合に、この評価の結果を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bea4a-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bea4a-107">注釈</span><span class="sxs-lookup"><span data-stu-id="bea4a-107">Remarks</span></span>  

 <span data-ttu-id="bea4a-108">`GetResult`メソッドは、評価が完了した後にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="bea4a-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="bea4a-109">評価が正常に完了した場合は、 `ppResult` 結果を指定します。</span><span class="sxs-lookup"><span data-stu-id="bea4a-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="bea4a-110">例外が発生して終了した場合は、スローされた例外が結果になります。</span><span class="sxs-lookup"><span data-stu-id="bea4a-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="bea4a-111">新しいオブジェクトの評価がの場合、結果は新しいオブジェクトへの参照になります。</span><span class="sxs-lookup"><span data-stu-id="bea4a-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bea4a-112">要件</span><span class="sxs-lookup"><span data-stu-id="bea4a-112">Requirements</span></span>  

 <span data-ttu-id="bea4a-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bea4a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bea4a-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bea4a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bea4a-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bea4a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bea4a-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bea4a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
