---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
ms.openlocfilehash: f5f0f11683043f1c287dd3ca3071830bcfb46502
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677558"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="9a922-102">ICorDebugComObjectValue::GetCachedInterfaceTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="9a922-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>

<span data-ttu-id="9a922-103">現在のオブジェクトがキャストされた、またはとして使用されたインターフェイス型の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="9a922-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a922-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a922-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a922-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a922-105">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="9a922-106">からメソッドが、 `IInspectable` ランタイム呼び出し可能ラッパー (RCW) によってキャッシュされた Windows ランタイムインターフェイス (インターフェイス) またはすべての COM インターフェイスだけを返すかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="9a922-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="9a922-107">入出力に従ってフィルター処理された、キャッシュされたインターフェイスの種類を表す、の型のオブジェクトへのアクセスを提供する、、の各型のオブジェクトへのアクセスを提供する、テキストを指すポインター `bIInspectableOnly` です。</span><span class="sxs-lookup"><span data-stu-id="9a922-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a922-108">解説</span><span class="sxs-lookup"><span data-stu-id="9a922-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a922-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="9a922-109">Requirements</span></span>  

 <span data-ttu-id="9a922-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a922-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a922-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a922-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a922-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a922-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a922-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a922-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a922-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a922-114">See also</span></span>

- [<span data-ttu-id="9a922-115">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a922-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="9a922-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a922-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
