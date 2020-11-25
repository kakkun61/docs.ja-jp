---
title: CorDebugStepReason 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 50903b3737c0fc63eda2b1190e4c3d961ce3ae7b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726042"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="e978a-102">CorDebugStepReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="e978a-102">CorDebugStepReason Enumeration</span></span>

<span data-ttu-id="e978a-103">個々のステップの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="e978a-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e978a-104">構文</span><span class="sxs-lookup"><span data-stu-id="e978a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="e978a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e978a-105">Members</span></span>  
  
|<span data-ttu-id="e978a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e978a-106">Member</span></span>|<span data-ttu-id="e978a-107">説明</span><span class="sxs-lookup"><span data-stu-id="e978a-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="e978a-108">同じ関数内で通常どおりにステップ実行が完了しました。</span><span class="sxs-lookup"><span data-stu-id="e978a-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="e978a-109">関数が返された後、通常どおりにステップ実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="e978a-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="e978a-110">新しく呼び出された関数の先頭で、ステップ実行は通常どおり続行されます。</span><span class="sxs-lookup"><span data-stu-id="e978a-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="e978a-111">例外が生成され、制御が例外フィルターに渡されました。</span><span class="sxs-lookup"><span data-stu-id="e978a-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="e978a-112">例外が生成され、制御が例外ハンドラーに渡されました。</span><span class="sxs-lookup"><span data-stu-id="e978a-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="e978a-113">コントロールがインターセプターに渡されました。</span><span class="sxs-lookup"><span data-stu-id="e978a-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="e978a-114">ステップが完了する前にスレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="e978a-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e978a-115">要件</span><span class="sxs-lookup"><span data-stu-id="e978a-115">Requirements</span></span>  

 <span data-ttu-id="e978a-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e978a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e978a-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e978a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e978a-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e978a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e978a-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e978a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e978a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e978a-120">See also</span></span>

- [<span data-ttu-id="e978a-121">StepComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="e978a-121">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="e978a-122">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e978a-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
