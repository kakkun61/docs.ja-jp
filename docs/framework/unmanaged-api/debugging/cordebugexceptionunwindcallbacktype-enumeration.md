---
title: CorDebugExceptionUnwindCallbackType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: 30de1448a7d1452e1e9049411010e7f43d13eb70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712639"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="62ed5-102">CorDebugExceptionUnwindCallbackType 列挙型</span><span class="sxs-lookup"><span data-stu-id="62ed5-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>

<span data-ttu-id="62ed5-103">アンワインド フェーズ中にコールバックによって通知されるイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="62ed5-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ed5-104">構文</span><span class="sxs-lookup"><span data-stu-id="62ed5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="62ed5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="62ed5-105">Members</span></span>  
  
|<span data-ttu-id="62ed5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="62ed5-106">Member</span></span>|<span data-ttu-id="62ed5-107">説明</span><span class="sxs-lookup"><span data-stu-id="62ed5-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="62ed5-108">アンワインドプロセスの開始。</span><span class="sxs-lookup"><span data-stu-id="62ed5-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="62ed5-109">例外がインターセプトされました。</span><span class="sxs-lookup"><span data-stu-id="62ed5-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62ed5-110">要件</span><span class="sxs-lookup"><span data-stu-id="62ed5-110">Requirements</span></span>  

 <span data-ttu-id="62ed5-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62ed5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ed5-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62ed5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62ed5-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62ed5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62ed5-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ed5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ed5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="62ed5-115">See also</span></span>

- [<span data-ttu-id="62ed5-116">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="62ed5-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
