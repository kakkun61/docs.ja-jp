---
title: ICorDebugGenericValue::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: dd1c1ba4a976a10d0c38c5295fff838faf072f51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728109"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="ac8dd-102">ICorDebugGenericValue::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="ac8dd-102">ICorDebugGenericValue::GetValue Method</span></span>

<span data-ttu-id="ac8dd-103">このジェネリックの値を、指定したバッファーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ac8dd-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac8dd-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac8dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac8dd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac8dd-105">Parameters</span></span>  

 `pTo`  
 <span data-ttu-id="ac8dd-106">入出力このは、この値オブジェクトによって表される値へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="ac8dd-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="ac8dd-107">値には、単純型または参照型 (つまり、ポインター) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ac8dd-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac8dd-108">要件</span><span class="sxs-lookup"><span data-stu-id="ac8dd-108">Requirements</span></span>  

 <span data-ttu-id="ac8dd-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac8dd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac8dd-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac8dd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac8dd-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac8dd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac8dd-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac8dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
