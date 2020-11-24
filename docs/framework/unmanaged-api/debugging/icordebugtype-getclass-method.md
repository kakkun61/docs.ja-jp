---
title: ICorDebugType::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 1cb9729f175a2e82e88386b0694467c6fe05636a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684461"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="5c15f-102">ICorDebugType::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="5c15f-102">ICorDebugType::GetClass Method</span></span>

<span data-ttu-id="5c15f-103">インスタンスジェネリック型を表す、のクラスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5c15f-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c15f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c15f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c15f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c15f-105">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="5c15f-106">入出力 `ICorDebugClass` インスタンスジェネリック型を表すインターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c15f-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c15f-107">注釈</span><span class="sxs-lookup"><span data-stu-id="5c15f-107">Remarks</span></span>  

 <span data-ttu-id="5c15f-108">`GetClass` は、特定の条件下でのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5c15f-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="5c15f-109">を [呼び出す前に](icordebugtype-gettype-method.md) 、を呼び出して `GetClass` ください。</span><span class="sxs-lookup"><span data-stu-id="5c15f-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="5c15f-110">`ICorDebugType::GetType`が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の CorElementType 値を返す場合は、を呼び出して、 `GetClass` ジェネリック型のインスタンス型を取得できます。</span><span class="sxs-lookup"><span data-stu-id="5c15f-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c15f-111">要件</span><span class="sxs-lookup"><span data-stu-id="5c15f-111">Requirements</span></span>  

 <span data-ttu-id="5c15f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c15f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c15f-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c15f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c15f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c15f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c15f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c15f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
