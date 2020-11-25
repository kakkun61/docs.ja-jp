---
title: ICorDebugHeapValue::IsValid メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: d9150d15ac183b65b87448424f265693ed7b7ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726575"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="78e33-102">ICorDebugHeapValue::IsValid メソッド</span><span class="sxs-lookup"><span data-stu-id="78e33-102">ICorDebugHeapValue::IsValid Method</span></span>

<span data-ttu-id="78e33-103">この値によって表されるオブジェクトが有効かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="78e33-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="78e33-104">このメソッドは .NET Framework バージョン2.0 では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="78e33-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e33-105">構文</span><span class="sxs-lookup"><span data-stu-id="78e33-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78e33-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78e33-106">Parameters</span></span>  

 `pbValid`  
 <span data-ttu-id="78e33-107">入出力ヒープ上のこの値が有効かどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="78e33-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78e33-108">注釈</span><span class="sxs-lookup"><span data-stu-id="78e33-108">Remarks</span></span>  

 <span data-ttu-id="78e33-109">値は、ガベージコレクターによって回収されている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="78e33-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="78e33-110">このメソッドの使用は非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="78e33-110">This method has been deprecated.</span></span> <span data-ttu-id="78e33-111">.NET Framework 2.0 では、すべての値は、"の値は無効になります。 [" が呼び出されるまで、](icordebugcontroller-continue-method.md) すべての値が有効になります。</span><span class="sxs-lookup"><span data-stu-id="78e33-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78e33-112">要件</span><span class="sxs-lookup"><span data-stu-id="78e33-112">Requirements</span></span>  

 <span data-ttu-id="78e33-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78e33-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e33-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78e33-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78e33-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78e33-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78e33-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e33-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
