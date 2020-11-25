---
title: 'ICorDebugCode4:: EnumerateVariableHomes メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 6d58efa5629bb02158a275dec61c0313bca821a1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720758"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="1f4f2-102">ICorDebugCode4:: EnumerateVariableHomes メソッド</span><span class="sxs-lookup"><span data-stu-id="1f4f2-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>

<span data-ttu-id="1f4f2-103">関数のローカル変数および引数に対する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="1f4f2-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4f2-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f4f2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f4f2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f4f2-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="1f4f2-106">関数内のローカル変数および引数の列挙子である、の [型](icordebugvariablehomeenum-interface.md) のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1f4f2-106">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f4f2-107">注釈</span><span class="sxs-lookup"><span data-stu-id="1f4f2-107">Remarks</span></span>  

 <span data-ttu-id="1f4f2-108">"ICorDebugEnum" インターフェイスから派生した標準列挙子で[ある、表示変数](icordebugvariablehomeenum-interface.md)[ホーム](icordebugvariablehome-interface.md)オブジェクトを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="1f4f2-108">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="1f4f2-109">コレクションには、同じスロットまたは引数インデックスに対して、関数内の異なるポイントに異なる [ホーム](icordebugvariablehome-interface.md) オブジェクトが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1f4f2-109">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f4f2-110">要件</span><span class="sxs-lookup"><span data-stu-id="1f4f2-110">Requirements</span></span>  

 <span data-ttu-id="1f4f2-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f4f2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f4f2-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f4f2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f4f2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f4f2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f4f2-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f4f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4f2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f4f2-115">See also</span></span>

- [<span data-ttu-id="1f4f2-116">ICorDebugCode4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f4f2-116">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="1f4f2-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f4f2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
