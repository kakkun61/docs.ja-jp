---
title: ICorDebugType::GetType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: f0f45d5f0b2ea8cefa6bd36e909ae43d80c968ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700887"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="ec7f8-102">ICorDebugType::GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="ec7f8-102">ICorDebugType::GetType Method</span></span>

<span data-ttu-id="ec7f8-103"><xref:System.Type>このコンポーネント型によって表される共通言語ランタイム (CLR) のネイティブ型を記述する CorElementType 値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ec7f8-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec7f8-104">構文</span><span class="sxs-lookup"><span data-stu-id="ec7f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec7f8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec7f8-105">Parameters</span></span>  

 `ty`  
 <span data-ttu-id="ec7f8-106">入出力 `CorElementType` このが表す CLR を示す列挙体の値へのポインター <xref:System.Type> `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="ec7f8-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec7f8-107">注釈</span><span class="sxs-lookup"><span data-stu-id="ec7f8-107">Remarks</span></span>  

 <span data-ttu-id="ec7f8-108">の値 `ty` が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の場合は、インスタンス type [:: getclass](icordebugtype-getclass-method.md) メソッドを呼び出してジェネリック型の型を取得することができます。それ以外の場合は、を呼び出さないで `ICorDebugType::GetClass` ください。</span><span class="sxs-lookup"><span data-stu-id="ec7f8-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec7f8-109">要件</span><span class="sxs-lookup"><span data-stu-id="ec7f8-109">Requirements</span></span>  

 <span data-ttu-id="ec7f8-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7f8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec7f8-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec7f8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec7f8-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec7f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec7f8-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec7f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
