---
title: ICorDebugHandleValue::Dispose メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
ms.openlocfilehash: dc24afd8f78a900ea52539bf9dcb522287223c4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705632"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="da90d-102">ICorDebugHandleValue::Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="da90d-102">ICorDebugHandleValue::Dispose Method</span></span>

<span data-ttu-id="da90d-103">インターフェイスポインターを明示的に解放せずに、このオブジェクトによって参照されるハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="da90d-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da90d-104">構文</span><span class="sxs-lookup"><span data-stu-id="da90d-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="da90d-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="da90d-105">Requirements</span></span>  

 <span data-ttu-id="da90d-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da90d-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da90d-107">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da90d-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da90d-108">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da90d-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da90d-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da90d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
