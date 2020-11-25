---
title: CorDebugExceptionObjectStackFrame 構造体
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
ms.openlocfilehash: 9b904596ed1cce4c4cf2676676508dfb3851e8ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712678"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="545a5-102">CorDebugExceptionObjectStackFrame 構造体</span><span class="sxs-lookup"><span data-stu-id="545a5-102">CorDebugExceptionObjectStackFrame Structure</span></span>

<span data-ttu-id="545a5-103">例外オブジェクトのスタック フレームの情報を表しています。</span><span class="sxs-lookup"><span data-stu-id="545a5-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="545a5-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="545a5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="545a5-105">Members</span></span>  
  
|<span data-ttu-id="545a5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="545a5-106">Member</span></span>|<span data-ttu-id="545a5-107">説明</span><span class="sxs-lookup"><span data-stu-id="545a5-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="545a5-108">現在のフレームのモジュールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="545a5-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="545a5-109">現在のフレームの命令ポインター (EIP/RIP) の値。</span><span class="sxs-lookup"><span data-stu-id="545a5-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="545a5-110">現在のフレームのメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="545a5-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="545a5-111">フレームが外部例外の最後のフレームであるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="545a5-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="545a5-112">注釈</span><span class="sxs-lookup"><span data-stu-id="545a5-112">Remarks</span></span>  

 <span data-ttu-id="545a5-113">呼び出し元は、使用されなくなったときに、モジュールオブジェクトへのポインターを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="545a5-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="545a5-114">要件</span><span class="sxs-lookup"><span data-stu-id="545a5-114">Requirements</span></span>  

 <span data-ttu-id="545a5-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="545a5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="545a5-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="545a5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="545a5-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="545a5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="545a5-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="545a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545a5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="545a5-119">See also</span></span>

- [<span data-ttu-id="545a5-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="545a5-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="545a5-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="545a5-121">Debugging</span></span>](index.md)
