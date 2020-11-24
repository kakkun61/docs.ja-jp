---
title: ICorDebugCode::GetILToNativeMapping メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 0adb9e58ca2c6b5b430a0413fa11ba59d79a0539
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688108"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="3c311-102">ICorDebugCode::GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="3c311-102">ICorDebugCode::GetILToNativeMapping Method</span></span>

<span data-ttu-id="3c311-103">Microsoft 中間言語 (MSIL) オフセットからネイティブオフセットへのマッピングを表す "COR_DEBUG_IL_TO_NATIVE_MAP" インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="3c311-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c311-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c311-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c311-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c311-105">Parameters</span></span>  

 `cMap`  
 <span data-ttu-id="3c311-106">[in] `map` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="3c311-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="3c311-107">入出力配列で返された実際の要素数へのポインター `map` 。</span><span class="sxs-lookup"><span data-stu-id="3c311-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="3c311-108">入出力構造体の配列。 `COR_DEBUG_IL_TO_NATIVE_MAP` それぞれが MSIL オフセットからネイティブオフセットへのマッピングを表します。</span><span class="sxs-lookup"><span data-stu-id="3c311-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="3c311-109">返される要素の配列への順序はありません。</span><span class="sxs-lookup"><span data-stu-id="3c311-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c311-110">注釈</span><span class="sxs-lookup"><span data-stu-id="3c311-110">Remarks</span></span>  

 <span data-ttu-id="3c311-111">メソッドは、 `GetILToNativeMapping` この "" コード "インスタンスが MSIL コードからコンパイルされた just-in-time (JIT) コードを表している場合にのみ、意味のある結果を返します。</span><span class="sxs-lookup"><span data-stu-id="3c311-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c311-112">要件</span><span class="sxs-lookup"><span data-stu-id="3c311-112">Requirements</span></span>  

 <span data-ttu-id="3c311-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c311-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c311-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c311-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c311-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c311-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c311-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c311-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c311-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c311-117">See also</span></span>

- [<span data-ttu-id="3c311-118">ICorDebugCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c311-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
