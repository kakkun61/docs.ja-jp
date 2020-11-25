---
title: CorDebugHandleType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
ms.openlocfilehash: a0ec83a5590e184b9ff60449a8147d1a3c90a6a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712457"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="a00ab-102">CorDebugHandleType 列挙型</span><span class="sxs-lookup"><span data-stu-id="a00ab-102">CorDebugHandleType Enumeration</span></span>

<span data-ttu-id="a00ab-103">ハンドル型を示します。</span><span class="sxs-lookup"><span data-stu-id="a00ab-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00ab-104">構文</span><span class="sxs-lookup"><span data-stu-id="a00ab-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="a00ab-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a00ab-105">Members</span></span>  
  
|<span data-ttu-id="a00ab-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a00ab-106">Member</span></span>|<span data-ttu-id="a00ab-107">説明</span><span class="sxs-lookup"><span data-stu-id="a00ab-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="a00ab-108">ハンドルは strong であり、ガベージコレクションによってオブジェクトが解放されるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="a00ab-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="a00ab-109">ハンドルは脆弱であり、ガベージコレクションによってオブジェクトが解放されるのを防ぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="a00ab-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="a00ab-110">オブジェクトが収集されると、ハンドルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="a00ab-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a00ab-111">要件</span><span class="sxs-lookup"><span data-stu-id="a00ab-111">Requirements</span></span>  

 <span data-ttu-id="a00ab-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a00ab-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a00ab-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a00ab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a00ab-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a00ab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a00ab-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a00ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00ab-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a00ab-116">See also</span></span>

- [<span data-ttu-id="a00ab-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="a00ab-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
