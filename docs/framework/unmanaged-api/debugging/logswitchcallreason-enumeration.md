---
title: LogSwitchCallReason 列挙型
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: dfb34595530a47b74762610f5824b68ea00a8a69
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671942"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="bab81-102">LogSwitchCallReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="bab81-102">LogSwitchCallReason Enumeration</span></span>

<span data-ttu-id="bab81-103">デバッグとトレースの切り替えで実行された操作を示します。</span><span class="sxs-lookup"><span data-stu-id="bab81-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab81-104">構文</span><span class="sxs-lookup"><span data-stu-id="bab81-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="bab81-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="bab81-105">Members</span></span>  
  
|<span data-ttu-id="bab81-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="bab81-106">Member</span></span>|<span data-ttu-id="bab81-107">説明</span><span class="sxs-lookup"><span data-stu-id="bab81-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="bab81-108">デバッグ/トレーススイッチが作成されました。</span><span class="sxs-lookup"><span data-stu-id="bab81-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="bab81-109">デバッグ/トレーススイッチが変更されました。</span><span class="sxs-lookup"><span data-stu-id="bab81-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="bab81-110">デバッグ/トレーススイッチが削除されました。</span><span class="sxs-lookup"><span data-stu-id="bab81-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bab81-111">要件</span><span class="sxs-lookup"><span data-stu-id="bab81-111">Requirements</span></span>  

 <span data-ttu-id="bab81-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bab81-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab81-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bab81-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bab81-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bab81-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bab81-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bab81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab81-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bab81-116">See also</span></span>

- [<span data-ttu-id="bab81-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="bab81-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
