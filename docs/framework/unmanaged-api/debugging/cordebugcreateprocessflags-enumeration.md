---
title: CorDebugCreateProcessFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: f6f589656a3063fc89bd276b32d0ed751fd8d2d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733400"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="783a8-102">CorDebugCreateProcessFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="783a8-102">CorDebugCreateProcessFlags Enumeration</span></span>

<span data-ttu-id="783a8-103">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md)メソッドの呼び出しで使用できる追加のデバッグオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="783a8-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="783a8-104">構文</span><span class="sxs-lookup"><span data-stu-id="783a8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="783a8-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="783a8-105">Members</span></span>  
  
|<span data-ttu-id="783a8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="783a8-106">Member</span></span>|<span data-ttu-id="783a8-107">説明</span><span class="sxs-lookup"><span data-stu-id="783a8-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="783a8-108">特別なオプションは設定されていません。</span><span class="sxs-lookup"><span data-stu-id="783a8-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="783a8-109">要件</span><span class="sxs-lookup"><span data-stu-id="783a8-109">Requirements</span></span>  

 <span data-ttu-id="783a8-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="783a8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="783a8-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="783a8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="783a8-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="783a8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="783a8-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="783a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="783a8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="783a8-114">See also</span></span>

- [<span data-ttu-id="783a8-115">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="783a8-115">Debugging Enumerations</span></span>](debugging-enumerations.md)
