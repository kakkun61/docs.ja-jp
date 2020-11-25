---
title: ICorDebugComObjectValue::GetCachedInterfacePointers メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: c3120a0dd859f581e6356fc260043cb83250ae9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724833"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="cb6ef-102">ICorDebugComObjectValue::GetCachedInterfacePointers メソッド</span><span class="sxs-lookup"><span data-stu-id="cb6ef-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>

<span data-ttu-id="cb6ef-103">現在のランタイム呼び出し可能ラッパー (RCW) にキャッシュされている生のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="cb6ef-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6ef-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb6ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb6ef-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb6ef-105">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="cb6ef-106">からメソッドが、 `IInspectable` ランタイム呼び出し可能ラッパー (RCW) によってキャッシュされた Windows ランタイムインターフェイス (インターフェイス) またはすべての COM インターフェイスだけを返すかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="cb6ef-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="cb6ef-107">からアドレスを取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="cb6ef-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="cb6ef-108">入出力 `CORDB_ADDRESS` で実際に返される値の数へのポインター `ptrs` 。</span><span class="sxs-lookup"><span data-stu-id="cb6ef-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="cb6ef-109">キャッシュされた `CORDB_ADDRESS` インターフェイスオブジェクトのアドレスを格納している値の配列の開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cb6ef-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb6ef-110">解説</span><span class="sxs-lookup"><span data-stu-id="cb6ef-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb6ef-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="cb6ef-111">Requirements</span></span>  

 <span data-ttu-id="cb6ef-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb6ef-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb6ef-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb6ef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb6ef-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb6ef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb6ef-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb6ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6ef-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb6ef-116">See also</span></span>

- [<span data-ttu-id="cb6ef-117">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb6ef-117">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="cb6ef-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb6ef-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
