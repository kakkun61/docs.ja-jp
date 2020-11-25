---
title: ICorDebugHandleValue::GetHandleType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
ms.openlocfilehash: 72ef9a0fe4cd08ce67594600375953c249243d4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734154"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="9113b-102">ICorDebugHandleValue::GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="9113b-102">ICorDebugHandleValue::GetHandleType Method</span></span>

<span data-ttu-id="9113b-103">この値オブジェクトによって参照されるハンドルの種類を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9113b-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9113b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9113b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9113b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9113b-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="9113b-106">入出力このハンドルの型を示す CorDebugHandleType 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9113b-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9113b-107">要件</span><span class="sxs-lookup"><span data-stu-id="9113b-107">Requirements</span></span>  

 <span data-ttu-id="9113b-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9113b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9113b-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9113b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9113b-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9113b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9113b-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9113b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
