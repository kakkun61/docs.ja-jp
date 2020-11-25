---
title: COR_PUB_ENUMPROCESS 列挙型
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
ms.openlocfilehash: 30a522fbf96aebaa96f33f4a1dc381683f183871
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726419"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="2805c-102">COR_PUB_ENUMPROCESS 列挙型</span><span class="sxs-lookup"><span data-stu-id="2805c-102">COR_PUB_ENUMPROCESS Enumeration</span></span>

<span data-ttu-id="2805c-103">列挙するプロセスの型を識別します。</span><span class="sxs-lookup"><span data-stu-id="2805c-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2805c-104">構文</span><span class="sxs-lookup"><span data-stu-id="2805c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="2805c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2805c-105">Members</span></span>  
  
|<span data-ttu-id="2805c-106">メンバー名</span><span class="sxs-lookup"><span data-stu-id="2805c-106">Member name</span></span>|<span data-ttu-id="2805c-107">説明</span><span class="sxs-lookup"><span data-stu-id="2805c-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="2805c-108">マネージプロセス。</span><span class="sxs-lookup"><span data-stu-id="2805c-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2805c-109">注釈</span><span class="sxs-lookup"><span data-stu-id="2805c-109">Remarks</span></span>  

 <span data-ttu-id="2805c-110">アンマネージデバッグ API の現在のバージョンは、マネージプロセスのみを列挙します。</span><span class="sxs-lookup"><span data-stu-id="2805c-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2805c-111">要件</span><span class="sxs-lookup"><span data-stu-id="2805c-111">Requirements</span></span>  

 <span data-ttu-id="2805c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2805c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2805c-113">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="2805c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2805c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2805c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2805c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2805c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2805c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2805c-116">See also</span></span>

- [<span data-ttu-id="2805c-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="2805c-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
