---
title: ICorDebugValueBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
ms.openlocfilehash: cf0a87afd1c0057c054205432fea7aa5844afb53
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684413"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="f1231-102">ICorDebugValueBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1231-102">ICorDebugValueBreakpoint Interface</span></span>

<span data-ttu-id="f1231-103">ICorDebugBreakpoint インターフェイスを拡張して、特定の値にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="f1231-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1231-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f1231-104">Methods</span></span>  
  
|<span data-ttu-id="f1231-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f1231-105">Method</span></span>|<span data-ttu-id="f1231-106">説明</span><span class="sxs-lookup"><span data-stu-id="f1231-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1231-107">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="f1231-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="f1231-108">ブレークポイントが設定されたオブジェクトの値を表す、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f1231-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1231-109">注釈</span><span class="sxs-lookup"><span data-stu-id="f1231-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1231-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f1231-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1231-111">要件</span><span class="sxs-lookup"><span data-stu-id="f1231-111">Requirements</span></span>  

 <span data-ttu-id="f1231-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1231-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1231-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1231-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1231-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1231-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1231-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1231-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1231-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1231-116">See also</span></span>

- [<span data-ttu-id="f1231-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1231-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
