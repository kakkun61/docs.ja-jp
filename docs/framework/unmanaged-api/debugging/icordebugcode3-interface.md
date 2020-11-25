---
title: ICorDebugCode3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 609cd557db71fac53aadf613534a23e988b14bde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720759"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="e428d-102">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e428d-102">ICorDebugCode3 Interface</span></span>

<span data-ttu-id="e428d-103">"" のコード "と" ICorDebugCode2 "を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e428d-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e428d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e428d-104">Methods</span></span>  
  
|<span data-ttu-id="e428d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e428d-105">Method</span></span>|<span data-ttu-id="e428d-106">説明</span><span class="sxs-lookup"><span data-stu-id="e428d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e428d-107">GetReturnValueLiveOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="e428d-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="e428d-108">指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="e428d-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e428d-109">注釈</span><span class="sxs-lookup"><span data-stu-id="e428d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e428d-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e428d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e428d-111">要件</span><span class="sxs-lookup"><span data-stu-id="e428d-111">Requirements</span></span>  

 <span data-ttu-id="e428d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e428d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e428d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e428d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e428d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e428d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e428d-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e428d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e428d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e428d-116">See also</span></span>

- [<span data-ttu-id="e428d-117">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e428d-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="e428d-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e428d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
