---
title: ICorDebugBlockingObjectEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: 232068a5fee8f7bd3dfbddf4d9452e80d6fd6170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719191"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="84726-102">ICorDebugBlockingObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="84726-102">ICorDebugBlockingObjectEnum::Next Method</span></span>

<span data-ttu-id="84726-103">現在の位置から開始して、指定した数の [CorDebugBlockingObject](cordebugblockingobject-structure.md) オブジェクトを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="84726-103">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84726-104">構文</span><span class="sxs-lookup"><span data-stu-id="84726-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="84726-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84726-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="84726-106">から取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="84726-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="84726-107">入出力 [CorDebugBlockingObject](cordebugblockingobject-structure.md) オブジェクトへのポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="84726-107">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="84726-108">入出力取得されたオブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="84726-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84726-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="84726-109">Return Value</span></span>  

 <span data-ttu-id="84726-110">このメソッドは、次の特定の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="84726-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="84726-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84726-111">HRESULT</span></span>|<span data-ttu-id="84726-112">説明</span><span class="sxs-lookup"><span data-stu-id="84726-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84726-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="84726-113">S_OK</span></span>|<span data-ttu-id="84726-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="84726-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="84726-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="84726-115">S_FALSE</span></span>|<span data-ttu-id="84726-116">`pceltFetched` は `celt` と一致しません。</span><span class="sxs-lookup"><span data-stu-id="84726-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84726-117">注釈</span><span class="sxs-lookup"><span data-stu-id="84726-117">Remarks</span></span>  

 <span data-ttu-id="84726-118">このメソッドは、一般的な COM 列挙子と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="84726-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="84726-119">入力配列の値は、少なくともサイズにする必要があり `celt` ます。</span><span class="sxs-lookup"><span data-stu-id="84726-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="84726-120">配列には、列挙体の次の `celt` 値、または残りのすべての値を格納し `celt` ます。</span><span class="sxs-lookup"><span data-stu-id="84726-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="84726-121">このメソッドから制御が戻るときに、取得された `pceltFetched` 値の数がに格納されます。</span><span class="sxs-lookup"><span data-stu-id="84726-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="84726-122">に `values` 無効なポインターが含まれている場合、またはより小さいバッファーを指している場合、 `celt` または `pceltFetched` が無効なポインターの場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="84726-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84726-123">[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体を解放する必要はありませんが、その中の "ICorDebugValue" インターフェイスは解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84726-123">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84726-124">要件</span><span class="sxs-lookup"><span data-stu-id="84726-124">Requirements</span></span>  

 <span data-ttu-id="84726-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84726-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84726-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84726-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84726-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84726-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84726-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84726-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84726-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="84726-129">See also</span></span>

- [<span data-ttu-id="84726-130">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84726-130">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="84726-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="84726-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="84726-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="84726-132">Debugging</span></span>](index.md)
