---
title: CorDebugGCType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: 6b3075613af0403527ecf67d574c0f5733a5cd8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712613"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="81cf2-102">CorDebugGCType 列挙型</span><span class="sxs-lookup"><span data-stu-id="81cf2-102">CorDebugGCType Enumeration</span></span>

<span data-ttu-id="81cf2-103">ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。</span><span class="sxs-lookup"><span data-stu-id="81cf2-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81cf2-104">構文</span><span class="sxs-lookup"><span data-stu-id="81cf2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="81cf2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81cf2-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="81cf2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="81cf2-106">Members</span></span>  
  
|<span data-ttu-id="81cf2-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="81cf2-107">Member name</span></span>|<span data-ttu-id="81cf2-108">説明</span><span class="sxs-lookup"><span data-stu-id="81cf2-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="81cf2-109">ガベージコレクターはワークステーション上で実行されています。</span><span class="sxs-lookup"><span data-stu-id="81cf2-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="81cf2-110">ガベージコレクターはサーバーで実行されています。</span><span class="sxs-lookup"><span data-stu-id="81cf2-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81cf2-111">解説</span><span class="sxs-lookup"><span data-stu-id="81cf2-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81cf2-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="81cf2-112">Requirements</span></span>  

 <span data-ttu-id="81cf2-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81cf2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81cf2-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81cf2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81cf2-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81cf2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81cf2-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81cf2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81cf2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="81cf2-117">See also</span></span>

- [<span data-ttu-id="81cf2-118">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="81cf2-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
