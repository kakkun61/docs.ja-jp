---
title: ECLRAssemblyIdentityFlags 列挙型
ms.date: 03/30/2017
api_name:
- ECLRAssemblyIdentityFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECLRAssemblyIdentityFlags
helpviewer_keywords:
- ECLRAssemblyIdentityFlags enumeration [.NET Framework hosting]
ms.assetid: d1e0b654-ccaf-4fa2-9aa3-8e007813c84d
topic_type:
- apiref
ms.openlocfilehash: c3fed9166d95c0ca71ac44f5447b95eee97af310
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726835"
---
# <a name="eclrassemblyidentityflags-enumeration"></a><span data-ttu-id="160d5-102">ECLRAssemblyIdentityFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="160d5-102">ECLRAssemblyIdentityFlags Enumeration</span></span>

<span data-ttu-id="160d5-103">アセンブリの id の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="160d5-103">Indicates the type of an assembly's identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="160d5-104">構文</span><span class="sxs-lookup"><span data-stu-id="160d5-104">Syntax</span></span>  
  
```cpp  
typedef enum _CLRAssemblyIdentityFlags {  
    CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT = 0  
} ECLRAssemblyIdentityFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="160d5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="160d5-105">Members</span></span>  
  
|<span data-ttu-id="160d5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="160d5-106">Member</span></span>|<span data-ttu-id="160d5-107">説明</span><span class="sxs-lookup"><span data-stu-id="160d5-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT`|<span data-ttu-id="160d5-108">Id は正規化されます。</span><span class="sxs-lookup"><span data-stu-id="160d5-108">The identity is canonicalized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="160d5-109">要件</span><span class="sxs-lookup"><span data-stu-id="160d5-109">Requirements</span></span>  

 <span data-ttu-id="160d5-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="160d5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="160d5-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="160d5-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="160d5-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="160d5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160d5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="160d5-113">See also</span></span>

- [<span data-ttu-id="160d5-114">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="160d5-114">Hosting Enumerations</span></span>](hosting-enumerations.md)
