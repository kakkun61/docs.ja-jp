---
title: ICorDebugObjectValue2::GetVirtualMethodAndType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
ms.openlocfilehash: 2a74688b90fbce63c9107d9389ddfd7bf5cd717b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695180"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="5005f-102">ICorDebugObjectValue2::GetVirtualMethodAndType メソッド</span><span class="sxs-lookup"><span data-stu-id="5005f-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>

<span data-ttu-id="5005f-103">このメソッドはまだ実装されていません。</span><span class="sxs-lookup"><span data-stu-id="5005f-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5005f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5005f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="5005f-105">解説</span><span class="sxs-lookup"><span data-stu-id="5005f-105">Remarks</span></span>  

 <span data-ttu-id="5005f-106">指定されたメンバー参照の最も派生したメソッドと型を表す "の型の関数" インスタンスおよび "参照型" インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5005f-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5005f-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="5005f-107">See also</span></span>
