---
title: ICorDebugObjectValue::GetVirtualMethod メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetVirtualMethod
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetVirtualMethod
helpviewer_keywords:
- GetVirtualMethod method [.NET Framework debugging]
- ICorDebugObjectValue::GetVirtualmethod method [.NET Framework debugging]
ms.assetid: f783ebc3-e952-46e6-9325-14dd2c666f21
topic_type:
- apiref
ms.openlocfilehash: 208723c42f58febc18182e8be67732bf310ccb56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695258"
---
# <a name="icordebugobjectvaluegetvirtualmethod-method"></a><span data-ttu-id="a7838-102">ICorDebugObjectValue::GetVirtualMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="a7838-102">ICorDebugObjectValue::GetVirtualMethod Method</span></span>

<span data-ttu-id="a7838-103">`GetVirtualMethod` は、このバージョンの .NET Framework では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="a7838-103">`GetVirtualMethod` is not implemented in this version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7838-104">構文</span><span class="sxs-lookup"><span data-stu-id="a7838-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethod (  
    [in]  mdMemberRef        memberRef,  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a7838-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="a7838-105">Requirements</span></span>  

 <span data-ttu-id="a7838-106">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7838-106">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7838-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7838-107">See also</span></span>
