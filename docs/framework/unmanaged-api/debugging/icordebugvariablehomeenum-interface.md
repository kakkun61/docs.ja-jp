---
title: ICorDebugVariableHomeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: 8e8caad9f0fc60121dbd1c738a6024da3e4d02f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726003"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="ec993-102">ICorDebugVariableHomeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec993-102">ICorDebugVariableHomeEnum Interface</span></span>

<span data-ttu-id="ec993-103">関数のローカル変数および引数に列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="ec993-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec993-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ec993-104">Methods</span></span>  
  
|<span data-ttu-id="ec993-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ec993-105">Method</span></span>|<span data-ttu-id="ec993-106">説明</span><span class="sxs-lookup"><span data-stu-id="ec993-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec993-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="ec993-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="ec993-108">関数内のローカル変数および引数に関する情報を格納している指定された数の表示変数 [home](icordebugvariablehome-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ec993-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec993-109">注釈</span><span class="sxs-lookup"><span data-stu-id="ec993-109">Remarks</span></span>  

 <span data-ttu-id="ec993-110">`ICorDebugVariableHomeEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="ec993-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="ec993-111">`ICorDebugVariableHomeEnum`インスタンスには、 [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md)メソッドを呼び出すことによって、表示[変数 home](icordebugvariablehome-interface.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec993-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="ec993-112">コレクション内 [の各は](icordebugvariablehome-interface.md) 、関数のローカル変数または引数を表します。</span><span class="sxs-lookup"><span data-stu-id="ec993-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="ec993-113">コレクション内  [のオブジェクトを](icordebugvariablehome-interface.md) 列挙するには、 [次](icordebugvariablehomeenum-next-method.md) のように指定します。</span><span class="sxs-lookup"><span data-stu-id="ec993-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec993-114">要件</span><span class="sxs-lookup"><span data-stu-id="ec993-114">Requirements</span></span>  

 <span data-ttu-id="ec993-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec993-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec993-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec993-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec993-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec993-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec993-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec993-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec993-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec993-119">See also</span></span>

- [<span data-ttu-id="ec993-120">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec993-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="ec993-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec993-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
