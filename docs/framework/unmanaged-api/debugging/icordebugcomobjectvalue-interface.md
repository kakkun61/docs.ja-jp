---
title: ICorDebugComObjectValue のインターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: 40df1416e68c86efe6d404119cb37277fe21ac56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677545"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="caa29-102">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="caa29-102">ICorDebugComObjectValue Interface</span></span>

<span data-ttu-id="caa29-103">ランタイム呼び出し可能ラッパー (RCW) に関連付けられている情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="caa29-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="caa29-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="caa29-104">Methods</span></span>  
  
|<span data-ttu-id="caa29-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="caa29-105">Method</span></span>|<span data-ttu-id="caa29-106">説明</span><span class="sxs-lookup"><span data-stu-id="caa29-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="caa29-107">GetCachedInterfacePointers メソッド</span><span class="sxs-lookup"><span data-stu-id="caa29-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="caa29-108">現在の RCW でキャッシュされている生のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="caa29-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="caa29-109">GetCachedInterfaceTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="caa29-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="caa29-110">現在のオブジェクトで使用または使用されているインターフェイス型の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="caa29-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caa29-111">注釈</span><span class="sxs-lookup"><span data-stu-id="caa29-111">Remarks</span></span>  

 <span data-ttu-id="caa29-112">"ICorDebugValue" インターフェイスのインスタンスが RCW を表すかどうかを確認するために、デバッガーは `QueryInterface` を使用して "icordebugvalue" でを呼び出し `IID_ICorDebugComObjectValue` ます。</span><span class="sxs-lookup"><span data-stu-id="caa29-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa29-113">要件</span><span class="sxs-lookup"><span data-stu-id="caa29-113">Requirements</span></span>  

 <span data-ttu-id="caa29-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caa29-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa29-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="caa29-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caa29-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caa29-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caa29-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa29-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa29-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="caa29-118">See also</span></span>

- [<span data-ttu-id="caa29-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="caa29-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="caa29-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="caa29-120">Debugging</span></span>](index.md)
