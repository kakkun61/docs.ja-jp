---
title: ICorDebugExceptionObjectCallStackEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 17d5367564ec1ec98efc264ad9a5794c0d04a947
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672137"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="5727f-102">ICorDebugExceptionObjectCallStackEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="5727f-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>

<span data-ttu-id="5727f-103">例外オブジェクトの呼び出し履歴の情報を格納している、指定した数の [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5727f-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5727f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5727f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5727f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5727f-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="5727f-106">から取得する [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="5727f-106">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="5727f-107">入出力ポインターの配列。それぞれが [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="5727f-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5727f-108">入出力実際に返された [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5727f-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5727f-109">解説</span><span class="sxs-lookup"><span data-stu-id="5727f-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5727f-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="5727f-110">Requirements</span></span>  

 <span data-ttu-id="5727f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5727f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5727f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5727f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5727f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5727f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5727f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5727f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5727f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5727f-115">See also</span></span>

- [<span data-ttu-id="5727f-116">ICorDebugExceptionObjectCallStackEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5727f-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="5727f-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5727f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
